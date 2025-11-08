# Wearable Emotion Recognition System Using IoT Sensors and Deep Learning

This repository contains the complete AI model and training notebook for a "Wearable Emotion Recognition System." This project is designed to capture and interpret physiological signals from IoT sensors to provide real-time emotional state classification.

This repository contains two main files:
1.  **`Training.ipynb`**: The complete Google Colab (Python/TensorFlow) notebook used to process the data, build, and train the AI model.
2.  **`emotion_model.tflite`**: The final, trained, and exported TensorFlow Lite model, ready for deployment in a mobile app.

---

## Project Details & AI Model

The core of this project is a Deep Learning model that can find complex patterns in physiological data. The entire process of data handling, model creation, and training is documented in the `Training.ipynb` file.

### 1. Dataset & Pre-processing

The model was trained on the public **WESAD (Wearable Stress and Affect Detection)** dataset. A significant part of this project involved processing this complex, multi-modal data.

The following steps were performed:
1.  **Loaded Data:** Raw subject data was loaded from the `.pkl` files.
2.  **Handled Multi-Frequency Signals:** The raw data streams were recorded at different sampling rates (e.g., BVP @ 64Hz, ACC @ 32Hz, EDA @ 4Hz, TEMP @ 4Hz, and labels @ 700Hz).
3.  **Signal Resampling:** To synchronize the data, all sensor streams were resampled to a common frequency of **4Hz**.
4.  **Feature Combination:** The resampled signals were combined into a single feature array with **6 features**:
    * 3-axis Accelerometer (ACC-X, ACC-Y, ACC-Z)
    * Blood Volume Pulse (BVP)
    * Electrodermal Activity (EDA)
    * Temperature (TEMP)
5.  **Windowing:** The continuous data was segmented into **30-second "windows"** with a 15-second overlap. This resulted in an input shape of `(120, 6)` for the model (120 samples = 30s @ 4Hz).
6.  **Labeling:** Each window was assigned a single label—`Baseline` (0), `Stress` (1), or `Amusement` (2)—based on the most frequent label in that window.
7.  **Scaling:** All features were scaled using `StandardScaler` from scikit-learn.

### 2. Model Architecture

A hybrid **Convolutional Neural Network (CNN) + Long Short-Term Memory (LSTM)** model was built using TensorFlow/Keras. This architecture is designed to first capture spatial features from the sensor data (the CNN) and then learn the temporal patterns in those features (the LSTM).

The model's architecture is as follows:

| Layer | Type | Output Shape | Parameters |
| :--- | :--- | :--- | :--- |
| `input_layer` | Input | (None, 120, 6) | 0 |
| `conv1d_1` | Conv1D | (None, 120, 64) | 1,984 |
| `maxpool_1` | MaxPooling1D | (None, 60, 64) | 0 |
| `lstm_1` | LSTM | (None, 128) | 98,816 |
| `dense_1` | Dense | (None, 64) | 8,256 |
| `output_layer` | Dense (Softmax) | (None, 3) | 195 |
| **Total** | | | **109,251** |

### 3. Training & Results

The model was trained on the processed data with the following results:

* **Final Test Accuracy: 98.33%**

*(Note: This high accuracy was achieved on a subset of the WESAD data (Subjects S16 & S8). While this proves the model's effectiveness in learning patterns from known subjects, training on a larger and more diverse pool of subjects would be required for a generalized, production-ready system.)*

The final trained model was then converted to a **TensorFlow Lite (`.tflite`)** file, making it lightweight and ready for on-device inference in a mobile application. The conversion successfully used `SELECT_TF_OPS` to ensure the LSTM layer was compatible.

---

## Dataset Used

* **WESAD (Wearable Stress and Affect Detection)**
* **Link:** [https://archive.ics.uci.edu/dataset/507/wesad+wearable+stress+and+affect+detection](https://archive.ics.uci.edu/dataset/507/wesad+wearable+stress+and+affect+detection)
