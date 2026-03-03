# DeltaGateNet: Bidirectional Temporal Dynamics Modeling for EEG-based Driving Fatigue Recognition

[![Paper](https://img.shields.io/badge/Paper-PDF-red)](https://arxiv.org/abs/2602.14071)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](你的Colab链接)

This repository contains the official PyTorch implementation of the paper: **"Bidirectional Temporal Dynamics Modeling for EEG-based Driving Fatigue Recognition"**.

---

## 📌 Overview

Driving fatigue is a major contributor to traffic accidents. **DeltaGateNet** is a novel deep learning framework designed to address the non-stationarity and asymmetric neural dynamics in EEG signals. 

### Key Contributions:
* **Bidirectional Delta Module:** Decomposes first-order temporal differences into positive and negative components to explicitly model asymmetric neural activation and suppression.
* **Gated Temporal Convolution (GTC):** Captures long-term temporal dependencies using depthwise convolutions and residual learning, preserving channel-wise specificity.
* **Performance:** Achieves State-of-the-Art (SOTA) results on the public SEED-VIG and SADT datasets.



---

## 🛠 Installation & Environment Setup

We provide two configuration options depending on your hardware.

### Option 1: Google Colab (Cloud)
*Recommended for quick reproduction or if you lack a local GPU.*

1.  Open your `.ipynb` file in Google Colab.
2.  Set Hardware Accelerator to **GPU** (`Runtime` > `Change runtime type`).
3.  Run the following commands in the first cell:
    ```bash
    # Install specific PyTorch version and dependencies
    !pip install torch==2.9.0 torchvision torchaudio --index-url [https://download.pytorch.org/whl/cu121](https://download.pytorch.org/whl/cu121)
    !pip install numpy pandas scikit-learn matplotlib tqdm
    
    # Mount Google Drive to access your dataset
    from google.colab import drive
    drive.mount('/content/drive')
    ```

### Option 2: Local Anaconda (Development)
*Recommended for extensive training and local data management.*

1.  **Create Environment:**
    ```bash
    conda create -n deltagatenet python=3.9 -y
    conda activate deltagatenet
    ```
2.  **Install PyTorch (Example for CUDA 12.1):**
    ```bash
    pip install torch==2.9.0 torchvision torchaudio --index-url [https://download.pytorch.org/whl/cu121](https://download.pytorch.org/whl/cu121)
    ```
3.  **Install Other Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

---

## 📂 Data Preparation

The model is evaluated on **SEED-VIG** and **SADT**. Please ensure your data directory follows this structure:

```text
data/
├── SEED_VIG/
│   └── raw_data/
└── SADT/
    ├── SADT_2022/
    └── SADT_2952/

```

---

## 🚀 Usage Guide

### 1. Training the Model

To start training DeltaGateNet on the SEED-VIG dataset (Intra-subject mode):

```bash
python train.py --dataset seed_vig --mode intra --batch_size 32 --lr 1e-4 --epochs 200

```

### 2. Evaluation

To evaluate a pre-trained model:

```bash
python eval.py --dataset sadt_2022 --checkpoint ./checkpoints/best_model.pth

```

---

## 📊 Experimental Results

Our model demonstrates superior performance compared to baseline models like EEGNet and TSception.

| Dataset | Evaluation Mode | Accuracy (Acc) |
| --- | --- | --- |
| **SEED-VIG** | Intra-subject | **81.89%** | 
| **SADT 2022** | Intra-subject | **96.81%** | 
| **SADT 2952** | Intra-subject | **96.84%** | 
| **SEED-VIG** | Inter-subject | **55.55%** | 
| **SADT 2022** | Inter-subject | **83.21%** | 
| **SADT 2952** | Inter-subject | **84.49%** | 

---

## 📝 Citation

If you find this work or code helpful in your research, please cite our paper:

```bibtex
@article{yip2026bidirectional,
  title={Bidirectional Temporal Dynamics Modeling for EEG-based Driving Fatigue Recognition},
  author={Yip, Tin Po and Wang, Jianming and Miao, Yutao and Zhang, Jiayan and Zhao, Yunxu and Ouyang, Xiaomin and Li, Zhihong and Zhang, Nevin L},
  journal={arxiv},
  year={2026}
}

```

---

## 📧 Contact

For any questions, please contact:

* **Name:** WANG Jianming
* **Email:** jwanggb@cse.ust.hk
* **Affiliation:** Hong Kong University of Science and Technology

