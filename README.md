# TT-STGCN for Sign Language Recognition

This repository implements a **Temporal Transformer Spatio-Temporal Graph Convolutional Network (TT-STGCN)** for **Sign Language Recognition (SLR)** using skeletal landmarks.
It fuses **Graph Convolutional Networks (GCNs)** with **Temporal Transformers** to model both spatial and long-range temporal dependencies efficiently.

---

## 🚀 Highlights

* **Transformer-Enhanced ST-GCN:** Integrates lightweight temporal transformer blocks for improved sequence modeling.
* **Adaptive Graph Learning:** Learns adjacency dynamically for better motion context understanding.
* **Cross-Stream Fusion:** Fuses **joint** and **bone** modalities using cross-attention to enhance spatial-temporal reasoning.
* **High Accuracy:**

  * **74.6% Top-1 accuracy** on **NSLT-100**
  * **72.0% Top-1 accuracy** on **NSLT-300**
* **Moderate Model Size:**
  ~**1.1M parameters**, achieving a strong balance between accuracy and efficiency.

---

## 🧠 Landmark Extraction

The **`landmarks-extraction.ipynb`** script employs **MediaPipe Holistic** to extract **65 keypoints per frame**, as inspired by the MSE-GCN and SLR literature.

**Extracted Features:**

* **23 Pose landmarks**
* **21 Left-hand landmarks**
* **21 Right-hand landmarks**

Each frame is represented using **Joint** and **Bone** streams:

* **Joint Stream:** Encodes raw (x, y, z, visibility) coordinates of each joint relative to a body-center reference.
* **Bone Stream:** Computes the **bone vectors**, **lengths**, and **angles** between connected joints to model motion dynamics.

All extracted features are saved as `.npz` NumPy files and used directly in training.

---

## 📁 Project Structure

```
TT-STGCN-for-Sign-Language-Recognition/
│
├── src/
│   ├── ttstgcn-300.ipynb              # Full training pipeline for 300-class SLR
│   ├── landmarks-extraction.ipynb     # Landmark extraction using MediaPipe Holistic
│
├── .gitignore
├── requirements.txt
└── README.md
```

---
## 📦 Dataset

This implementation uses the **WLASL2000** dataset (resized version):
🔗 **[Kaggle – WLASL2000 Resized Dataset](https://www.kaggle.com/datasets/sttaseen/wlasl2000-resized)**

Each video contains sign language gestures annotated with gloss labels.
The dataset supports **300+ isolated sign classes**, ideal for benchmark evaluation of lightweight SLR models.





## ⚙️ Installation

```bash
git clone https://github.com/Muhammad-Huzifa/TT-STGCN-for-Sign-Language-Recognition.git
cd TT-STGCN-for-Sign-Language-Recognition
pip install -r requirements.txt
```

---

## 🧩 Model Overview

### 1️⃣ **Depthwise-Separable Convolutions**

Reduce parameters by ~8–10× while preserving feature richness.

### 2️⃣ **Temporal Transformer Block**

Captures long-term temporal dependencies using efficient attention across frames.

### 3️⃣ **Adaptive Graph Convolution**

Learns an optimized adjacency matrix for the skeleton graph dynamically.

### 4️⃣ **Cross-Stream Fusion**

Allows the joint stream to attend to bone features, improving sign differentiation.

---

## 📊 Performance Summary

| Dataset  | # Classes | Parameters | Top-1 Accuracy |
| -------- | --------- | ---------- | -------------- |
| NSLT-100 | 100       | ~1.1M      | **74.6%**      |
| NSLT-300 | 300       | ~1.1M      | **72.0%**      |

---

## 🧩 Applications

* Continuous and Isolated Sign Language Recognition
* Gesture / Action Recognition
* Human Motion Analysis
* Real-time SLR systems for accessibility tools

---

## 👨‍🔬 Author

**Muhammad Huzaifa**
Sign Language Recognition Researcher | Deep Learning Engineer
📬 **[mhuzaifa3202@gmail.com](mailto:mhuzaifa3202@gmail.com)**

---

## 🧾 Citation (if used in research)

If this project aids your research, please cite:

```
@misc{huzaifa2025ttstgcn,
  author = {Muhammad Huzaifa},
  title = {TT-STGCN for Sign Language Recognition},
  year = {2025},
  url = {https://github.com/Muhammad-Huzifa/TT-STGCN-for-Sign-Language-Recognition}
}
```

---

✨ *A robust transformer-augmented GCN for accurate and interpretable Sign Language Recognition.*
