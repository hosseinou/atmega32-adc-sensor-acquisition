# ATmega32 ADC & Sensor Data Acquisition

This repository contains my C code and Proteus simulations for **Experiment 4: Analog-to-Digital Converter (ADC)** from the Microprocessor Laboratory course at Shiraz University[cite: 1].

## Experiment Overview
This experiment covers the usage of the ATmega32's internal ADC. Since microprocessors operate on digital data, and many sensors (temperature, gas, etc.) provide analog signals, we utilize the ADC to convert these signals into a digital format[cite: 1]. The experiment involves configuring the ADC registers (specifically `ADMUX` and `ADCSRA`) to handle 10-bit resolution and interface with sensors on the lab training board[cite: 1].

## Theory & Math (As per Lab Manual)
The lab manual defines the fundamental ADC operation using the following equations[cite: 1]:

**Equation (1-4): Digital Output Calculation**
$$Digital~Output = V_{Analog} \times \frac{2^{n}}{V_{Ref}}$$

**Equation (2-4): Real-World Value Calculation**
$$Real~Value = f(V_{Analog}) = f\left(Digital~Output \times \frac{2^{n}}{V_{Ref}}\right)$$

*Where $n$ represents the ADC resolution (10-bit) and $V_{Ref}$ is the reference voltage[cite: 1].*

### Sensor Identifier Table
The following identifiers are used for LCD output as defined in Table 1-4[cite: 1]:

| Sensor Type | LCD Identifier |
| :--- | :--- |
| Volume | T:V |
| Gas | T:G |
| Temperature | T:T |
| Humidity | T:H |
| NTC | T:N |
| CDS | T:C |

## Sensor Implementations
* **/D1_Volume:** Implementation for the potentiometer base test.
* **/D2_LM35:** Standard data acquisition for the LM35 temperature sensor.
* **/D3_Gas:** Polling implementation for the analog gas sensor.
* **/D5_LM35_Filtered:** Implementation of the noise filtering extension. As discussed in the lab manual, the temperature readings often contain high-frequency noise which must be addressed via code (e.g., using a filtering approach) to stabilize the display[cite: 1].
* **/docs:** Original laboratory manual (Experiment 4).

## Technical Stack
* **Microcontroller:** ATmega32[cite: 1]
* **Language:** Embedded C[cite: 1]
* **IDE:** CodeVisionAVR (using Code Wizard for ADC register configuration)[cite: 1]
* **Simulation:** Proteus ISIS
