# Deteksi-Anomali-Data-Sensor-IoT-pada-dataset-MetroP3-Air-Compressor-dengan-metode-hybrid-CNN-LSTM


## 👥 Tim Pengembang
| Nama | NPM | Peran |
| :--- | :--- | :--- |
| **M. Febri Ardiansyah** | G1A022049 | Model Architecture & Tuning |
| **Baim Mudrik Aziz** | G1A022071 | Data Preprocessing & Analysis |
| **Mezi** | G1A022077 | Deployment & Documentation |
**Link Demo :** *(klik tautan ini [https://youtu.be/IUVmgL9oYG4](https://youtu.be/IUVmgL9oYG4) untuk menonton)*

**Dosen Pengampu:** 👨‍🏫 **Ir. Arie Vatresia, S.T., M.T.I., P.hD., IPP.**

---

# 🚂 IoT Anomaly Detection on MetroPT-3 Dataset
### Pengembangan Sistem Deteksi Anomali pada Data Sensor IoT Industri Menggunakan Arsitektur Hybrid CNN-LSTM

[![Python](https://img.shields.io/badge/Python-3.10-blue)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)](https://www.tensorflow.org/)
[![Status](https://img.shields.io/badge/Status-Completed-success)]()

> **Proyek Ujian Akhir Semester (UAS) Mata Kuliah Deep Learning** > Program Studi Informatika, Fakultas Teknik, Universitas Bengkulu.

---



## 📺 Demo & Presentasi
Saksikan penjelasan lengkap mengenai metodologi, arsitektur model, dan demo simulasi real-time pada video berikut:

[![Youtube Video](https://github.com/FebriArdiansyah27/Deteksi-Anomali-Data-Sensor-IoT-pada-dataset-MetroP3-Air-Compressor-dengan-metode-hybrid-CNN-LSTM/blob/main/images/thumbnail.jpg)](https://youtu.be/IUVmgL9oYG4)

*(Klik gambar di atas atau [tautan ini](https://youtu.be/IUVmgL9oYG4) untuk menonton)*

---



## 📖 Ringkasan Proyek
Proyek ini bertujuan untuk membangun sistem **Predictive Maintenance** pada komponen kompresor udara (*Air Compressor*) kereta Metro. Kami menggunakan pendekatan **Deep Learning Hybrid** yang menggabungkan:
1.  **CNN (Convolutional Neural Network):** Untuk mengekstrak fitur spasial dari sinyal sensor.
2.  **LSTM (Long Short-Term Memory):** Untuk mempelajari ketergantungan waktu (temporal) dan tren degradasi mesin.

Model ini dirancang untuk mendeteksi kegagalan seperti **Kebocoran Udara (Air Leak)** dan **Overheat** secara otomatis, serta siap diimplementasikan pada perangkat Edge IoT.

### 🌟 Fitur Utama
* **Anti-Data Leakage:** Fitur indikator kerusakan (`TP2`, `Oil_temperature`) hanya digunakan untuk labeling, dan **dihapus** dari input training untuk menjamin validitas prediksi.
* **Imbalanced Handling:** Menggunakan teknik *Class Weighting* untuk menangani ketidakseimbangan data (Normal vs Anomali).
* **Hyperparameter Tuning:** Optimasi otomatis menggunakan Keras Tuner.
* **Edge Ready:** Model dikonversi ke format **TensorFlow Lite (.tflite)** dengan ukuran < 60 KB.
* **Smart Smoothing:** Implementasi algoritma *Buffer* untuk mencegah alarm palsu (*False Alarm*) pada simulasi real-time.

---

## 📊 Dataset
Kami menggunakan **MetroPT-3 Dataset** dari UCI Machine Learning Repository. Dataset ini berisi data sensor analog dari unit kompresor kereta api (Air Production Unit) yang dikumpulkan selama tahun 2020.

* 📥 **Link Dataset:** [UCI Machine Learning Repository - MetroPT-3 Dataset](https://archive.ics.uci.edu/dataset/791/metropt+3+dataset)
* **Fitur Input (Training):** `TP3` (Pressure), `H1` (Humidity), `DV_pressure`, `Reservoirs`, `Motor_current`.
* **Target:** Binary Classification (0: Normal, 1: Anomali).

---

## 🛠️ Arsitektur Model & Metodologi



1.  **Preprocessing:** Normalisasi (MinMax), Sliding Window (Size=50).
2.  **CNN Layer:** Conv1D + MaxPooling untuk ekstraksi fitur lokal.
3.  **LSTM Layer:** Memproses urutan waktu (Sequence Modeling) dengan `unroll=True`.
4.  **Output:** Dense Layer dengan aktivasi Sigmoid.

---

## 📈 Hasil Evaluasi
Model Hybrid CNN-LSTM dibandingkan dengan baseline Machine Learning (SVM & Random Forest).

| Model | Akurasi | Precision | Recall | F1-Score | AUC |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Hybrid CNN-LSTM** | **99.29%** | **0.99** | **0.99** | **0.99** | **0.99** |
| Random Forest | 99.30% | 0.99 | 0.99 | 0.99 | - |
| SVM (Baseline) | 99.27% | 0.99 | 0.99 | 0.99 | - |

> *Meskipun performa setara, CNN-LSTM dipilih karena skalabilitas pada Big Data dan kemampuan deployment ke IoT yang lebih efisien.*

---

