# ATmega32 ADC & Sensor Data Acquisition

This repository contains my C code and Proteus simulations for **Experiment 4: Analog-to-Digital Converter (ADC)** from the Microprocessor Laboratory course at Shiraz University.

## 📌 Overview
The goal of this experiment was to interface analog sensors with the ATmega32 microcontroller. Since microcontrollers operate on digital logic, we utilized the internal 10-bit ADC to convert continuous analog voltage levels into discrete digital values. 

The experiment focuses on:
*   Configuring the ADC registers (specifically `ADMUX` and `ADCSRA`) for 10-bit resolution and a 62.5 kHz clock frequency.
*   Selecting appropriate voltage reference sources (AVCC pin).
*   Mapping raw digital output to real-world physical quantities (e.g., Temperature, Gas concentration)[cite: 5].

## ⚙️ Theory & Configuration
The ATmega32 features an 8-channel ADC[cite: 5]. The digital output is calculated based on the reference voltage ($V_{Ref}$) and the input analog voltage ($V_{Analog}$):

$$Digital~Output = V_{Analog} \times \frac{2^n}{V_{Ref}}$$

*Where $n$ is the ADC resolution (10-bit).*

### Sensor Mapping Table
In accordance with the lab manual, the following identifiers were used on the Alphanumeric LCD to distinguish between sensors[cite: 5]:

| Sensor Type | LCD Identifier |
| :--- | :--- |
| Volume (Potentiometer) | T:V |
| Gas | T:G |
| Temperature (LM35) | T:T |
| Humidity | T:H |
| NTC | T:N |
| CDS (Light) | T:C |

## 📂 Repository Contents
* **/D1_Volume:** Implementation for the potentiometer base test.
* **/D2_LM35:** Standard data acquisition for the LM35 temperature sensor.
* **/D3_Gas:** Polling implementation for the analog gas sensor.
* **/D5_LM35_Filtered:** Extension implementation using a moving average algorithm to stabilize the LM35 temperature readings against high-frequency noise[cite: 5].
* **/docs:** Original lab manual (Experiment 4).

## 🛠️ Technical Stack
* **Microcontroller:** ATmega32[cite: 5]
* **Language:** Embedded C[cite: 5]
* **IDE:** CodeVisionAVR (using Code Wizard for register configuration)[cite: 5]
* **Simulation:** Proteus ISIS
