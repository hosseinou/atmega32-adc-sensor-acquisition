# ATmega32 ADC & Sensor Data Acquisition

This repository contains my C code and Proteus simulations for the Analog-to-Digital Converter (ADC) experiment from my Microprocessor Laboratory course at Shiraz University. 

## 📌 Overview
The project explores reading analog voltages from multiplexed sensors using the ATmega32's internal 10-bit ADC. It handles configuring the ADC registers, reading raw data, applying transfer functions to calculate physical quantities, and displaying the telemetry on a 16x2 Alphanumeric LCD.

## ⚙️ Hardware Configuration & Math
The internal ADC is configured with a **62.5 kHz clock frequency** to ensure stable readings, utilizing the `AVCC` pin as the voltage reference ($V_{Ref}$).

The 10-bit digital value (0–1023) is converted back into the measured analog voltage using:
$$V_{Analog}=Digital\_Output\times\frac{V_{Ref}}{1024}$$

Specific transfer functions (e.g., the LM35's 10 mV/°C scale factor) are then applied in C to calculate the real physical quantity.

## 🔌 Sensor Implementations
* **Volume / Potentiometer:** Simple 0-5V voltage divider measurement with threshold-based GPIO trigger logic.
* **Gas Sensor:** Monitoring raw analog gas concentration levels.
* **LM35 Temperature Sensor:** Converting raw voltage to Celsius.
* **Noise Filter:** Implementation of a software-based moving average filter (10-sample window) to stabilize fluctuating high-frequency noise from the LM35 sensor.

## 📂 Folder Structure
* `/D1_Volume` - Potentiometer base test and output control logic.
* `/D2_LM35` - Standard temperature data acquisition.
* `/D3_Gas` - Analog gas sensor polling.
* `/D5_LM35_Filtered` - Temperature reading with the moving average algorithm applied.
* `/docs` - Original laboratory manual for the experiment.

## 🛠️ Technical Stack
* **Microcontroller:** ATmega32 (8-bit)
* **Language:** Embedded C
* **IDE:** CodeVisionAVR
* **Simulation:** Proteus ISIS
