# Tugas 05 - Image Classification Using ResNet18 and EfficientNet-B0

## Deskripsi

Proyek ini merupakan eksperimen klasifikasi citra hewan menggunakan dataset **Oxford-IIIT Pet** dengan 10 kelas terpilih.

Eksperimen dilakukan untuk membandingkan beberapa strategi training deep learning menggunakan arsitektur **ResNet18**, yaitu:

- B1: Training From Scratch
- B2: Feature Extraction
- B3: Progressive Fine-Tuning
- B4: Data Augmentation Analysis

Selain itu, dilakukan eksperimen tambahan menggunakan **EfficientNet-B0** sebagai model dengan arsitektur yang lebih efisien.

---

# Dataset

Dataset yang digunakan:

**Oxford-IIIT Pet Dataset**

Jumlah kelas yang digunakan: **10 kelas**

Kelas:
- Abyssinian
- Bengal
- Birman
- Bombay
- British Shorthair
- American Bulldog
- Beagle
- Boxer
- German Shorthaired
- Chihuahua

Pembagian dataset:

| Dataset Split | Jumlah Data |
|---|---:|
| Train | 697 gambar |
| Validation | 149 gambar |
| Test | 150 gambar |
| Total | 996 gambar |

---

# Metodologi Eksperimen

## B1 - ResNet18 From Scratch

Model ResNet18 dilatih dari awal menggunakan bobot random initialization.

Konfigurasi:
- Tidak menggunakan pretrained weight
- Seluruh parameter model dilatih

Tujuan:
- Mengetahui performa model tanpa transfer learning.

---

## B2 - ResNet18 Feature Extraction

Menggunakan ResNet18 pretrained ImageNet.

Strategi:
- Backbone model dibekukan
- Hanya classifier layer yang dilatih

Tujuan:
- Menguji kemampuan fitur pretrained untuk klasifikasi dataset target.

---

## B3 - ResNet18 Progressive Fine-Tuning

Menggunakan pendekatan progressive fine-tuning.

Strategi:
- Membuka sebagian layer backbone
- Melatih layer tingkat tinggi dan classifier
- Menggunakan learning rate berbeda

Tujuan:
- Melakukan adaptasi fitur pretrained terhadap dataset Oxford-IIIT Pet.

---

## B4 - Data Augmentation

Eksperimen dilakukan untuk mengetahui pengaruh augmentasi terhadap performa model.

Perbandingan:

| Kondisi | Transformasi |
|---|---|
| Tanpa Augmentation | Transformasi dasar |
| Dengan Augmentation | RandomResizedCrop, RandomHorizontalFlip, RandomRotation, ColorJitter |

---

## B5 - EfficientNet-B0

Eksperimen tambahan menggunakan EfficientNet-B0.

Tujuan:
- Membandingkan performa dengan ResNet18
- Melihat efisiensi jumlah parameter model

---

# Hasil Eksperimen

## Perbandingan Model

| Model | Strategi | Accuracy | Macro F1 |
|---|---|---:|---:|
| B1 ResNet18 | From Scratch | 0.3600 | 0.3395 |
| B2 ResNet18 | Feature Extraction | 0.9867 | 0.9867 |
| B3 ResNet18 | Progressive Fine-Tuning | 0.9867 | 0.9866 |
| B5 EfficientNet-B0 | Feature Extraction | 0.9733 | 0.9733 |

---

## Pengaruh Data Augmentation

| Kondisi | Accuracy | Macro F1 |
|---|---:|---:|
| Tanpa Augmentation | 0.9800 | 0.97998 |
| Dengan Augmentation | 0.9733 | 0.9735 |

---

# Struktur Repository
