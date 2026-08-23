---

---
We are setting up the access point SSID/password.

```plain text
const char* ssid     = "ESP8266-Access-Point";
const char* password = "123456789";
```

The HTML page to return on server access:

```plain text
const char index_html[] PROGMEM = R"rawliteral(
<!DOCTYPE HTML>
<html>
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <style>
      html {
        font-family: Arial;
        display: inline-block;
        margin: 0px auto;
        text-align: center;
      }
      h2 {
        font-size: 3.0rem;
      }
      p {
        font-size: 3.0rem;
      }
      .units {
        font-size: 1.2rem;
      }
      .input {
        font-size: 20px;
        margin-bottom: 10px;
      }
      .wifi-form {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-around;
      }
    </style>
  </head>
  <body>
    <div class="wifi-form">
      <h1>Test</h1>
      <input id="ssid" class="input" type="text" maxlength="32">
      <input id="password" class="input" type="password">
      <button onclick="connectToWifi()">Connect</button>
    </div>
  </body>
  <script>
    function connectToWifi() {
      var ssid = document.getElementById("ssid").value;
      var password = document.getElementById("password").value;
      var xhr = new XMLHttpRequest(); xhr.open("POST", "/", true);
      xhr.setRequestHeader('Content-Type', 'application/json');
      xhr.send(ssid + ":" + password);
    }
  </script>
</html>)rawliteral";
```

It's a simple form asking you for your SSID and password to your local wifi. **connectToWifi **function will send the data back to the server POST request. Let's set up the server that will handle those requests.

Add this as a global variable.

```plain text
AsyncWebServer server(80);
```

Create an access point function.

```plain text
void createAccessPoint() {
  WiFi.softAP(ssid, password);
  IPAddress IP = WiFi.softAPIP();
  Serial.print("AP IP address: ");
  Serial.println(IP);
  // Print ESP8266 Local IP Address
  Serial.println(WiFi.localIP());
  server.on("/", HTTP_GET, [](AsyncWebServerRequest *request) {
    request->send_P(200, "text/html", index_html);
  });
  server.on("/", HTTP_POST, [](AsyncWebServerRequest *request){},NULL, [](AsyncWebServerRequest *request, uint8_t *data, size_t len, size_t index, size_t total) {
    ssidWifi = "";
    passwordWifi = "";
    String res((char *)data);
    int sepIndex = -1;
    for (int i = 0; i < len; ++i) {
      if (res[i] != ':') {
        if (sepIndex == -1) {
          ssidWifi.concat(res[i]);
        }
        if (i > sepIndex && sepIndex != -1) {
          passwordWifi.concat(res[i]);
        }
      }
      else {
        sepIndex = i;
      }
    }
    writeEEPROM(ssidWifi, ssidIndex);
    writeEEPROM(passwordWifi, passwordIndex);
    request->send(200, "text/plain", "SUCCESS");
  });
  server.begin();
}
```

Let's go through this.

```plain text
WiFi.softAP(ssid, password);
```

This creates an access point with SSID and password passed and the beginning.

```plain text
IPAddress IP = WiFi.softAPIP();
Serial.print("AP IP address: ");
Serial.println(IP);
// Print ESP8266 Local IP Address
Serial.println(WiFi.localIP());
```

Logging part. It is needed for debugging.

```plain text
server.on("/", HTTP_GET, [](AsyncWebServerRequest *request) {
    request->send_P(200, "text/html", index_html);
});
```

Handles HTTP GET requests and returns our HTML page.

```plain text
server.on("/", HTTP_POST, [](AsyncWebServerRequest *request){},NULL, [](AsyncWebServerRequest *request, uint8_t *data, size_t len, size_t index, size_t total) {
    ssidWifi = "";
    passwordWifi = "";
    String res((char *)data);
    int sepIndex = -1;
    for (int i = 0; i < len; ++i) {
      if (res[i] != ':') {
        if (sepIndex == -1) {
          ssidWifi.concat(res[i]);
        }
        if (i > sepIndex && sepIndex != -1) {
          passwordWifi.concat(res[i]);
        }
      }
      else {
        sepIndex = i;
      }
    }
    writeEEPROM(ssidWifi, ssidIndex);
    writeEEPROM(passwordWifi, passwordIndex);
    request->send(200, "text/plain", "SUCCESS");
  });
```

The  above code handles the post request. We need to add the fifth parameter  as an AsyncWebServer request to take the body. The algorithm is pretty simple. Clear saved ssidWifi and passwordWifi, which are global variables. Parse SSID:password in such format and save data to EEPROM. Afterward, we start the server. ssidIndex equals 0, and it is the start address of data. passwordIndex  equals 33 because SSID max length is 32 bytes, and one byte is reserved  for the length of the string. You'll see it in the writeEEPROM  function:

```plain text
void writeEEPROM(String value, int address) {
  int len = value.length();
  EEPROM.put(address, len);
  for (int i = address + 1; i < len + address + 1; ++i) {
    EEPROM.put(i, value[i - address - 1]);
  }
  EEPROM.commit();
}
```

Now we need to be able to read that data from EEPROM:

```plain text
String readEEPROM(int address) {
  uint8_t len = EEPROM.read(address);
  if (len == 255) return "";
  String res;
  for (int i = address + 1; i < len + address + 1; ++i) {
    char c = (char)EEPROM.read(i);
    res.concat(c);
  }
  return res;
}
```

255  -> means empty data. Here we're getting the first byte assigned to  the data length that proceeds afterward, reads that data, and returns the result.

Now we have everything to wrap it all together.

```plain text
void setup() {
  Serial.begin(9600);
  EEPROM.begin(128);
  ssidWifi = readEEPROM(ssidIndex);
  passwordWifi = readEEPROM(passwordIndex);
  if (ssidWifi.length() > 0 && passwordWifi.length() > 0 && WiFi.status() != WL_CONNECTED) {
    WiFi.softAPdisconnect(true);
    server.end();
    WiFi.begin(ssidWifi, passwordWifi);
    while (WiFi.status() != WL_CONNECTED) {
      delay(1000);
    }
  }
  else
  {
    createAccessPoint();
  }
}void loop() {
  if (ssidWifi.length() > 0 && passwordWifi.length() > 0 && WiFi.status() != WL_CONNECTED) {
    WiFi.softAPdisconnect(true);
    server.end();
    WiFi.begin(ssidWifi, passwordWifi);
    while (WiFi.status() != WL_CONNECTED) {
      delay(1000);
    }
  }
}
```

That's  it. We have a working system that starts a server with a webpage where you can set your wifi credentials without needing to hardcode that.