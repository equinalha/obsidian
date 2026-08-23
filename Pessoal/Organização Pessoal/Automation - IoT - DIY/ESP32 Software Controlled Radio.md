---

---
[https://www.cnx-software.com/2023/01/25/socorad32-esp32-walkie-talkie-board-also-supports-data-communication-crowdfunding/?s=09](https://www.cnx-software.com/2023/01/25/socorad32-esp32-walkie-talkie-board-also-supports-data-communication-crowdfunding/?s=09)

SOCORAD32, aka ESP**32** **So**ftware **Co**ntrolled **Rad**io, is a hackable, open-source hardware ESP32-based amateur radio board for walkie-talkie and data communication applications.

The board comes with an ESP32 module with WiFi 4 and Bluetooth connectivity, an RDA Microelectronics RDA1846 RF IC used in many commercial walkie-talkies and offering a range up of to 5 km, a small display, a speaker, and a 18650 battery holder.

[SOCORAD32 ESP32 Walkie-Talkie board](https://cdn.cnx-software.com/wp-content/uploads/2023/01/SOCORAD32-ESP32-Walkie-Talkie-board.jpg?lossy=0&strip=none&ssl=1)

![[SOCORAD32-ESP32-Walkie-Talkie-board.jpg]]

SOCORAD32 specifications:

- Microcontroller module – [ESP32-WROOVER-32E](https://www.cnx-software.com/2022/01/30/wappstobit-go-esp32-board-sensors-microbit-compatibility/) with ESP32 dual-core microcontroller, 4MB flash, 2.4 GHz WiFi and Bluetooth connectivity, built-in PCB antenna
- Walkie-talkie chip – RDA1846 single-chip transceiver for Walkie-Talkie applications (See [datasheet and programming guide](https://github.com/phishman/RDA1846/tree/master/Datasheets) for details) 
	- Frequency Range: ISM 400 – 470 MHz
	- Frequency Step: 5 K / 6.25 K / 12.5 K / 25 K
	- RF Output Power: 2 W / 0.5 W (+5 KM @ 2 W) set to what the local law permits
	- RF Input Sensitivity: -122 dBm
	- Voice Scrambling: 8 type
	- Voice Compression & Expansion
	- SMS Exchange: Send and receive SMS (or, for IoT, send and receive data)
	- CTCSS (38 group) + CDCSS (83 group)
	- Automatic Tail Elimination – Eliminates the squelch burst often heard at the end of transmission as the PTT is released
	- Volume: Adjustable speaker output (1-8)
	- Squelch level adjustable (0-9)
	- MIC sensitivity level adjustable (1-8)
	- Sleep mode: 0.1μA
	- External antenna
- Display – OLED display
- Audio – Speaker, built-in microphone
- USB – Micro USB port for control, programming, and charging
- Expansion – 12-pin ESP32 I/O header
- Misc – 2x Volume/Channel buttons, Enable and Reset buttons, and 2x LEDs
- Battery – 16850 battery holder

[ESP32 Walkie-Talkie 5km range](https://cdn.cnx-software.com/wp-content/uploads/2023/01/ESP32-Talkie-Walkie-5km-range.jpg?lossy=0&strip=none&ssl=1)

![[ESP32-Talkie-Walkie-5km-range.jpg]]

The SOCORAD32 can be controlled through AT commands to configure the audio volume, tone squelching, CTCSS, CDSS codes, and more. Here are some examples:

To turn on voice-operated exchange (VOX) where X is the sensitivity level (1-8).

To control speaker volume where X is the loudness level (1-8).

To change communication parameters where RFV = receive frequency, TFV = transmit frequency, RXCT = CTCSS/CDCSS coding, TXCT = CTCSS/CDCSS transmit coding, Flag = busy locking/band setting (narrow or wide), and Flag1 = transmit power settings high (2 W) or low (0.5 W). Example:

You’ll find the AT command set and some basic code (Arduino sketch to set the ESP32 as a Bluetooth serial device) [on GitHub](https://github.com/MordFIdel/SOCORAD32). Besideswalkie-talkie applications, the SOCORAD32 board could be used as an Intercom, a Pager, a voice-activated audio monitor, and for long-range IoT applications, as well as amateur radio experimentation.

Made by Mord Technologies in Nigeria, the SOCORAD32 board has [just launched on Crowd Supply](https://www.crowdsupply.com/mord-technologies/socorad32) with a $5,600 funding goal that’s almost reached. There’s a single reward with the SOCORAD32 controller offered with a speaker and an antenna with a pledge of $80 plus $8 for shipping to the US and $18 to the rest of the world. You’d just need a 18650 battery to get started, and you’ll probably want to get two boards although the SOCORAD32 can be programmed to be compatible with commercial walkie-talkies.