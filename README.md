# ✍️ MNIST Handwritten Digit Classification using CNN (TensorFlow)

This repository contains a Deep Learning project for classifying handwritten digits (0–9) from the **MNIST dataset** using **Convolutional Neural Networks (CNN)** built with **TensorFlow**.

---

## 📌 Project Overview
The goal of this project is to recognize handwritten digits accurately from 28x28 grayscale images. The project explores two different CNN architectures: a baseline 2-layer CNN model and a deeper AlexNet-style 3-layer CNN model with Local Response Normalization.

---

## 🏗️ Model Architectures & Comparisons

| Model / Notebook | Architecture Highlights | Iterations / Batch | Test Accuracy |
| :--- | :--- | :--- | :--- |
| **`MNIST_Simple_CNN.ipynb`** | 2 Conv Layers (5x5 filters) + MaxPool + Dropout + 2 FC Layers | 1,000 iters / Batch 128 | **86.44%** |
| **`MNIST_AlexNet_CNN.ipynb`** | 3 Conv Layers (3x3 filters) + MaxPool + LRN + Dropout + 3 FC Layers | 3,000 iters / Batch 64 | **94.12%** |

---

## 📁 Repository Structure
```text
├── input_data.py             # Data loader script to download and parse MNIST files
├── MNIST_Simple_CNN.ipynb    # Baseline 2-layer CNN implementation
├── MNIST_AlexNet_CNN.ipynb   # Deeper 3-layer AlexNet-style CNN implementation
└── README.md                 # Project documentation
