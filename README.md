## BISNIS PROBLEM
Asuransi perjalanan adalah jenis asuransi yang memberikan perlindungan selama kita melakukan perjalanan baik dalam negeri maupun luar negeri. Beberapa negara bahkan telah mewajibkan para pelancong untuk memiliki asuransi perjalanan, misalnya negara-negara di Eropa dan Amerika. Besarnya premi tergantung pada cakupan yang diinginkan, lama perjalanan, dan tujuan perjalanan. 

Suatu perusahaan yang bergerak di bidang asuransi perjalanan ingin mengetahui pemegang polis yang akan mengajukan klaim asuransi untuk pertanggungan. Data pemegang polis pada perusahaan asuransi merupakan data historis yang terdiri dari destinasi, produk asuransi, dan sebagainya.

Perusahaan asuransi mendasarkan bisnis mereka pada asumsi dan asumsi risiko. Mereka menghasilkan pendapatan dengan membebankan premi kemudian menginvestasikan premi tersebut di aset penghasil bunga lainnya. Untuk menghasilkan keuntungan, perusahaan asuransi memastikan bahwa premi yang mereka tetapkan lebih besar daripada klaim apa pun di masa mendatang.

Target : 
- 0 : Tidak diklaim 
- 1 : Diklaim

### PROBLEM STATEMENT
Perusahaan asuransi perjalanan ingin memprediksi pemegang polis mana yang kemungkinan akan mengajukan klaim asuransi untuk pertanggungan, agar dapat mengidentifikasi dan mengurangi potensi kerugian secara proaktif.

### GOALS
Dengan menggunakan classification model machine learning, perusahaan dapat menganalisis data riwayat pemegang polis seperti produk asuransi, dan detail perjalanan untuk memprediksi secara akurat pemegang polis mana yang memiliki risiko lebih tinggi untuk mengajukan klaim. Hal ini akan memungkinkan perusahaan untuk mengambil tindakan pencegahan untuk kompensasi biaya klaim dan meningkatkan kinerja keuangan secara keseluruhan.

### ANALYTIC APPROACH
Selanjutnya adalah menganalisis data untuk menemukan pola dari fitur-fitur yang ada untuk membedakan pemegang polis yang mengajukan klaim dan yang tidak.
Kemudian membangun model klasifikasi yang akan membantu perusahaan memprediksi apakah pemegang polis akan mengajukan klaim atau tidak.

### MATRIX EVALUATION
Berdasarkan tujuan diatas, model tersebut harus baik dalam memprediksi pemegang polis yang akan mengajukan klaim di masa depan. Jadi dalam hal ini kita perlu mengurangi jumlah false positive rate, artinya kita akan kehilangan lebih banyak uang jika model memprediksi pemegang polis yang tidak mengklaim tetapi sebenarnya mereka mengklaim sehingga precision skor akan menjadi metrik evaluasi kali ini.
- Type 1 error : False Positive
Konsekuensi : Perusahaan tidak dapat membebankan premi/biaya lebih kepada pemegang polis yang pada kenyataannya mengajukan klaim di masa mendatang tetapi diprediksikan "tidak akan mengklaim" oleh model tersebut. Yang berarti perusahaan kehilangan uang.
- Type 2 error : False Negative
Konsekuensi : Membebankan biaya diluar premi kepada pemegang polis yang kemungkinan besar tidak akan mengajukan klaim di masa depan.

### Features
-	Agency: Nama agency.
-	Agency Type: Tipe agensi asuransi travel.
-	Distribution Channel: Channel agensi asuransi travel.
-	Product Name: Nama produk asuransi travel.
-	Gender: Jenis Kelamin.
-	Duration: Durasi Perjalanan.
-	Destination: Tujuan Perjalanan.
-	Net Sales: Banyak nominal Penjualan polis asuransi perjalanan.
-	Commission (in value): Komisi yang diterima agensi asuransi travel.
-	Age: Umur.
-	Claim: Status Klaim.



## Kesimpulan dan Rekomendasi
Kesimpulan :

- Pada model benchmarking - K Fold dapat disimpulkan bahwa model KNN adalah yang terbaik untuk mean precisionnya dari setiap model yang menggunakan default hyperparameter dengan nilai 0.095238 / 9%.
- Pada model benchmarking test data XGBoost mempunyai performance terbaik tapi dengan precision score hanya 0.20
- Karena data memiliki imbalance yang cukup tinggi, maka dilakukan uji undersampling dan oversampling, dengan hasil 
    - Untuk uji Under Sampling Logistic Regression dengan nilai mean precision tertinggi dengan nilai 0.770920 / 77%
    - Untuk uji Over Sampling Random Forest	dengan nilai mean precision tertinggi dengan nilai 0.985803 / 98%
- Untuk uji selanjutnya menggunakan Logistic Regression hasil dari uji Under Sampling
- Untuk Precission Score setelah dan sebelum tuning :
    - Precision Score Prediction Sebelum Tuning:  77%
    - Precision Score Prediction Setelah Tuning:  79%
- Untuk dataset yang seimbang dengan random under sampling dan tuning didapatkan hasil precision score untuk model logistic regression meningkat sebesar 2 %


Rekomendasi :

- Setelah Tuning terlihat bahwa Precision score meningkat sebesar 2%. Jadi dengan model Regresi Logistik setelah tuning dapat mengurangi tingkat False positif. Yang dapat membantu perusahaan memprediksi pemegang polis yang akan lebih mungkin mengajukan klaim di masa mendatang.
- Maka dapat direkomendasikan bahwa data ini perlu memiliki lebih banyak pemegang polis yang mengklaim. Tujuan kami dalam memprediksi 'klaim' sangat buruk, dikarenakan imbalance sampai data dilakukan uji Random Sampling.
- Kedepannya dapat mencoba algorithm Machine Learning yang lain dan juga mencoba hyperparameter tuning kembali, untuk mendapatkan hasil lebih baik.

