---

---
# **MODULE 1: Getting Started with the Raspberry Pi**

This Module is a quick introduction to the Raspberry Pi. You’ll set up your Raspberry Pi for the first time: install the operating system and establish an SSH connection with your Pi using your computer.

![[Smart_home_module_1.jpg]]

- **1.1** Introducing the Raspberry Pi
- **1.2** Installing the Operating System
- **1.3** Connecting via SSH to the RPi

---

# **MODULE 2: Getting Started with Node-RED**

In this Module, you’ll get started with Node-RED software on the Raspberry Pi. You’ll install Node-RED, learn some basic concepts, and create simple flows to control the Raspberry Pi GPIOs. You’ll also learn about Node-RED dashboard, a set of nodes to easily create a user interface.

![[Smart_home_module_2.jpg]]

- **2.1** Node-RED Introduction
- **2.2** Installing Node-RED
- **2.3** Node-RED Overview
- **2.4** Node-RED Dashboard
- **2.5** Controlling an LED with Node RED

---

# **MODULE 3: Getting Started with MQTT**

This section is an introduction to the MQTT protocol. MQTT stands for Message Queuing Telemetry Transport, a simple messaging protocol suitable for communication between IoT devices. Learn MQTT basic concepts, install an MQTT broker and create a simple publish/subscribe flow.

![[Smart_home_module_3.jpg]]

- **3.1** Introducing MQTT
- **3.2** Installing Mosquitto Broker
- **3.3** MQTT with Node-RED

---

# **MODULE 4: Introducing the ESP32 and ESP8266 Boards**

This Module is a quick introduction to the ESP32 and ESP8266 boards. We’ll take a quick look at its features, specifications, and pinout. We’ll also show you how to program your boards using Arduino IDE.

![[Smart_home_module_4.jpg]]

- **4.1** Introducing the ESP8266
- **4.2** Introducing the ESP32
- **4.3** Installing Arduino IDE
- **4.4** Testing the Installation

---

# **MODULE 5: Connecting the ESP32/ESP826 with Node-RED (MQTT)**

In this Module, you’ll learn how to program your ESP32 and ESP8266 boards to connect to your broker to publish messages and subscribe to topics. This way, we’ll be able to establish a communication between the ESP boards and Node-RED using MQTT. You’ll learn how to control the ESP outputs using Node-RED dashboard and to display sensor readings published by your boards.

![[Smart_home_module_5.jpg]]

- **5.1** Connect the ESP32/ESP8266 with Node-RED (Introduction)
- **5.2** Publish and Subscribe (Basic Example)
- **5.3** Publish Sensor Readings
- **5.4** Subscribe to Multiple Topics and Control Multiple Outputs

---

# **MODULE 6: InfluxDB Time-Series Database**

InfluxDB is a time-series database. Each record on the database is associated with a timestamp, which makes it ideal for data logging, IoT, and home automation projects. InfluxDB also provides dashboard tools to visualize data in different formats like charts, gauges, histograms, etc. You can easily connect Node-RED to InfluxDB and save your readings on the database and use their dashboard to analyze the data in many different formats.

![[Smart_home_module_6.jpg]]

- **6.1** Getting Started with InfluxDB
- **6.2** Install InfluxDB (Raspberry Pi)
- **6.3** Monitoring your Raspberry Pi using InfluxDB Telegraf
- **6.4** MQTT + Node-RED + InfluxDB
- **6.5** Monitoring GPIO States on InfluxDB
- **6.6** Get Data from InfluxDB
- **6.7** Delete InfluxDB Data

---

# **MODULE 7: Sending Notifications with Node-RED**

In this Module, you’ll learn how to send notifications with Node-RED. We’ll show you how to send emails, Telegram messages, and WhatsApp messages. We’ll also create a simple project to send the notification of your choice whenever motion is detected.

![[Smart_home_module_7.jpg]]

- **7.1** Email Alerts with Node-RED
- **7.2** Telegram Messages with Node-RED
- **7.3** WhatsApp Messages with Node-RED
- **7.4** Motion Detector with Notifications

---

# **MODULE 8: Adding Rules and Triggering Events**

In this Module, you’ll learn how to automatically set all GPIOs to a defined state using master switches and modes. You’ll also learn how to trigger events when something happens (a notification, a threshold value, etc.) Finally, you’ll learn how to set timers and schedule events.

![[Smart_home_module_8.jpg]]

- **8.1** Creating Master Switches or Modes
- **8.2** Trigger Events Based on Threshold Values
- **8.3** Triggering Time-based Events
- **8.4** Time-based Events with Big Timer

---

# **MODULE 9: Accessing Your Local System from Anywhere**

This Module explains how to set up a Cloudflare tunnel to access your Node-RED home automation system and InfluxD monitoring dashboards from anywhere.

![[Smart_home_module_9.jpg]]

- **9.1** Accessing Your System from Anywhere

---

# **MODULE 10: Creating a Cloud Server**

If you don’t have a Raspberry Pi to follow along, you can create your system on the cloud. We provide instructions for installing Node‑RED, InfluxDB, and Mosquitto broker on Digital Ocean (hosting).

![[Smart_home_module_10.jpg]]

- **10.1** Introducing Digital Ocean
- **10.2** Installing Node-RED on the Cloud
- **10.3** Installing Mosquitto MQTT Broker on the Cloud
- **10.4** Installing InfluxDB on the Cloud

---

# **MODULE 11: Setting up a Surveillance Camera**

In this section, you’ll learn how to add an ESP32-CAM surveillance camera to your Node-RED home automation system. The ESP32-CAM is a development board with an ESP32-S chip, an OV2640 camera, microSD card slot and several GPIOs to connect peripherals.

![[MODULE_11_Thumbnail.jpg]]

- **11.1** Introducing the ESP32-CAM
- **11.2** ESP32-CAM Video Streaming
- **11.3** Surveillance Camera on Node-RED

---

# **APPENDIX**

This section provides additional information that might be useful like executing commands on the Raspberry Pi using Node-RED and a quick guide with Linux commands.

![[Smart_home_appendix.jpg]]

- Sending Linux Commands Through Node-RED UI
- Learning Basic Linux Commands