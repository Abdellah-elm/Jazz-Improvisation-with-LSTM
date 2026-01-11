# 🎷 Jazz Solo Generation with LSTM Networks

This project implements a sequence model based on **Long Short-Term Memory (LSTM)** networks to generate original jazz music. By learning the patterns, rhythms, and structures found in a dataset of jazz compositions, the model can "improvise" its own musical sequences.

## 📌 Project Overview

Music is a sequence of values (notes, durations, and pitches) that follow specific temporal patterns. Standard Neural Networks fail to capture these dependencies, but **LSTMs** are specifically designed to remember information over long periods, making them ideal for music synthesis.

In this project, I built a model that:

1. Processes a corpus of jazz music.
2. Trains an LSTM to predict the next note in a sequence.
3. Uses **inference-time sampling** to generate a completely new 20-beat jazz solo.

---

## 🛠️ Technical Architecture

The model utilizes the **Keras Functional API**, which allows for more complex structures than the Sequential API. This is particularly useful here because the model needs to share weights across different time steps during the generation phase.

### Key Components:

* **Input Layer:** Categorical musical values (represented as one-hot vectors).
* **LSTM Layer:** 64 hidden units that capture the "style" and "melody" of the jazz samples.
* **Dense Layer + Softmax:** Outputs a probability distribution over the 78 possible unique musical values.
* **Weight Sharing:** The same LSTM cell and Dense layers are reused across  time steps during inference to ensure consistency in the generated "voice."

---

## 🎵 How Music is Generated

Unlike standard classification, music generation happens in a loop:

1. **Seed:** Provide an initial input (usually a zero-vector or a starting note).
2. **Predict:** The model outputs a probability distribution for the next note.
3. **Sample:** A note is chosen (sampled) from that distribution.
4. **Feedback:** The chosen note is fed back into the LSTM as the input for the next time step.

---

## 🚀 Getting Started

### Prerequisites

* Python 3.x
* TensorFlow / Keras
* Music21 (for MIDI processing)
* NumPy & Matplotlib

### Installation

```bash
git clone [https://github.com/your-username/jazz-lstm-generator.git](https://github.com/Abdellah-elm/Jazz-Improvisation-with-LSTM)
cd Jazz-Improvisation-with-LSTM
pip install -r requirements.txt

```

### Dataset

The model is trained on a dataset of jazz snippets formatted into values representing pitches and durations. These are pre-processed into  (sequences of 30 notes) and  (the note immediately following the sequence).

---

## 📊 Results

After training for ~100 epochs, the model begins to transition from random noise to structured melodic patterns.

* **Training Loss:** Successfully minimized Categorical Crossentropy.
* **Output:** The generated MIDI files can be found in the `/output` folder.

> **Note:** The "creativity" of the model can be adjusted by introducing a "temperature" parameter during sampling to make the solo more predictable or more chaotic.

---

## 🎓 Acknowledgments

This project was completed as part of the **Deep Learning Specialization (Sequence Models)** by DeepLearning.AI on Coursera.

---
