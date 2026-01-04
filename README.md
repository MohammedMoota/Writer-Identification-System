# Writer Identification System ✍️🔍

An efficient, CPU-friendly Deep Learning system for identifying writers from handwritten documents. Developed for the Global Intelligence Authority (GIA) forensic analysis.

![Accuracy](https://img.shields.io/badge/Accuracy-82.86%25-green)
![Platform](https://img.shields.io/badge/Platform-CPU-blue)
![Model](https://img.shields.io/badge/Model-MobileNetV2-orange)

## 📌 Project Overview
This project implements a multi-class classification model to identify writers based on the stylistic features of their handwriting (slant, pressure, curvature) rather than the text content. It is designed to run on standard hardware (CPU) without requiring a GPU, making it suitable for portable forensic deployment.

## 📂 Project Structure
*   `train.py`: Main script to train the model using Transfer Learning (MobileNetV2).
*   **`run.py`**: Deployment script for inference. Extracts patches and uses a **Voting Mechanism** to identify writers.
*   `model.keras`: The trained Deep Learning model.
*   *(Dataset folders `train/` and `test/` included)*

## 🚀 How to Run

### 1. Setup
Install requirements:
```bash
pip install -r requirements.txt
```

### 2. Testing (Inference)
To test the model on images in the `test/` folder:
```bash
python run.py
```
This will:
1.  Read images from `test/`.
2.  Preprocess them (Grayscale + CLAHE + Patch Extraction).
3.  Predict the writer using the specific Ensemble Voting mechanism.
4.  Save results to `result.csv`.

### 3. Training (Optional)
To retrain the model from scratch:
```bash
python train.py
```

## 🧠 Methodology
*   **Preprocessing**: Grayscale conversion, CLAHE contrast enhancement, and 300x300 patch extraction.
*   **Model**: **MobileNetV2** (Transfer Learning) with a custom classification head.
*   **Feature Engineering**: A "Bag-of-Features" approach where 35 randomly sampled patches from a page vote on the writer's identity.

## 📊 Results
*   **Test Accuracy**: **82.86%**
*   **Inference Speed**: ~0.8s per image (CPU)

## 👤 Author
**Mohammed Moota**
[GitHub Profile](https://github.com/MohammedMoota)
