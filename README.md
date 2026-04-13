# ESP32-Smart-Inventory

Project Overview: Real-Time Smart Inventory System
This project is an IoT-based solution designed to automate stock monitoring and inventory tracking. Developed and simulated entirely on the Wokwi platform, it utilizes an ESP32 microcontroller to track item quantity and weight in real-time.

Key Features:

Distance-Based Tracking: Uses an HC-SR04 Ultrasonic sensor to monitor the height/level of stock in a container.

Weight Simulation: Integrates a potentiometer to simulate load-cell (weight) data.

Blynk IoT Integration: Features a live mobile/web dashboard for remote monitoring.

Local Display: I2C LCD 16x2 for real-time status updates without needing a phone.

Automatic Alerts: An integrated buzzer system that triggers a "Low Stock" warning when inventory drops below 20%.

Tech Stack:

Hardware: ESP32 (Simulation)

Sensors: Ultrasonic HC-SR04, Potentiometer

Platform: Blynk IoT Cloud

Simulation Environment: Wokwi

Language: C++ (Arduino Framework)
