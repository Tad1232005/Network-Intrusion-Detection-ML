# Network-Intrusion-Detection-ML
Lab6: ML model for network intrusion detection using various ml algorithms


# 🛡️ Network Intrusion Detection System (IDS) using Machine Learning

![Python](https://img.shields.io/badge/Python-3.10-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

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

## 🏗 Project Architecture

Hệ thống được thiết kế theo mô hình Pipeline khép kín:
1. **Data Ingestion:** Load 8 file CSV từ dataset CIC-IDS2017.
2. **Preprocessing:** Clean dữ liệu, xử lý Inf/NaN, chuẩn hóa StandardScaler.
3. **Balancing:** Sử dụng SMOTE & RandomUnderSampler để xử lý mất cân bằng class.
4. **Feature Selection:** Lọc lấy 18 đặc trưng quan trọng nhất (theo yêu cầu Lab).
5. **Model Training:** Huấn luyện song song 5 thuật toán (LR, SVM, NB, KNN, RF).
6. **Deployment:** Đóng gói Best Model (Random Forest) để nhận diện traffic thời gian thực.

## 📁 Project Structure
```bash
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
│   └── realtime_alert.py
├── .gitignore
├── requirements.txt
└── README.md
```

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
- File `.pkl` > 100MB, quá lớn để push lên GitHub
- Tải tại: https://drive.google.com/drive/folders/1l7Bx__SAxebHVo8CPBx4ZOVsgK_Xwveo
- Đặt vào thư mục `models/`

---

## 🚀 Usage

### 1. Chạy toàn bộ quy trình huấn luyện
Mở file `notebooks/main.ipynb` và nhấn **Run All**. File này sẽ thực hiện từ tiền xử lý đến đánh giá mô hình.

### 2. Chạy mô phỏng Real-time Alert (Mục 2.6)
Để kiểm tra khả năng phát hiện tấn công của mô hình Random Forest:
```bash
python src/realtime_alert.py
```

---
## 👥 Thành viên nhóm & Phân công 

| Thành viên | MSSV | Nhiệm vụ chính |
| :--- | :---: | :--- |
| **Lê Thành Đạt** | N23DVCN009 | **Team Leader**, EDA & Cleaning, Logistic Regression |
| **Nguyễn Quốc Đạt** | N23DVCN010 | Imbalance & Scaling, Support Vector Machine (SVM)|
| **Lê Kim Bửu** | N23DVCN008 | Feature Selection, Naive Bayes |
| **Nguyễn Trần Mạnh Dũng** | N23DVCN015 | K-Nearest Neighbors |
| **Nguyễn Thái Bình** | N23DVCN006 | Random Forest & Real-time Alert |



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

## 📊 Kết quả so sánh mô hình (Model Comparison)

> **Lưu ý:** Chỉ số **Recall** được ưu tiên hàng đầu để giảm thiểu việc bỏ sót các cuộc tấn công mạng.

| Model | Accuracy | Precision | Recall (Attack) | F1-Score |
| :--- | :---: | :---: | :---: | :---: |
| **Logistic Regression** | 68.00% | 94.00% | 68.00% | 77.00% |
| **Support Vector Machine** | 57.28% | 93.00% | 57.00% | 67.00% |
| **Naive Bayes** | 13.094% | 94.00% | 14.00% | 18.00% |
| **K-Nearest Neighbors** | 98.04% | 99.00% | 98.00% | 98.00% |
| **Random Forest (Best)** | **99.00%** | **99.00%** | **99.00%** | **99.00%** |
