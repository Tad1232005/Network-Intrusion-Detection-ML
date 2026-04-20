# Network-Intrusion-Detection-ML
Lab6: ML model for network intrusion detection using various ml algorithms


# 🛡️ Network Intrusion Detection System (IDS) using Machine Learning

![Python](https://img.shields.io/badge/Python-3.10-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)

---

## 📖 Introduction

This project builds a **real-time Network Intrusion Detection System (IDS)**
using Machine Learning techniques applied to the **CIC-IDS2017** dataset
from the Canadian Institute for Cybersecurity.

The system is capable of classifying network traffic as **Benign** or one of
several attack types including DoS, DDoS, PortScan, Web Attack, and more.
When a threat is detected, the system generates a **Suricata-style alert log**
in real time.

### Dataset
- **Source:** [CIC-IDS2017 on Kaggle](https://www.kaggle.com/datasets/chethuhn/network-intrusion-dataset)
- **Size:** 8 CSV files, ~2.8 million records
- **Features:** 78 numerical network flow features + 1 Label column
- **Attack Types:** DoS, DDoS, PortScan, Web Attack, Infiltration, Botnet

---

## 📁 Project Structure
Network-Intrusion-Detection-ML/
├── data/               # Dataset (not included, see instructions below)
│   └── README.md
├── logs/
│   └── alerts.log      # Real-time alert output
├── models/
│   └── README.md       # Model download link
├── notebooks/
│   └── main.ipynb      # Main notebook
├── src/
│   ├── preprocessing.py
│   ├── models.py
│   └── realtime_alert.py
├── .gitignore
├── requirements.txt
└── README.md

## ⚙️ Installation Guide

### 1. Clone the repository
```bash
git clone <link_repo>
cd Network-Intrusion-Detection-ML
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Download the dataset (data/data.md)
- Vào link: https://www.kaggle.com/datasets/chethuhn/network-intrusion-dataset
- Bấm **Download** → Giải nén
- Đặt tất cả 8 file CSV vào thư mục `data/`

### 4. Download trained model (models/model.md)
- File `.pkl` quá lớn để push lên GitHub
- Tải tại: **[Google Drive Link]**
- Đặt vào thư mục `models/`

---

## 🛠 Quy trình làm việc nhóm (Git Workflow)

### Quy tắc đặt tên nhánh

- Bắt buộc đặt tên nhánh theo tên cá nhân (viết liền, không dấu, ngăn cách bằng dấu `-`).
- Ví dụ: `le-thanh-dat`, `le-kim-buu`.

### Workflow 5 bước chuẩn

1. **Trước khi code, luôn cập nhật `main` mới nhất:**

```bash
git checkout main
git pull origin main
```

2. **Tạo nhánh cá nhân theo đúng quy tắc tên:**

```bash
git checkout -b le-thanh-dat
```

3. **Code tính năng, sau đó add và commit rõ ràng:**

```bash
git add .
git commit -m "feat: mo ta ngan gon thay doi"
```

4. **Đẩy nhánh cá nhân lên GitHub:**

```bash
git push origin le-thanh-dat
```

5. **Tạo Pull Request (PR) để Leader review và merge vào `main`.**

### Lưu ý quan trọng

- Không bao giờ push trực tiếp lên `main`.
- Luôn kiểm tra và xử lý conflict trước khi merge PR.
