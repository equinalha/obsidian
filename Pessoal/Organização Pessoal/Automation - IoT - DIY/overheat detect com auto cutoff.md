---

---
[https://how2electronics.com/over-heat-detector-auto-cut-off-system/?s=09](https://how2electronics.com/over-heat-detector-auto-cut-off-system/?s=09)

![[海外轮播动图.gif]]

![[Over-Heat-Detector-using-Op-Amp-1200x658.jpg]]

### **Overview: Over Heat Detector with Auto Cut-Off System using Op-Amp**

In this **mini electronics project**, we will build a simple **Over Heat Detector with Auto Cut-Off System** using Dual Op-Amp IC [**LM358**](https://how2electronics.com/lm358-dual-op-amp-features-pins-working-applications/). The circuit can also be called a **Heat Sensor**. The circuit basically triggers an alarm or turns on the LED when the temperature of the surrounding rises and goes beyond the desired level. The circuit can help to completely shut down the working system after over heat is sensed.

The usage of the **Over Heat Detector circuit** is inside your PC or in your kitchen. In an oven, it is desired that does not exceed a maximum temperature and prevent anything from burning. Similarly in a cooling system for perishable foods, it is desired that the temperature does not exceed a maximum level. **Heat sensor circuit** or **Over Heat Detector Circuit** senses the heat from various electronic devices like **amplifiers**, **computer** and thus generates the warning alarm.

The circuit has an **output relay**. This relay can connect to any system to warn of an emergency. This could be a sound device, a light source of any other indicator. The relay can also trigger a system to disconnect the **heat source**. This project for the **over heat detector** uses a **10K NTC thermistor**. NTC thermistors are often the preferred choice for temperature sensing because of their small package sizes and attractive price-performance ratios.

### **Components Required**

Following are the components required for making the project. All the components can be easily purchased from Amazon.

| S.N. | Components | Description | Quantity |
| --- | --- | --- | --- |
| 1 | LM358 | Dual Op-Amp IC | 1 |
| 2 | Resistor | 1 KΩ | 2 |
| 3 | Resistor | 33 K Ω | 1 |
| 4 | Potentiometer/Trimmer | 10K | 1 |
| 5 | Capacitor | 100 µF, 25V (Electrolytic Capacitor) | 1 |
| 6 | NTC Thermistor | 10K | 1 |
| 7 | BC549 | PNP Transistor | 1 |
| 8 | LED | 5mm Any Color | 1 |
| 9 | 1N4007 | Rectifier Diode | 1 |
| 10 | Relay | 12V Relay | 1 |
| 11 | Power Supply | 12V Battery/Adapter | 1 |

### **Over Heat Detector Circuit**

The **circuit diagram** of the Over Heat detector is shown below. It is built using an **NTC Thermistor**, popular [**Dual Op-Amp LM358**](https://www.st.com/resource/en/datasheet/cd00000464.pdf), 12V, 1C/O relay, and a few other components.

The **NTC Thermistor** along with **Op-Amp LM358** has been used here for sensing temperature variations. At room temperature, thermistor resistance is around **10K**. But when the temperature increases, the thermistor’s resistance becomes low and the output of LM358 becomes **high**. Consequently, the NPN transistor conducts and activates the Relay.

For testing the circuit you can introduce the hot Iron near thermistor to check whether its working or not. Similarly, you can rotate the Potentiometer to adjust the **sensitivity of the Sensor**.