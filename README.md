Wearable Emotion Recognition System Using IoT Sensors and Deep Learning

This repository contains the complete system architecture, patent documentation, and the trained AI model for a "Wearable Emotion Recognition System." This project is designed to capture and interpret physiological signals from IoT sensors to provide real-time emotional state classification.

This project is broken into two main components:

The System Architecture (The "Patent"): A detailed breakdown of the invention, its components, and its logic.

The AI Model (The "Brain"): A trained CNN-LSTM model capable of classifying emotional states from sensor data.

1. The AI Model (The "Brain")

The core of this invention is a Deep Learning model that can find complex patterns in physiological data. The model was trained on the public WESAD (Wearable Stress and Affect Detection) dataset.

Model Type: Convolutional Neural Network (CNN) for feature extraction, combined with a Long Short-Term Memory (LSTM) network for temporal pattern analysis.

Sensors Used: Electrodermal Activity (EDA), Blood Volume Pulse (BVP for HRV), Accelerometer (Motion), and Skin Temperature.

Emotions Classified: Baseline (Calm), Stress, Amusement.

Files

Training Notebook (.ipynb): The complete Google Colab (Python/TensorFlow) notebook used to process the WESAD data, build the model, and train it.

Exported Model (.tflite): The final, trained, and exported TensorFlow Lite model. This 135KB file is ready to be deployed into a mobile application.

2. Patent & System Architecture

This project is fully documented in the provided patent disclosure, which includes a detailed description of the invention, its novelty compared to existing art, and its system logic.

Full Patent Document: The complete patent disclosure file.

System Logic Diagrams

The system's logic is defined by three core diagrams, which correspond to the software implementation.

Figure 1: System Data Flowchart

This diagram shows the high-level flow of data, from the IoT sensors, through the AI "brain," and into the user feedback loop.

Figure 2: System State Chart

This diagram defines the system's "states" as a state machine. It shows how the system moves from Idle to Monitoring, what happens when an AnomalyDetected (like "Stress") occurs, and how the FeedbackLoop works to refine the model.

Figure 3: System Sequence Diagram

This diagram shows the exact order of messages between the components. It illustrates how the Wearable Sensors send data to the AI System, which sends a prediction to the Application, which then alerts the Patient (User) and collects feedback.

Dataset

This model was trained on the WESAD (Wearable Stress and Affect Detection) dataset.

Link: https://archive.ics.uci.edu/dataset/507/wesad+wearable+stress+and+affect+detection

Future Work (Next Steps)

With the system architecture defined and the AI model trained, the next logical step is the front-end implementation:

Mobile Application: Integrate the emotion_model.tflite file into a mobile app (using Flutter or React Native).

Hardware Integration: Connect the app to a real-world IoT wearable via Bluetooth Low Energy (BLE).

Complete the Feedback Loop: Connect the app to a Firebase backend. When a user provides feedback (as shown in Figure 2), the app uploads the data, which can be used to periodically re-train and improve the AI model.
