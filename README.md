# Strawberry Classification

Proyek ini bertujuan untuk mengklasifikasikan buah stroberi ke dalam dua kategori utama: **Pickable** (layak petik) dan **UnPickable** (belum layak petik/rusak). Proyek ini menggunakan dua pendekatan Machine Learning/Deep Learning, yaitu **Multilayer Perceptron (MLP)** dan arsitektur CNN **MobileNetV2**.

## Struktur Direktori

```text
01 - Strawbery Classification MobileNetV2/
│
├── strawberryDataset/                # Dataset utama (Training & Validation)
│   ├── Pickable/                     # Gambar stroberi yang layak dipetik
│   └── UnPickable/                   # Gambar stroberi yang tidak layak dipetik
│
├── testingDataset/                   # Dataset untuk pengujian model (Testing)
│
├── strawberry_mobilenetv2.ipynb      # Notebook berisi kode pelatihan dengan MobileNetV2
├── strawberry_mlpclassifier.ipynb    # Notebook berisi kode pelatihan dengan MLP Classifier
│
├── strawberry_mobilenetv2_model.keras        # Model akhir MobileNetV2 (.keras)
├── warmup_checkpoint_mobilenetv2_model.keras # Checkpoint awal/pemanasan MobileNetV2
├── strawberry_mlp_model.pkl                  # Model MLP yang disimpan menggunakan Pickle
└── strawberry_mlp_results.png                # Visualisasi performa dari model MLP
```

## Model yang Digunakan

1. **MobileNetV2** (`strawberry_mobilenetv2.ipynb`)
   - Pendekatan menggunakan _Convolutional Neural Network (CNN)_ modern (Transfer Learning) yang dirancang agar komputasinya ringan (efisien) namun akurat.
   - Gambar diproses dalam dua dimensi dan mengekstraksi fitur visual seperti warna dan tekstur secara mendalam.
   - Cocok untuk diimplementasikan di perangkat *mobile* atau sistem *real-time*.
   - Model keluaran disimpan ke format `.keras`.

2. **Multilayer Perceptron / MLP** (`strawberry_mlpclassifier.ipynb`)
   - Pendekatan *Artificial Neural Network* (ANN) klasik.
   - Digunakan sebagai *baseline* (model perbandingan) untuk melihat apakah arsitektur Neural Network sederhana dapat mengklasifikasikan stroberi dengan baik.
   - Model disimpan ke dalam bentuk `.pkl`.

## Persyaratan (Prerequisites)

Untuk menjalankan Jupyter Notebook dalam proyek ini, Anda memerlukan versi Python (3.10.x) dan beberapa *library* berikut:
- **TensorFlow / Keras** (Untuk melatih dan menguji model MobileNetV2)
- **Scikit-learn** (Untuk implementasi MLP dan kalkulasi metrik evaluasi seperti Confusion Matrix)
- **OpenCV / Pillow (PIL)** (Untuk pembacaan dan pemrosesan gambar)
- **NumPy & Pandas** (Untuk pengolahan array dan struktur data)
- **Matplotlib & Seaborn** (Untuk plotting grafik hasil akurasi/loss)

## Cara Menjalankan

1. **Buka Terminal / Command Prompt** dan masuk ke direktori proyek ini.
2. **Instal Library yang Dibutuhkan** (jika belum):
   ```bash
   pip install tensorflow scikit-learn opencv-python pillow numpy pandas matplotlib seaborn jupyter
   ```
3. **Jalankan Jupyter Notebook**:
   ```bash
   jupyter notebook
   ```
4. **Buka file** `strawberry_mobilenetv2.ipynb` atau `strawberry_mlpclassifier.ipynb` melalui browser.
5. Jalankan sel kode satu per satu *(Run All)*. Pastikan sel pendefinisian direktori membaca lokasi dari folder `strawberryDataset/` dan `testingDataset/` dengan tepat.

## Tentang Dataset

Dataset diperoleh dari https://www.kaggle.com/datasets/abdulbasit31/strawberry-dataset
Gambar-gambar dibagi ke dalam 2 kelas:
- **Pickable**: Stroberi yang sudah merah, matang merata, dan siap dipanen.
- **UnPickable**: Stroberi yang masih berwarna hijau, putih (belum matang), atau dalam kondisi busuk/rusak.

Dataset diproses dan diubah ukurannya (*resize*) lalu dinormalisasi nilainya sebelum masuk ke dalam jaringan saraf model (Neural Network) untuk menjaga stabilitas pelatihan (Training).
