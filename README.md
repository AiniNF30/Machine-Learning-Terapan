
# Laporan Project Machine Learning - Aini Nurpadilah


# Domain Proyek 
![image](https://user-images.githubusercontent.com/90955264/218612110-4e3edfec-babc-4b10-8124-e701f73fbe7d.png)


![milk](https://user-images.githubusercontent.com/90955264/218314296-5ab8799e-bb51-4290-bee5-e856f3ba1797.jpeg)

# Business Understanding
Prediksi Kualitas Susu  adalah dataset yang bertujuan untuk memprediksi kualitas susu yang dihasilkan oleh sapi berdasarkan berbagai fitur seperti pH,	Temprature,	Taste	,Odor,	Fat,	Turbidity,	Colour,	Grade. Tujuan dari kumpulan data ini adalah untuk memberikan wawasan berharga tentang kualitas produksi susu.

## Problem Statements
* memprediksi secara akurat kualitas susu berdasarkan data yang tersedia, dengan mempertimbangkan faktor-faktor yang saling mempengaruhi yang mempengaruhi kualitas susu.

## Goals
Tujuan dibuatnya proyek ini adalah sebagai berikut :

Membangun model terbaik untuk melakukan memprediksi secara akurat kualitas susu berdasarkan data yang tersedia, dengan mempertimbangkan faktor-faktor yang saling mempengaruhi yang mempengaruhi kualitas susu. Ini membutuhkan pemahaman yang mendalam tentang peternakan dan produksi susu, serta kemampuan untuk memproses dan menganalisis data dalam jumlah besar secara efektif.


## Solution statements
* Menganalisis data dengan melakukan univariate analysis dan multivariate analysis. Memahami data juga dapat dilakukan dengan visualisasi. Memahami data dapat membantu untuk mengetahui kolerasi antar fitur dan mendeteksi outlier.
* Menyiapkan data agar bisa digunakan dalam membangun model.
* Melakukan hyperparameter tuning menggunakan grid search dan membangun model regresi yang dapat memprediksi bilangan kontinu. ALgoritma yang dipakai dalam proyek ini adalah K-Nearest Neighbour, Random Forest, dan AdaBoost.

# Data Understanding

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

<img width="164" alt="missing value" src="https://user-images.githubusercontent.com/90955264/218315758-e1f1cf49-0c2d-4fce-8044-02df3808cd35.png">

tidak terdapat missing value dalam dataset tersebut.

## Menangani Outliers
Pada kasus ini, untuk mendeteksi outliers digunakan teknis visualisasi data (boxplot). Kemudian untuk menangani outliers digunakan metode IQR.

<img width="413" alt="Screenshot 2023-02-12 at 21 07 41" src="https://user-images.githubusercontent.com/90955264/218315910-3b0bc34e-115d-45c8-8495-504a715a4ecb.png">
<img width="396" alt="Screenshot 2023-02-12 at 21 07 57" src="https://user-images.githubusercontent.com/90955264/218315916-12e88491-9a92-4b77-a502-46f78c1cd051.png">
<img width="396" alt="Screenshot 2023-02-12 at 21 07 57" src="https://user-images.githubusercontent.com/90955264/218315929-80878e23-8556-4644-be68-67404adb83e0.png">
<img width="356" alt="Screenshot 2023-02-12 at 21 08 05" src="https://user-images.githubusercontent.com/90955264/218315936-3bbdc57b-e447-4839-8117-a58c63ce6c8c.png">

terdapat outliers pada data pH, Temprature, dan colour.

### Kemudian untuk menangani outliers digunakan metode IQR.

Seltman dalam “Experimental Design and Analysis” [2] menyatakan bahwa outliers yang diidentifikasi oleh boxplot (disebut juga “boxplot outliers”) didefinisikan sebagai data yang nilainya 1.5 IQR di atas Q3 atau 1.5 IQR di bawah Q1.

Berikut persamaannya:

Batas bawah = Q1 - 1.5 * IQR Batas atas = Q3 + 1.5 * IQR

<img width="375" alt="Screenshot 2023-02-12 at 21 13 38" src="https://user-images.githubusercontent.com/90955264/218316204-29d723e7-35f3-492c-bef9-603403181b9e.png">
<img width="381" alt="Screenshot 2023-02-12 at 21 13 44" src="https://user-images.githubusercontent.com/90955264/218316210-5aafda54-be35-4cef-a9aa-f406af6e5fcf.png">
 
dataset sudah bersih dari outliers


## Univariate Analysis
Selanjutnya, akan dilakukan proses analisis data dengan teknik Univariate EDA. Pada kasus ini semua fiturnya adalah fitur numerik dan tidak ada fitur kategorikal. Sehingga hanya perlu dilakukan analisa terhadap fitur numerik, sebagai berikut:
 
#### Kategorikal Fitur 

<img width="414" alt="Screenshot 2023-02-12 at 21 17 09" src="https://user-images.githubusercontent.com/90955264/218316421-6f83ac1e-94bb-42ab-ac44-9419c3c45aee.png">


## Analisa Fitur Numerik
Untuk melihat distribusi data pada tiap fitur akan digunakan visualisasi dengan histogram sebagai berikut:
<img width="1203" alt="Screenshot 2023-02-12 at 21 18 26" src="https://user-images.githubusercontent.com/90955264/218316499-9c1847cc-88f4-4966-9bf0-5f485e9582e3.png">
<img width="781" alt="Screenshot 2023-02-12 at 21 18 33" src="https://user-images.githubusercontent.com/90955264/218316505-0b4e80b5-9d81-46e2-a131-c85f3c183958.png">
 
Dari hasil visualisasi histogram di atas, kita bisa memperoleh beberapa informasi, antara lain:



## Multivariate Analysis

### Korelasi antara Fitur Numerik
Untuk mengevaluasi skor korelasi hubungan antara fitur numerik, akan digunakan fungsi corr() dengan output sebagai berikut.

<img width="570" alt="Screenshot 2023-02-12 at 21 22 41" src="https://user-images.githubusercontent.com/90955264/218316717-7336c484-9bda-4c57-9d4f-81d7b337283f.png">

Koefisien korelasi berkisar antara -1 dan +1. Semakin dekat nilainya ke 1 atau -1, maka korelasinya semakin kuat. Sedangkan, semakin dekat nilainya ke 0 maka korelasinya semakin lemah.

Dari grafik korelasi di atas, pH, Temprature, Odor, Fat, Grade memiliki korelasi yang kuat (mendekati -1, dibawah -0.85) dengan fitur target auqlity. Sementara itu,Taste, Turbidity, dan Colour mempunyai korelasi yang rendah.

## Data Preparation
## Reduksi dimensi dengan Principal Component Analysis (PCA).

PCA umumnya digunakan ketika variabel dalam data yang memiliki korelasi yang tinggi. Korelasi tinggi ini menunjukkan data yang berulang atau redundant. Sebelumnya kita perlu cek kembali korelasi antar fitur dengan menggunakan pairplot.

## Train Test Split
Dataset akan dibagi menjadi data latih (train) dan data uji (test). Tujuan langkah ini sebelum proses lainnya adalah agar tidak mengotori data uji dengan informasi yang didapat dari data latih. Contoh pada proses standarisasi dimana jika belum di bagi menjadi data latih dan uji, maka keduanya akan terkena transformasi data yang menggunakan informasi (mean dan standard deviation) dari gabungan data latih dan uji. Hal ini berpotensi menimbulkan kebocoran data (data leakage). Oleh karena itu langkah awal sebelum melakukan tranformasi data adalah membagi dataset terlebih dahulu [3].

Pada kasus ini akan menggunakan proporsi pembagian sebesar 90:10 dengan fungsi train_test_split dari sklearn dengan output sebagai berikut.

<img width="364" alt="Screenshot 2023-02-13 at 22 12 00" src="https://user-images.githubusercontent.com/90955264/218495988-22b584b9-cdee-4a19-804b-2fe026093e86.png">




## Standarisasi
Proses standarisasi bertujuan untuk membuat fitur data menjadi bentuk yang lebih mudah diolah oleh algoritma. Pada kasus ini akan digunakan metode StandarScaler() dari library Scikitlearn.

StandardScaler melakukan proses standarisasi fitur dengan mengurangkan mean kemudian membaginya dengan standar deviasi untuk menggeser distribusi. StandarScaler menghasilkan distribusi deviasi sama dengan 1 dan mean sama dengan 0.


Berikut output yang dihasilkan dari metode StandardScaler :

<img width="574" alt="Screenshot 2023-02-12 at 21 36 27" src="https://user-images.githubusercontent.com/90955264/218317411-c78c69dc-e8e5-4436-b193-87efa98e930a.png">

## Modeling
Pada tahap ini, kita akan menggunakan tiga algoritma untuk kasus regresi ini. Kemudian, kita akan mengevaluasi performa masing-masing algoritma dan menetukan algoritma mana yang memberikan hasil prediksi terbaik. Ketiga algoritma yang akan kita gunakan, antara lain:

K-Nearest Neighbor
Kelebihan algoritma KNN adalah mudah dipahami dan digunakan sedangkan kekurangannya kika dihadapkan pada jumlah fitur atau dimensi yang besar rawan terjadi bias.

Random Forest
Kelebihan algoritma Random Forest adalah menggunakan teknik Bagging yang berusaha melawan overfitting dengan berjalan secara paralel. Sedangkan kekurangannya ada pada kompleksitas algoritma Random Forest yang membutuhkan waktu relatif lebih lama dan daya komputasi yang lebih tinggi dibanding algoritma seperti Decision Tree.

Boosting Algorithm
Kelebihan algoritma Boosting adalah menggunakan teknik Boosting yang berusaha menurunkan bias dengan berjalan secara sekuensial (memperbaiki model di tiap tahapnya). Sedangkan kekurangannya hampir sama dengan algoritma Random Forest dari segi kompleksitas komputasi yang menjadikan waktu pelatihan relatif lebih lama, selain itu noisy dan outliers sangat berpengaruh dalam algoritma ini.

Untuk langkah pertama, kita akan siapkan DataFrame baru untuk menampung nilai metrik (MSE - Mean Squared Error) pada setiap model / algoritma. Hal ini berguna untuk melakukan analisa perbandingan antar model.


## Evaluation
Dari proses sebelumnya, telah dibangun dan dilatih tiga model yang berbeda (KNN, Random Forest, Boosting). Selanjutnya perlu mengevaluasi model-model tersebut menggunakan data uji dan metrik yang digunakan dalam kasus ini yaitu mean_squared_error. Hasil evaluasi kemudian disimpan ke dalam df_models.

