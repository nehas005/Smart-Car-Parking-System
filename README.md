# 🚗 Smart Car Parking System

## 📌 Overview

The **Smart Car Parking System** is an Arduino-based project designed to automate parking management using ultrasonic sensors, a servo motor, and an LCD display. It detects vehicle presence, manages entry/exit, and displays parking availability in real time.

---

## ⚙️ Features

* 🚘 Detects cars using ultrasonic sensors
* 🚧 Automatic gate control using a servo motor
* 📟 Real-time parking status on LCD display
* 🔋 Stable power supply using capacitor filtering
* 🧠 Runs on Arduino with simple, efficient code

---

## 🧰 Components Used

* Arduino Uno
* 2 × HC-SR04 Ultrasonic Sensors
* Servo Motor
* I2C LCD Display 
* Breadboard
* Capacitor (25V 2200µF)
* Jumper Wires

---

## 🔌 Connections

### 1. Power Connections

* Arduino 5V → Breadboard + rail
* Arduino GND → Breadboard – rail

### 2. Capacitor (25V 2200µF)

* Positive (+) → Breadboard + rail
* Negative (–) → Breadboard – rail

### 3. Sensor 1 (HC-SR04 – Right Side)

* VCC → Breadboard + rail
* GND → Breadboard – rail
* TRIG → Arduino Digital Pin D7
* ECHO → Arduino Digital Pin D6

### 4. Sensor 2 (HC-SR04 – Left Side)

* VCC → Breadboard + rail
* GND → Breadboard – rail
* TRIG → Arduino Digital Pin D5
* ECHO → Arduino Digital Pin D4

### 5. Servo Motor

* Red (VCC) → Breadboard + rail
* Brown/Black (GND) → Breadboard – rail
* Orange/Yellow (Signal) → Arduino Digital Pin D9

### 6. LCD Display (I2C)

* GND → Arduino GND
* VCC → Arduino 5V
* SDA → Arduino Analog Pin A4
* SCL → Arduino Analog Pin A5

---

## 💻 Software Setup

1. Install Arduino IDE
2. Open the provided `.ino` code file
3. Select your board (e.g., Arduino Uno)
4. Select the correct COM port
5. Upload the code to your Arduino

---

## ▶️ How It Works

1. Ultrasonic sensors detect incoming and outgoing vehicles
2. Distance data is processed by Arduino
3. Servo motor opens/closes the gate accordingly
4. LCD displays parking availability (e.g., "Slots Available" or "Parking Full")

---

## 🎥 Project Demonstration

[![Watch Demo](https://img.youtube.com/vi/plL0EiuXplA/0.jpg)](https://youtube.com/shorts/plL0EiuXplA)

```
