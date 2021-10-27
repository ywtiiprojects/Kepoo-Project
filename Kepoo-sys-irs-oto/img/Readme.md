## **1. Alur Proses Bisnis PT Kepoo Solusi Indonesia**

PT Kepoo Solusi Indonesia berdiri pada tahun 2018 dibawah naungan PT Ezyload Nusabangkit yang menjadi core company dalam distributor pulsa indosat. PT Ezyload Nusabangkit ini memiliki sister company yakni PT Kepoo Solusi Indonesia dan PT Daffina Retailindo. 
PT Ezyload Nusabangkit ini bergerak dibidang telekomunikasi dimana menjadi salah satu distributor pulsa indosat terbesar di indonesia, sebagai distributor pulsa tentunya harus memiliki penghubung untuk menjual produk - produk indosat tersebut.
yakni melalui perusahaan yang harus *door to door* menjual ke reseller adalah 

PT Kepoo Solusi Indonesia yang bergerak dibidang yang sama, market penjualannya adalah pulsa elektrik. 
Produk yang dijual ezyload adalah pulsa indosat Rp. 5000 dan Rp. 10000, baik itu pulsa elektrik maupun voucher dan kartu perdana.

PT Kepoo Solusi Indonesia selain menjual pulsa indosat, ia bekerja sama degan supplier yang menyediakan produk provider lainnya, seperti : Telkomsel, Tree, XL, Smartfrend dll. Informasi produk lebih lengkap dapat mengunjungi [disini](https://rapopoo.com/).
PT Kepoo Solusi Indonesia ini sebagai pengelola transaksi dalam proses pembelian antara server reseller dan server KSI, dan PT Ezyload sebagai sumber pulsa. Artinya PT KSI inilah yang menghabiskan atau membeli saldo pulsa yang nanti akan dijual kembali ke reseller - reseller.

Sedangkan PT Dafinna Retailindo bergerak untuk market penjualan yang berupa fisik seperti voucher, dan kartu perdana. Selain bekerja sama dengan indosat, PT Dafinna Retailindo juga bekerja sama dengan supllier yang menyediakan produk provider lainnya seperti Telkomsel, Tree, XL, Smartfrend dll. Penjualan produk dafinna melalui website resminya [disini](https://dafinnareload.com)

Berikut Alur Proses Bisnis System Otomax & IRS

<img src=../img/alur-proses-system.PNG width=800px>

Detail Flowchart :

* Langkah Pertama Buyer melakukan request top up pulsa ke KSI dengan status buyer sudah menjadi member IP / Jabber
* Langkah kedua kemudian akan diterima oleh server IRS Bumi / Otomax Neptunus sebagai filter awal sebelum dialihkan ke chip supplier dan H2H ( *Host to Host* ) supplier.
* Langkah ke tiga jika buyer request pembelian pulsa di luar provider indosat maka system IRS Bumi atau Otomax Neptunus akan mentransfer transaksi buyer ke chip SPL.
* Langkah ke emapat jika buyer request pembelian pulsa provider indosat seharga Rp. 5000 / Rp. 10000 maka system IRS Bumi atau Otomax Neptunus akan mentrasfer transaksi buyer ke H2H SPL


# **2. Penjelasan IRS & Otomax System**

## 1. System IRS

System IRS *(Integrated Reload System)* adalah aplikasi server pulsa yang digunakan untuk memproses penjualan pulsa. IRS ini selain digunakan untuk memproses penjualan pulsa juga melayani penjualan seperti produk PLN, pembayaran BPJS, dan lain - lain.

### Modul - Modul yang tersedia di IRS system adalah sebagai berikut :

* Terminal 

Modul Terminal adalah modul yang digunakan untuk memproses dan mengelola suatu transaksi.

* Engine

Modul Engine ini digunakan untuk mengontrol dan menjalankan terminal - terminal yang tersedia di system IRS. Modul ini sangan berperan penting pada jalannya system IRS, karena engine inilah yang akan menampilkan database - database yang tersedia di system IRS. 

Namun, jika system mengalami kendala crash maka yang dilakukan operator atau customer service adalah melakukan ping ip system IRS menggunakan engine.
Engine ini hanya tersedia di IRS system saja.

* SMS Sender

Modul sms sender digunakan untuk mengirimkan pesan ke buyer ketika selesai proses transaksi atau pengecekan status transaksi.

* Sms Center

Modul sms center digunakan untuk melakukan pengecekan pesan masuk baik dari reseller maupun supplier. Biasanya pesan yang masuk berisi informasi tentang status transaksi pengisian pulsa baik menggunakan chip kepoo maupun menggunakan chip SPL (suplier).

* Penjualan

Modul Penjualan ini digunakan untuk melakukan proses mensukseskan, menggagalkan, dan mengecek detail transaksi. 
Dalam modul perjualan ini terdapat menu control yang dapat mendukung jalannya sebuah transaksi.

Berikut menu control yang digunakan oleh operator maupun customer service.

| Menu Kontrol | Deskripsi |
|   :----------|  :--------|
| Ulang trx | Menu ini digunakan untuk mengirim ulang transaksi secara manual, biasanya kondisi ini digunakan untuk mengalihkan transaksi ke terminal supplier dengan alasan tertentu. Untuk mengirim ulang transaksi ini biasanya operator akan mengirimkan sms sender. Kondisi ini terjadi saat buyer melakukan transaksi yang sama secara berulang.|
| Resend | Menu ini digunakan untuk mengirim ulang transaksi ke terminal sebelumnya, kondisi ini terjadi saat terminal chip kepoo atau chip supplier habis saldo (*saldo chip*), maka operator akan mengirim ulang transaksi.|
| Sukseskan Transaksi | Menu ini digunakan untuk mensukseskan transaksi, seperti transaksi dinyatakan sudah berhasil mendapatkan SN, namun status transaksi masih pending.|
| Gagalkan Transaksi | Menu ini digunakan untuk menggalkan transaksi, hal ini terjadi karena mendapatkan info dari supplier terjadinya proses trx gagal.|
| Buat Pending | Menu ini digunakan untuk membuat transaksi menjadi pending, tujuannya adalah agar transaksi ini bisa diproses ulang. Kondisi ini terjadi karena proses transaksi masih di proses oleh supplier, untuk itu jika operator / customer service melakukan pengecekan di server supplier seperti : **Nomor tujuan reseller, nominal. nama server yang digunakan**.|
| Blacklist Nomor| Menu ini digunakan untuk memblokir nomor agar nomor tidak bisa ditransaksikan.|
| Ganti SN | Menu ini digunakan untuk mengubah atau mengupdate SN (*serial number*), Pemberian SN ini diberikan oleh provider. Ada kondisi dimana buyer tidak mendapatkan SN, maka buyer akan konfirmasi melalui Customer Service kemudian CS akan melakukan pengecekan di system jika transaksi berhasil, namun provider tidak mengirimkan SN. Maka CS akan update manual di system untuk penambahan SN.|
| Ganti Keterangan | Menu ini digunakan untuk mengubah keterangan suatu transaksi, biasanya hal ini digunakan jika ada balasan informasi dari supplier.|
| Kirim Pesan ke Reseller | Menu ini digunakan untuk mengirim pesan ke buyer / reseller, biasanya pesan yang dikirimkan mengenai informasi transaksi masih diproses.|
| Detail Transaksi | Menu ini digunakan untuk melihat detail transaksi yang masuk melalui inbox, biasanya operator / Customer Service yang menegecek pesan dari supplier.|
| Stock Terminal | Menu ini adalah **Shortcut** yang digunakan untuk melihat stok saldo di terminal.|
| Set Produk Aktif | Menu ini adalah **Shortcut** untuk mengarahkan suatu produk yang akan diproses ke terminal, selain itu dapat mengubah status prosuk misal sedang mengalami gangguan jaringan, operator dapat merubah status terminal.|


* Produk

Modul produk ini diguanakan untuk mendaftarkan harga produk baru dan merubah harga produk jika terjadi perubahan kenaikan dan penurunan harga. Biasanya informasi kenaikan dan penurunan harga diberikan oleh divisi bisnis development.
Kemudian produk yang sudah di setting nantinya akan ditampilkan dimodul set produk aktif.

* Set Produk Aktif

Modul set produk aktif ini digunakan  untuk menampilkan produk - produk yang sudah aktif dan siap dipasarkan. Dan mengarahkan produk yang akan diproses ke terminal.

* Daftar Reseller

Modul daftar reseller ini digunakan untuk mendaftarkan member baru baik member yang terdaftar di IP maupun Jabber. Modul ini juga yang mengatur untuk pergantian pin akun reseller, penambahan deposit, merubah data reseller, dan menghapus data reseller.

* Keuangan 

Modul keuangan ini digunakan untuk melakukan transaksi deposit, refund dan input tiket deposit.


## 2. System Otomax

System Otomax ( Orisinil Topup Machine) adalah aplikasi server pulsa serba otomatis dengan kecepatan, akurasi, dan stabilitas yang tinggi dan mudah digunakan.

### Modul - Modul yang tersedia di Otomax System sebagai berikut :


* Sms Center

Modul sms center digunakan untuk melakukan pengecekan pesan masuk baik dari reseller maupun supplier, Biasanya pesan yang masuk berisi informasi tentang status transaksi pengisian pulsa baik menggunakan chip kepoo maupun menggunakan chip SPL (*supplier*).

* Sms Sender

Modul sms sender digunakan untuk mengirimkan pesan ke buyer ketika selesai proses transaksi atau pengecekan status transaksi.