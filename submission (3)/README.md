Proyek Akhir - Klasifikasi Gambar Menggunakan CNN
Proyek ini bertujuan untuk membangun model klasifikasi gambar untuk membedakan antara wajah yang menggunakan masker dan tidak menggunakan masker.

Dataset
Dataset yang digunakan terdiri dari dua kelas:

WithMask: Gambar wajah menggunakan masker.

WithoutMask: Gambar wajah tanpa masker.

Dataset telah dibagi menjadi tiga folder berdasarkan peruntukannya:

train: Digunakan untuk melatih model.

val: Digunakan untuk validasi selama pelatihan.

test: Digunakan untuk menguji performa akhir model.

Distribusi gambar relatif seimbang di tiap subset, sehingga tidak diperlukan teknik khusus untuk menangani ketidakseimbangan data.

Eksplorasi Data
Visualisasi distribusi data menunjukkan jumlah gambar sebagai berikut:

Subset	WithMask	WithoutMask
Train	5416	    4161
Val	    1653	    892
Test	1653	    892

Distribusi ini divisualisasikan menggunakan diagram batang per kelas dan subset.

Data Preparation & Augmentasi
Data preprocessing dilakukan menggunakan ImageDataGenerator.

Augmentasi untuk data train:

Rotasi (±20 derajat)

Zoom (±20%)

Pergeseran horizontal & vertikal

Flip horizontal

Val & Test: hanya dilakukan rescale (normalisasi pixel)

Semua gambar diubah ukurannya menjadi 150x150 piksel dan diproses dalam mode 'categorical'.

Model CNN
Model CNN dibangun menggunakan arsitektur sebagai berikut:

Conv2D → MaxPooling2D

Conv2D → MaxPooling2D

Flatten

Dense (128 unit) + Dropout

Dense (output layer: 2 unit, softmax)

Model dikompilasi dengan:

Loss: categorical_crossentropy

Optimizer: Adam

Metrics: accuracy

Model menggunakan EarlyStopping dan ModelCheckpoint.

Hasil Evaluasi
Setelah pelatihan:

Akurasi Validasi: mencapai >85%

Evaluasi pada data test menunjukkan performa yang baik dengan akurasi dan metrik klasifikasi yang menunjukkan model dapat mengenali kedua kelas dengan cukup seimbang.

Visualisasi
Grafik akurasi dan loss pada training & validation ditampilkan.

Confusion matrix pada data test divisualisasikan untuk mengevaluasi prediksi model.

File dan Folder
notebook.ipynb: Notebook utama proyek

README.md: Dokumentasi proyek ini

split_dataset/: Folder dataset hasil pembagian train/val/test

models/: Folder penyimpanan model hasil pelatihan 