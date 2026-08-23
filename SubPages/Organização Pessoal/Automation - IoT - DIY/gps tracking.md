---

---
[https://how2electronics.com/gps-gsm-based-vehicle-tracking-system-using-arduino/?s=09](https://how2electronics.com/gps-gsm-based-vehicle-tracking-system-using-arduino/?s=09)

![[海外轮播动图 2.gif]]

![[GPS-Vehicle-Tracking-System-Arduino-1080x607.jpg]]

Table of Contents

### **Overview: GPS Vehicle Tracking System Arduino**

In this project, we will learn about how to make **GPS & GSM Based Vehicle Tracking System using Arduino**. Most of the **vehicle tracking system** available in the market is too costly. So, I decided to make my own Tracking System. The vehicle tracking system will send you the **location** to your mobile phone along with the **Google map coordinate**. You can request the location at any time & view the location on Google Maps installed on your mobile phone.

This is a cheaper solution than a two-way GPS communication system where the communication is done in both ways with **GPS satellites**. This project uses only one GPS device and two-way communication is achieved using a **GSM modem**. The GSM modem with a 2G SIM card is used for communication between the device and mobile phone.

For this project, I have to select a proper **low power GSM & GPS Module**. So, I selected **A9G GSM/GPRS/GPS Module**. The device is very small and can fit anywhere & can be operated using a simple **3.7V Lithium-Ion Battery**. The Board has a 32-bit ATSAMD21 controller from Atmel which can be programmed using Arduino IDE. You can also make this project using **Neo-6M GPS Module** & **SIM 800/900 GSM Module** with Arduino UNO Board. But this will make the device size large. We will discuss in detail about this **Arduino GPS & GSM Based Vehicle Tracking System** .

If you want to make a GPS tracker using a 4G internet connection instead of 2G, you can use [**SIM7600 4G LTE**](https://how2electronics.com/using-sim7600-4g-gsm-with-arduino-at-commands-call-sms/) modem.

### **Bill of Materials**

The Arduino based GPS Tracker Project can be done in 2 ways. The first way is using a single integrated device that has a combined **GSM + GPS + Microcontroller**. The second way is using the different available GSM & GPS Modules available in the market along with the Arduino Board.

I prefer the first method due to the compact size, low power consumption, and faster response. You can buy the combined module from the following link.

| S.N. | Components Name | Description | Quantity | Purchase Links |
| --- | --- | --- | --- | --- |
| 1 | Maduino Zero Board | Maduino Zero GPRS/GPS A9G | 1 | [https://makerfabs.com/maduino-zero-a9g.html](https://makerfabs.com/maduino-zero-a9g.html) |
| 2 | Battery | 3.7V 1000 mah Lithium-Ion Battery | 1 | [**Amazon**](https://amzn.to/3I5GpLG) | [**AliExpress**](https://s.click.aliexpress.com/e/_DDpe3dd) |

If you want to make this **GPS tracker using Arduino** by the second method, you can buy the components separately and assemble on the breadboard or a PCB Board. All these components can be purchased from Amazon. The components purchase link is given below.

| S.N. | Components Name | Quantity | Purchase Links |
| --- | --- | --- | --- |
| 1 | Arduino UNO Board | 1 | [**Amazon**](https://amzn.to/3BcqtTh) | [**AliExpress**](https://s.click.aliexpress.com/e/_DCmitEX) |
| 2 | 16x2 LCD Display | 1 | [**Amazon**](https://amzn.to/3iKbKsD) | [**AliExpress**](https://s.click.aliexpress.com/e/_Dk3L5XH) |
| 3 | SIM800/900 GSM Module | 1 | [**Amazon**](https://amzn.to/3YyIh5c) | [**AliExpress**](https://s.click.aliexpress.com/e/_DCuL2gr) |
| 4 | Neo-6M GPS Module | 1 | [**Amazon**](https://amzn.to/3Wsx9Fu) | [**AliExpress**](https://s.click.aliexpress.com/e/_DCCGBjh) |
| 5 | Potentiometer 10K | 1 | [**Amazon**](https://amzn.to/3P7MF6Y) | [**AliExpress**](https://s.click.aliexpress.com/e/_DBWV9LV) |
| 6 | Connecting Jumper Wires | 10 | [**Amazon**](https://amzn.to/3F8fLhW) | [**AliExpress**](https://s.click.aliexpress.com/e/_DnqCpEJ) |
| 7 | Breadboard | 1 | [**Amazon**](https://amzn.to/3Bg68wE) | [**AliExpress**](https://s.click.aliexpress.com/e/_DnDCZk7) |

### **Maduino Zero A9G GPRS/GPS Board**

This is a low power **A9G GSM+GPS+GPRS** Module integrated with **32-bit Atmel’s SAMD21 Microcontroller**. Its front side and backside look something like this.

The developer of the A9G GSM GPS Module is **Ai-Thinker**. The module can be **programmed** via **micro USB Port** and can be powered via 3.7V Lithium-Ion Battery. It has a switch to turn ON & OFF. The digital Input-Output pins are there which can be used to connect any other modules or sensors.

Arduino has an 8-bit controller but it has a 32 bit Atmel [** ATSAMD21G18**](https://www.microchip.com/wwwproducts/en/ATsamd21g18) controller, which makes the device super fast. It has a voltage regulator IC to control the excess voltage. Similarly, there are two antennas, one is the **GSM Antenna** & another one the **GPS Antenna**. The signal problem is not seen in this module because of its best design. You can insert a micro sim here. Remember this is a 2G Modem only, so only 2G Sim can be used according to the **frequency band**. It also has a **Micro-SD** Port. You can also use an **SD Card** to save the data in text format.

The board doesn’t need any external DC Jack or higher power supply. It can be powered using a **3.7V, 100mah Lithium-Ion Battery**. There are two battery ports in the module, one port is for the Battery charging and the other for the Battery power supply. Once the battery is connected, you can slide the switch to turn on the device. Two LEDs are there which indicated the status of the power.

This board is assembled and manufactured by **Makerfabs**, one of the best startup companies in China. You can directly purchase this board from the following link.

If you want to learn the basic interfacing and how to use **AT Commands** with the A9G Module, you can follow the following previous projects below. Apart from that, you can also learn about the GPS Tracker Project along with SMS Project & Cellular IoT Connectivity.

**1. Basic A9G GPRS/GSM Module Arduino Tutorial:** [**Check Here**](https://how2electronics.com/a9g-gsm-gprs-gps-module-with-arduino/)**2. GPS Tracker using Arduino & A9G:** [**Check Here**](https://how2electronics.com/gps-tracker-using-a9g-gprs-gps-module-arduino/)**3. Cellular IoT using Arduino & A9G:** [**Check Here**](https://how2electronics.com/internet-with-a9g-low-power-gprsgps-module-arduino/)

Now let us move towards our main project, i.e. GPS+GSM Based Vehicle Tracking System using Arduino.

### **GPS+GSM Based Vehicle Tracking System using Arduino**

You don’t need any external hardware part except connecting the Battery. All the documentation part is explained above. Now let us set up directly to the Arduino IDE setup part.

The Arduino IDE doesn’t have any pre-installed support for **SAMD Board**. So you need to add the Board first to the Arduino IDE. So, go to the board manager and search for Arduino Zero.

So here is the **32 bit ARM Cortex Board**. You can install this board.

On the hardware part, connect the micro USB cable to the Maduino Zero Board. And also connect the other end to the computer USB port.

Now go to the tools, here you will find the Arduino SAMD Board. So from the list select the **Arduino Zero Native USB Port**. Also from the list select the com port.

### **Source Code/Program**

So, you can see the program here. It is a little bit different compared to other GSM GPS Module & Arduino Boards. The AT Command **AT+GPS=1 **will turn on the GPS of the board. Similarly,** AT+LOCATION =2** will retrieve the GPS Location as Latitude & Longitude Code.

Copy the complete code and upload it to the Arduino Zero Board.

| 123456789101112131415161718192021222324252627282930313233343536373839404142434445464748495051525354555657585960616263646566676869707172737475767778798081828384858687888990919293949596979899100101102103104105106107108109110111112113114115116117118119120121122123124125126127128129130131132133134135136137138139140141142143144145146147148149150151152153154155156157158159160161162163164165166167168169170171172173174175176177178179180181182183184185186187188189190191192193194195196197198199200201202203204 | #include<string.h>#define DEBUG trueint PWR_KEY = 9;int RST_KEY = 6;int LOW_PWR_KEY = 5;String msg = String("");int SmsContentFlag = 0;String mob;String loct;void setup(){pinMode(PWR_KEY, OUTPUT);pinMode(RST_KEY, OUTPUT);pinMode(LOW_PWR_KEY, OUTPUT);digitalWrite(RST_KEY, LOW);digitalWrite(LOW_PWR_KEY, HIGH);digitalWrite(PWR_KEY, HIGH);// String msg = String("");// int SmsContentFlag = 0;SerialUSB.begin(115200);Serial1.begin(115200);//modulePowerOn();delay(2000);SerialUSB.println("Checking Module...");int i = 1;String res;while (i) {Serial1.println("AT");while (Serial1.available() > 0) {if (Serial1.find("OK"))i = 0;}delay(500);}SerialUSB.println("Module Connected");//GprsTextModeSMS();SerialUSB.print("Text Mode: ");i = 1;while (i) {Serial1.println("AT+CMGF=1\r");while (Serial1.available() > 0) {if (Serial1.find("OK"))i = 0;}delay(500);}SerialUSB.println("ON");Serial1.println("AT+GPS=1");SerialUSB.println("GPS Intializing...");delay(5000);SerialUSB.println("GPS Initialized");SerialUSB.flush();i = 1;String str;while (i) {Serial1.println("AT+LOCATION=2");delay(100);while (Serial1.available() <= 0);if (Serial1.find("AT+LOCATION=2")) {str = Serial1.readString();//SerialUSB.println(str);i = 0;}delay(500);}loct = str.substring(4, 23);SerialUSB.print("Location: ");SerialUSB.println(loct);//while(1);SerialUSB.println("Send sms to get the location");}void loop(){char SerialInByte;if (Serial1.available()){//char SerialInByte;SerialInByte = (unsigned char)Serial1.read();if ( SerialInByte == 13 ) //0x0D{ProcessGprsMsg();}if ( SerialInByte == 10 ){}else{//EN: store the current character in the message string buffermsg += String(SerialInByte);}}if (SmsContentFlag == 1) {int i;SerialUSB.println("Flag Cleared");SerialUSB.print("Message: ");SerialUSB.println(msg);if (msg.indexOf("Location")) {SerialUSB.println("Message Received");i = msg.indexOf("+91");//SerialUSB.print("index: ");//SerialUSB.println(i);//SerialUSB.println(msg[i+1]);i = i + 3;for (int j = 0; j < 10; j++, i++) {mob += msg[i];}SerialUSB.print("Mobile: ");SerialUSB.println(mob);String cmd = "AT+CMGS=\"";cmd += mob;cmd += "\"";cmd += "\r";Serial1.println(cmd);delay(100);Serial1.print("Your Vehicle Current Location ");Serial1.print(loct);Serial1.print("\n");Serial1.print("Check Map: \n");Serial1.print(" https://www.google.com/maps/@");Serial1.println(loct);Serial1.println((char)26);delay(1000);}ClearGprsMsg();SmsContentFlag = 0;msg.remove(0);mob.remove(0);}delay(100);}// EN: Request Text Mode for SMS messagingvoid GprsTextModeSMS(){Serial1.println( "AT+CMGF=1" );}void GprsReadSmsStore( String SmsStorePos ){// Serial.print( "GprsReadSmsStore for storePos " );// Serial.println( SmsStorePos );Serial1.print( "AT+CMGR=" );Serial1.println( SmsStorePos );}// EN: Clear the GPRS shield message buffervoid ClearGprsMsg(){msg = "";}// EN: interpret the GPRS shield message and act appropiatelyvoid ProcessGprsMsg(){SerialUSB.println("");// Serial.print( "GPRS Message: [" );SerialUSB.print( msg );// Serial.println( "]" );if ( msg.indexOf( "Call Ready" ) >= 0 ){SerialUSB.println( "*** GPRS Shield registered on Mobile Network ***" );GprsTextModeSMS();}//EN: unsolicited message received when getting a SMS messageif ( msg.indexOf( "+CIEV" ) >= 0 ){SerialUSB.println( "*** SMS Received ***" );}//EN: SMS store readed through UART (result of GprsReadSmsStore request)if ( msg.indexOf( "+CMT:" ) >= 0 ){// EN: Next message will contains the BODY of SMSSmsContentFlag = 1;// EN: Following lines are essentiel to not clear the flag!//ClearGprsMsg();return;}// EN: +CMGR message just before indicate that the following GRPS Shield message// (this message) will contains the SMS bodyif ( SmsContentFlag == 1 ){SerialUSB.println( "*** SMS MESSAGE CONTENT ***" );SerialUSB.println( msg );SerialUSB.println( "*** END OF SMS MESSAGE ***" );//ProcessSms( msg );}/*ClearGprsMsg(); //EN: Always clear the flag SmsContentFlag = 0; */} |
| --- | --- |

### **Working of the Arduino GPS+GSM Vehicle Tracking**

After uploading the code, open the **Serial Monitor**. The Serial Monitor will display the initialization message. If the location is fixed Serial Monitor will display the **Latitude** and **Longitude**. If the location is still not retrieved, the Serial Monitor will still display **Checking Module**.

Now you can send the **SMS** to get the Location. So, on your mobile phone open the messaging app and then enter the phone number of the SIM used in the Arduino Zero board. After that, type the word **“Location”**, and then simply send it.

Within a while, the Serial Monitor will display the **message received status** and also tells about the date time, and mobile number. Similarly, you will [**receive an SMS**](https://www.receivesms.co/) on your mobile phone with the **Latitude Longitude coordinate**. Along with the coordinate, you will receive a link to **google maps**. You can click the link and open it either using google maps or using a Chrome browser.

So, you can see it’s pointing to the same location where I am right now. This is really a great project and can be implemented in your vehicles for a **vehicle tracking project**. It can be used for controlling the theft of the vehicle. Or it can be used in finding the location of someone who is using your vehicle.

### **Arduino based GPS Tracker Project using SIM800/900 & NEO-6M GPS Module**

The same project can be done using **Arduino UNO Board, SIM900 or SIM800 GSM Module**, and also **NEO-6M GPS Tracker Module**. An extra LCD is also added to the circuit for displaying the status.

### **Source Code/Program**

Here is the Source for the above circuit that is based on SIM800/900 GSM Module & NEO-6M GPS Module. This code a little bit smaller and requires a little modification like replacing a mobile phone number. Thus, **GPS Based Vehicle Tracking System using Arduino** can be easily tested.

| 123456789101112131415161718192021222324252627282930313233343536373839404142434445464748495051525354555657585960616263646566676869707172737475767778798081828384858687888990919293949596979899100101102103104105106107108109110111112113114115116117118119120121122123124125126127128129130131132133134135136137138139140141142143144145146147148149150151152153154155156157158159160161162163164165166167168169170171172173174175176177178 | #include <TinyGPS++.h>#include <SoftwareSerial.h>#include<LiquidCrystal.h>LiquidCrystal lcd(13, 12, 11, 10, 9, 8);static const int RXPin = 4, TXPin = 3;static const uint32_t GPSBaud = 9600;// The TinyGPS++ objectTinyGPSPlus gps;int temp=0,i;// The serial connection to the GPS deviceSoftwareSerial ss(RXPin, TXPin);String stringVal = "";void setup(){Serial.begin(9600);ss.begin(GPSBaud);lcd.begin(16,2);pinMode(13,OUTPUT);digitalWrite(13,LOW);lcd.print("Vehicle Tracking");lcd.setCursor(0,1);lcd.print(" System ");delay(2000);gsm_init();lcd.clear();Serial.println("AT+CNMI=2,2,0,0,0");lcd.print("GPS Initializing");lcd.setCursor(0,1);lcd.print(" No GPS Range ");delay(2000);lcd.clear();lcd.print("GPS Range Found");lcd.setCursor(0,1);lcd.print("GPS is Ready");delay(2000);lcd.clear();lcd.print("System Ready");temp=0;}void loop(){serialEvent();while(temp){while (ss.available() > 0){gps.encode(ss.read());if (gps.location.isUpdated()){temp=0;digitalWrite(13,HIGH);tracking();}if(!temp)break;}}digitalWrite(13,LOW);}void serialEvent(){while(Serial.available()>0){if(Serial.find("Track Vehicle")){temp=1;break;}else{temp=0;}}}void gsm_init(){lcd.clear();lcd.print("Finding Module..");boolean at_flag=1;while(at_flag){Serial.println("AT");delay(1);while(Serial.available()>0){if(Serial.find("OK"))at_flag=0;}delay(1000);}lcd.clear();lcd.print("Module Connected..");delay(1000);lcd.clear();lcd.print("Disabling ECHO");boolean echo_flag=1;while(echo_flag){Serial.println("ATE0");while(Serial.available()>0){if(Serial.find("OK"))echo_flag=0;}delay(1000);}lcd.clear();lcd.print("Echo OFF");delay(1000);lcd.clear();lcd.print("Finding Network..");boolean net_flag=1;while(net_flag){Serial.println("AT+CPIN?");while(Serial.available()>0){if(Serial.find("+CPIN: READY"))net_flag=0;}delay(1000);}lcd.clear();lcd.print("Network Found..");delay(1000);lcd.clear();}void init_sms(){Serial.println("AT+CMGF=1");delay(400);Serial.println("AT+CMGS=\"850xxxxxxx\""); // use your 10 digit cell no. heredelay(400);}void send_data(String message){Serial.print(message);delay(200);}void send_sms(){Serial.write(26);}void lcd_status(){lcd.clear();lcd.print("Message Sent");delay(2000);lcd.clear();lcd.print("System Ready");return;}void tracking(){init_sms();send_data("Vehicle Tracking Alert:");Serial.println(" ");send_data("Your Vehicle Current Location is:");Serial.println(" ");Serial.print("Latitude: ");Serial.print(gps.location.lat(), 6);Serial.print("\n Longitude: ");Serial.println(gps.location.lng(), 6);// https://www.google.com/maps/@8.2630696,77.3022699,14zSerial.print("https://www.google.com/maps/@");Serial.print(gps.location.lat(), 6);Serial.print(',');Serial.print(gps.location.lng(), 6);Serial.print(",14z");send_sms();delay(2000);lcd_status();} |
| --- | --- |

### **Video Tutorial & Guide**

An advanced version of GPS Tracker project could be [**Geofencing**](https://how2electronics.com/geo-fence-with-gps-module-nodemcu-esp8266/) project. Geofencing is a location-based service in which gives information of a virtual boundary set up around a geographical location, known as a geofence.