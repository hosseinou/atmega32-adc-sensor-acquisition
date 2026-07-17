# ATmega32 ADC & Sensor Data Acquisition

This repository contains my laboratory work, C code, and Proteus simulations for **Experiment 4: Analog-to-Digital Converter (ADC)** from the Microprocessor Laboratory course at Shiraz University[cite: 4].

## Experiment Overview
Microprocessors operate exclusively in the digital domain, yet real-world physical quantities—such as temperature, light intensity, gas concentration, and mechanical position—are inherently analog[cite: 4]. The objective of this experiment was to bridge this gap by utilizing the ATmega32's internal Analog-to-Digital Converter (ADC) to sample continuous analog voltages and convert them into discrete digital data[cite: 4].

The project demonstrates how to configure the microcontroller's ADC subsystem to interface with various sensors, perform data acquisition, and translate raw ADC counts into human-readable physical units displayed on a 16x2 Alphanumeric LCD[cite: 4].

## Technical Theory & Configuration
The ATmega32 features an 8-channel, 10-bit ADC capable of high-precision data acquisition[cite: 4]. The ADC was configured with a **62.5 kHz clock frequency** to balance sampling speed and signal stability[cite: 4].

### Reference Voltage Selection
The accuracy of the conversion depends on the voltage reference ($V_{Ref}$). Per the laboratory instructions, we implemented the following configurations[cite: 4]:
1.  **AVCC Pin:** Connected to the microcontroller's supply voltage.
2.  **AREF Pin:** Allowing for an external precision reference.
3.  **Internal 2.56V:** An internal bandgap reference.

### Conversion Formula
The digital output is calculated using the following relationship between the analog input ($V_{Analog}$) and the chosen reference ($V_{Ref}$)[cite: 4]:

$$Digital~Output = V_{Analog} \times \frac{2^n}{V_{Ref}}$$

*Where $n$ represents the ADC resolution (10-bit)[cite: 4].*

## 🔌 Sensor Implementations
Each sensor was connected to the ADC channels as required by the lab manual[cite: 4]:

| Sensor Type | LCD Identifier | Description |
| :--- | :--- | :--- |
| **Volume (Potentiometer)** | `T:V` | Used for voltage divider measurements and threshold triggers[cite: 4]. |
| **Gas Sensor** | `T:G` | Monitored raw analog concentration levels[cite: 4]. |
| **LM35 (Temperature)** | `T:T` | Calculated using the 10 mV/°C scale factor[cite: 4]. |
| **Humidity** | `T:H` | Analog data acquisition and unit conversion[cite: 4]. |
| **NTC** | `T:N` | Resistance-based temperature measurement[cite: 4]. |
| **CDS (Light)** | `T:C` | Light-dependent resistor voltage measurement[cite: 4]. |

## Noise Filtering Extension
A significant challenge encountered with the LM35 temperature sensor was high-frequency noise and instability in the LCD readout[cite: 4]. 

Because temperature changes in a typical environment are slow (low frequency), the rapid fluctuations observed were identified as high-frequency noise[cite: 4]. To address this, I implemented a **software-based moving average filter** (10-sample window) as an extension task[cite: 4]. This technique effectively separates the desired slow-changing signal from the high-frequency interference, providing a stable and readable output on the LCD[cite: 4].

## Folder Structure
* **/D1_Volume:** Implementation for the potentiometer base test.
* **/D2_LM35:** Standard data acquisition for the LM35 temperature sensor.
* **/D3_Gas:** Polling implementation for the analog gas sensor.
* **/D5_LM35_Filtered:** Implementation of the moving average noise filter.
* **/docs:** Original laboratory manual (Experiment 4).

## Technical Stack
* **Microcontroller:** ATmega32[cite: 4]
* **Language:** Embedded C[cite: 4]
* **IDE:** CodeVisionAVR (using Code Wizard for register initialization)[cite: 4]
* **Simulation:** Proteus ISIS
