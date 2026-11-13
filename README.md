# 🔢 Handwritten Digit Recognition using CNN and AlexNet-style Network (TensorFlow)

Two Convolutional Neural Networks built in **TensorFlow** to classify handwritten digits from the **MNIST** dataset: a simple 2-layer CNN and a deeper AlexNet-style network. The project compares both models on test accuracy.

![Python](https://img.shields.io/badge/Python-3.5-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-1.x-orange)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626)

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Dataset](#-dataset)
- [Project Workflow](#-project-workflow)
- [Model Architectures](#-model-architectures)
- [Results](#-results)
- [Limitations & Future Improvements](#-limitations--future-improvements)
- [Repository Structure](#-repository-structure)
- [Getting Started](#-getting-started)
- [Tech Stack](#-tech-stack)

---

## 🔍 Overview

Handwritten digit recognition is a classic computer vision task used in postal sorting, bank cheque reading and form digitisation. This project trains and compares two CNNs:

1. A **simple CNN** with 2 convolution layers
2. An **AlexNet-style CNN** with 3 convolution layers, local response normalisation and an extra fully connected layer

---

## 📊 Dataset

- **Name:** MNIST handwritten digits
- **Images:** 28 × 28 grayscale, 10 classes (digits 0–9)
- **Split (via `input_data.py`):** 55,000 training, 5,000 validation, 10,000 test images
- **Preprocessing:** pixel values scaled from [0, 255] to [0, 1]; labels one-hot encoded

`input_data.py` downloads the MNIST files automatically on first run and provides mini-batches through `next_batch()`.

---

## 🛠 Project Workflow

1. **Load data:** download and read MNIST with `input_data.read_data_sets`.
2. **Define parameters:** learning rate, iterations, batch size, dropout probability.
3. **Create TensorFlow placeholders** for images, labels and dropout.
4. **Initialise weights and biases** for each convolution and fully connected layer.
5. **Build the network:** Convolution → ReLU → Max Pooling → Dropout stages, followed by fully connected layers and a 10-class output.
6. **Loss and optimizer:** softmax cross-entropy loss with the Adam optimizer.
7. **Train** on mini-batches, printing the loss every 100 iterations.
8. **Evaluate** accuracy on the 10,000-image test set (dropout switched off).

---

## 🧠 Model Architectures

| | Simple CNN (`TensorFlow.ipynb`) | AlexNet-style CNN (`AlexNet(TensorFlow).ipynb`) |
|---|---|---|
| Convolution layers | 2 (5×5; 32 and 64 filters) | 3 (3×3; 64, 128 and 256 filters) |
| Extra layers | Max pooling, dropout | Max pooling, Local Response Normalisation, dropout |
| Fully connected | 1024 → 10 | 1024 → 1024 → 10 |
| Learning rate | 0.001 | 0.01 |
| Batch size | 128 | 64 |
| Iterations | 1000 | 3000 |
| Dropout keep probability | 0.5 | 0.75 |
| Optimizer | Adam | Adam |

---

## 📈 Results

| Model | Test Accuracy |
|---|---|
| Simple CNN | **86.44%** |
| AlexNet-style CNN | **94.12%** |

The deeper AlexNet-style network clearly outperforms the simple CNN. Adding more convolution layers, normalisation and longer training improved accuracy by about 7.7 percentage points.

---

## 🚧 Limitations & Future Improvements

- [ ] Use better weight initialisation (Xavier/He) instead of `random_normal` with standard deviation 1, which causes very large loss values
- [ ] Add Batch Normalisation and a lower learning rate for more stable training
- [ ] Train longer and use the validation set for hyperparameter tuning
- [ ] Add data augmentation (rotation, shifts)
- [ ] Track validation accuracy and plot loss/accuracy curves
- [ ] Migrate the code from TensorFlow 1.x to TensorFlow 2 / Keras

---

## 📁 Repository Structure

```
├── TensorFlow.ipynb                # Simple 2-layer CNN
├── AlexNet(TensorFlow).ipynb       # AlexNet-style CNN
├── input_data.py                   # MNIST download and batch loader
└── README.md                       # Project documentation
```

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>
```

### 2. Install dependencies

The notebooks use the TensorFlow 1.x API (`tf.placeholder`, `tf.Session`), so use TensorFlow 1.x:

```bash
pip install "tensorflow<2" numpy six jupyter
```

### 3. Launch a notebook

```bash
jupyter notebook
```

Open `TensorFlow.ipynb` or `AlexNet(TensorFlow).ipynb` and run all cells. MNIST is downloaded automatically on the first run.

> **Note:** the notebooks import `tensorflow.examples.tutorials.mnist`. If this is unavailable in your TensorFlow version, use the included `input_data.py` instead: `import input_data`.

---

## 🧰 Tech Stack

- **Language:** Python
- **Deep learning:** TensorFlow 1.x
- **Data handling:** NumPy, six
- **Environment:** Jupyter Notebook

---

## 📚 Reference

[TensorFlow Examples: Convolutional Network](https://github.com/aymericdamien/TensorFlow-Examples/blob/master/notebooks/3%20-%20Neural%20Networks/convolutional_network.ipynb)

---
