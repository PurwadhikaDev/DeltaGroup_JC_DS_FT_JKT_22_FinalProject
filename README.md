# **Bank Marketing Campaign**

## **1. Business Understanding**
### **Context**
Sebagai institusi keuangan, Bank X yang merupakan salah satu contoh bank di portugal yang menggantungkan sumber pendapatannya pada bunga dari pinjaman yang disalurkan kepada nasabah. Pinjaman tersebut berasal dari dana yang disimpan oleh nasabah lain seperti deposito berjangka. Semakin banyak nasabah yang menempatkan dana mereka dalam bentuk deposito, semakin besar kapasitas bank untuk memberikan pinjaman dan meningkatkan pendapatannya.

Namun seperti bank lainnya, Bank X harus tetap bersaing untuk mempertahankan dan menarik nasabah. Salah satu strategi yang digunakan adalah melakukan kampanye pemasaran melalui direct marketing. Kampanye ini sering dilakukan melalui direct marketing di mana bank menghubungi calon nasabah secara langsung melalui kontak pribadi, email, telepon seluler, atau saluran komunikasi lainnya untuk menawarkan produk-produk baru seperti deposito dengan bunga kompetitif dan produk pinjaman yang menguntungkan. 

**Target**

`0: Tidak (Tidak melakukan deposito)`

`1: Ya (Melakukan deposito)`

### **Problem Statement**
Tim marketing memegang peranan yang sangat penting karena menjadi salah satu faktor yang secara langsung mempengaruhi keputusan seorang nasabah. Akan tetapi jika tim marketing menghubungi semua nasabah untuk menawarkan produk deposito tersebut maka sistem kerja menjadi tidak efisien dan memerlukan biaya yang tinggi.

Sebaliknya jika tim marketing hanya menghubungi sebagian nasabah, maka mereka berisiko kehilangan nasabah yang sebenarnya berpotensi melakukan deposito. Oleh karena itu tim marketing perlu memiliki kemampuan untuk memprediksi nasabah mana yang akan tertarik untuk membeli deposito. Dengan demikian mereka dapat meminimalisir biaya pemasaran sekaligus memaksimalkan pendapatan dari deposito. 
### **Tujuan**
Berdasarkan permasalahan tersebut tim marketing harus memiliki kemampuan memprediksi dan memahami karakteristik  pelanggan mana yang cenderung melakukan deposito dan yang tidak. sehingga tim marketing dapat merancang program-program yang lebih efisien untuk meningkatkan jumlah pelanggan yang melakukan deposito.
### **Analytic Approach**
Jadi rencana kita adalah menganalisa data dengan tujuan mengidentifikasi pola dan  mengembangkan model klasifikasi yang akan membantu tim marekting memprediksi seorang nasabah yang akan melakukan deposito ataupun tidak. 
### **Evaluation Metric**
Sebelum masuk pada evaluasi metrik terlebih dahulu kita akan memberikan gambaran konsekuensi secara kuantitatif, maka kita akan coba menghitung dampak biaya berdasarkan asumsi berikut:

- Gaji telemarketing di portugal sekitar €2,497 per bulan ([Sumber](https://www.paylab.com/pt/salaryinfo/banking)).
- Hari kerja dalam sebulan 22 Hari ([Sumber](https://www.bluselection.com/blog/2022/12/working-days-in-portugal-everything-you-need-to-know?source=chatgpt.com))
- Jam kerja dalam sehari 8 Jam ([Sumber](https://www.bluselection.com/blog/2022/12/working-days-in-portugal-everything-you-need-to-know?source=chatgpt.com))
- Upah per jam : €2,497/bulan (22 Hari/ bulan x 8 jam/hari) = €14,19 per jam
- Rata-rata durasi telemarketing per orang sekitar 180 detik.
- Rata-rata jumlah deposit per nasabah sekitar 2500 Euro per orang. ([sumber](https://www.ceicdata.com/en/portugal/banking-indicators/pt-deposit-accounts-per-1000-adults-commercial-banks)).
- Interest Rate : 4.5% ([sumber](https://take-profit.org/en/statistics/interest-rate/portugal/))
- Lending Rate : 5.98% ([sumber](https://take-profit.org/en/statistics/interest-rate/portugal/))

Berdasarkan asumsi di atas maka kita dapat coba kuantifikasi konsekuensinya sebagai berikut :

- Hilangnya biaya dan waktu untuk telemarketing --> maka kita menyia-nyiakan biaya sebesar : €14,19 x 180/3600 = 0,709 Euro per orang.
- Hilangnya potensi pendapatan --> maka kita kehilangan potensi pendapatan sebesar :(5.98% - 4.5%) * 2500 Euro = 37 Euro per orang.

Berdasarkan asumsi di atas sehingga kita bisa menyimpulkan bahwa:

**Type 1 error: False Positive (Nasabah yang sebenarnya tidak akan melakukan deposito tetapi diprediksi akan melakukan deposito).**

Konsekuensi: akan mengakibatkan pemborosan biaya telemarketing. Biaya telemarketing yang terbuang: €14,19 x 180/3600 = 0,709 Euro per orang.

**Type 2 error: False Negative (Nasabah yang sebenarnya akan melakukan deposito tetapi diprediksi tidak akan melakukan deposito).**

Konsekuensi: akan menyebabkan kehilangan potensi pendapatan dari nasabah yang sebenarnya akan melakukan deposito. Potensi pendapatan yang hilang karena kegagalan mengidentifikasi nasabah yang sebenarnya akan melakukan deposito = (5.98% - 4.5%) * 2500 Euro = 37 Euro per orang


Berdasarkan konsekuensi di atas tujuan kita adalah membuat model prediksi yang dapat mengurangi False Negatif (Nasabah yang sebenarnya akan melakukan deposito tetapi diprediksi tidak akan melakukan deposito) dan juga meminimalisir biaya telemarketing yang tidak tepat. Oleh karena itu, metrik yang kita gunakan adalah 'Recall' karena false negatif memiliki kerugian yang lebih besar daripada false positif.


____________________________________________________________________________________________________________________________________________________________________
Explore the interactive Tableau dashboard [di sini](https://public.tableau.com/app/profile/nur.hafizah3798/viz/GroupDeltaFinproBankMarketingCampaign/DemografiDashboard?publish=yes)
___
Dataset : [kaggle](https://www.kaggle.com/volodymyrgavrysh/bank-marketing-campaigns-dataset)
