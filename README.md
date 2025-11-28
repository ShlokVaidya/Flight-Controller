# SIMPLE FLIGHT CONTROLLER

SFC is a DIY-friendly flight controller designed for makers, students, and hobbyists who want to learn how real FCs work or build their own drone/robotic autopilot from scratch.
The board integrates the essential sensors and power systems required for stabilizing multirotors, fixed-wing aircraft, and autonomous ground vehicles.

This project includes:

Full schematic (KiCad)
![Schematic](/images/schematic.png)

Board layout
![3d](/images/Screenshot%202025-11-28%20233438.png)

Bill of materials
![bill1](/images/Screenshot%202025-11-29%20000221.png)
![bill2](/images/Screenshot%202025-11-29%20000238.png)

✨ Features
🔧 Core Hardware

STM32F7 MCU
High-performance ARM Cortex-M7 processor with FPU and fast peripherals.

ICM-42605 6-Axis IMU
High-speed SPI gyro/accelerometer suitable for flight control loops.

BMP/BME280 Barometer
Accurate altitude measurement for autonomous flight modes.

MicroSD Card (SPI)
Blackbox logging of flight data at high frequency.

### 🛰️ GPS & Compass Support

Compatible with:

UBLOX M8/M9 series GPS

QMC5883L / HMC5883L compass modules

Standard 5V UART GPS interface

External magnetometer via I²C

### ⚡ Power System

5V Buck-Boost Regulator
Stable 5V output for GPS, receiver, and accessories.

3.3V LDO Regulator
Clean analog power for IMU, barometer, and MCU.

VBAT and Current Sense (optional)
Battery voltage monitoring for OSD/telemetry.

Noise-Isolated IMU Power
Ferrite bead + decoupling = reduced gyro jitter.

### 🌀 Servo Outputs

4× Servo outputs (for gimbal, fixed-wing, or robotics)

### 📡 Connectivity

USB-C for flashing firmware and debugging

2× UARTs (GPS, receiver, telemetry)

I²C for compass, peripherals

SPI for IMU & SD card

Boot & Reset buttons

### 🧭 Intended Uses

SFC can be used for:

✔️ RC Multirotors

Quadcopters, tri-copters, experimental airframes.

✔️ Fixed-Wing Aircraft

Servos + GPS + barometer for autonomous flight.

✔️ Ground Robots

Small rovers, mapping robots, GPS-guided platforms.

✔️ Research & Education

Sensor fusion, flight control algorithms, blackbox logging.


### 📐 Hardware Block Diagram
        ┌────────────────────────────┐
        │            SFC             │
        │                            │
        │ STM32F7 MCU                │
        │  ├─ IMU (SPI)              │
        │  ├─ Barometer (I²C)        │
        │  ├─ GPS (UART)             │
        │  ├─ SD Card (SPI)          │
        │  ├─ Receiver (UART/I²C)    │
        │  └─ Motor Outputs (PWM)    │
        │                            │
        │ Power                      │
        │  ├─ 5V Buck-Boost          │
        │  └─ 3.3V LDO               │
        └────────────────────────────┘

### 🧩 Repository Structure
/hardware
   ├─ SimpleFlightController.kicad_sch
   ├─ SimpleFlightController.kicad_pcb
   └─ BOM.csv

### 📄 License

This project is 100% open-source under the MIT License.
Use it, modify it, and contribute improvements!