# Proyek Machine Learning - Laily Rachmah
---

## Domain Proyek
---

### Latar Belakang
Deposito masih merupakan pilihan utama bagi masyarakat untuk berinvestasi saat ini dan hal itu merupakan kesempatan bagi bank-bank untuk menentukan strategi pemasaran dan promosi yang lebih efisien dengan tidak terlalu banyak menggunakan biaya sehingga masyarakat tertarik untuk berinvestasi pada produk deposito dari bank tersebut.
Deposito adalah salah satu produk simpanan yang disediakan oleh perbankan untuk nasabahnya dan masih menjadi pilihan utama masyarakat untuk berinvestasi. Produk ini juga kesempatan bagi bank-bank untuk melakukan marketing contohnya adalah telemarketing. Sulitnya memasarkan produk mereka kepada pelanggan baru akan menyebabkan banyaknya kegagalan dalam proses marketing. Selain itu, perbankan juga memiliki kesulitan dalam membedakan atau mengkategorikan nasabah yang memiliki potensi untuk melakukan deposito. 

Dalam hal ini, diperlukan strategi marketing yang tepat dan promosi yang efisien agar tidak salah sasaran yang mengakibatkan banyaknya nasabah yang berpotensi menolak tawaran produk yang menurut mereka tidak relevan dengan kebutuhan. Sehingga dengan ini dikembangkan sebuah supervised machine learning algorithms untuk memprediksi nasabah yang berpotensi untuk melakukan deposito pada marketing selanjutnya.

## Business Understanding
---

### Problem Statement
* Bagaimana cara untuk mengolah data agar dapat dilatih baik?
* Bagaimana untuk menentukan model yang tepat pada masalah regresi perbankan?

### Goals
Tujuan proyek ini dibuat adalah sebagai berikut :
* Dapat mengolah data untuk meningkatkan tingkat akurasi model
* Mendapat model dengan akurasi, re-call dan precision minimal 80%

### Solution Statement
* Melakukan Analisis data, data cleaning untuk mencari missing value, eksporasi dengan visualisasi data untuk menemukan outliers dll., dan preprosessing data yang tepat sebelum dilakukan train atau latih
* Menggunakan model logistik regresi untuk memprediksi nilai Boolean (benar atau salah)


## Data Understanding
---
Dataset yang digunakan pada proyek ini adalah dataset bank marketing yang diunduh dari link [berikut ini](https://www.kaggle.com/datasets/janiobachmann/bank-marketing-dataset).

Dataset ini memiliki format .csv dengan total 11162 baris data dan 17 column atau features. Berukit informasi pada masing-masing column:
1. age: umur (numerik)
2. job: pekerjaan (kategori)
3. marital: status pernikahan (boolean)
4. education: pendidikan (kategori)
5. default: credit secara default (boolean)
6. balance: bank balance
7. housing: pinjaman untuk rumah (boolean)
8. loan: pinjaman pribadi (boolean)
9. contact: tipe contact person (kategori)
10. month: kontak terakhir dengan bank dalam bulan (kategori)
11. day: kontak terakhir dengan bank dalam hari (kategori)
12. duration: durasi kontak dengan bank (num)
13. campaign: jumlah kontak selama campaign (num)
14. pdays: jumlah hari sejak terakhir dihubungi dari campaign sebelumnya (num)
15. previous: jumlah kontak dengan klien sebelum campaign (num)
16. poutcome: hasil dari marketing campaign sebelumnya (kategori)
17. deposit: melakukan deposit (boolean)

### Exploratory Data Analysis
Setelah dilakukan 4 tahapan exploratory data yaitu missing value, duplicate, univariate dan multivariate analysis didapatkan data ini cukup bersih seperti tidak adanya missing value sehingga tidak terlalu banyak memerlukan proses data cleaning, tetapi beberapa data imbalance yang menyebabkan data bias terhadap suatu kategori, dan melakukan down-sampling terhadap data setelah dilakukan korelasi antar fitur numerik.


# Data Preparation
---
### One-Hot Encoding
Karena banyaknya colum dengan tipe data object maka perlu dilakukan one-hot encoding. Pertama dibagi kedalam 2 kategori yaitu tipe Boolean yang berisi nilai ‘yes’ atau ‘no’ dan tipe kategori, kemudian direpresentasi ulang menggunakan angka 0 atau 1. Hal ini dilakukan agar data bisa digunakan pada train data menggunakan model logistic regression.

### Splitting Data
Data ini dibagi menjadi 2 yaitu train dan test. Train data digunakan sebagai training model dan test data digunakan sebagai validasi untuk mengetahui keakuratan dari data yang dilatih menggunakan model. Dengan jumlah data tersebut, data dibagi dengan proporsi 8:2 yitu 80% digunakan untuk train dan 20% digunakan untuk test atau validasi.

### Standarisasi Data
Standarisasi data menggunakan standard scaler. Ketika sebelumnya kita melakukan perbahan tipe data oject menjadi numerik, sekarang data numerik akan kita samakan skala standar deviasinya agar tidak terlalu tinggi untuk dibandingkan dengan data lain.


# Modeling
---

Model yang digunakan dalam proyek ini adalah logistic regression. Dengan hyperparameter solver, penalty dan nilai C. 

Pertama menggunakan hyperparameter solver liblinear karena hasil atau target klasifikasi merupakan binary class. Kemudian menggunakan penalty untuk melakuka spesifikasi penalty untuk soveler liblinear yang dapat menggunakan penalty l1 dan l2 dalam prosesnya. Kemudian menggunakan nilai C untuk memperkuat regulasi pada model.


# Evaluation Model
---

Setelah membuat model machine learning, sangat penting untuk melakukan evaluasi akurasi model. Pada proyek ini digunaknan confusion matrix untuk klasifikasi binary class.

Hasil dari model ini sebagai berikut 

![image](https://user-images.githubusercontent.com/91611703/190533551-09b60271-a208-483c-b8a9-087d86102033.png)

Dengan akurasi model lebih dari 80% diharapkan model ini dapat membantu untuk menentukan pelanggan yang diikutkan dalam marketing selanjutnya.


# Referensi (APA7)  :
---

* Tanone, R., & Emmanuel, A. B. (2020). Prediksi Not Operational Transaction Menggunakan Logistic Regression pada Bank XYZ di Kota Kupang. AITI, 17(1), 42-55.
[Tauran](https://ejournal.uksw.edu/aiti/article/view/3526)

* Puteri, A. N., & Arizal, A. D. A. (2021). Feature Selection Correlation-Based pada Prediksi Nasabah Bank Telemarketing untuk Deposito Feature Selection Correlation-Based on Bank Telemarketing Customer Predictions for Time Deposits. 
[Tautan](https://scholar.archive.org/work/hkmyhngxg5be5ns27bjuc2kq24/access/wayback/https://journal.universitasbumigora.ac.id/index.php/matrik/article/download/1183/695)

* Hou, S., Cai, Z., Wu, J., Du, H., & Xie, P. (2022). Applying Machine Learning to the Development of Prediction Models for Bank Deposit Subscription. International Journal of Business Analytics (IJBAN), 9(1), 1-12.
[Tautan](https://www.igi-global.com/article/applying-machine-learning-to-the-development-of-prediction-models-for-bank-deposit-subscription/288514)
