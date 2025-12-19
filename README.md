# Deteksi-Anomali-Data-Sensor-IoT-pada-dataset-MetroP3-Air-Compressor-dengan-metode-hybrid-CNN-LSTM
Deteksi Anomali Data Sensor IoT Industri pada dataset MetroP3(Air Compressor) dengan metode hybrid CNN LSTM


# 🚂 IoT Anomaly Detection on MetroPT-3 Dataset
### Pengembangan Sistem Deteksi Anomali pada Data Sensor IoT Industri Menggunakan Arsitektur Hybrid CNN-LSTM

[![Python](https://img.shields.io/badge/Python-3.10-blue)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)](https://www.tensorflow.org/)
[![Status](https://img.shields.io/badge/Status-Completed-success)]()

> **Proyek Ujian Akhir Semester (UAS) Mata Kuliah Deep Learning** > Program Studi Informatika, Fakultas Teknik, Universitas Bengkulu.

---

## 📺 Demo & Presentasi
Saksikan penjelasan lengkap mengenai metodologi, arsitektur model, dan demo simulasi real-time pada video berikut:

[![Youtube Video](https://img.youtube.com/vi/VIDEO_ID_HERE/0.jpg)](MASUKKAN_LINK_YOUTUBE_DISINI)

*(Klik gambar di atas atau [tautan ini](MASUKKAN_LINK_YOUTUBE_DISINI) untuk menonton)*

---

## 👥 Tim Pengembang
| Nama | NPM | Peran |
| :--- | :--- | :--- |
| **M. Febri Ardiansyah** | G1A022049 | Model Architecture & Tuning |
| **Baim Mudrik Aziz** | G1A022071 | Data Preprocessing & Analysis |
| **Mezi** | G1A022077 | Deployment & Documentation |

**Dosen Pengampu:** 👨‍🏫 **Ir. Arie Vatresia, S.T., M.T.I., P.hD., IPP.**

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

## 💻 Cara Menjalankan Project

### 1. Clone Repository
```bash
git clone [https://github.com/username-anda/nama-repo.git](https://github.com/username-anda/nama-repo.git)
cd nama-repo


### 3. Jalankan Notebook
Buka file `Final_Project_Notebook.ipynb` (atau nama file `.ipynb` Anda) di Google Colab atau Jupyter Notebook. Eksekusi seluruh sel kode secara berurutan untuk:
* Mendownload dataset.
* Melatih model Hybrid CNN-LSTM.
* Mengevaluasi hasil training.
* Mengonversi model ke format TFLite.

### 4. Simulasi Model TFLite
Di bagian akhir notebook, jalankan skrip **Simulasi Data Stream** untuk melihat demonstrasi sistem mendeteksi anomali secara real-time menggunakan file `.tflite`. Simulasi ini mencakup fitur *smoothing buffer* untuk mencegah alarm palsu.

---

## 📂 Struktur Folder
Berikut adalah susunan direktori proyek ini:

```text
├── dataset/                # File dataset (jika diizinkan upload, atau link sumber)
├── models/
│   └── iot_anomaly_detector.tflite  # Model hasil training (siap deploy ke IoT)
├── notebooks/
│   └── Final_Project.ipynb          # Source code utama (Training, Eval, Export)
├── reports/
│   └── Laporan_UAS_Final.pdf        # Dokumen laporan lengkap (PDF)
├── images/                 # Aset gambar untuk dokumentasi/README
└── README.md               # Dokumentasi proyek ini
