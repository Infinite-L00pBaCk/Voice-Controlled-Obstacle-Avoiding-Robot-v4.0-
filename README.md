# 🚗 Voice-Controlled Obstacle Avoiding Car (Raspberry Pi)

**Version:** 4.0
**Status:** Stable & Tested
**Platform:** Raspberry Pi (GPIO – BOARD mode)

This project implements a **smart autonomous car** using a Raspberry Pi that combines **obstacle avoidance**, **voice control**, and **motion detection** for safe and robust navigation. The system uses ultrasonic scanning with a servo motor, PIR-based human/motion detection, and real-time voice commands to control the car. 

**Core Functionality** The robot operates on a sophisticated sense-think-act cycle. Unlike basic robots that "bump and turn," this model utilizes a Move-Stop-Scan logic. By halting the motors before rotating the ultrasonic-mounted servo, the system eliminates mechanical vibration and electrical interference, ensuring the distance data for the Left, Center, and Right paths is pinpoint accurate.

---

## ✨ Features

* 🎤 **Voice Control**

  * Start and stop the car using simple voice commands like *“start”*, *“go”*, *“stop”*
  * Uses Google Speech Recognition via `speech_recognition` library
  * Runs voice listening in a background thread (non-blocking)

* 🚧 **Obstacle Avoidance**

  * Ultrasonic sensor mounted on a servo motor
  * Scans **Left – Center – Right**
  * Chooses the safest direction dynamically
  * Handles trapped scenarios by backing out safely

* 🧠 **Intelligent Decision Logic**

  * Move → Stop → Scan → Decide → Move loop
  * Prevents blind movement while scanning
  * Adjustable critical distance threshold

* 🛑 **PIR Motion Safety**

  * Detects nearby motion (human/animal)
  * Immediately reverses and stops for safety

* ⚙️ **Hardware Stability Fixes**

  * Servo jitter elimination using controlled PWM pulses
  * Motor shutdown during scanning for accurate distance readings
  * Clean GPIO and PWM shutdown on exit

---

## 🧰 Hardware Requirements

* Raspberry Pi (any model with GPIO)
* L298N / L293D Motor Driver
* DC Motors + Robot Chassis
* Ultrasonic Sensor (HC-SR04)
* Servo Motor (SG90 recommended)
* PIR Motion Sensor
* USB Microphone
* External Power Supply (recommended for motors)

---

## 🔌 Pin Configuration (BOARD Mode)

| Component       | GPIO Pin |
| --------------- | -------- |
| ENA             | 12       |
| ENB             | 16       |
| IN1             | 7        |
| IN2             | 11       |
| IN3             | 13       |
| IN4             | 15       |
| Ultrasonic TRIG | 29       |
| Ultrasonic ECHO | 31       |
| Servo Motor     | 33       |
| PIR Sensor      | 18       |

---

## 📦 Software Requirements

Install required Python libraries:

```bash
pip install SpeechRecognition
pip install pyaudio
```

> ⚠️ `pyaudio` may require system dependencies:

```bash
sudo apt install portaudio19-dev
pip install pyaudio
```

Enable GPIO access:

```bash
sudo raspi-config
```

→ Interface Options → Enable GPIO

---

## ▶️ How It Works

1. **Voice Listener** runs in the background
2. Say **“Start”** → car begins autonomous exploration
3. The car:

   * Stops
   * Scans left, center, right
   * Measures distances
   * Chooses safest direction
4. PIR sensor overrides everything for safety
5. Say **“Stop”** → car halts immediately

---

## 🧪 Example Voice Commands

* 🟢 `"start"`, `"go"`, `"move"`
* 🔴 `"stop"`, `"halt"`, `"wait"`

---

## 🛠️ How to Run

```bash
python3 obstacle_avoiding_car.py
```

Press **Ctrl + C** to safely stop the program.

---

## 🧹 Safe Shutdown

The program ensures:

* Motors stop
* PWM signals are released
* GPIO pins are cleaned up properly

---

## 📈 Future Improvements

* Mobile app or Bluetooth control
* Camera-based object detection
* SLAM mapping
* Offline voice recognition
* Speed control using PID

---

## 📜 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙌 Author
**Priyam Prakash** *B.Tech – Electronics and Communication Engineering* 

