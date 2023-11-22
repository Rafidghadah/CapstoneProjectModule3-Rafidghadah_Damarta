# **Travel Insurance - Capstone Project 3**

*Travel insurance* / asuransi perjalanan adalah jenis asuransi yang memberikan perlindungan finansial kepada pemegang polis selama melakukan perjalanan, baik domestik maupun internasional. Perlindungan tersebut mencakup berbagai risiko, mulai dari biaya medis, kerusakan atau kehilangan bagasi, pembatalan perjalanan, hingga kecelakaan, cacat permanen, dan kematian.

Untuk mendapatkan manfaat asuransi, pemegang polis harus membayar premi kepada perusahaan asuransi. Besarnya premi tergantung pada berbagai faktor, termasuk pertanggungan yang diinginkan, lama perjalanan, dan tujuan perjalanan.

Dalam dunia usaha asuransi, beberapa perusahaan asuransi memiliki agen asuransi (berbentuk perseorangan atau agensi berbadan hukum) sebagai perantara untuk menjual produk asuransinya kepada seseorang yang ingin melakukan perjalanan.

Perusahaan asuransi mendapatkan keuntungan dari asuransi perjalanan melalui berbagai cara, antara lain:

- Pembatalan polis: Jika pemegang polis membatalkan polis, perusahaan asuransi akan menyimpan semua premi yang telah dibayarkan.
- Investasi premi: Perusahaan asuransi dapat menginvestasikan premi yang diterimanya di pasar finansial untuk mendapatkan keuntungan.
- Tidak ada klaim: Jika tidak ada klaim yang terjadi selama masa kontrak asuransi, perusahaan asuransi akan mendapatkan keuntungan dari premi yang telah dibayarkan.

Asuransi perjalanan merupakan salah satu produk asuransi yang penting bagi setiap orang yang sering bepergian. Dengan memiliki asuransi perjalanan, Anda dapat terlindungi dari berbagai risiko finansial yang dapat terjadi selama perjalanan.

## **Problem Statement**

Sebuah perusahaan asuransi perjalanan ingin meningkatkan pendapatan. Salah satu penyebabnya adalah strategi sales / marketing yang tidak efektif. Strategi tersebut mengeluarkan anggaran yang sama untuk semua jenis pelanggan, terlepas dari potensi mereka untuk mengajukan klaim asuransi. Jika strategi ini terus dilakukan, perusahaan akan mengalami kerugian karena harus membayar klaim asuransi.

## **Goals**

Berdasarkan permasalahan tersebut, Perusahaan asuransi perjalanan ingin memprediksi calon pemegang polis yang akan mengajukan klaim asuransi. Caranya adalah dengan menggunakan model prediksi yang dilatih dengan data historis dari pemegang polis yang telah mengajukan klaim. Dengan mengetahui karakteristik calon pemegang polis yang akan mengajukan klaim, sales / marketing asuransi perjalanan dapat fokus pada calon pemegang polis yang berpotensi tidak mengajukan klaim. Informasi tentang karakteristik calon pemegang polis yang akan mengajukan klaim juga dapat digunakan untuk merencanakan pendekatan strategi sales dan marketing yang lebih baik.

## **Analytic Approach**

Analisis data akan dilakukan untuk menemukan perbedaan pola antara pemegang polis yang mengajukan klaim dan tidak mengajukan klaim, serta memperoleh insight tentang peluang klaim berdasarkan jenis produk asuransi yang dijual. Target:
* No (0)  : Tidak mengajukan klaim
* Yes (1) : Mengajukan klaim

Selanjutnya, kita akan membangun model yang diharapkan dapat membantu perusahaan memprediksi kemungkinan seorang calon pemegang polis akan mengajukan klaim atau tidak. Oleh karena itu, model yang akan dibuat adalah model klasifikasi. Pemodelan akan dilakukan menggunakan beberapa algoritma model klasifikasi seperti Logistic Regression, Desicion Tree, KNN, dan XGBoost.

Berikut beberapa kemungkinan yang dapat terjadi saat model mendefinisian status klaim pemegang polis:

![Metric](https://miro.medium.com/v2/resize:fit:640/format:webp/1*jMs1RmSwnYgR9CsBw-z1dw.png)

* TN : Jumlah pemegang polis yang memang benar tidak melakukan klaim
* TP : Jumlah pemegang polis yang memang benar melakukan klaim

- Type 1 error (FP) : Jumlah pemegang polis yang dinyatakan melakukan klaim padahal tidak melakukan klaim.  
Konsekuensi : Dana asuransi dari hasil pencairan menjadi idle money (uang menganggur / tidak digunakan untuk apa pun dan tersimpan begitu saja tanpa tujuan yang jelas). Hal ini dapat menghambat pelaksanaan kegiatan lain dalam perusahaan yang juga membutuhkan dana serta terjadinya opportunity loss bagi perusahaan.

- Type 2 error (FN) : Jumlah pemegang polis yang dinyatakan tidak melakukan klaim padahal melakukan klaim  
Konsekuensi : Kurangnya persiapan dana asuransi sehingga dapat menghambat proses klaim pemegang polis, akibatnya kualitas dan kapabilitas perusahaan akan dipertanyakan dan akan berdampak buruk pada penjualan produk di masa depan karena hilangnya kepercayaan masyarakat.

Melihat resiko akibat kesalahan pendefinisian kelas positif dan negatif, maka fokus utama dari model yang akan kita buat adalah metric evaluation yang akan digunakan adalah ROC/AUC (Receiver Operating Characteristic) sebagai metric utama. Metric Accuracy tidak dipilih karena setelah diteliti, data merupakan data imbalance. Kita juga akan meminimalkan Error type 2 karena konsekuensi dari False Negative lebih serius daripada False Positives. Error tipe 2 ini jenis kesalahan ini berpotensi menurunkan pendapatan perusahaan yang diakibatkan dari kehilangan calon pelanggan potensial.Oleh karena itu, metric evaluation yang akan digunakan adalah recall score sebagai metric utama. Metric Accuracy tidak dipilih karena setelah diteliti, data merupakan data imbalance. Beberapa model akan diseleksi berdasarkan hasil evaluasi metriknya dan model dengan performa terbaik akan dipilih untuk dilanjutkan pada proses hyperparameter tuning dengan harapan dapat meningkatkan performa model.
