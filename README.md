# Hector 9000 🍹🤖

Hector 9000 is an open-source Raspberry Pi based cocktail robot with automated valve control, a stepper motor driven arm, weight-based liquid dispensing and a modern web interface for configuration, calibration and drink mixing.

---

# Features

## 🍸 Automated Drink Mixing

* Automatic cocktail preparation
* Multiple ingredients and recipes
* Valve-based liquid dispensing
* Pump controlled filling system

## ⚖️ Weight-Based Dispensing

* HX711 load cell integration
* Dispensing by grams instead of time
* Multi-point scale calibration
* Automatic tare support
* Calibration point management through the web interface

## 🤖 Stepper Motor Arm

* DRV8825 based stepper control
* Endstop based homing/reference system
* Automatic IN/OUT positioning
* Configurable speed and direction
* Safety timeout protection

## 🌐 Web Interface

* Modern touch-friendly UI
* Ingredient management
* Valve configuration
* Manual hardware testing
* Scale calibration page
* Live sensor feedback
* Backend-connected hardware controls

## 🔧 Hardware Testing

* Manual valve testing
* Pump testing
* Arm IN/OUT testing
* Endstop status monitoring
* Scale raw value monitoring

---

# Hardware

## Main Controller

* Raspberry Pi 3B / 4B

## Stepper System

* NEMA17 stepper motor
* DRV8825 stepper driver
* Stepper breakout board
* Endstop switch

## Weight System

* HX711 amplifier
* Load cell / scale

## Valve Control

* PCA9685 PWM controller
* Servo-driven valves

## Pump Control

* Relay / SSR controlled pump

---

# GPIO Pin Configuration

## Stepper Motor

| Function | GPIO    |
| -------- | ------- |
| STEP     | GPIO 27 |
| DIR      | GPIO 22 |
| ENABLE   | GPIO 17 |
| Endstop  | GPIO 21 |

## HX711

| Function | GPIO    |
| -------- | ------- |
| DT       | GPIO 20 |
| SCK      | GPIO 16 |

## Pump

| Function   | GPIO    |
| ---------- | ------- |
| Pump Relay | GPIO 24 |

## I2C

| Function | GPIO   |
| -------- | ------ |
| SDA      | GPIO 2 |
| SCL      | GPIO 3 |

---

# Scale Calibration

The scale system supports multi-point calibration.

Instead of using only a single factor, Hector 9000 stores multiple calibration points:

* Raw HX711 value
* Reference weight in grams

This allows more accurate conversion between raw values and real weights.

Example:

| Raw Value | Reference |
| --------- | --------- |
| 10104022  | 300 g     |
| 10195785  | 400 g     |
| 10281139  | 500 g     |

The backend automatically calculates:

* Offset
* Scale factor
* Interpolation between calibration points

---

# Arm Homing System

The arm uses an endstop-based reference system.

Important:

* The endstop is located at the OUT position.
* Home position is the IN position.

Homing process:

1. Move arm OUT until endstop is triggered
2. Count steps to endstop
3. Move exact number of steps back to IN
4. Save reference position

---

# Installation

## Clone Repository

```bash
git clone https://github.com/YOUR_USERNAME/hector9000.git
cd hector9000
```

## Install Dependencies

```bash
pip install -r requirements.txt
```

## Start Backend

```bash
python3 app.py
```

## Open Web Interface

```text
http://localhost:3000
```

or from another device:

```text
http://RASPBERRY_PI_IP:3000
```

---

# Safety Notes ⚠️

* Never work on wiring while power is connected.
* SSRs and pumps may switch dangerous voltages.
* Use proper grounding.
* Use fused power supplies.
* Stepper drivers can overheat if current is set too high.

---

# Project Goals

* Reliable automated cocktail preparation
* Modular hardware architecture
* Fully configurable web interface
* Accurate weight-based dispensing
* Open-source development

---

# Future Plans

* Automatic cleaning mode
* Recipe database
* Multi-user profiles
* Mobile interface
* Statistics and logging
* AI-assisted recipe creation
* Ingredient level monitoring


---

# Status

🚧 Mostly Finished
