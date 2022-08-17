# Proyek-Pertama-Predictive-Analytics-ML-Terapan-Dicoding
# Laporan Proyek Machine Learning Prediksi Biaya Premi Asuransi - Haris Amaldi

## Domain Proyek

Asuransi adalah perjanjian antara dua orang atau lebih dimana pihak tertanggung harus membayarkan premi dan pihak lainnya harus memberikan jaminan sepenuhnya kepada pembayaran premi jika sesuatu menimpa pihak tertanggung.
Salah satu jenis asuransi adalah asuransi kesehatan dimana lembaga akan menjamin pembayaran biaya berobat bagi anggota anggotanya yang membayar premi dengan syarat dan ketentuan yang sudah disepakati oleh kedua belah pihak.
Besaran premi tersebut bisa berbeda-beda bergantung dengan usia, kondisi kesehatan, gaya hidup, dan domisili anggotanya.
Proyek ini dibuat untuk memprediksi biaya premi yang akan dibebankan oleh pihak asuransi kepada pelanggan baik pria maupun wanita dari berbagai usia, kondisi kesehatan (BMI dan aktif merokok atau tidaknya pelanggan), jumlah anak yang ditanggung, dan domisili pelanggan.
Hal ini dibutuhkan agar si calon pengguna bisa mengetahui lebih awal mengenai premi asuransi yang akan dibebankan kepada mereka jika mengikuti asuransi tersebut.


## Business Understanding
Dataset yang digunakan pada proyek ini didapatkan dari link di bawah ini:
https://www.kaggle.com/datasets/teertha/ushealthinsurancedataset

### Problem Statements

Masalah pada proyek ini antara lain:
- Apakah umur anggota akan mempengaruhi biaya premi yang dibebankan kepada anggota asuransi?
- Apakah jenis kelamin anggota mempengaruhi biaya premi yang dibebankan kepada anggota asuransi?
- Apakah BMI anggota mempengaruhi biaya premi yang dibebankan kepada anggota asuransi?
- Apakah jumlah anak yang dimiliki anggota mempengaruhi biaya premi yang dibebankan kepada anggota asuransi?
- Apakah kebiasaan merokok dari anggota mempengaruhi biaya premi yang dibebankan kepada anggota asuransi?
- Apakah domisili anggota mempengaruhi biaya premi yang dibebankan kepada anggota asuransi?
- Apa model yang paling akurat pada kasus proyek ini?
- Berapa error yang akan terjadi pada hasil prediksi model terakurat pada kasus proyek ini?


### Goals

Tujuan dari proyek ini antara lain:
- Menentukan faktor apa saja yang mempengaruhi biaya premi yang harus dibayar.
- Memprediksi biaya premi yang harus ditanggung seakurat mungkin.

### Solution statements
- Solusi ini akan membandingkan prediksi hasil K nearest Neighbour, Random forest, dan boost


## Data Understanding
Data ini berisi 1338 anggota asuransi dari berbagai wilayah dan usia. Data ini memiliki beberapa fitur antara lain:
- age : Usia anggota;
- sex : Jenis kelamin;
- bmi : Body mass index. Perbandingan berat badan anggota dalam kg dan pangkat dua dari tinggi badan anggota dalam meter;
- children : Jumlah anak yang dimiliki; 
- smoker : Kebiasaan merokok dari anggota asuransi;
- Region : Domisili anggota;
- charges : Beban premi yang harus dibayarkan.

## Data Preparation
Preparasi data dilakukan dengan cara menghapus data-data outliers, membuang fitur yang sama sekali tidak berkorelasi dengan fitur-fitur lainnya, menggabungkan usia dan bmi menjadi fitur baru bernama "Faktor kesehatan", dan melakukan standarisasi untuk mempermudah perhitungan.
Dari proses ini diketahui bahwa:
- Pada gambar di bawah bisa diketahui bahwa jenis kelamin hampir tidak mempengaruhi biaya premi dimana rerata biaya premi untuk wanita hampir sama dengan pria.
![proyek 1a](https://user-images.githubusercontent.com/106704301/185205315-81c19e62-a6ad-47b2-9ee0-bd9c8fa01361.png)
- Pada gambar di bawah bisa diketahui bahwa kebiasaan merokok SANGAT mempengaruhi biaya premi yang dibebankan dimana rerata biaya premi yang dibebankan kepada anggota yang perokok aktif 3 kali lebih besar daripada kepada anggota yang tidak merokok.
![proyek 1b](https://user-images.githubusercontent.com/106704301/185205721-c58ca518-8532-4e7e-a384-0f206f049444.png)
- Pada gambar di bawah ini bisa diketahui bahwa daerah domisili anggota juga mempengaruhi besarnya biaya premi yang dibebankan dimana northeast menjadi wilayah yang dikenai rata-rata premi termahal dan southwest menjadi wilayah yang dikenai rata-rata premi termurah.
![proyek 1c](https://user-images.githubusercontent.com/106704301/185206543-7cf45196-d881-44ca-8731-273d577575cf.png)
- Dari gambar di bawah bisa diketahui bahwa umur sedikit mempengaruhi BMI dan cukup mempengaruhi biaya premi. BMI sendiri memang tidak mempengaruhi biaya premi, akan tetapi besarnya BMI anggota sedikit dipengaruhi oleh umur anggota. Satu-satunya faktor yang tidak berkorelasi pada faktor apapun adalah jumlah anak. Maka dari itu, fitur "children" bisa dihapus.
![proyek 1d](https://user-images.githubusercontent.com/106704301/185207129-4b0f7832-f308-47be-a609-635f01bfd041.png)

## Modeling
- Modeling proyek ini dilakukan dengan 3 metode yang akan dibandingkan satu sama lain antara lain KNN, random forest, dan boosting. Parameter K pada KNN yang digunakan adalah sebesar 3, lalu parameter RF yang digunakan adalah pohonnya sebanyak 100 dan kedalaman sebesar 25, dan untuk boosting learning ratenya sebesar 0.001.
- Dalam proyek ini, saya akan menggunakan KNN karena hasil prediksinya yaitu 3364.4 yang lebih mendekati hasil aslinya (2523.17). Bandingkan dengan 4170 jika menggunakan random forest dan 4384.3 jika menggunakan boosting.

## Evaluation
- Evaluasi pada proyek ini adalah tingkat ketelitiannya yang masih kecil dimana hasil yang paling mendekati hasil aslinya memiliki perbedaan/error sebesar 33.34% dari nilai aslinya.
- Dibutuhkan optimalisasi lebih lanjut utamanya pada random forest dan boosting agar bisa mendapatkan hasil prediksi yang lebih mendekati hasil aslinya.

**---Ini adalah bagian akhir laporan---**

