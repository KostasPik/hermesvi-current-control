# HermesVI Current Control System

## Overview

The **HermesVI Current Control System** is a program developed for the Raspberry Pi Pico, using the C/C++ SDK, to manage the current drawn from the battery of the HermesVI airplane. HermesVI, constructed by the EUROAVIA Athens team, is a participant in the Air Cargo Challenge Competition 2024. This system ensures that the current remains within specified limits to minimize any competition penalties and enhance operational efficiency.

## Key Features

- **PID Controller**: Utilizes a Proportional-Integral-Derivative (PID) controller to regulate the current drawn from the battery.

- **State Management**: Operates in three distinct states:
  - **NO_CONTROL**: No regulation of current.
  - **LOW_CONTROL**: Ensures that current does not exceed the `LOW_THRESHOLD`.
  - **HIGH_CONTROL**: Ensures that current does not exceed the `HIGH_THRESHOLD`.

- **Interrupt-Based State Changes**: Detects state transitions using interrupts to avoid blocking code and ensure real-time responsiveness.

- **PWM Input Reading**: Reads the PWM input signal from the radio controller using interrupts to avoid blocking operations.

- **PWM Output**: Generates a PWM signal to control the airplane’s ESC (Electronic Speed Controller) for effective motor management.

- **Current Measurement**: Measures current using the Raspberry Pi Pico’s ADC by converting voltage across a shunt resistor to current using Ohm’s Law.

- **Real-Time Filtering**: Implements a sliding window filter to reduce noise in the current measurements, providing smoother and more accurate control.

- **Dual-Core Utilization**: The program utilizes both cores of the Raspberry Pi Pico:
  - **Core 0**: Handles ADC input reading.
  - **Core 1**: Executes the PID control algorithm and manages state transitions.

- **Mutual Exclusion**: Ensures safe access to shared resources between cores using locks to prevent race conditions and maintain data integrity.

## Authors

- Konstantinos Pikoulas
- Alexis Vavvas