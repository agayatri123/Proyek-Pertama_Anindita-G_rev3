# **Laporan Proyek Machine Learning - Anindita Gayatri**

## DOMAIN PROYEK : Kesehatan
Penulis adalah UKM produsen dalam industri makanan bernama JAVANA ROYAL (IG @JavanaRoyalOfficial) yaitu makanan sehat, murni dan alami yang bahan bakunya di-supply langsung dari para petani di pedalaman Indonesia. Khususnya Madu Murni kualitas export yang menjadi flagship product kami. Karena berdasar survey kami 2x thn 2019 dan 2022 ternyata hasilnya konsisten 100% konsumen Madu menginginkan manfaat kesehatan. Khususnya bagi para penderita diabetes, kanker, dsb yang menghindari gula tebu, rafinasi, gula jagung, dsb yang memiliki kadar indeks glikemik tinggi. Namun sayangnya pasar Indonesia dikuasai madu oplosan. Juga para importer luar negeri cenderung menghindari produk madu karena keraguan kredibilitas eksportir madu dari Indonesia mengenai kemurnian madu. Sedangkan kualitas kemurnian madu hanya bisa dideteksi melalui test lab dari lab berkredibilitas Indonesia yang mahal dan memakan waktu untuk mengetahui hasilnya.

Dari masalah inilah kami dari Madu JAVANA ROYAL merasa penting adanya suatu alat detektor kemurnian madu. Disamping untuk melindungi hak konsumen, khususnya para penderita sakit serius, juga memberi keadilan transparansi bagi para produsen madu yang benar-benar murni alami. Juga membuka peluang eksport Madu Murni Indonesia. 

## REFERENSI: 
Bogdanov, S. (2009). "Honey quality and international standards." Food Control 20(6): 548–559.
Meena, D., et al. (2020). "Detection of honey adulteration using high-performance liquid chromatography." Food Chemistry 305: 125410. 

## BUSINESS UNDERSTANDING
Dengan adanya handheld detector untuk real-time honey purity checker akan mempermudah, mempercepat dan mempermurah masalah keraguan kualitas madu selama ini yang bersumber paling utama pada kemurnian madu.

## Problem Statements
Bagaimana cara mempersingkat waktu pemeriksaan di laboratorium untuk uji kemurnian madu? Hal ini karena :
- Dunia termasuk Indonesia memiliki masalah keraguan kualitas madu selama ini yang bersumber paling utama pada kemurnian madu.
- Khususnya Indonesia yang dikuasai pasar madu oplosan/palsu alias tidak 100% murni lagi
- Konsumen madu umumnya para penderita sakit berat yang menghindari pemanis lain yang memiliki efek buruk pada kesehatan.

## Goals
- handheld detector untuk real-time honey purity checker akanmemberi solusi yang mempermudah, mempercepat dan mempermurah. 
- Memberikan kepastian madu murni berkualitas pada konsumen
- Memberi transparansi kualitas pada pemain value chain madu murni 

## SOLUTION STATEMENT 
Idealnya untuk masalah ini digunakan "Predictive Analytics" dengan algoritma yang dipakai adalah ANN, namun penulis sudah berkonsultasi pada mentor, bertanya di forum diskusi dicoding maupun tanya chatgpt, gemini, googling, browsing, dsb tidak ditemukan coding yang diharapkan dan penulis dapat pahami esensi nya.
Sehingga penulis menggunakan 3 cara seperti pada latihan Studi Kasus Pertama : K-Nearest Neighbour, Random Forest and Boosting Algoritm.

## DATA UNDERSTANDING
- Dibutuhkan dataset yang besar, beragam dan realible dari spesifikasi madu.
Karena dataset tersebut belum tersedia, maka diambil data yang ada dari Umair Zia di Kaggle terdiri dari 12 variable.
**Terdiri dari 247.903 data & 11 column.**
https://www.kaggle.com/datasets/stealthtechnologies/predict-purity-and-price-of-honey 

- Dalam dataset terdiri dari 11 column dengan jenis datanya masing-masing sbb :
<img width="232" alt="image-5" src="https://github.com/user-attachments/assets/e2de22f8-c3f9-4121-8f5a-010717dfee6b">

- Berikut adalah sebaran nilai per column datanya:
<img width="630" alt="image" src="https://github.com/user-attachments/assets/d2baad17-6178-482e-b13b-740654ba6131">

- Berikut hasilnya setelah data di-drop:
<img width="363" alt="image-8" src="https://github.com/user-attachments/assets/e94523fe-3c2e-452d-99af-2dfcf6c7ddc2">

- Ternyata variable EC, F dan G memiliki korelasi NOL atau mendekati itu sehingga perlu di-drop seperti bukti 
Correlation Matrix untuk Fitur Numerik pada gambar di bawah ini:
<img width="409" alt="image-7" src="https://github.com/user-attachments/assets/5588ccb8-ef53-476d-a249-c2da47c8d0d6">

- Dengan penjelasan tiap variable sbb :
    - CS (Color Score): Menunjukkan nilai warna dari sample madu berkisar dari 1.0 hingga 10.0. 
    Nilai nya semakin rendah menunjukkan warna yang semakin pudar, semakin tinggi berarti semakin gelap warnanya.
    - Density: menunjukkan densitas sample madu dalam grams/cubic.cm pada suhu 25°C. Berkisaran 1.21 hingga 1.86.
    - WC (Water Content): Menunjukkan kadar air pada sample madu berkisaran 12.0% hingga 25.0%.
    - pH: Menunjukkan pH level atau keasaman dari sample madu, berkisaran 2.50 hingga 7.50.
    - EC (Electrical Conductivity): Menunjukkan konduktifitas elektrik dari sample madu dalam milliSiemens per cm.
    - F (Fructose Level): Menunjukkan kadar fruktosa dalam sample madu, berkisaran 20 hingga 50.
    - G (Glucose Level): Menunjukkan kadar gula glukosa dalam sample madu, berkisaran 20 hingga 45.
    - Pollen_analysis: Menunjukkan sumber nektar bunga dari sample madu. Yang tercakup antara lain cengkeh, bunga liar, Orange Blossom, Alfalfa, 
    Acacia, Lavender, Eucalyptus, Buckwheat, Manuka, Sage, Sunflower, Borage, Rosemary, Thyme, Heather, Tupelo, Blueberry, Chestnut & Avocado.
    - Viscosity: Menunjukkan viskositas sample madu dalam centipoise, berkisaran 1500 hingga 10000. 
    - Nilai Viskositas antara 2500 & 9500 dianggap optimal untuk suatu kemurnian.
    - Purity: Variable target menunjukkan kemurnian dari sample madu, berkisaran 0.01 hingga 1.00.
    - Price: Hitungan harga dari madu.

- Variabel-variabel pada dataset predict-purity-and-price-of-honey dari Kaggle di atas (beserta deskripsinya terdiri dari variable :
CS, Density, WC, pH, EC, F, G, Viscosity, Purity & Price

Ini terbukti dari hasil run coding. ** Tidak terdapat missing data (nilai nol/kosong) sbb** : 

<img width="238" alt="image-6" src="https://github.com/user-attachments/assets/509a1df6-aa3e-4382-8069-db0e65a5449f">

- **Tidak terdapat data outliers** dgn contoh bukti sbb:
<img width="346" alt="image-1" src="https://github.com/user-attachments/assets/af944b30-6075-42d8-8475-8819325ed500">

## DATA PREPARATION
Teknik yang digunakan adalah Exploratory data analysis (EDA).
Sedangkan pembagian data train & test adalah 70% dan 30%. 
- Di-check seandainya ada variable yang bernilai nol ataupun kosong.
Ternyata dari hasil coding pengecheckan seandainya ada nilai data nol, tidak diketemukan adanya yang nol.

Sehingga walau dilakukan coding: drop baris yang memiliki nilai nol maka hasil total data dari yang awalnya 247903 mjd tetap 247903.

- Setelahnya dilihat Correlation Matrix untuk Fitur Numerik nya ternyata variable EC, F dan G memiliki korelasi NOL atau mendekati itu.
Ini artinya ketiga nya paling tidak memiliki korelasi sehingga perlu di-drop.

- Lalu variable Pollen_analysis di-one hot encoder karena bukan berupa angka. Berikut gambar table hasil one-hot-encoder.
<img width="907" alt="image-9" src="https://github.com/user-attachments/assets/d3e9234d-567d-4d0f-b626-c9d938ac74a4">


- Kemudian dataset dibagi menjadi 2 :
X (variable input): CS, Density, WC, pH, EC, F, G, Viscosity & Price
y (variable target): Purity
- Kemudian data distandarisasi, dengan hasil gambar seperti di bawah ini.
<img width="346" alt="image-10" src="https://github.com/user-attachments/assets/6a8456b5-705a-4821-984e-2c640b100782">

## MODELLING
Lalu dilakukan Model Development With K-Nearest Neighbour, Random Forest dan Boosting Algoritm. Masing-masing model Development sbb :
- KNN
    - Cara kerja:
      - Pada grafik yang bernilai A pada sumbu X ditandai 10 titik yang paling mendekati nilai A yang dipilih.
      Nilai prediksi terbaik untuk A berdasarkan 10 titik tsb menghasilkan satu titik prediksi yg adl nilai rata-ratanya.
      Lalu dilakukan hal ini pada semua kemungkinan nilai masukan sehingga memperoleh nilai prediksi di beberapa tempat.
      Terakhir menghubungkan setiap prediksi ini sehingga memberi kita hasil regresi.
    - Parameter:
      - Pertama adalah K yang digunakan bernilai 10 (jumlah tetangga).
        Kedua Euclidean distance untuk mengukur jarak antara titik adalah bernilai default.
- Random Forest
    - Cara kerja:
      - Model ini membagi menjadi cabang-cabang berdasarkan nilai fitur nya, bentuknya seperti percabangan pohon.
        Random Forest secara acak menyeleksi subsets data dengan penggantian pada pelatihan tiap pohon.
        Dimaksudkan untuk menghindari overfitting dan meningkatkan kemampuan generalisasi model.
        kemudian melakukan prediksi value based pada tiap nilai rata-rata dari data yg dilatih di tiap percabangan.
        Akhirnya didapat nilai prediksi dimana merupakan nilai rata-rata prediksi dari semua pohon.
    - Parameter:
      - n_estimators atau jumlah pohon di forest yang digunakan adalah 50.
        Max depth atau kedalaman atau panjang pohon (yg dapat splitting) senilai 16.
        Random state yang digunakan untuk mengontrol random number generator bernilai 55.
        Sedangkan n_jobs atau jumlah job (pekerjaan) yang digunakan secara paralel senilai 1. 
    
- Boosting Algoritm (AdaBoost or Adaptive Boosting)
    - Cara kerja:
      - Semua data latih memiliki weight atau bobot yang sama.
        Tiap tahapan, model akan memeriksa apakah observasi yang dilakukan sudah benar.
        Bobot bernilai lebih tinggi akan diberikan pada model yang salah shg akan dimasukkan ke dalam tahapan selanjutnya. Proses iteratif ini terus berlangsung hingga didapatkan model yang memiliki akurasi yang diharapkan.
    - Parameter:
      - learning rate atau bobot yang diterapkan pada setiap regressor di tiap iterasi senilai 0,05.
      random state bernilai 55 untuk mengontrol random number generator yang digunakan.

Penulis sebenar nya ingin membuat modelling Feedforward Neural Network dengan Backpropagation berdasar pengalaman penulis meng-coding 
di MATLAB dahulu dimana menghasilkan prediksi bagus untuk data fluktuatif sekalipun. Namun konsultasi dengan mentor, forum diskusi
Dicoding, chatgpt, dsb nya untuk cara pengkodingan nya kurang berhasil. 

## EVALUATION 
- Dilakukan scalling dan dihitung MSE nya pada data train data test (bentuk angka dan chart) sbb :
RF senilai nol koma sekian, KNN lebih dari 1 dan Boosting memiliki MSE tertinggi yaitu lebih dari 7.
- Ternyata K-Nearest Neighbour memiliki nilai error terkecil sehingga dipilih menjadi kualitas terbaik.
- Saat di-testing pun ternyata ketika y_true senilai 0,88 maka KNN senilai 0,88 pula (pembulatan 2 digit belakang koma).
sedangkan RF bernilai 0,9 dan Boosting senilai 0,7.
<img width="346" alt="image-2" src="https://github.com/user-attachments/assets/f380ae83-8c18-4dd7-83f9-94dd0da451a6">
Gambar hasil evaluasi ketiga Gambar

<img width="292" alt="image-4" src="https://github.com/user-attachments/assets/6124bfcd-e79f-4948-a4b7-9da44a77a556">
Gambar hasil prediksi ketiga nya terhadap y_true

## KESIMPULAN
Sehingga dapat disimpulkan model KNN yang akan kita pilih sebagai model terbaik untuk melakukan prediksi kemurnian madu.
Walau sebenarnya belum terlalu mencapai harapan solusi di lapangan karena sebagian dataset adalah Pollen bunga yang unfamiliar di Indonesia.
Sehingga diharapkan ke depannya penulis bisa mendapatkan dataset pollen bunga khas Indonesia seperti bunga mangga, bunga kopi, dsb.
Sehingga AI Honey Purity Detector lebih aplicable dipakai untuk madu Indonesia. 

---Ini adalah bagian akhir laporan---
