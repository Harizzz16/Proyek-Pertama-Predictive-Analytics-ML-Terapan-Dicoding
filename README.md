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
- Apa saja faktor-faktor yang dimiliki anggota yang akan mempengaruhi biaya premi yang dibebankan kepada anggota asuransi?
- Apa model yang paling akurat pada kasus proyek ini?
- Berapa error yang akan terjadi pada hasil prediksi model terakurat pada kasus proyek ini?


### Goals

Tujuan dari proyek ini antara lain:
- Menentukan faktor-faktor apa saja yang mempengaruhi biaya premi yang harus dibayar.
- Menentukan model yang bisa memprediksi paling akurat pada proyek ini.
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
Preparasi data dilakukan dengan tahapan sebagai berikut:
- menghapus data-data outliers 
  Dalam hal ini, akan dihapus data data outlier atau yang keluar dari trend. Pada proyek ini data outlier adalah data angka BMI yang berlebihan.
  ![outlier1](https://user-images.githubusercontent.com/106704301/185286463-05ba9db6-7bd7-4a09-b31f-9e0a627943ed.png)
![outlier 2](https://user-images.githubusercontent.com/106704301/185286476-f2c216a4-7923-4ed5-abd7-52fdd27f4ddf.png)
- melihat kondisi data sampel
![jenis kelamin](https://user-images.githubusercontent.com/106704301/185286627-ddba4e62-7d94-4bc9-8642-55db5c490a04.png)
![perokok](https://user-images.githubusercontent.com/106704301/185286634-bc6fe4db-ec48-4011-859e-4912db5d9177.png)
![domisili](https://user-images.githubusercontent.com/106704301/185286649-2f4e9064-c283-4b25-b39b-9d6a10a68847.png)
![data1](https://user-images.githubusercontent.com/106704301/185286658-d86159d2-1b73-4321-8b8d-ec3bed4e6a3d.png)
![data2](https://user-images.githubusercontent.com/106704301/185286664-a749ffca-0fe1-45aa-aaee-e37b83df29cd.png)

- membuang fitur yang sama sekali tidak berkorelasi dengan fitur-fitur lainnya 
Dalam hal ini, faktor jumlah anak tidak berkorelasi pada fitur fitur apapun, sehingga fitur "children" bisa dihapus.
![proyek 1d](https://user-images.githubusercontent.com/106704301/185286823-394aab8c-4005-4edf-b07e-cb9d5d667120.png)

- menggabungkan usia dan bmi menjadi fitur baru bernama "Faktor kesehatan"
- melakukan standarisasi untuk mempermudah perhitungan.
![standarisasi](https://user-images.githubusercontent.com/106704301/185287071-deaa77b6-8754-473c-9c07-6a0d402e23a4.png)

Dari proses ini diketahui bahwa:
- Pada gambar di bawah bisa diketahui bahwa jenis kelamin hampir tidak mempengaruhi biaya premi dimana rerata biaya premi untuk wanita hampir sama dengan pria.
![proyek 1a](https://user-images.githubusercontent.com/106704301/185205315-81c19e62-a6ad-47b2-9ee0-bd9c8fa01361.png)
- Pada gambar di bawah bisa diketahui bahwa kebiasaan merokok sangat mempengaruhi biaya premi yang dibebankan dimana rerata biaya premi yang dibebankan kepada anggota yang perokok aktif 3 kali lebih besar daripada kepada anggota yang tidak merokok.
![proyek 1b](https://user-images.githubusercontent.com/106704301/185205721-c58ca518-8532-4e7e-a384-0f206f049444.png)
- Pada gambar di bawah ini bisa diketahui bahwa daerah domisili anggota juga mempengaruhi besarnya biaya premi yang dibebankan dimana northeast menjadi wilayah yang dikenai rata-rata premi termahal dan southwest menjadi wilayah yang dikenai rata-rata premi termurah.
![proyek 1c](https://user-images.githubusercontent.com/106704301/185206543-7cf45196-d881-44ca-8731-273d577575cf.png)
- Dari gambar di bawah bisa diketahui bahwa umur sedikit mempengaruhi BMI dan cukup mempengaruhi biaya premi. BMI sendiri memang tidak mempengaruhi biaya premi, akan tetapi besarnya BMI anggota sedikit dipengaruhi oleh umur anggota. Satu-satunya faktor yang tidak berkorelasi pada faktor apapun adalah jumlah anak. Maka dari itu, fitur "children" bisa dihapus.
![proyek 1d](https://user-images.githubusercontent.com/106704301/185207129-4b0f7832-f308-47be-a609-635f01bfd041.png)

## Modeling
- Modeling proyek ini dilakukan dengan 3 metode yang akan dibandingkan satu sama lain antara lain KNN, random forest, dan boosting. Parameter K pada KNN yang digunakan adalah sebesar 3, lalu parameter RF yang digunakan adalah pohonnya sebanyak 100 dan kedalaman sebesar 25, dan untuk boosting learning ratenya sebesar 0.001.
- Pada proyek ini, MSE terkecil dicetak oleh boosting, lalu disusul oleh RF, dan MSE terbesar adalah model KNN.
![MSE](https://user-images.githubusercontent.com/106704301/185289185-e0ffa27f-ffa4-4091-baec-79d88ef1b648.png)
- Sedangkan untuk hasil prediksi, nilai terdekat dari nilai sesungguhnya (2523.1695) adalah dari KNN sebesar 3364.44, disusul oleh RF sebesar 4170, dan yang paling jauh dari nilai sesungguhnya adalah boosting sebesar 4384.3
![prediksi](https://user-images.githubusercontent.com/106704301/185289208-bedcb92e-50e1-4ba2-9219-4f410685a308.png)
- Dalam proyek ini, saya akan menggunakan KNN karena hasil prediksinya paling mendekati nilai sesungguhnya.

## Evaluation
- Evaluasi pada proyek ini adalah tingkat ketelitiannya yang masih kecil dimana hasil yang paling mendekati hasil aslinya memiliki perbedaan/error sebesar 33.34% dari nilai aslinya.
- Dibutuhkan optimalisasi lebih lanjut utamanya pada random forest dan boosting agar bisa mendapatkan hasil prediksi yang lebih mendekati hasil aslinya.

**---Ini adalah bagian akhir laporan---**

