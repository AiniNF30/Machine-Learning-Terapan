
# Laporan Project Machine Learning - Aini Nurpadilah


## Domain Proyek



## Business Understanding

## Variabel-variabel pada Milk Quality Data Set :

- pH :
- Temprature: mendefinisikan Suhu susu yang berkisar dari 34'C hingga 90'C maks : 34'C hingga 45,20'C
- Taste : mendefinisikan Rasa susu yang merupakan data kategori 0 (Buruk) atau 1 (Baik) maks : 1 (Baik)
- Odor : mendefinisikan Bau susu yang merupakan data kategori 0 (Buruk) atau 1 (Baik) maks : 0 (Buruk)
- Fat :	mendefinisikan Bau susu yang merupakan data kategori 0 (Rendah) atau 1 (Tinggi) maks : 1 (Tinggi)
- Turbidity	: mendefinisikan Kekeruhan susu yang merupakan data kategorikal 0 (Rendah) atau 1 (Tinggi) maks : 1 (Tinggi)
- Colour : Kolom ini menentukan Warna susu yang berkisar dari 240 hingga 255 maks : 255
- Grade : mendefinisikan Grade (Target) susu yang merupakan data kategori Dimana Rendah (Buruk) atau Sedang (Sedang) Tinggi

## Menangani Missing Value
Untuk mendeteksi missing value digunakan fungsi isnull().sum() dan diperoleh: 


## Menangani Outliers
Pada kasus ini, untuk mendeteksi outliers digunakan teknis visualisasi data (boxplot). Kemudian untuk menangani outliers digunakan metode IQR.

Seltman dalam “Experimental Design and Analysis” [2] menyatakan bahwa outliers yang diidentifikasi oleh boxplot (disebut juga “boxplot outliers”) didefinisikan sebagai data yang nilainya 1.5 IQR di atas Q3 atau 1.5 IQR di bawah Q1.

Berikut persamaannya:

Batas bawah = Q1 - 1.5 * IQR Batas atas = Q3 + 1.5 * IQR

Tabel 2. Visualisasi Boxplot Sebelum dan Sesudah Dikenakan Metode IQR


## Univariate Analysis
Selanjutnya, akan dilakukan proses analisis data dengan teknik Univariate EDA. Pada kasus ini semua fiturnya adalah fitur numerik dan tidak ada fitur kategorikal. Sehingga hanya perlu dilakukan analisa terhadap fitur numerik, sebagai berikut:

## Analisa Fitur Numerik
Untuk melihat distribusi data pada tiap fitur akan digunakan visualisasi dengan histogram sebagai berikut:

## Multivariate Analysis

## Korelasi antara Fitur Numerik


## Data Preparation

## Train Test Split
Dataset akan dibagi menjadi data latih (train) dan data uji (test). Tujuan langkah ini sebelum proses lainnya adalah agar tidak mengotori data uji dengan informasi yang didapat dari data latih. Contoh pada proses standarisasi dimana jika belum di bagi menjadi data latih dan uji, maka keduanya akan terkena transformasi data yang menggunakan informasi (mean dan standard deviation) dari gabungan data latih dan uji. Hal ini berpotensi menimbulkan kebocoran data (data leakage). Oleh karena itu langkah awal sebelum melakukan tranformasi data adalah membagi dataset terlebih dahulu [3].

Pada kasus ini akan menggunakan proporsi pembagian sebesar 90:10 dengan fungsi train_test_split dari sklearn dengan output sebagai berikut.



## Standarisasi
Proses standarisasi bertujuan untuk membuat fitur data menjadi bentuk yang lebih mudah diolah oleh algoritma. Pada kasus ini akan digunakan metode StandarScaler() dari library Scikitlearn.

StandardScaler melakukan proses standarisasi fitur dengan mengurangkan mean kemudian membaginya dengan standar deviasi untuk menggeser distribusi. StandarScaler menghasilkan distribusi deviasi sama dengan 1 dan mean sama dengan 0.

Berikut output yang dihasilkan dari metode StandardScaler dengan menggunakan fungsi describe():


## Modeling

## Evaluation
Dari proses sebelumnya, telah dibangun dan dilatih tiga model yang berbeda (KNN, Random Forest, Boosting). Selanjutnya perlu mengevaluasi model-model tersebut menggunakan data uji dan metrik yang digunakan dalam kasus ini yaitu mean_squared_error. Hasil evaluasi kemudian disimpan ke dalam df_models.

