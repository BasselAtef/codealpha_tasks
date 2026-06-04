# 🎵 Simple AI Music Generator

A lightweight Python notebook that trains a single-layer LSTM neural network on JSB Chorales melody data to generate new, simple melodies exported directly as MIDI files.

## 🚀 Features

* **Automated Dataset Download:** Fetches and extracts the JSB Chorales dataset.
* **Data Preprocessing:** Extracts single-voice melodies and converts MIDI note values into structured sequence pairs ($SEQ\_LEN = 30$).
* **LSTM Architecture:** Implements an Embedding layer, an LSTM layer, and a Softmax Dense layer via TensorFlow/Keras.
* **Smart Training:** Utilizes `EarlyStopping` and `ModelCheckpoint` callbacks to preserve the best model weights and prevent overfitting.
* **Probabilistic Generation:** Generates 100 new sequential notes based on model probability distributions rather than deterministic argmax.
* **MIDI Export:** Uses `music21` to output the generated melody into a playable `simple_output.mid` file.

---

## 🛠️ Requirements & Installation

Before running the notebook, ensure you have the required dependencies installed:

```bash
pip install music21 tensorflow numpy

```

---

## 📂 Project Structure & Workflow

The code inside `MusicGenAi.ipynb` follows a clean 7-step pipeline:

| Step | Objective | Description |
| --- | --- | --- |
| **1** | **Setup** | Installs and imports libraries (`tensorflow`, `music21`, `numpy`). |
| **2** | **Data Load** | Downloads `jsb-chorales-quarter.pkl` (229 training tracks). |
| **3** | **Preprocessing** | Extracts the primary melody voice, maps unique notes, and creates overlapping sequences. |
| **4** | **Model Architecture** | Defines the Keras Sequential model and compiles it using `adam` and `categorical_crossentropy`. |
| **5** | **Training** | Trains for up to 50 epochs (automatically early-stops around epoch 16 based on validation loss). |
| **6** | **Music Generation** | Seeds the model with a random sequence to predict 100 sequential notes. |
| **7** | **Export** | Builds a `music21` stream and writes the performance to `simple_output.mid`. |

---

## 📊 Model Summary

```text
Layer (type)                      Output Shape                Param #
=====================================================================
embedding (Embedding)             (None, 30, 64)              2,432
lstm (LSTM)                       (None, 128)                 98,816
dense (Dense)                     (None, 38)                  4,902
=====================================================================
Total params: 106,150 (414.65 KB)

```

---

## 🎮 How to Use

1. Open `MusicGenAi.ipynb` in Google Colab or your local Jupyter environment.
2. (Optional) Enable GPU acceleration for faster training (though the lightweight model trains in under a minute on CPU).
3. Run all cells.
4. Download and play your freshly composed `simple_output.mid` file in any media player (eg. Windows Media Player).