# Micromouse
Micromouse robot designed for the IEEE Zagazig competition
# 🐭 Micromouse Robot

A custom-designed autonomous **Micromouse robot** developed for the **IEEE Zagazig competition**, where our team achieved **2nd place**.

The robot is designed to autonomously navigate a maze using distance sensors, determine its position and orientation, and control two DC motors for accurate movement.

> 🥈 **Competition Result: 2nd Place — IEEE Zagazig**

---

## 🏆 Competition

This project was developed and tested for an **IEEE Zagazig Micromouse competition**.

Our team achieved:

**🥈 2nd Place**

The competition required the robot to autonomously navigate a maze while accurately controlling its movement and responding to the maze structure.

---

## 🚀 Project Overview

The Micromouse is a small autonomous robot capable of navigating a maze without external control.

The robot uses multiple distance sensors to detect walls and obstacles, an IMU to measure orientation, wheel encoders for movement feedback, and a microcontroller to process sensor data and control the motors.

The project includes both the **electronic hardware** and **custom PCB design** developed specifically for the robot.

### Main Features

* Autonomous maze navigation
* Three front/side-facing ToF distance sensors
* Wheel encoder feedback
* IMU-based orientation measurement
* Closed-loop motor control
* Custom PCB designed in Altium Designer
* Dual DC motor drive
* Compact two-layer PCB design
* Dedicated power distribution and decoupling
* I²C communication between the ESP32-C3 and sensors

---

# 🧠 System Architecture

The main system can be divided into four sections:

```text
                  ┌──────────────────┐
                  │    ESP32-C3      │
                  │   Main MCU       │
                  └────────┬─────────┘
                           │
          ┌────────────────┼────────────────┐
          │                │                │
          ▼                ▼                ▼
   ┌────────────┐   ┌────────────┐   ┌────────────┐
   │ VL53L0X ×3 │   │  MPU6050   │   │  Encoders  │
   │ ToF Sensors│   │    IMU     │   │            │
   └────────────┘   └────────────┘   └────────────┘
                           │
                           │
                           ▼
                    ┌────────────┐
                    │  Control   │
                    │ Algorithms │
                    └─────┬──────┘
                          │
                          ▼
                    ┌────────────┐
                    │  DRV8833   │
                    │ Motor Driver│
                    └─────┬──────┘
                          │
                    ┌─────┴─────┐
                    ▼           ▼
                 Motor L     Motor R
```

---

# 🔌 Hardware

## Main Controller

### ESP32-C3

The **ESP32-C3** acts as the main controller of the robot.

It is responsible for:

* Reading the distance sensors
* Reading IMU data
* Processing encoder feedback
* Running the navigation and control algorithms
* Generating motor control signals
* Communicating with the peripheral devices through I²C and GPIO

---

## 📡 Distance Sensors

The robot uses **three VL53L0X Time-of-Flight sensors** for wall detection.

The sensors provide distance measurements that are used to determine the robot's position relative to the maze walls.

Using three sensors allows the robot to obtain information from multiple directions while navigating.

### I²C Addressing

Because the VL53L0X sensors share the same default I²C address, the design uses the sensors' shutdown/control pins to initialize them individually and assign unique I²C addresses.

This allows all three sensors to operate on the same I²C bus.

---

## 🧭 MPU6050

An **MPU6050 IMU** is used to obtain orientation and motion information.

The IMU provides:

* 3-axis accelerometer
* 3-axis gyroscope

The gyroscope data can be used to estimate the robot's rotation during turns and improve movement accuracy.

---

## ⚙️ Motor Driver

The robot uses a **DRV8833 dual H-bridge motor driver** to control the two DC motors.

The driver provides independent control of:

* Left motor
* Right motor

The ESP32-C3 generates the required control signals to control motor direction and speed.

---

## 🔄 Encoders

The motors include wheel encoders that provide feedback about wheel rotation.

Encoder feedback allows the controller to estimate:

* Distance traveled
* Wheel speed
* Difference between left and right wheel movement
* Movement accuracy during straight-line motion
* Rotation during turns

This feedback is important for implementing closed-loop motion control.

---

# 🖥️ PCB Design

The PCB was designed using **Altium Designer**.

The custom board integrates the major electronics required by the Micromouse into a single compact PCB.

### PCB Design Considerations

Several design considerations were taken into account during PCB development:

* Power distribution
* Decoupling capacitors
* Motor-driver current paths
* Sensor communication
* I²C routing
* Grounding
* Separation of noisy motor circuitry from sensitive sensors
* Compact component placement
* Connector accessibility
* Manufacturability

The PCB contains dedicated circuitry for the MCU, sensors, motor driver, power system, and external connections.

---

# ⚡ Power System

The PCB includes the required power distribution for the robot's electronics and motors.

Separate consideration was given to the motor supply and the low-voltage digital electronics to reduce the effect of motor switching noise on the sensors and microcontroller.

Decoupling capacitors were placed close to the relevant IC power pins to improve supply stability and reduce high-frequency noise.

---

# 📐 Hardware Files

The repository contains the hardware design files used during development.



The hardware files include the PCB design, schematic, component libraries, manufacturing files, and other supporting design files.


---

# 🧪 Testing & Verification

The hardware was tested throughout the development process before being used in the competition.

Testing included:

* Power supply verification
* Motor driver testing
* Sensor communication testing
* I²C communication
* Encoder feedback
* IMU measurements
* Motor direction and speed control
* PCB electrical-rule checking
* PCB design-rule checking
* Full robot movement testing
* Maze navigation testing

---

# 🛠️ Tools & Technologies

| Category         | Technology                   |
| ---------------- | ---------------------------- |
| Microcontroller  | ESP32-C3                     |
| Distance Sensors | VL53L0X ×3                   |
| IMU              | MPU6050                      |
| Motor Driver     | DRV8833                      |
| Motors           | DC Gear Motors with Encoders |
| PCB Design       | Altium Designer              |
| Communication    | I²C                          |
| Motor Control    | PWM                          |
| Programming      | C / Embedded C               |
| Manufacturing    | Custom PCB                   |

---

# 📁 Repository Structure

```
Micromouse/
│
├── Hardware/
│    ├── Bottom_Floor/
│    ├── Full_project/
│    ├── Top_floor/
│   
│  
│
│
├── docs/
│      Micromouse_BOM 1.pdf
│      Micromouse_Calculations_IEEE_RAS.pdf
│
├── Media/
│   ├── Images
│
│
└── README.md
```

---

# 👥 Team

This was a team project developed for the IEEE Zagazig competition.

**Team Members:**

* Mohamed Hany 
* Abdallah Ahmed

### My Contribution

My main contributions to the project included:

* PCB design and development
* Schematic design
* Component selection
* ESP32-C3 hardware integration
* Sensor integration
* Motor-driver integration
* Power distribution
* PCB routing and layout
* Hardware testing and debugging

# 🏁 Result

## 🥈 2nd Place — IEEE Zagazig

The completed Micromouse successfully competed in the IEEE Zagazig competition and achieved **2nd place**.

The project provided practical experience in:

* Embedded systems
* PCB design
* Sensor integration
* Motor control
* Power electronics
* Hardware debugging
* Autonomous robotics
* Team-based engineering

---

# 📜 License

This project is provided for educational and portfolio purposes.

Please contact the project contributors before using the hardware design commercially.
