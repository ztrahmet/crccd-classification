# 🔬 CRCCD Classification: Deep Learning Benchmark

### Comparative Analysis of CNN Architectures for Colorectal Cancer Detection

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)
![Platform](https://img.shields.io/badge/Platform-Google%20Colab-orange)
![Status](https://img.shields.io/badge/Status-Research%20Complete-success)

## 📖 Overview

This project presents a comprehensive benchmark study of Deep Learning methods for the automated classification of colorectal cancer tissues. Utilizing the **CRCCD_V1 (Colorectal Cancer Classification and Detection)** dataset, the study evaluates the performance of **10 different CNN architectures**, ranging from lightweight mobile models to heavy transfer learning networks and custom-designed architectures.

The entire pipeline—from data acquisition to model evaluation—is implemented in a **single, comprehensive Jupyter Notebook**, designed for seamless execution on **Google Colab**.

---

## 🏆 Benchmark Results

The study benchmarks heavy architectures (`DenseNet169`, `InceptionResNetV2`), lightweight mobile models (`MobileNetV2`, `NASNetMobile`), and a custom CNN (`OzNET`) trained from scratch.

| Model | Accuracy | F1-Score | Kappa | Performance Note |
| :--- | :--- | :--- | :--- | :--- |
| **DenseNet169** | **93.91%** | **0.9388** | **0.9344** | 🏆 **SOTA Performance** |
| **DenseNet121** | 92.53% | 0.9249 | 0.9196 | Highly stable training. |
| **MobileNetV2** | **92.31%** | 0.9228 | 0.9171 | 🚀 **Best Efficiency/Speed Balance**. |
| InceptionV3 | 91.39% | 0.9132 | 0.9073 | Strong generalization. |
| Xception | 90.63% | 0.9055 | 0.8991 | Fast convergence. |
| OzNET (Custom) | 81.11% | 0.8056 | 0.7965 | Strong baseline for scratch training. |

*(Full results for all 10 models are detailed in the notebook.)*

---

## 📂 Repository Structure

This repository is structured for simplicity and reproducibility. The core analysis is contained within a single notebook, while outputs are stored separately.

```text
.
├── crccd_benchmarking.ipynb    # End-to-End pipeline (Data DL, Preprocessing, Training, Eval)
├── models_and_plots/           # Generated artifacts (Confusion Matrices, ROC Curves, Training Logs)
└── README.md                   # Project documentation

```

* **crccd_benchmarking.ipynb:** Handles the entire workflow. It connects to Google Drive, downloads the CRCCD dataset dynamically (or loads from Drive), performs augmentation, trains selected models, and visualizes results.
* **models_and_plots/:** Contains the visual outputs of the analysis, including confusion matrices and performance graphs generated during the study.

---

## 🚀 Usage & Reproduction

The easiest way to reproduce the results is using **Google Colab**.

1. **Open the Notebook:**
Click the file `crccd_benchmarking.ipynb` in this repository and open it.
2. **Open in Colab:**
Replace the GitHub URL with `colab.research.google.com/github/...` or download the `.ipynb` file and upload it to Colab.
3. **Data Setup (Automatic):**
The notebook includes a script to download/extract the dataset. Ensure you have the necessary API keys or Drive permissions if the dataset source requires authentication (the code handles Drive mounting).
4. **Run All:**
Select `Runtime` > `Run all` to execute the pipeline.
* *Note: Training 10 models may take significant time. It is recommended to use a GPU runtime (T4 or better).*



---

## 📉 Key Insights & Analysis

### 1. The "Esophagitis" vs. "Z-Line" Challenge

A consistent pattern observed across almost all models—including the top-performing DenseNet169—was the confusion between **'ESOPHAGITIS'** and **'Z-LINE'** classes.

* **Reason:** Morphological similarity and color histogram overlap between these two tissue types.
* **Impact:** This specific confusion was the primary factor preventing models from reaching >95% accuracy.

### 2. Efficiency of Mobile Architectures

**MobileNetV2** achieved **92.31%** accuracy, trailing the massive DenseNet169 by only ~1.6%. This demonstrates that lightweight models are viable candidates for deploying diagnostic support systems on portable medical devices.

### 3. Custom vs. Transfer Learning

While the custom **OzNET** model (81.11%) outperformed random guessing significantly, it highlighted the immense value of **Transfer Learning** in medical imaging where labeled data is scarce.

---

## 👨‍💻 Author

**Ahmet Öztürk**

---

## ⚠️ Academic Disclaimer

This project was developed as a term project for the **Introduction to Artificial Intelligence** course (Fall 2025-2026). The models provided are for **research and educational purposes only** and should not be used for clinical diagnosis without further validation.
