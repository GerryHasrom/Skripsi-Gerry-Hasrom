# 🌊 Klasifikasi Level Air Banjir Berbasis Citra Visual Menggunakan CNN

> Penelitian komparatif performa arsitektur Deep Learning untuk estimasi ketinggian banjir berbasis objek referensi visual tanpa sensor fisik.

## 📖 Ringkasan Proyek

Proyek ini mengembangkan sistem klasifikasi level kedalaman air banjir (**Depth 0–3**) menggunakan pendekatan *image classification* berbasis Convolutional Neural Network (CNN). Berbeda dengan metode konvensional yang mengandalkan sensor IoT atau citra satelit, penelitian ini memanfaatkan **objek manusia dan kendaraan sebagai "penggaris alami"** untuk estimasi visual-relatif yang cepat dan berbiaya rendah.

Sistem ini mengintegrasikan **18 varian model** hasil eksperimen komparatif antara tiga arsitektur backbone (*DenseNet121, ResNet50, EfficientNetV2S*) pada dua jenis objek referensi dan tiga skema distribusi data, kemudian diimplementasikan dalam antarmuka web interaktif menggunakan Streamlit.

## ✨ Fitur Utama

-   **Multi-Architecture Comparison:** Evaluasi empiris 3 arsitektur CNN modern dengan transfer learning & fine-tuning.
-   **Object-Centric Flood Estimation:** Klasifikasi berdasarkan proporsi objek terendam (Manusia & Kendaraan) mengikuti adaptasi metodologi Chaudhary et al. (2020).
-   **Robust Data Pipeline:** Implementasi 3 skema splitting (60:30:10, 70:20:10, 80:10:10) dengan augmentasi geometri & fotometri.
-   **Interactive Web Demo:** Antarmuka Streamlit untuk pengujian real-time dengan pemilihan model dinamis dan confidence score.
-   **Comprehensive Evaluation:** Analisis metrik lengkap (Accuracy, Precision, Recall, F1-Score) + Confusion Matrix per kelas depth.

##  Hasil Performa Terbaik

| Objek Referensi | Arsitektur Terbaik | Skema Data | Accuracy | F1-Score |
| :--- | :--- | :--- | :--- | :--- |
| 👤 Manusia | DenseNet121 | 70:20:10 | **0.94** | **0.94** |
| 🚗 Kendaraan | ResNet50 | 80:10:10 | **0.87** | **0.87** |

> ** Temuan Kunci:** Penambahan volume data latih tidak selalu berkorelasi positif dengan performa. Karakteristik objek sangat memengaruhi konfigurasi optimal; manusia mencapai puncak pada data menengah (70%), sementara kendaraan memerlukan data lebih masif (80%).

## 🛠️ Tech Stack

-   **Deep Learning:** TensorFlow, Keras, ImageDataGenerator
-   **Architectures:** DenseNet121, ResNet50, EfficientNetV2S (ImageNet Pretrained)
-   **Deployment:** Streamlit, Pickle (Model Serialization)
-   **Analysis:** Scikit-learn, Matplotlib, Seaborn, Pandas
-   **Environment:** Python 3.9+, CUDA-enabled GPU

##  Struktur Repository

```text
├── app.py                  # Streamlit Web Application
├── models/                 # Directory berisi 18 .h5 trained models
├── notebooks/              # Jupyter Notebooks (Training & Analysis)
├── src/                    # Source code preprocessing & augmentation
├── requirements.txt        # Dependencies
├── SKRIPSI_PDD_GERRY_HASROM.pdf  # Full Thesis Document
└── README.md
