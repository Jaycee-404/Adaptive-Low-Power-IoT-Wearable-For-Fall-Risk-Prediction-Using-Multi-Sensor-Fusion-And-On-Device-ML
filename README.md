# Adaptive Low-Power IoT Wearable for Fall Risk Prediction (TinyML + Sensor Fusion)

![MIT License](https://img.shields.io/badge/License-MIT-green.svg)

> **3-Credit Semester Project | IoT + Embedded ML | Real-Time Wearable System**

## Project Overview
Falls are a major safety risk for elderly and mobility-impaired individuals. This project presents an **energy-efficient IoT wearable** capable of **real-time fall detection** and **fall-risk prediction** using **multi-sensor fusion** and **on-device machine learning (TinyML)**.

The system is built around **ESP32-C3**, ensuring **low latency**, **privacy (cloud-free inference)**, and suitability for wearable deployment.

---

## Objectives
- Acquire real-time motion + altitude/pressure signals from wearable sensors
- Fuse multi-sensor data for improved reliability
- Perform **embedded ML inference** using a lightweight model
- Trigger **immediate alert** upon fall detection (LED/Buzzer)

---

## System Architecture
Overall pipeline:

**Sensors → Preprocessing → Feature Extraction → TinyML Inference → Alert**

<img width="303" height="599" alt="image" src="https://github.com/user-attachments/assets/b2980494-c82c-480d-9048-e0d30ef86acb" />

Key processing includes:
- Sensor acquisition in real time
- Noise reduction and normalization
- Sliding window segmentation
- Feature extraction / sensor fusion
- On-device inference and alert triggering

---

## Hardware Design

<img width="750" height="298" alt="image" src="https://github.com/user-attachments/assets/5298b8a7-76a7-4b52-a961-b813caa090f5" />

### Components Used
- **ESP32-C3 Dev Board** (main controller)
- **MPU6050 / MPU9250** (accelerometer + gyroscope)
- **BMP280** (pressure/altitude sensing)
- **Li-ion Battery (3.7V)**
- **AMS1117 regulator (3.3V)**
- **LED / Buzzer** (alert mechanism)

### Circuit & Connections (I²C)
Sensors communicate via **I²C**.

| Signal | ESP32-C3 | Sensor |
|-------|----------|--------|
| VCC   | 3.3V     | VCC    |
| GND   | GND      | GND    |
| SDA   | GPIO8    | SDA    |
| SCL   | GPIO9    | SCL    |

I²C addresses:
- MPU6050: `0x68`
- BMP280: `0x76`

---

## Software Methodology

### Data Pipeline
- Sensor sampling (real-time streaming)
- Noise reduction + normalization
- Sliding window segmentation
- Feature extraction (statistical motion + fused features)

### TinyML Deployment
- Model trained offline using Python/TensorFlow
- Converted to **TensorFlow Lite Micro**
- **Post-training quantization (int8)** for smaller size and faster inference
- On-device inference executed on ESP32-C3 in real time

---

## Dataset Information
Primary dataset used for training and evaluation:
- **SisFall dataset** (fall types + daily activities based on IMU signals)

---

## Model Architecture (Summary)
- Lightweight **CNN classifier** designed for embedded deployment
- Output classes: **ADL / Fall** (or multi-class depending on experiment design)
- Uses multi-sensor fusion features for improved robustness

---

## Experimental Results & Performance
Summary outcomes:
- Overall accuracy: **~91%**
- Real-time inference latency: **<100 ms**
- Quantized deployment enables low memory usage and stable ESP32 inference

Performance evaluation was carried out using:
- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix analysis

---

## Conclusion
This project demonstrates a practical **low-power TinyML wearable** for fall detection and fall-risk prediction using **multi-sensor fusion**. By deploying a **quantized embedded ML model** directly on ESP32-C3, the system achieves **high accuracy**, **low latency**, and **privacy-preserving operation**, making it suitable for assistive healthcare and continuous monitoring applications.

---

## Repo Structure
- docs/ -> report/presentation
- images/ -> diagrams, prototype photos, results plots
- hardware/ -> BOM + wiring notes
- software/ -> firmware + ML pipeline
- results/ -> evaluation metrics and output
