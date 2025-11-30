# Single Flight Controller (SFC) – Project Documentation

This repository contains the design files, schematic, and explanation for my custom Single Flight Controller (SFC). The goal of this project was to create a compact, modular, and fully functional flight controller with built-in sensors, logging capability, and support for standard RC aircraft peripherals. This design was heavily inspired by Hack Club’s Guided Project: SFC.

![Schematic](/images/schematic.png)

![PCB](/images/pcb.png)

![Bill](/images/image.png)

## Overview

This flight controller integrates all the essential modules required for basic autonomous flight experimentation on a single PCB. It includes computation, sensing, logging, and connectivity features normally spread across multiple boards.

The system is built around an STM32 microcontroller, with supporting components for power regulation, sensor interfacing, GPS reception, and servo control.

---

## Features

### 1. Microcontroller

The design centers around an STM32F722RETx MCU. It provides high-speed processing, multiple UART/SPI/I2C peripherals, and enough GPIO pins for sensors and servo output.

### 2. Four 3-Pin Servo Connectors

The board includes four standard 3-pin (Signal, 5V, GND) servo output connectors.
These can be used for:

* Control surfaces (aileron, elevator, rudder)
* Throttle signal
* Or any PWM-output peripheral

The PCB includes appropriate decoupling capacitors and routing to ensure clean, low-noise PWM signals.

### 3. UART Port

A dedicated UART port is broken out on the PCB.
This can be used for:

* Telemetry modules
* Debug serial output
* External communication
* RC Receiver (if using SBUS or another serial protocol)

### 4. Built-In Sensors and Modules

#### GPS Module: u-blox Neo-M9N

A high-performance GNSS receiver is integrated directly onto the PCB.
Features include:

* Fast acquisition
* High update rate options
* Reliable lock in outdoor flight conditions
* Direct UART communication with the STM32

#### Barometer

The barometer module (BMP-series) provides altitude estimation for stability and navigation algorithms.
It interfaces over I2C and includes proper filtering capacitors for noise reduction.

#### Accelerometer and Temperature Sensor

An onboard IMU provides acceleration data for movement detection and flight stabilization.
Temperature reading is also used internally by IMUs to compensate sensor drift.

### 5. SD Card Slot for Data Logging

The board includes a microSD card slot for logging flight data such as:

* GPS coordinates
* Barometric altitude
* Acceleration
* Temperature
* System debug information

The microcontroller communicates with the SD card via SPI.

### 6. Power Management

The design includes onboard regulators and filtering stages to provide stable supplies for:

* 5V rail (servos and peripherals)
* 3.3V rail (MCU, sensors, GPS)
* Noise isolation between digital and analog sections

---

## How the Flight Controller Was Designed

### Schematic Stage

I began by identifying the essential modules needed for the first version of the flight controller. I collected reference designs from datasheets and existing open-source boards, then arranged everything into a master schematic. Each module was divided into blocks:

* MCU core section
* Power regulation
* Servo outputs
* GPS
* Sensors (Barometer + IMU)
* SD card interface
* UART and additional connectors

I ensured all power, ground, and communication lines were properly labeled and referenced across schematic pages.

### PCB Routing

This was the most challenging part of the entire project.

#### Challenges Faced

1. **Dense routing around the STM32F7 MCU**
   The microcontroller has many high-speed pins in tight clusters. Routing SPI, I2C, UART, SWD, and PWM signals without crossing too many traces was difficult.

2. **Interference concerns between GPS and digital signals**
   GPS modules are sensitive to noise. Keeping the antenna section clean required careful placement and ground-plane management.

3. **Power distribution**
   Servos can draw significant current. Ensuring thick enough traces and minimizing voltage drops was a challenge.

4. **SD Card signal integrity**
   SPI lines need clean routing and matched lengths to avoid read/write instability. I had to reroute multiple times to avoid crosstalk.

5. **Fitting everything on a reasonable board size**
   With multiple connectors, sensors, and the MCU, arranging components efficiently took several iterations.

### What I Learned

1. **Importance of reference designs**
   Studying vendor schematics helped avoid basic mistakes, especially with decoupling and pull-up requirements.

2. **Routing strategy matters**
   Planning major traces (power rails, GPS lines, SD card lines) before others saves time.

3. **Decoupling capacitors are not optional**
   Correct placement greatly affected reliability during testing.

4. **Grounding techniques for mixed-signal boards**
   Separating analog and digital grounds and using ground pours improved noise performance.

5. **Iterative design is normal**
   The first layout is rarely perfect. Revision cycles teach you more than documentation ever will.

---

## Reference

This project was inspired by and based on concepts from Hack Club’s Guided Project: Single Flight Controller (SFC).

Their documentation, examples, and approach helped me understand:

* How to break complex designs into modular blocks
* Good PCB routing practices
* How sensing modules interact on a flight controller
* The importance of logging and debugging tools

---

## Conclusion

This Single Flight Controller is the result of combining research, reference designs, and hands-on PCB design practice. With integrated GPS, IMU, barometer, servo outputs, UART, and SD card logging on one board, it serves as a compact platform for experimenting with flight algorithms and embedded systems.


Note: 
Due to unavaiable components on JLCPCB i would request to get tickets instead of the PCB.

Thank You,
Shlok Vaidya