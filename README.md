# ATmega32 ADC & Sensor Data Acquisition

This repository contains my laboratory work, C code, and Proteus simulations for **Experiment 4: Analog-to-Digital Converter (ADC)** from the Microprocessor Laboratory course at Shiraz University.

## Experiment Overview
Microprocessors operate exclusively in the digital domain, yet real-world physical quantities—such as temperature, light intensity, gas concentration, and mechanical position—are inherently analog. The objective of this experiment was to utilize the ATmega32's internal 10-bit ADC to sample continuous analog voltages and convert them into discrete digital data.

The project demonstrates how to configure the microcontroller's ADC subsystem to interface with various sensors, perform data acquisition, and translate raw ADC counts into human-readable physical units displayed on a 16x2 Alphanumeric LCD.

## Theory & Math (As per Lab Manual)
The lab manual defines the fundamental ADC operation using the following equations:

**Digital Output Calculation (Equation 1-4):**
Digital Output = V_Analog * (2^n / V_Ref)

**Real-World Value Calculation (Equation 2-4):**
Real Value = f(V_Analog) = f(Digital Output * (2^n / V_Ref))

*Where 'n' represents the ADC resolution (10-bit) and 'V_Ref' is the reference voltage.*

### Sensor Identifier Table
The following identifiers are used for LCD output as defined in the manual (Table 1-4):

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
* **/D5_LM35_Filtered:** Implementation of the noise filtering extension. As discussed in the lab manual, the temperature readings often contain high-frequency noise which was mitigated via a software-based moving average filter to stabilize the display.

## Technical Stack
* **Microcontroller:** ATmega32
* **Language:** Embedded C
* **IDE:** CodeVisionAVR (using Code Wizard for ADC register configuration)
* **Simulation:** Proteus ISIS
