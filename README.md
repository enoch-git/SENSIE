# SENSIE: Continuous Vital Sign Tracking & Alert System for Seniors 👴👵

[![Hardware: ESP32-S3](https://img.shields.io/badge/Hardware-ESP32--S3-blue.svg)](#)
[![EDA: KiCad 9](https://img.shields.io/badge/EDA-KiCad_9-orange.svg)](#)
[![CAD: Autodesk Fusion](https://img.shields.io/badge/CAD-Autodesk_Fusion-red.svg)](#)
[![Firmware: C++](https://img.shields.io/badge/Firmware-C++-00599C.svg)](#)
[![Backend: Python/Flask](https://img.shields.io/badge/Backend-Python%20%7C%20Flask-green.svg)](#)

> **SENSIE** is an end-to-end, IoT-enabled wearable wristband designed to protect seniors by continuously tracking vital signs around the clock. Featuring a custom-designed PCB, ergonomic 3D-printed enclosure, edge anomaly detection, and a real-time health dashboard, SENSIE bridges the gap between independent living and instant caregiver intervention.

---

## 📸 Product Preview

| Assembled Wearable | Custom PCB Layout (KiCad 9) | Health Dashboard |
| :---: | :---: | :---: |
| ![SENSIE Wearable](SENSIE_MEDIA/view3.png) | ![PCB Routing](SENSIE_MEDIA/view4.png) 

---

## ✨ Key Features

* **24/7 Continuous Monitoring:** Real-time tracking of Heart Rate (BPM) and Blood Oxygen Saturation ($\text{SpO}_2$) utilizing the high-sensitivity MAX30102 optical sensor.
* **Edge Anomaly Detection:** On-device **Moving Average** algorithm implemented in C++ to establish dynamic user baselines, filter out motion artifacts, and instantly flag abnormal vitals.
* **Instant Caregiver Alerts:** Wi-Fi enabled automatic alerts triggered immediately upon detecting critical thresholds or irregular patterns.
* **Historical Health Dashboard:** A responsive web interface built with Python and Flask that logs trend data, allowing family members and healthcare providers to review past health events anytime.
* **Custom Hardware & Ergonomics:** Purpose-built two-layer PCB routed in KiCad 9, housed in a custom PLA wristband enclosure designed in Autodesk Fusion.

---

## 🏗️ System Architecture

SENSIE operates on a three-tier architecture: **Edge Sensing & Processing**, **Wireless Transmission**, and **Cloud Logging & Visualization**.

```text
+-----------------------------------------------------------------+
|                       SENSIE WRISTBAND                          |
|                                                                 |
|  +----------------+      I2C      +--------------------------+  |
|  | MAX30102       | ------------> | ESP32-S3-WROOM-1         |  |
|  | (HR & SpO2)    |               | (C++ / Moving Average)   |  |
|  +----------------+               +--------------------------+  |
|                                                 |               |
|  +----------------+                             | Wi-Fi         |
|  | TP4056 ESOP8   | <--- Li-Ion Battery         | (HTTP/REST)   |
|  +----------------+                             |               |
+-------------------------------------------------|---------------+
                                                  v
                                    +--------------------------+
                                    | Python / Flask Server    |
                                    | (API & Data Processing)  |
                                    +--------------------------+
                                                  |
                                                  v
                                    +--------------------------+
                                    | Caregiver Dashboard      |
                                    | (History & Alert Logs)   |
                                    +--------------------------+
