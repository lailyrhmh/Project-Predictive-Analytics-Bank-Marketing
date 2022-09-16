# Proyek Machine Learning - Laily Rachmah
---

## Domain Proyek
---

### Latar Belakang
Deposito masih merupakan pilihan utama bagi masyarakat untuk berinvestasi saat ini dan hal itu merupakan kesempatan bagi bank-bank untuk menentukan strategi pemasaran dan promosi yang lebih efisien dengan tidak terlalu banyak menggunakan biaya sehingga masyarakat tertarik untuk berinvestasi pada produk deposito dari bank tersebut.
Deposito adalah salah satu produk simpanan yang disediakan oleh perbankan untuk nasabahnya dan masih menjadi pilihan utama masyarakat untuk berinvestasi. Produk ini juga kesempatan bagi bank-bank untuk melakukan marketing contohnya adalah _telemarketing_. Sulitnya memasarkan produk mereka kepada pelanggan baru akan menyebabkan banyaknya kegagalan dalam proses marketing. Selain itu, perbankan juga memiliki kesulitan dalam membedakan atau mengkategorikan nasabah yang memiliki potensi untuk melakukan deposito. 

Dalam hal ini, diperlukan strategi marketing yang tepat dan promosi yang efisien agar tidak salah sasaran yang mengakibatkan banyaknya nasabah yang berpotensi menolak tawaran produk yang menurut mereka tidak relevan dengan kebutuhan. Sehingga dengan ini dikembangkan sebuah _supervised machine learning algorithms_ untuk memprediksi nasabah yang berpotensi untuk melakukan deposito pada marketing selanjutnya.

## Business Understanding
---

### Problem Statement
* Bagaimana cara untuk mengolah data agar dapat dilatih baik?
* Bagaimana untuk menentukan model yang tepat pada masalah regresi perbankan?

### Goals
Tujuan proyek ini dibuat adalah sebagai berikut :
* Dapat mengolah data untuk meningkatkan tingkat akurasi model
* Mendapat model dengan akurasi, _re-call_ dan _precision_ minimal 80%

### Solution Statement
* Melakukan Analisis data, data cleaning untuk mencari missing value, eksporasi dengan visualisasi data untuk menemukan outliers dll., dan preprosessing data yang tepat sebelum dilakukan train atau latih
* Menggunakan model logistik regresi untuk memprediksi nilai _Boolean_ (benar atau salah)


## Data Understanding
---
Dataset yang digunakan pada proyek ini adalah dataset bank _marketing_ yang diunduh dari link [berikut ini](https://www.kaggle.com/datasets/janiobachmann/bank-marketing-dataset).

Dataset ini memiliki format .csv dengan total 11162 baris data dan 17 column atau features. Berukit informasi pada masing-masing column:
1. age: umur (numerik)
2. job: pekerjaan (kategori)
3. marital: status pernikahan (boolean)
4. education: pendidikan (kategori)
5. default: credit secara default (boolean)
6. balance: bank balance
7. housing: pinjaman untuk rumah (boolean)
8. loan: pinjaman pribadi (boolean)
9. contact: tipe _contact person_ (kategori)
10. month: kontak terakhir dengan bank dalam bulan (kategori)
11. day: kontak terakhir dengan bank dalam hari (kategori)
12. duration: durasi kontak dengan bank (num)
13. campaign: jumlah kontak selama campaign (num)
14. pdays: jumlah hari sejak terakhir dihubungi dari campaign sebelumnya (num)
15. previous: jumlah kontak dengan klien sebelum campaign (num)
16. poutcome: hasil dari marketing campaign sebelumnya (kategori)
17. deposit: melakukan deposit (boolean)

### Exploratory Data Analysis
Setelah dilakukan 4 tahapan exploratory data yaitu _missing value, duplicate, univariate dan multivariate analysis_ didapatkan data ini cukup bersih seperti tidak adanya _missing value_ sehingga tidak terlalu banyak memerlukan proses data cleaning, tetapi beberapa data imbalance yang menyebabkan data bias terhadap suatu kategori, dan melakukan _down-sampling_ terhadap data setelah dilakukan korelasi antar fitur numerik.


# Data Preparation
---
### One-Hot Encoding
Karena banyaknya colum dengan tipe data object maka perlu dilakukan one-hot encoding. Pertama dibagi kedalam 2 kategori yaitu tipe Boolean yang berisi nilai ‘yes’ atau ‘no’ dan tipe kategori, kemudian direpresentasi ulang menggunakan angka 0 atau 1. Hal ini dilakukan agar data bisa digunakan pada train data menggunakan model _logistic regression_.

### Splitting Data
Data ini dibagi menjadi 2 yaitu _train_ dan _test_. Train data digunakan sebagai training model dan test data digunakan sebagai validasi untuk mengetahui keakuratan dari data yang dilatih menggunakan model. Dengan jumlah data tersebut, data dibagi dengan proporsi 8:2 yaitu 80% digunakan untuk train dan 20% digunakan untuk test atau validasi.

### Standarisasi Data
Standarisasi data menggunakan standard scaler. Ketika sebelumnya kita melakukan perbahan tipe data _oject_ menjadi numerik, sekarang data numerik akan kita samakan skala standar deviasinya agar tidak terlalu tinggi untuk dibandingkan dengan data lain.


# Modeling
---

Model yang digunakan dalam proyek ini adalah _logistic regression_. Dengan hyperparameter solver dengan nilai liblinear karena klasifikasi pada proyek ini merupakan klasifikasi 2 kelas, _penalty_ yang dapat digunakan untuk solver liblinear adalah l1 dan l2 dan nilai C berada pada range 1 sampai 100 yang akan dicari _best model_-nya menggunakan _Grid search_. 

Pertama menggunakan hyperparameter solver liblinear karena hasil atau target klasifikasi merupakan binary class. Kemudian menggunakan penalty untuk melakuka spesifikasi penalty untuk soveler liblinear yang dapat menggunakan penalty l1 dan l2 dalam prosesnya. Kemudian menggunakan nilai C untuk memperkuat regulasi pada model.


# Evaluation Model
---

Setelah membuat model machine learning, sangat penting untuk melakukan evaluasi akurasi model. Pada proyek ini digunaknan confusion matrix untuk klasifikasi binary class.

Hasil dari model ini sebagai berikut: 

                   precision    recall  f1-score   support

               0       0.81      0.87      0.84      1176
               1       0.84      0.78      0.81      1057

        accuracy                           0.83      2233
       macro avg       0.83      0.82      0.82      2233
    weighted avg       0.83      0.83      0.82      2233

pada baris 0 menunjukan nilai untuk _precision_-nya yaitu 0.81 dan nilai _recall_ 0.87 yang artinya memiliki akurasi 87% saat memprediksi kategori 0 atau orang yang tidak akan melakukan deposito. kemudian pada baris 1 untuk nilai precision-nya yaitu 0.84 dan nilai _recall_ 0.78 atau akurasi 78% pada prediksi kategori 1 atau orang yang akan melakukan deposito. dan untuk akurasi keseluruhan yaitu 0.83 atau 83% untuk model menggunakan _logistic linear_ ini.


# Kesimpulan 
---

Model Machine learning untuk memprediksi orang yang akan melakukan deposito pada _marketing_ bank yang dikembangkan menggunakan logistic regression mendapatkan hasil akurasi rata-rata diatas 80% dan presisi diatas 80% yang artinya sudah memenuhi _goals_ atau tujuan yang ingin dicapai diharapkan dengan model ini dapat membantu untuk menentukan pelanggan yang diikutkan dalam _marketing_ selanjutnya. Dalam pengembangan model selanjutnya diharapkan bisa meningkatkan akurasi model untuk mencapai hasil yang lebih baik misalnya menggunakan algoritma untuk klasifikasi yang lain seperti KKN dan Naive Bayer.


# Referensi (APA7)  :
---

[1] Tanone, R., & Emmanuel, A. B. (2020). Prediksi Not Operational Transaction Menggunakan Logistic Regression pada Bank XYZ di Kota Kupang. AITI, 17(1), 42-55.
[Tautan](https://ejournal.uksw.edu/aiti/article/view/3526)

[2] Puteri, A. N., & Arizal, A. D. A. (2021). Feature Selection Correlation-Based pada Prediksi Nasabah Bank Telemarketing untuk Deposito Feature Selection Correlation-Based on Bank Telemarketing Customer Predictions for Time Deposits. 
[Tautan](https://scholar.archive.org/work/hkmyhngxg5be5ns27bjuc2kq24/access/wayback/https://journal.universitasbumigora.ac.id/index.php/matrik/article/download/1183/695)

[3] Hou, S., Cai, Z., Wu, J., Du, H., & Xie, P. (2022). Applying Machine Learning to the Development of Prediction Models for Bank Deposit Subscription. International Journal of Business Analytics (IJBAN), 9(1), 1-12.
[Tautan](https://www.igi-global.com/article/applying-machine-learning-to-the-development-of-prediction-models-for-bank-deposit-subscription/288514)
