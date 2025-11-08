# Wearable Emotion Recognition System Using IoT Sensors and Deep Learning

This repository contains the complete AI model and training notebook for a "Wearable Emotion Recognition System." This project is designed to capture and interpret physiological signals from IoT sensors to provide real-time emotional state classification.

This repository contains two main files:
1.  **`Training.ipynb`**: The complete Google Colab (Python/TensorFlow) notebook used to process the WESAD data, build, and train the AI model.
2.  **`emotion_model.tflite`**: The final, trained, and exported TensorFlow Lite model, ready for deployment in a mobile app.

---

## The AI Model (The "Brain")

The core of this project is a Deep Learning model that can find complex patterns in physiological data. The model was trained on the public **WESAD (Wearable Stress and Affect Detection)** dataset.

* **Model Type:** Convolutional Neural Network (CNN) for feature extraction, combined with a Long Short-Term Memory (LSTM) network for temporal pattern analysis.
* **Sensors Used:** Electrodermal Activity (EDA), Blood Volume Pulse (BVP for HRV), Accelerometer (Motion), and Skin Temperature.
* **Emotions Classified:** `Baseline` (Calm), `Stress`, `Amusement`.

### Files
* **[Training Notebook (`.ipynb`)](./Training.ipynb)**: The complete Google Colab notebook used to process the WESAD data, build the model, and train it.
* **[Exported Model (`.tflite`)](./emotion_model.tflite)**: The final, trained, and exported TensorFlow Lite model. This file is ready to be deployed into a mobile application.

---

## Dataset

This model was trained on the **WESAD (Wearable Stress and Affect Detection)** dataset.
* **Link:** [https://archive.ics.uci.edu/dataset/507/wesad+wearable+stress+and+affect+detection](https://archive.ics.uci.edu/dataset/507/wesad+wearable+stress+and+affect+detection)
