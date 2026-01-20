# Adaptive Low-Power IoT Wearable for Fall Risk Prediction (TinyML + Sensor Fusion)

> **3-Credit Semester Project | IoT + Embedded ML | Real-Time Wearable System**

📌 A low-power wearable device that performs fall detection and fall-risk prediction using multi-sensor fusion and on-device TinyML inference (ESP32-C3 + TFLite Micro).

---

## 🖼️ Project Banner (Add Here)
**Add:** `images/banner.png` *(prototype photo / poster-style banner)*

```md
![Project Banner](images/banner.png)
Project Overview
Falls are a major safety risk for elderly and mobility-impaired individuals. This project presents an energy-efficient IoT wearable capable of real-time fall detection and fall-risk prediction using multi-sensor fusion and on-device machine learning (TinyML).

The system is built around ESP32-C3, ensuring low latency, privacy (cloud-free inference), and suitability for wearable deployment.

Objectives
Acquire real-time motion + altitude/pressure signals from wearable sensors

Fuse multi-sensor data for improved reliability

Perform embedded ML inference using a lightweight model

Trigger immediate alert upon fall detection (LED/Buzzer)

System Architecture
Overall flow:

Sensors → Preprocessing → Feature Extraction → TinyML Inference → Alert

🖼️ Add Architecture Diagram Here
Add: images/system_architecture.png

![System Architecture](images/system_architecture.png)
Hardware Design
Components Used
ESP32-C3 Dev Board (main controller)

MPU6050 / MPU9250 (accelerometer + gyroscope)

BMP280 (pressure/altitude sensing)

Li-ion Battery (3.7V)

AMS1117 regulator (3.3V)

LED / Buzzer (alert)

🖼️ Add Prototype Photo Here
Add: images/hardware_prototype.jpg

![Hardware Prototype](images/hardware_prototype.jpg)
Circuit & Connections (I²C)
Sensors communicate via I²C.

Signal	ESP32-C3	Sensor
VCC	3.3V	VCC
GND	GND	GND
SDA	GPIO8	SDA
SCL	GPIO9	SCL
I²C addresses:

MPU6050: 0x68

BMP280: 0x76

🖼️ Add Circuit/Wiring Diagram Here
Add: images/circuit_diagram.png

![Circuit Diagram](images/circuit_diagram.png)
Software Methodology
Data Pipeline
Sensor sampling (real-time streaming)

Noise reduction + normalization

Sliding window segmentation

Feature extraction (motion statistics + fused features)

TinyML Deployment
Model trained offline (Python/TensorFlow)

Converted to TensorFlow Lite Micro

int8 quantization to reduce size and speed up inference

Embedded inference executed on ESP32-C3

🖼️ Add Workflow / Pipeline Diagram Here
Add: images/workflow_flowchart.png

![Workflow](images/workflow_flowchart.png)
Dataset Information
Training and evaluation were performed using:

SisFall dataset (fall types + daily activities using IMU signals)

(More dataset details and references are available in the full report.)

Model Architecture (Summary)
Lightweight CNN classifier designed for embedded deployment

Output classes: ADL / Fall (or multi-class depending on experiment)

Uses multi-sensor fusion features for improved robustness

(Full architecture details are provided in the report.)

Experimental Results & Performance
Key Results (Summary)
Accuracy: ~91%

Real-time inference latency: <100 ms

Quantized model enabled low memory usage and stable ESP32 inference

🖼️ Add Confusion Matrix Here
Add: images/confusion_matrix.png

![Confusion Matrix](images/confusion_matrix.png)
🖼️ Add Serial Output Proof Here
Add: images/serial_output.png (Arduino Serial Monitor output: “Fall Detected”)

![Live Output](images/serial_output.png)
(Optional but recommended)

🖼️ Add Accuracy/Loss Curves Here
Add:

images/accuracy_curve.png

images/loss_curve.png

![Accuracy Curve](images/accuracy_curve.png)
![Loss Curve](images/loss_curve.png)
Conclusion
This project successfully demonstrates a low-power TinyML wearable for fall detection and fall-risk prediction using multi-sensor fusion. By deploying a quantized embedded ML model directly on ESP32-C3, the system achieves high accuracy, low latency, and privacy-preserving operation, making it suitable for real-world assistive healthcare monitoring.

Documentation
Full project report: docs/Project report - Final.pdf
