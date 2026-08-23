---

---
[https://how2electronics.com/dark-activated-automatic-evening-lamp-ldr-555/?s=09](https://how2electronics.com/dark-activated-automatic-evening-lamp-ldr-555/?s=09)

![[海外轮播动图 4.gif]]

![[Dark-Activated-Automatic-Evening-Lamp-LDR-555-1080x446.jpg]]

In this mini electronics project we learn how to make Dark Activated 220V Automatic Evening Lamp using LDR & 555 Timer IC.

- [Overview](https://how2electronics.com/dark-activated-automatic-evening-lamp-ldr-555/?s=09#Overview)
- [Bill of Materials](https://how2electronics.com/dark-activated-automatic-evening-lamp-ldr-555/?s=09#Bill_of_Materials)
- [Circuit Diagram of Dark Activated Lamp using 555 & LDR](https://how2electronics.com/dark-activated-automatic-evening-lamp-ldr-555/?s=09#Circuit_Diagram_of_Dark_Activated_Lamp_using_555_LDR)
	- [1. Power supply Unit](https://how2electronics.com/dark-activated-automatic-evening-lamp-ldr-555/?s=09#1_Power_supply_Unit)
	- [2. Control unit](https://how2electronics.com/dark-activated-automatic-evening-lamp-ldr-555/?s=09#2_Control_unit)
	- [3. Switching unit](https://how2electronics.com/dark-activated-automatic-evening-lamp-ldr-555/?s=09#3_Switching_unit)
- [Circuit Simulation](https://how2electronics.com/dark-activated-automatic-evening-lamp-ldr-555/?s=09#Circuit_Simulation)

### **Overview**

The Automatic Evening Lamp circuit gets activated when the sun starts setting as light level drops. Thus it is called a Dark Activated Lamp & made using [555 Timer IC](https://how2electronics.com/555-timer-ic-features-pinout-working-circuit-operating-modes/) configured in Bi-Stable Mode. This can be used in automatic street light projects or can be used for House or Small Farm. The circuit is made using 555 Timer IC & Light Dependent Resistor (LDR). The bulb used in the circuit is turn on automatically in low light (evening) and turn off in the morning.

The LDR (Light-dependent resistor) or photoresistor is used to sense the Light. When the daylight or room lamp light falls on the surface of the LDR its resistance decreases hence the 555 IC makes the Bulb off. At night time when there is no light on the surface of the LDR the resistance of LDR increases due to which the 555 IC activates the light.

You can check one of our previous projects: [Automatic Street Light using 555 Timer Circuit](https://how2electronics.com/automatic-street-light-using-555-timer-circuit/)

### **Bill of Materials**

Following are the components required for learning this tuorial practically.

| S.N. | Components | Description | Quantity |
| --- | --- | --- | --- |
| 1 | Resistor | 220 Ω, 1W | 2 |
| 2 | Resistor | 470 KΩ | 3 |
| 3 | Resistor | 1 KΩ | 3 |
| 4 | Capacitor | 1 µF, 400V | 2 |
| 5 | Capacitor | 470 µF, 16V Electrolytic | 1 |
| 6 | Capacitor | 10nF Ceramic Disk | 1 |
| 7 | Capacitor | 10 µF, 16V (Electrolytic Capacitor) | 1 |
| 8 | Diode | 1N4007 | 5 |
| 9 | LED | 5mm Any Color | 2 |
| 10 | Transistor | BC547 | 1 |
| 11 | LDR |   | 1 |
| 12 | 555 Timer IC | NE555 | 1 |
| 13 | Relay Module | 5V | 1 |
| 14 | Bulb | 220V, 60W | 1 |

### **Circuit Diagram of Dark Activated Lamp using 555 & LDR**

The Dark Activated Lamp circuit is designed using readily available components like timer IC 555, an LDR, resistors, capacitors, diode and transistor.

The circuit can be divided into 3 different unit, i.e
 1. Power supply Unit
 2. Control unit
 3. Switching unit

### **1. Power supply Unit**

The power supply unit is designed using resistors, capacitors, and bridge rectifier diode. The two capacitors C1 and C2 are used to drop the mains voltage up to the desired level. Similarly resistors R1 and R2 are used as current limiters which protect the circuit from instant high current. Resistors R3 and R4 connected parallel to capacitor C1 and C2 discharge the capacitor when power is off.

The low voltage output of capacitor C1 and C2 is changed to DC voltage using a bridge rectifier circuit built around rectifier diode 1N4007. This rectified output is filtered using capacitor C3. The LED indicates the power status of the circuit whether its turned on or not.

### **2. Control unit**

The control unit for Dark Activated Lamp is designed 555 Timer IC and LDR. The timer IC 555 is configured in bi-stable mode. To learn more about the 555 Timer Working Mode, you can refer to [LM555 Datasheets](https://www.ti.com/lit/ds/symlink/lm555.pdf?ts=1588677840130). The trigger & threshold pin is connected to the output of LDR. The R6 resistor adjusts the sensitivity of LDR. It can be changed to a higher value for better results. The threshold and trigger of 555 Timer IC is controlled with LDR and a 470K Resistor.

When LDR offers low resistance the threshold of IC 555 becomes high as a reset the internal flipflop reset and output become low. When LDR offers high resistance the threshold of IC 555 becomes low as a result the internal flip fop sets and output become high. The output of the 555 Timer IC is available at pin 3.

### **3. Switching unit**

The switching circuit is designed using a 5V relay and transistor Q1. When the output of 555 is high Transistor Q1 starts to conduct as a result the relay energized. The energized relay switch on the Bulb till the resistor of LDR become low.

When the daylight or room lamp light falls on the surface of the LDR its resistance decreases hence the 555 IC makes the Bulb off. At night time when there is no light on the surface of the LDR the resistance of LDR increases due to which the 555 IC activates the light.

### **Circuit Simulation**

The circuit can be simulated using Proteus Software. The below circuit simulated gives the perfect output on the Oscilloscope. You can change the value of resistors to observer the change in the waveform.