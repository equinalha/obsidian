---

---
> [!tip] 💡
> In order to setup your Arduino IDE to work with your esp8266 arduino compatible module you need to make the following steps:
> 1. Connect your ESP8266-01 Module to PC
> 2. Open your Arduino IDE
> 3. Go to File -> Preferences
> 4. Add this link to Additional Board Manager
> 5. Go to Tools -> Board Manager
> 6. Find ESP8266 board set and activate it
> 7. Select Generic ESP8266 board from Tools->Boards
> 8. Choose your programmer COM port
> 9. You are ready to go!

![[SubPages/Pessoal/images/Untitled 35.png]]

Biblioteca para comunicação com Alexa

 https://github.com/vintlabs/fauxmoESP 

![[SubPages/Pessoal/images/Untitled 36.png|Operação do ESP01 / Evitando acionamento indevido do relé com um capacitor]]

[http://www.forward.com.au/pfod/ESP8266/GPIOpins/index.html](http://www.forward.com.au/pfod/ESP8266/GPIOpins/index.html)

## Capacitive Touch button simulating

EDIT: Nevermind, I made a small change in your script and it's now working without the need for an external transistor. I just set the pin to LOW in the setup and only toggled the pinMode in the loop like this:

```plain text
void setup() {
  // put your setup code here, to run once:
  pinMode(2, OUTPUT); //internal LED for keeping track
  digitalWrite(32, LOW); //connected to capacitive pin on air purifier
}

void loop() {
  // put your main code here, to run repeatedly:
  digitalWrite(2, HIGH);
  pinMode(32, INPUT);
  delay(3000);
  digitalWrite(2, LOW);
  pinMode(32, OUTPUT);
  delay(3000);
}
```