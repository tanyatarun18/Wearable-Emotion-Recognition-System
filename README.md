# Wearable Emotion Recognition System Using IoT Sensors and Deep Learning

This repository contains the complete system architecture, patent documentation, and the trained AI model for a "Wearable Emotion Recognition System." This project is designed to capture and interpret physiological signals from IoT sensors to provide real-time emotional state classification.

This repository is broken into three main files:

1.  **`patent.docx`**: The full patent disclosure, including all system architecture diagrams (Flowchart, State Chart, and Sequence Diagram).

2.  **`training.ipynb`**: The complete Google Colab (Python/TensorFlow) notebook used to process the data, build, and train the AI model.

3.  **`emotion_detection.tflite`**: The final, trained, and exported TensorFlow Lite model, ready for deployment in a mobile app.

---

## 1. The AI Model (The "Brain")

The core of this invention is a Deep Learning model that can find complex patterns in physiological data. The model was trained on the public **WESAD (Wearable Stress and Affect Detection)** dataset.

* **Model Type:** Convolutional Neural Network (CNN) for feature extraction, combined with a Long Short-Term Memory (LSTM) network for temporal pattern analysis.

* **Sensors Used:** Electrodermal Activity (EDA), Blood Volume Pulse (BVP for HRV), Accelerometer (Motion), and Skin Temperature.

* **Emotions Classified:** `Baseline` (Calm), `Stress`, `Amusement`.

### Files

* **[Training Notebook (`.ipynb`)](./training.ipynb)**: The complete Google Colab notebook used to process the WESAD data, build the model, and train it.

* **[Exported Model (`.tflite`)](./emotion_detection.tflite)**: The final, trained, and exported TensorFlow Lite model. This file is ready to be deployed into a mobile application.

---

## 2. Patent & System Architecture

This project is fully documented in the provided patent disclosure, which includes a detailed description of the invention, its novelty compared to existing art, and its system logic.

* **[Full Patent Document](./patent.docx)**: The complete patent disclosure file.

### System Logic Diagrams

The system's logic is defined by three core diagrams, which are **all included within the `patent.docx` file.**

#### Figure 1: System Data Flowchart

**(See `patent.docx` for this diagram)**

This diagram shows the high-level flow of data, from the IoT sensors, through the AI "brain," and into the user feedback loop for refinement.

#### Figure 2: System State Chart

**(See `patent.docx` for this diagram)**

This diagram defines the system's "states" as a state machine. It shows how the system moves from `Idle` to `Monitoring`, what happens when an `AnomalyDetected` (like "Stress") occurs, and how the `FeedbackLoop` works to refine the model.

#### Figure 3: System Sequence Diagram

**(See `patent.docx` for this diagram)**

This diagram shows the exact order of messages between the components. It illustrates how the `Wearable Sensors` send data to the `AI System`, which sends a prediction to the `Application`, which then alerts the `Patient (User)` and collects feedback.

---

## Dataset

This model was trained on the **WESAD (Wearable Stress and Affect Detection)** dataset.

* **Link:** [https://archive.ics.uci.edu/dataset/507/wesad+wearable+stress+and+affect+detection](https://archive.ics.uci.edu/dataset/507/wesad+wearable+stress+and+affect+detection)
