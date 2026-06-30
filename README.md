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
> Seluruh model dilakukan *fine-tuning* dengan strategi **Early Stopping** (`patience=30`) dan **Model Checkpoint** untuk memastikan bobot terbaik tersimpan sebelum *overfitting* merusak generalisasi. 
> 
> Dengan kata lain, jika proses pelatihan berjalan hingga 30 *epoch* namun performa terbaik dicapai pada *epoch* ke-8, maka sistem akan secara otomatis menyimpan dan menggunakan bobot dari *epoch* ke-8 sebagai model akhir.





##  Hasil Performa Terbaik

| Objek Referensi | Arsitektur Terbaik | Skema Data | Accuracy | F1-Score |
| :--- | :--- | :--- | :--- | :--- |
| 👤 Manusia | DenseNet121 | 70:20:10 | **0.94** | **0.94** |
| 🚗 Kendaraan | ResNet50 | 80:10:10 | **0.87** | **0.87** |

> ** Temuan Kunci:** Penambahan volume data latih tidak selalu berkorelasi positif dengan performa. Karakteristik objek sangat memengaruhi konfigurasi optimal; manusia mencapai puncak pada data menengah (70%), sementara kendaraan memerlukan data lebih masif (80%).
