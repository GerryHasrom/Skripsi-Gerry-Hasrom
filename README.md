# 🌊 Klasifikasi Level Air Banjir Berbasis Citra Visual Menggunakan CNN

> Penelitian komparatif performa arsitektur *Deep Learning* untuk klasifikasi ketinggian banjir berbasis objek referensi visual.

## 🏗️ Arsitektur *Pre-trained* yang Digunakan

Penelitian ini menggunakan tiga arsitektur *backbone* dari [Keras Applications](https://keras.io/api/applications/) yang telah dilatih sebelumnya pada dataset ImageNet:

| Arsitektur | Karakteristik Utama | Parameter | Input Size |
| :--- | :--- | :--- | :--- |
| **DenseNet121** | *Dense connectivity*, *feature reuse* maksimal, gradien stabil | ~8M | 224×224 |
| **ResNet50** | *Residual learning*, *skip connections*, anti-*vanishing gradient* | ~25M | 224×224 |
| **EfficientNetV2S** | *Compound scaling*, *fused-MBConv*, efisiensi komputasi tinggi | ~21M | 224×224 |

> **📌 Catatan Mekanisme Pelatihan:**
> 1. Seluruh model dilakukan *fine-tuning* dengan strategi **Early Stopping** (`patience=30`) dan **Model Checkpoint** untuk memastikan bobot terbaik tersimpan sebelum *overfitting* merusak generalisasi.
> 2. Sebagai contoh, jika proses pelatihan berjalan hingga 30 *epoch* namun performa terbaik dicapai pada *epoch* ke-8, maka sistem akan secara otomatis menyimpan dan menggunakan bobot dari *epoch* ke-8 sebagai model akhir.

## 📸 Sampel Citra Uji (Case Images)

Berikut adalah contoh citra uji yang digunakan untuk mengevaluasi kemampuan generalisasi model dalam mengklasifikasikan level kedalaman banjir:

### 👤 Objek Manusia

<h3 align="center">Case Image 1 - Depth 0</h3>
<p align="center">
  <img src="assets/case_image/cs_image1.jpg" alt="Case Image 1 - Manusia Depth 0" width="300" />
</p>

<h3 align="center">Case Image 2 - Depth 1</h3>
<p align="center">
  <img src="assets/case_image/cs_image2.jpg" alt="Case Image 2 - Manusia Depth 1" width="300" />
</p>

<h3 align="center">Case Image 3 - Depth 2</h3>
<p align="center">
  <img src="assets/case_image/cs_image3.jpg" alt="Case Image 3 - Manusia Depth 2" width="300" />
</p>

<h3 align="center">Case Image 4 - Depth 3</h3>
<p align="center">
  <img src="assets/case_image/cs_image4.jpg" alt="Case Image 4 - Manusia Depth 3" width="300" />
</p>

### 🚗 Objek Kendaraan

<h3 align="center">Case Image 5 - Depth 0</h3>
<p align="center">
  <img src="assets/case_image/cs_image5.jpg" alt="Case Image 5 - Kendaraan Depth 0" width="300" />
</p>

<h3 align="center">Case Image 6 - Depth 1</h3>
<p align="center">
  <img src="assets/case_image/cs_image6.jpg" alt="Case Image 6 - Kendaraan Depth 1" width="300" />
</p>

<h3 align="center">Case Image 7 - Depth 2</h3>
<p align="center">
  <img src="assets/case_image/cs_image7.jpg" alt="Case Image 7 - Kendaraan Depth 2" width="300" />
</p>

<h3 align="center">Case Image 8 - Depth 3</h3>
<p align="center">
  <img src="assets/case_image/cs_image8.jpg" alt="Case Image 8 - Kendaraan Depth 3" width="300" />
</p>

---

**Keterangan Level Kedalaman:**
- **Depth 0**: Kondisi tidak banjir
- **Depth 1**: Air mencapai kaki/roda
- **Depth 2**: Air setinggi pinggang/kap mesin
- **Depth 3**: Air mencapai dada/kaca mobil


##  Hasil Performa Terbaik

| Objek Referensi | Arsitektur Terbaik | Skema Data | Accuracy | F1-Score |
| :--- | :--- | :--- | :--- | :--- |
| 👤 Manusia | DenseNet121 | 70:20:10 | **0.94** | **0.94** |
| 🚗 Kendaraan | ResNet50 | 80:10:10 | **0.87** | **0.87** |

> ** Temuan Kunci:** Penambahan volume data latih tidak selalu berkorelasi positif dengan performa. Karakteristik objek sangat memengaruhi konfigurasi optimal; manusia mencapai puncak pada data menengah (70%), sementara kendaraan memerlukan data lebih masif (80%).
