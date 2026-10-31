# Riwayat Versi Pilar ERP

Catatan perubahan tiap versi aplikasi desktop Pilar ERP. Installer: [Releases](https://github.com/NaviaAng/pilar-erp-installer/releases/latest) atau https://app.pilarsukses.com/unduh/.

## 1.0.37 (31 Oktober 2026)

### Baru
- **Dasbor admin › Server**: keamanan VPS tanpa SSH. Melihat aturan firewall, IP yang diblokir fail2ban, pengaturan SSH, pembaruan keamanan
  yang tertunda dan perlu-restart, port yang terbuka ke internet, pengguna sudo, dan status layanan.
- **Dasbor admin › Server**: tambah / hapus aturan firewall (izinkan atau blokir, dari satu IP / jaringan / semua alamat, ke satu port / semua
  port), blokir dan buka blokir IP di fail2ban, login password SSH hidup/mati, pasang pembaruan keamanan sekarang, restart caddy / postgresql /
  pilar-erp / fail2ban. Setiap perubahan meminta password admin dan tercatat di riwayat (siapa, kapan, dari IP mana, hasilnya).
- **Dasbor admin › Ringkasan**: peringatan baru untuk firewall mati, port terbuka yang tidak diharapkan, pembaruan keamanan menumpuk, server
  perlu restart, layanan inti mati, dan login password SSH yang masih hidup.

### Perlu diperhatikan
- Perubahan firewall dan SSH dari dasbor berlaku sementara: tekan **Tetap pakai** dalam 60 detik, kalau tidak server mengembalikannya sendiri.
  Port SSH/HTTP/HTTPS dan alamat IP pengelola tidak bisa ditutup dari dasbor.
- Halaman Server baru bisa mengubah server setelah skrip server di VPS diperbarui; sebelum itu halamannya kosong.

## 1.0.36 (31 Oktober 2026)

### Baru
- **Pembelian › Pesanan Pembelian** (PO) untuk semua supplier, menggantikan Permintaan Grup. Supplier umum: harga perkiraan & jenis PPN,
  tanggal dibutuhkan, cetak (dengan / tanpa harga) dan **Salin untuk WhatsApp**. Supplier grup (GRP-…): pesanan langsung masuk ke perusahaan
  penjual seperti Permintaan Grup sebelumnya.
- **Pembelian › Baru › Dari pesanan**: faktur pembelian diisi dari sisa pesanan (supplier, jenis PPN, item, harga). Harga & qty boleh diubah,
  item lain boleh ditambah; qty lebih dari sisa pesanan (mis. berat timbangan) disimpan setelah dikonfirmasi. Status pesanan (Terbuka / Sebagian /
  Selesai) mengikuti fakturnya.
- **Pengaturan Perusahaan › Pembelian › Pesanan Pembelian**: pilihan "faktur pembelian dari supplier umum wajib dari pesanan" dan "penjualan grup
  ke perusahaan ini wajib dari pesanan". Bawaan keduanya mati: pesanan opsional, alur lama tetap jalan.
- Master Supplier & Konsumen: kolom **Jenis** (Umum / Grup).
- Pesanan Pembelian ikut **Riwayat**, **Data Terhapus** (Pulihkan), dan **Bersihkan Data** per jenis.
- **Dasbor admin** (console) bertampilan baru bergaya dasbor modern: latar putih dan abu-abu muda, garis tipis, menu samping setinggi layar
  dengan **Cari menu** (Enter membuka hasil pertama) dan nama pengguna serta tombol keluar di bawahnya, judul halaman di bilah atas, dan
  kartu angka dengan ikon lingkaran berwarna. Mode gelap otomatis tetap ada. Situs lain tidak berubah.

### Perbaikan
- Faktur pembelian biasa ke supplier grup (GRP-…) kini ditolak: pembelian dari perusahaan grup dicatat lewat **Terima dari grup**, supaya stok
  & hutang tidak tercatat dua kali. Faktur lama tetap bisa diubah.

### Perlu diperhatikan
- Menu **Pembelian › Permintaan Grup** kini bernama **Pesanan Pembelian**, **Penjualan › Permintaan Masuk** menjadi **Pesanan Masuk**, dan
  **Dari permintaan** di Faktur Penjualan menjadi **Dari pesanan**. Permintaan lama ikut pindah (nomornya tetap), begitu juga hak jabatan dan
  format nomornya (dokumen baru bernomor PO).
- Pengaturan "penjualan grup wajib dari permintaan" pindah dari tab Perusahaan ke tab Pembelian.
- Aplikasi desktop versi lama tidak bisa membuka menu pesanan: perbarui aplikasi bersamaan dengan server.

## 1.0.35 (31 Oktober 2026)

### Baru
- **Dasbor admin › Tim** (console): pengelola bisa memantau Tim perusahaan pelanggan mana pun dari browser, tanpa login ke perusahaan itu.
  Isinya sama dengan **Beranda › Tim** di aplikasi: kartu User (siapa online / idle / sibuk, cabang yang sedang dibuka, menu terakhir, jam aktif
  & idle hari ini, asal login), tab Perangkat (per user × perangkat per tanggal, idle menurut aktivitas aplikasi atau mouse & keyboard),
  grafik waktu lajur cabang per aplikasi dengan latency, dan rentang waktu dari jam:menit sampai jam:menit. Jam menurut WIB; data terbaru
  lewat tombol **Muat ulang**. **Perusahaan pelanggan** punya tautan **Lihat** ke Tim tiap perusahaan.
- **Tampilan web baru** (dasbor admin, landing Pilar ERP, situs PT Pilar Sukses Sinergi, halaman unduh): gaya lebih modern dengan permukaan lega,
  bayangan lembut, dan sudut membulat; **mode gelap otomatis** mengikuti pengaturan perangkat; gerak halus saat halaman dibuka dan saat digulir
  (mati bila perangkat meminta gerak dikurangi). Dasbor admin: menu samping dan kartu angka berikon, foto inisial pengguna, dan kerangka abu-abu
  saat halaman dimuat.

### Perbaikan
- **Beranda › Tim**: koneksi ke server yang putus saat Tim terbuka tidak lagi memunculkan pesan "Tidak bisa terhubung ke server"; data terakhir
  tetap tampil. Tim (tab User dan Perangkat) tidak lagi memuat ulang sendiri tiap 30 detik: tekan **Muat Ulang** untuk data terbaru.

### Perlu diperhatikan
- Menu **Beranda › Tim** di aplikasi desktop tetap ada dan tetap bisa dipakai pelanggan.
- Pengelola kini bisa melihat aktivitas dan IP karyawan pelanggan; sebutkan pemantauan ini di perjanjian layanan. User yang memilih
  **Tidak tampak** tetap terlihat Offline di kartu Tim dasbor.

## 1.0.34 (30 Oktober 2026)

### Baru
- **Penjualan › Permintaan Masuk**: perusahaan penjual kini punya daftar sendiri untuk Permintaan Pembelian Grup yang masuk dari perusahaan satu
  grup usaha: no., tanggal, perusahaan & cabang peminta, status (Terbuka / Sebagian / Selesai / Ditutup / Batal), jumlah item dan item sisa, no.
  faktur Anda, no. pembelian penerimanya, dan masalah yang menghalangi (mis. kode item belum ada di perusahaan ini). Item permintaan terpilih
  tampil di bawah dengan qty diminta, terkirim, dan sisa.
- Bawaannya **Belum selesai saja** (yang masih ada sisanya, tanggal berapa pun); hilangkan centang untuk melihat semua status menurut tanggal.
  Daftar per cabang: hanya permintaan untuk cabang ini atau untuk semua cabang.
- **Buat Faktur** (atau klik dua kali) membuka Faktur Penjualan baru dengan permintaan itu sudah terpilih di **Dari permintaan**: konsumen grup dan
  sisa item terisi dengan harga modal. Setelah disimpan, daftar dimuat ulang. **Lihat Faktur** membuka faktur yang sudah dibuat dari permintaan
  itu, di cabangnya.
- **Akuntansi › Aset Tetap**: daftar aset tetap per cabang dengan harga, akumulasi, nilai buku, sisa umur dan status per tanggal. Form aset
  menghitung **jadwal penyusutan** sampai habis saat mengetik, dengan tab Dibayar dari, Jadwal dan Riwayat. Asal perolehan: **Beli sekarang**
  (jurnal perolehan dari akun kas / bank, hutang lain-lain, hutang leasing, …), **Sudah dijurnal** (tanpa jurnal) atau **Saldo awal**
  (akumulasi awal per tanggal, jurnal saldo awal opsional). Kode aset otomatis per kelompok, mis. PRL-0001.
- **6 metode penyusutan**: Garis Lurus, Saldo Menurun, Saldo Menurun lalu Garis Lurus, Jumlah Angka Tahun, Satuan Pemakaian (km / jam,
  diisi tiap bulan) dan Tidak Disusutkan (tanah). Amortisasi aset tak berwujud memakai Garis Lurus. Pembulatan rupiah tanpa selisih menumpuk,
  tidak pernah melewati nilai sisa.
- **Ubah Estimasi** di daftar aset: umur, nilai sisa, metode, tarif atau perkiraan pemakaian diubah mulai bulan pertama yang belum diposting,
  selisihnya dibagi rata ke sisa umur; jadwal sebelum / sesudah tampil berdampingan, alasan wajib, tercatat di tab Riwayat.
- **Akuntansi › Aset Tetap › Penyusutan**: satu dokumen per cabang per bulan dengan jurnal beban / akumulasi otomatis per kelompok. Bulan
  yang terlewat (aset didaftarkan terlambat) disusulkan sekaligus, **Posting s/d bulan** membuat bulan-bulan yang tertinggal, batal hanya
  dokumen bulan terakhir.
- **Tutup Periode** memposting penyusutan yang belum diposting secara otomatis (sudah tampil di pratinjau laba rugi & jurnal penutup) dan
  membatalkannya lagi bila periode dibuka kembali. Pemeriksaan baru: penyusutan bulan ini, pemakaian kosong, **aset tetap = buku besar**,
  dan kelompok aset yang akunnya belum lengkap.
- **Akuntansi › Aset Tetap › Pelepasan Aset**: aset dijual atau dihapus (rusak / hilang); harga perolehan & akumulasinya dikeluarkan, laba ke
  Laba Penjualan Aset Tetap (4-2400) dan rugi ke Rugi Penjualan Aset Tetap (6-3000). Juga lewat tombol **Lepas** di daftar aset.
- **Akuntansi › Aset Tetap › Kelompok Aset**: akun aset / akumulasi / beban dan metode & umur bawaan per kelompok. Perusahaan mendapat
  kelompok bawaan sesuai jenis usahanya (peralatan dapur, mesin kopi, furnitur, komputer, kendaraan, armada, bangunan, renovasi, tanah, aset
  tak berwujud).
- **Menu Laporan › Laporan Aset Tetap**: Daftar Aset Tetap (rinci, per kelompok, per cabang, dibanding buku besar), Penyusutan (kolom per
  bulan, per kelompok, per dokumen) dan Pelepasan Aset.

### Perlu diperhatikan
- Menu **Permintaan Masuk** memakai hak **Penjualan** (Lihat untuk daftar, Buat untuk Buat Faktur); tidak ada hak baru.
- Jabatan yang boleh membuat Jurnal Umum otomatis mendapat hak Aset Tetap, Penyusutan & Pelepasan Aset; jabatan yang boleh melihat Neraca
  mendapat laporan aset. Fitur bisa dimatikan di **Pengaturan Perusahaan › Fitur › Akuntansi**.
- Template akun baru **1-3090 Akumulasi Amortisasi Aset Tak Berwujud**; perusahaan lama bisa mengimpornya lewat **Akun (COA) › Template…**.
  Akun 4-2400 / 6-3000 dipakai sebagai akun sistem laba / rugi pelepasan aset (bila kodenya dipakai akun lain, petakan di Pengaturan ›
  Akuntansi). Kelompok aset di perusahaan dengan bagan akun hasil migrasi bisa berakun kosong: isi dulu di Kelompok Aset.
- Penyusutan yang selama ini dicatat lewat Jurnal Umum jangan diulang: daftarkan asetnya sebagai **Saldo awal** per tanggal terakhir
  penyusutan manual itu.

## 1.0.33 (30 Oktober 2026)

### Baru
- **Akuntansi › Buku Besar**: menu baru untuk melihat mutasi per akun (saldo awal, debit, kredit, saldo berjalan) di satu cabang atau semua cabang yang
  boleh diakses. Klik dua kali baris membuka dokumen asalnya langsung di formnya: faktur penjualan / pembelian, penerimaan piutang / pembayaran hutang,
  kas masuk / keluar / transfer, jurnal umum, saldo awal, item masuk / keluar, transfer, titipan, rakitan, pecah stok, opname, dan retur. Penyesuaian nilai
  persediaan membuka dokumen yang memicunya; jurnal tanpa dokumen asal (jurnal umum, saldo awal akun, tutup buku) membuka jurnalnya sendiri.
  Pilih satu akun, akun induk (semua akun di bawahnya), atau kosongkan untuk semua akun. Bisa diekspor ke Excel dan dicetak.
- **Akuntansi › Buku Besar**: kolom **No Dokumen** menampilkan nomor dokumen asal tiap jurnal otomatis (mis. kas keluar `KK/01/2609/0020` di samping
  jurnalnya `JU/01/2609/0947`). Kedua nomor kini berupa link: klik **No Jurnal** untuk membuka jurnalnya, klik **No Dokumen** untuk membuka dokumen
  asalnya (kas masuk / keluar / transfer, faktur, pelunasan, retur, koreksi, transfer, titipan, rakitan, pecah stok, opname, saldo awal) langsung dari
  Buku Besar, tanpa lewat Jurnal Umum dulu. Klik dua kali baris tetap membuka dokumen asalnya; klik kanan sel untuk menyalin nomornya. Jurnal umum,
  saldo awal akun, dan tutup buku tidak punya No Dokumen karena jurnalnya sendiri dokumennya.
- **Kas & Bank › Tagihan Biaya**: biaya bulan ini yang dibayar nanti (listrik pascabayar, royalti, jasa akuntan) dicatat di bulan tagihannya
  atas nama supplier, lalu dibayar lewat **Pembayaran Hutang** seperti faktur pembelian. Tagihan ikut laporan hutang (saldo, umur, kartu, jatuh tempo)
  tetapi tidak ikut laporan pembelian. Baris boleh minus untuk potongan, mis. PPh 4(2) / 23 yang dipotong ke akun hutang pajak.
- **Kas & Bank › Biaya Rutin**: jadwal biaya berulang per cabang (sewa, gaji, listrik, internet, BPJS, setor PB1, PPh Final, royalti) tiap bulan, tiap
  beberapa bulan atau tahunan, dengan bulan mulai & berakhir. Jumlah tiap baris bisa tetap, diisi saat dicatat, persen dari penjualan neto (+ biaya
  layanan) cabang di bulan itu, atau saldo akun per akhir bulan sebelumnya. Satu layar per bulan menunjukkan status tiap jadwal (Belum, Terlambat,
  Dicatat, Dilewati) dengan nomor dokumennya.
  - **Catat** membuka form Kas Keluar / Tagihan Biaya / Jurnal Umum yang sudah terisi dari jadwal; periksa, ubah bila perlu, lalu Simpan.
  - **Catat Sekaligus** mencatat baris yang dicentang tanpa membuka form, satu dokumen per jadwal (semua atau tidak sama sekali).
  - **Lewati** untuk bulan yang memang tidak ada biayanya (alasan wajib).
  - Biaya tidak pernah tercatat sendiri tanpa diklik. Dokumen hasil yang dibatalkan membuat jadwalnya kembali Belum.
- **Kunci & Tutup Buku**: pemeriksaan baru "Biaya rutin sudah dicatat" memperingatkan jadwal bulan itu yang belum dicatat / dilewati.

### Perlu diperhatikan
- Hak baru **Buku Besar** (Lihat) di Jabatan & Hak Akses, grup Akuntansi. Jabatan yang sudah boleh melihat Laporan Buku Besar otomatis mendapatnya, dan jabatan
  bawaan Akunting mendapatnya di perusahaan baru. Membuka dokumen asal dari baris tetap butuh hak Lihat di menu dokumen itu; tanpa hak itu muncul pesan yang
  menyebut menu yang dibutuhkan.
- Laporan Buku Besar di Menu Laporan tidak berubah dan tetap mengikuti hak laporannya; angka keduanya sama.
- Hak baru **Tagihan Biaya** dan **Biaya Rutin** di Jabatan & Hak Akses, grup Kas & Bank. Jabatan yang sudah boleh membuat Kas Keluar otomatis
  mendapat keduanya; jabatan bawaan Akunting mendapatnya di perusahaan baru. Catat butuh juga hak Buat di menu hasilnya (Kas Keluar, Tagihan Biaya,
  atau Jurnal Umum).
- Pemeriksaan buku bantu hutang di Tutup Periode kini menghitung tagihan biaya; Bersihkan Data punya jenis baru **Tagihan biaya**.

## 1.0.32 (30 Oktober 2026)

### Baru
- **Akun (COA) › Template…**: melihat template bagan akun bawaan (per jenis usaha, atau **Semua jenis usaha**) berdampingan dengan bagan akun perusahaan Anda. Tiap akun diberi status: **Baru** (belum ada), **Sudah ada**, **Nama sama** (akun bernama sama sudah ada dengan kode lain) atau **Kode dipakai** (kodenya sudah dipakai akun lain).
- Akun yang belum ada bisa **diimpor** ke perusahaan yang sudah berjalan: centang akunnya (yang **Baru** sudah tercentang; klik dua kali baris kelompok untuk memilih atau mengosongkan seisinya), lalu **Impor**. Akun induk yang belum ada ikut dibuat otomatis, sedangkan akun yang sudah ada tidak diubah dan akun yang kodenya bentrok dilewati. Kotak **Sembunyikan yang sudah ada** menyisakan akun yang belum ada.
- Melihat template butuh hak **Akun (COA) › Lihat**; mengimpor butuh hak **Buat**.

### Perlu diperhatikan
- Contoh: **Akumulasi Penyusutan – Peralatan** (1-2900) dan **Beban Penyusutan Peralatan** (6-2000) ada di template, jadi perusahaan lama tinggal mengimpornya, tidak perlu membuat sendiri.

## 1.0.31 (29 Oktober 2026)

### Baru
- **Pembelian › Permintaan Grup**: cabang perusahaan pembeli bisa **meminta item & qty** ke perusahaan satu grup usaha. Perusahaan penjual lalu membuat **Faktur Penjualan** dan memilih permintaan itu di **Dari permintaan**: konsumen grup dan item sisa permintaan terisi otomatis dengan harga modal. Qty boleh dikurangi (sisanya bisa dikirim kemudian), item lain tidak bisa ditambah. Fakturnya diterima pembeli lewat **Pembelian › Terima dari grup** seperti biasa.
- Status permintaan mengikuti faktur penjual: **Terbuka**, **Sebagian**, **Selesai**, **Ditutup**, atau **Batal**. Daftar permintaan menampilkan no. faktur penjual dan no. pembelian penerimanya; form permintaan menampilkan **Terkirim** dan **Sisa** per item. Permintaan yang sudah dibuatkan faktur tidak bisa diubah atau dihapus, hanya **ditutup** (alasan wajib) bila sisanya tidak perlu dikirim.
- **Faktur Penjualan** ke perusahaan grup tetap bisa dibuat langsung tanpa permintaan, jadi kedua cara bisa dipakai bersamaan. Daftar faktur punya kolom **Permintaan**.
- **Pengaturan Perusahaan › Grup usaha › Penjualan grup ke perusahaan ini wajib dari Permintaan** (bawaan mati): dicentang di perusahaan pembeli, faktur penjualan grup **ke perusahaan itu** harus dibuat dari permintaannya. Hanya transaksi antar perusahaan grup; pembelian ke supplier biasa, penjualan, Kasir, dan import tidak terpengaruh.
- **Cabang pengirim** (opsional) di form permintaan: kosong = cabang penjual mana pun boleh memenuhi; diisi = hanya cabang itu yang melihat permintaannya di **Faktur Penjualan › Dari permintaan**, dan fakturnya harus dibuat di cabang itu.
- **Faktur dari permintaan hanya bisa diterima di cabang peminta.** Di cabang pembeli lain faktur itu tidak muncul di **Pembelian › Terima dari grup**. Faktur grup tanpa permintaan tetap bisa diterima di cabang mana pun.
- Hak baru **Permintaan Pembelian Grup** di **Sistem › Jabatan & Hak Akses** (Batal = juga Tutup) dan nomor dokumen **PMG** di Penomoran Dokumen.

### Perbaikan
- **Import Data › Item**: harga pokok stok awal yang tidak sampai ke HPP kini diberi **peringatan** di Periksa dan Import (sebelumnya jatuh diam-diam). Peringatan muncul bila **Stok bertambah tanpa Harga Pokok** pada item yang HPP-nya masih 0 (stok awal bernilai 0 di persediaan dan HPP penjualannya 0), dan bila **Harga Pokok diisi padahal Stok kosong, 0, atau tidak lebih besar dari stok sistem** (HPP hanya terbentuk dari stok yang bertambah, jadi Harga Pokok itu diabaikan). Pesannya menyebut cara memperbaiki HPP yang sudah terlanjur 0: ubah **Harga Pokok** baris item itu di **Stok Opname** "Import item (stok awal)". Catatan kolom **Harga Pokok** di template ikut diperjelas.

### Perlu diperhatikan
- Item dicocokkan antar perusahaan lewat **kode item yang sama** dan satuan dasar yang sama, seperti Terima dari grup.
- Jabatan yang sudah boleh membuat Pembelian (termasuk Gudang) otomatis mendapat hak Permintaan Pembelian Grup.

## 1.0.30 (29 Oktober 2026)

### Baru
- **Hak lihat harga modal per menu persediaan**: enam hak baru di **Sistem › Jabatan & Hak Akses**, selain hak yang sudah ada untuk Penjualan, Pembelian & Item, dan Cetak. **Lihat Harga Modal di Item Masuk/Keluar & Saldo Awal Stok**, **di Transfer Antar Cabang**, **di Titipan**, **di Stok Opname**, **di Rakitan / Produksi**, dan **di Pecah Stok**. Tanpa hak itu, harga pokok, jumlah, nilai selisih, dan total menu tersebut **disembunyikan di semua tempat**: daftar, form, **Riwayat**, **Laporan Sistem › Log Aktivitas**, **Data Terhapus**, dan cetakan. Nilainya **tidak dikirim server**. Qty tetap terlihat seperti biasa.
- **Hak lihat harga di Pembelian & Retur Pembelian** (hak ketujuh, **Lihat Harga di Pembelian & Retur Pembelian**): tanpa hak ini harga, potongan, DPP, PPN, total, jumlah yang sudah dibayar, dan sisa hutang dokumen **Pembelian** dan **Retur Pembelian** disembunyikan di daftar, form, **Riwayat**, **Data Terhapus**, dan cetakan, serta tidak dikirim server. Qty, supplier, tanggal, dan catatan tetap bisa dikerjakan.
- **Gudang bisa mencatat pembelian tanpa melihat harga.** Pembelian oleh user tanpa hak itu memakai **harga beli terakhir** item (kalau belum pernah dibeli, HPP rata-rata), tanpa potongan, dan **kredit seluruhnya**; saat diubah, harga, potongan, pembulatan, dan pembayaran yang tersimpan tetap. Item yang belum pernah dibeli dan belum punya HPP ditolak. Harga yang sebenarnya dikoreksi kemudian oleh jabatan yang punya hak itu (mis. Akunting) lewat ubah pembelian, yang menghitung ulang HPP seperti biasa.
- **Retur Pembelian** menentukan potongan hutang dan uang kembali, jadi **membuat dan mengubahnya** butuh hak yang sama; user tanpa hak hanya bisa melihat qty-nya, membatalkan atau menghapus sesuai hak menunya.
- **Yang tidak boleh melihat harga modal juga tidak bisa mengisinya.** Item Masuk, Saldo Awal Stok, Titip Masuk, dan Stok Opname oleh user tanpa hak memakai harga otomatis: **HPP rata-rata**; untuk Titip Masuk dari penitip, harga setoran terakhir lalu HPP rata-rata. Saat dokumen diubah, baris lama **tetap pada harga tersimpannya**, juga bila satuannya diganti (misalnya box menjadi pcs). Item yang **belum punya HPP ditolak** dengan pesan tanpa angka, supaya tidak tercatat bernilai 0; mintalah user yang punya hak untuk mencatatnya. **Import Data dikecualikan**: pemegang hak Import Data bekerja dengan harga pokok / harga titip dari file, dan hasil importnya tetap menampilkan total.
- **Setoran ke Penitip** untuk user tanpa hak Titipan: kolom **Perkiraan** dan baris **Selisih ke HPP** tidak tampil, dan harga setoran bawaan hanya harga setoran terakhir. Untuk item yang belum pernah disetor, isi harganya dari tagihan penitip.
- **Cetak "dengan harga"** dokumen persediaan butuh hak **Cetak …: dengan harga** di menunya dan hak **Lihat Harga Modal** menu itu (bila tidak, harga pokoknya tertutup); template "dengan harga" tidak ditawarkan tanpa keduanya, jadi tidak ada cetakan berisi harga atau "TOTAL NILAI" 0.

### Perbaikan
- **HPP di Retur Penjualan** dan **HPP di Riwayat faktur penjualan** kini mengikuti hak **Lihat HPP / Harga Modal di Penjualan**; sebelumnya masih terkirim ke user tanpa hak itu. **Detail** daftar Kasir / Faktur tidak lagi menampilkan "HPP 0" untuk user tersebut.
- **Master Item**: HPP resep, Est. HPP, dan margin di tab Resep, serta harga bawaan **Retur Pembelian** tanpa faktur asal, kini mengikuti hak **Lihat Harga Modal di Pembelian & Item**. Harga beli terakhir hanya dikirim ke user dengan hak itu. HPP rata-rata item hanya dikirim ke user yang punya salah satu hak harga modal / harga pokok, dan perkiraan HPP hanya ke user yang punya hak Lihat HPP di Penjualan.

### Perlu diperhatikan
- **Jual ke perusahaan grup** berharga HPP rata-rata, jadi kini butuh hak **Lihat HPP / Harga Modal di Penjualan**; jabatan yang sudah ada otomatis memilikinya.
- Hak diberikan per **jabatan**. Jabatan yang sudah ada otomatis mendapat hak harga modal untuk menu yang memang boleh dibukanya; Gudang & Akunting bawaan mendapat keenamnya, sama seperti perusahaan baru. Jadi tampilannya tidak berubah sampai Admin mencabutnya. Contoh: agar gudang tidak melihat HPP di **Item Keluar** dan **Transfer Keluar**, hilangkan centang **Lihat Harga Modal di Item Masuk/Keluar & Saldo Awal Stok** dan **di Transfer Antar Cabang** pada jabatan Gudang. **Jabatan baru** harus dicentang sendiri. Untuk mengatur satu user saja, buat jabatan khusus untuk user itu.
- Agar HPP benar-benar tertutup, cabut juga hak **Lihat harga pokok (HPP) di laporan**, karena **Laporan, Analisa & Kartu Stok** mengikuti hak itu. **Jurnal / Buku Besar** mengikuti hak menunya, dan **Rekalkulasi HPP** menampilkan HPP semua dokumen.
- Kartu **Pembelian** di Dasbor kini butuh hak **Lihat Harga di Pembelian & Retur Pembelian** (atau hak Laporan Pembelian). Jabatan yang sudah ada otomatis memiliki hak baru ini bila boleh membuka Pembelian / Retur Pembelian.
- **Harga Setoran ke Penitip** dan **harga jual Laku Titipan** adalah harga kesepakatan, bukan harga modal, sehingga tetap terlihat.
- Menyimpan jabatan dari aplikasi versi lama tidak mengubah keenam hak baru ini; perbarui aplikasi untuk mengaturnya. Sebaiknya naikkan **versi minimum aplikasi** ke 1.0.30 setelah rilis.

## 1.0.29 (29 Oktober 2026)

### Baru
- **Beranda › Tim › Perangkat › Grafik** kini berbentuk **lajur per cabang**: sumbu tegak = cabang yang dibuka hari itu, ditambah lajur **Hilang** (tidak ada aplikasi terbuka: belum login, sudah keluar, PC mati / sleep, atau internet putus). Satu **garis per aplikasi**; **pindah cabang** = garis pindah lajur. Titik per interval berwarna status: **hijau aktif, kuning idle, abu-abu hilang**; tooltip berisi rincian aktif / idle / cabang di interval itu. Urutan aktif → idle → hilang → aktif kini terlihat jelas.
- **Interval** grafik: **15 / 30 / 60 menit** atau **4 / 8 / 12 / 24 jam** (bawaan 15 menit). Garis **Latency (ms)** kini bawaan mati, centang untuk menampilkan.
- **Idle menurut** (tab Perangkat): **Aktivitas aplikasi** (bawaan) = tidak ada aksi ke server selama 5 menit (buka menu, cari, muat, simpan, cetak; mouse yang sekadar digerakkan tidak dihitung), atau **Mouse & keyboard** = tidak ada gerak mouse / ketikan di jendela aplikasi. Keduanya dicatat di setiap detak; data sebelum versi ini hanya punya mouse & keyboard.
- **Dua aplikasi dibuka di PC yang sama** (mis. beda cabang): grafik menggambar dua garis (Aplikasi 1, Aplikasi 2), kolom **Status** menyebut jumlah aplikasi yang terbuka, kolom **Cabang** berisi semua cabang yang dibuka hari itu, dan **Keluarkan perangkat** mengeluarkan semua aplikasi di PC itu.
- **Rentang waktu** di bawah grafik: daftar dari jam:menit sampai jam:menit kini juga menyebut **Cabang** dan **Aplikasi** ke berapa.

### Perbaikan
- **Tim › Perangkat**: **Lama Aktif / Lama Idle** tidak lagi dobel bila dua aplikasi terbuka bersamaan di PC yang sama (dihitung aktif bila salah satu aplikasi aktif). Sesi yang dimulai kemarin dan masih berjalan ikut terhitung hari ini.
- **Grafik perangkat**: 5 menit pertama sebelum idle kini ikut idle (sebelumnya tercatat aktif di grafik, sedangkan tabel sudah idle), untuk data sesudah versi ini.

## 1.0.28 (28 Oktober 2026)

### Baru
- **Bagan akun awal mengikuti jenis usaha.** Perusahaan baru kini mendapat akun yang sesuai bisnisnya, bukan satu daftar yang sama untuk semua. Pilihan **Jenis usaha** bertambah: **Restoran**, **Kafe / Coffee Shop**, **UMKM / Produksi Rumahan**, **Toko Oleh-oleh**, **Pengangkutan / Ekspedisi**, Restoran + Toko Oleh-oleh, dan Lainnya. Akun yang disiapkan sekitar 85 sampai 130, bertingkat rapi. Contoh: kafe mendapat Mesin Kopi dan Komisi Pesan-Antar, UMKM mendapat Beban Produksi dan Pajak Final 0,5%, pengangkutan mendapat BBM, Tol, Uang Jalan, Armada, dan Hutang Leasing. Akun lain bisa ditambah atau dihapus kapan saja di **Akuntansi › Bagan Akun**.
- **Wizard Perusahaan Baru** (Sistem › Admin Platform › Baru, dan **Daftar perusahaan baru** di layar login): lima langkah, yaitu Perusahaan, Jenis usaha, Cabang pertama, Administrator, lalu Ringkasan. Di langkah Jenis usaha, daftar akun awal yang akan dibuat langsung tampil di sebelah kanan. Pendaftaran dari layar login yang dulu tidak menanyakan jenis usaha kini menanyakannya. Password admin diminta dua kali. Langkah Cabang kini meminta **kode cabang** (dipakai di nomor dokumen, mis. PJ/ST/2610/0001), disarankan dari nama cabang dan dilengkapi contoh nomornya. Dulu semua perusahaan baru otomatis berkode 01.
- **Menu yang tampil mengikuti jenis usaha.** Perusahaan baru hanya melihat menu yang relevan: **Titipan** untuk restoran, kafe, dan toko oleh-oleh (titip jual); **Rakitan** dan **Pecah Stok** untuk semua kecuali Pengangkutan; Pengangkutan tanpa Titipan, Rakitan, Pecah Stok, Transfer, dan Promo. Menu yang disembunyikan bisa dinyalakan kapan saja di **Pengaturan › Fitur**.
- Kafe ikut memungut **PB1 dan biaya layanan** di cabang Outlet, sama seperti restoran.
- **Hak akses persediaan dipisah per menu**: di **Sistem › Jabatan & Hak Akses**, **Item Masuk**, **Item Keluar**, **Transfer Keluar**, dan **Transfer Masuk** kini masing-masing punya baris hak sendiri (dulu Item Masuk/Keluar satu hak dan Transfer satu hak). Gunanya untuk perusahaan yang ingin mencegah kecurangan: yang menambah stok dan yang mengurangi stok, atau yang mengirim dan yang menerima transfer, bisa dibuat orang yang berbeda. Contoh: petugas cabang tujuan hanya diberi **Transfer Masuk** tanpa bisa mengirim, atau gudang hanya **Item Keluar** tanpa bisa menambah stok. Perusahaan yang tidak butuh pemisahan cukup mencentang keduanya.
- **Hak cetak tanpa harga dan dengan harga per menu**: tiap menu persediaan (Item Masuk, Item Keluar, Transfer Keluar, Transfer Masuk, Stok Opname, Rakitan, Pecah Stok, Titipan, Saldo Awal Stok) punya dua hak, **Cetak …: tanpa harga** dan **Cetak …: dengan harga**, yang berdiri sendiri (boleh salah satu saja). Barisnya ada tepat di bawah menunya; tombol **Cetak ▾** hanya menawarkan template yang boleh dipakai.

### Perlu diperhatikan
- **Hak lama diubah otomatis** saat server diperbarui, jadi tidak ada yang hilang: hak Koreksi → hak yang sama di Item Masuk dan Item Keluar; hak Transfer → Transfer Keluar dan Transfer Masuk; hak Cetak Persediaan → cetak tanpa harga di menu yang bisa dibuka jabatan itu, dan cetak dengan harga bila dulu juga boleh mencetak dengan nilai dan dengan harga modal. Periksa lagi jabatan Anda bila ingin memisahkannya.
- **Cetak Faktur Pembelian dengan Harga Modal** (dulu "Cetak dengan Harga Modal") kini hanya untuk faktur pembelian; dokumen persediaan cukup hak "dengan harga" di menunya.
- Perbarui aplikasi di semua PC: versi lama tidak mengenal hak baru, sehingga menu Item Masuk/Keluar, Transfer, dan tombol cetak persediaan tidak muncul untuk user selain Admin.
- Perusahaan yang sudah berjalan **tidak berubah**. Mengubah Jenis usaha di Pengaturan Perusahaan juga tidak membuat ulang akun. Akun baru dibuat hanya saat perusahaan dibuat atau lewat **Bersihkan Data** (semua cabang, termasuk akun).

## 1.0.27 (28 Oktober 2026)

### Baru
- **Beranda › Tim kini punya dua tab.** Tab **User**: kartu ringkas (foto, nama, jabatan, status, pesan status, cabang yang sedang dibuka, lama aktif dan idle hari ini). Tab **Perangkat** (Admin atau hak Lihat Log Aktivitas): satu baris per **user di satu perangkat** pada satu hari, berisi nama device, aplikasi & versi, **login pertama**, jumlah login dan keluar, **aktif atau tidak sekarang**, lama aktif dan idle, serta latency. Pilih tanggal dengan kalender (bawaan hari ini).
- **Grafik waktu per perangkat**: tombol **Grafik** (atau klik dua kali baris) menampilkan kolom **aktif (hijau), idle (kuning), keluar (abu-abu)** sepanjang hari, dengan interval **1 / 5 / 10 / 30 menit atau 1 jam**, plus garis **latency (ms)** ke server. Tombol **Keluarkan perangkat** pindah ke tab ini. Grafik hanya ada untuk hari sesudah versi ini terpasang di PC user.
- **Pengaturan Cetak › Tanda tangan**: judul tanda tangan per dokumen bisa diubah, mis. `Gudang;Checker;Penerima`. Jumlah judul = jumlah kotak (1 sampai 4), `-` = tanpa tanda tangan, kosong = bawaan. Berlaku untuk A4, setengah A4, dan dot matrix; struk thermal tetap bawaan.
- **Cetakan tanpa harga lebih ringkas**: struk thermal satu baris per barang (`5 PCS  Nama barang`), dan urutan kolom tabel menjadi Qty, Satuan, Nama. Tanda tangan baru: penerimaan barang **Diserahkan, Diperiksa, Diterima**; bukti persediaan **Dikeluarkan** (item / transfer / titipan keluar) atau **Diserahkan**, Diperiksa, Diterima; Surat Jalan: Dibuat oleh, Pengirim, Penerima.

### Perbaikan
- **Bukti item masuk / keluar tanpa harga** tidak lagi mencetak **akun lawan (COA)** yang tidak dimengerti petugas lapangan; di cetakan dengan harga tetap tampil.
- **Beranda › Tim**: kartu user tidak lagi kosong.

## 1.0.26 (28 Oktober 2026)

### Baru
- **Cetakan tanpa harga lebih ringkas**: pada struk thermal, tiap barang kini **satu baris** `qty  satuan  nama` (kode item hanya tampil bila opsinya aktif). Pada tabel A4, setengah A4, dan form kontinu, urutan kolom menjadi **Qty, Satuan, Nama**, lalu harga bila ada.
- **Tanda tangan sesuai praktik umum**: **Bukti Penerimaan Barang** (pembelian) = Diserahkan, Diperiksa, Diterima. **Bukti persediaan** = **Dikeluarkan** (item / transfer / titipan keluar) atau **Diserahkan** (masuk), Diperiksa, Diterima. **Surat Jalan** = Dibuat oleh, Pengirim, Penerima. Bukti retur disesuaikan dengan arah barangnya.

### Perbaikan
- **Beranda › Tim**: kartu user tidak lagi kosong (nama, status, perangkat, dan hitungan kini tampil).

## 1.0.25 (28 Oktober 2026)

### Baru
- **Satu user di beberapa perangkat**: tiap login (PC / HP) kini punya **sesi sendiri** dengan ID unik (JTI) di tokennya. **Hitungan jam kerja, login, keluar, lama, aktif, dan idle dipisah per perangkat**; total user = jumlah semua perangkat. Laporan **Laporan Sistem › Jam Kerja Karyawan** punya pilihan baru **Per Perangkat**.
- **Batas perangkat per user** di **Pengaturan Perusahaan › Keamanan › Perangkat**: bebas, atau maksimal 1 / 2 / 3 / 4 / 5 / 10 perangkat. Bila terlampaui, pilih **keluarkan perangkat yang paling lama** atau **tolak login baru** (pesan menyebut perangkat yang sedang dipakai). Admin selalu mengeluarkan yang terlama supaya tidak terkunci.
- **Keluarkan perangkat**: di kartu **Beranda › Tim**, tombol **Keluarkan perangkat…** (akun sendiri, atau Admin / hak Ubah User untuk user lain). Perangkat itu langsung ditolak dan kembali ke layar login. **Sign Out** juga mencabut tokennya, sehingga token yang bocor tidak bisa dipakai lagi.
- **Kartu Tim** kini juga menampilkan **sedang di cabang mana**, **menu yang terakhir dibuka**, dan daftar perangkat dengan hitungannya masing-masing.
- **Riwayat pemakaian**: aplikasi mencatat **jam berapa user membuka menu apa dan di cabang mana** (ringkas, tanpa isi data; menu yang sama berturut-turut dalam 20 detik dihitung satu). Lihat di **Laporan Sistem › Log Aktivitas › Riwayat Pemakaian Menu**, dengan hak akses yang sama dengan Log Aktivitas. Dihapus bersama log lama sesuai masa simpan log.
- **Beranda › Tim** kini berbentuk **kartu** (CardView). Tiap kartu menampilkan foto, status, pesan status, **login terakhir dari mana** (aplikasi & versi, nama PC; alamat IP hanya terlihat oleh admin), **berapa kali login dan keluar** hari ini, serta **lama**, **aktif**, dan **idle** hari ini. Keluar dihitung dari sesi yang berakhir (Sign Out, aplikasi ditutup, atau terputus).

### Perbaikan
- **Template Cetak**: pengelompokan per dokumen tidak lagi hilang setelah Muat ulang, Aktifkan / Nonaktifkan, atau menyimpan dari designer.

## 1.0.24 (28 Oktober 2026)

### Baru
- **Hak harga modal**, tiga hak baru di **Jabatan & Hak Akses** (jabatan yang sudah ada tetap memilikinya; cabut sesuai kebutuhan):
  - **Lihat HPP / Harga Modal di Penjualan**: kolom HPP di daftar & faktur penjualan. Tanpa hak ini kolomnya hilang dan nilainya tidak dikirim server.
  - **Lihat Harga Modal di Pembelian & Item**: kolom HPP rata-rata & harga beli terakhir di daftar Item, label HPP di form Item, dan harga bawaan faktur pembelian (dari harga beli terakhir / HPP). Tanpa hak ini harga pembelian diketik sendiri.
  - **Cetak dengan Harga Modal**: template cetak "dengan harga" untuk faktur pembelian dan dokumen persediaan. Tanpa hak ini hanya template "tanpa harga" yang tampil.
- **Pengaturan Perusahaan › Penjualan › Harga jual di bawah HPP › Untuk user tanpa hak HPP**: bila pilihannya Peringatan, user yang tidak boleh melihat HPP akan **perlu persetujuan atasan** (pesan hanya menyebut itemnya, tanpa angka HPP) atau **tanpa peringatan**. Pilihan Tolak tetap berlaku untuk semua, juga tanpa angka HPP bagi yang tidak berhak.
- **Sistem › Pengaturan Cetak** (menu sendiri, hak akses sendiri **Pengaturan Cetak**: Lihat / Ubah; jabatan yang boleh mengubah Pengaturan Perusahaan mendapatkannya otomatis; berlaku untuk semua cabang): pilih **tampilkan nama perusahaan** dan **nama cabang** di kepala cetakan, **margin struk thermal** (kiri, kanan, bawah dalam mm; kiri / kanan boleh dikecilkan, bawah ditambah supaya mudah disobek), dan **kode item di cetakan tanpa harga**.
- **Cetakan tanpa harga** (penerimaan barang, surat jalan, bukti item keluar) tidak lagi menampilkan kode item; nyalakan di pengaturan Cetakan bila ingin kodenya.
- **Hak cetak dipisah: tanda terima dan faktur.** Hak yang sudah ada menjadi **Cetak … tanpa harga** (surat jalan, tanda terima / bukti penerimaan), dan ada hak baru **Cetak … dengan harga** (struk, faktur, nota retur) untuk Penjualan, Pembelian, dan Persediaan. Jabatan yang sudah boleh mencetak tetap boleh keduanya; hak "dengan harga" butuh juga hak dasarnya. Bukti kas tetap satu hak.
- **Sistem › Template Cetak**: centang beberapa template (atau centang baris judul dokumen untuk satu kelompok) lalu tekan **Aktifkan** atau **Nonaktifkan** untuk mengubah statusnya sekaligus. Template utama dilewati dengan keterangan (jadikan template lain utama dulu).

### Perbaikan
- **Struk thermal 80 mm dan 58 mm terpotong di kanan** (tanggal dan kolom nominal): lebar isi template bawaan dikecilkan sesuai area cetak printer thermal (80 mm menjadi 6,9 cm, 58 mm menjadi 4,8 cm). Margin kini bisa diatur di Pengaturan Cetakan (bawaan kiri 2 mm, kanan 8 mm, bawah 10 mm). Berlaku untuk semua template bawaan; salinan template yang sudah Anda simpan tetap berlebar lama, buat salinan baru dari template bawaan bila perlu.

### Perlu diperhatikan
- HPP rata-rata item masih ikut dikirim ke aplikasi untuk mengisi harga bawaan form persediaan (Item Masuk, Opname, Rakitan), jadi di sana hanya disembunyikan di layar, bukan dikosongkan dari server.

## 1.0.23 (27 Oktober 2026)

### Baru
- **Profil Saya** (menu akun, klik nama Anda di kanan atas): pasang **foto profil** (PNG / JPG, dikecilkan otomatis; tampil di lingkaran akun), pilih **status** (Otomatis, Sibuk, atau Tidak tampak) dan tulis **pesan status** (maks. 140 karakter, mis. "Di gudang sampai jam 3"). Tiap user mengatur profilnya sendiri.
- **Beranda › Tim** (baru): semua user perusahaan dengan foto, status **Online / Idle / Sibuk / Offline**, pesan status, terakhir terlihat, dan jam **aktif** serta **idle** hari ini. Disegarkan otomatis tiap 30 detik. User yang memilih Tidak tampak terlihat Offline oleh yang lain.
- **Jam kerja karyawan**: aplikasi mencatat lama dipakai tiap sesi (login sampai Sign Out / ditutup). **Aktif** = ada gerak mouse atau ketikan; **Idle** = tanpa input lebih dari 5 menit (termasuk saat layar terkunci). Laporan **Laporan Sistem › Jam Kerja Karyawan**: per user per hari (masuk pertama, terakhir terlihat, menit aktif / idle, % aktif) dan ringkasan per user dalam rentang tanggal.

- **Logo perusahaan** (satu per perusahaan, bukan per cabang): pasang di **Sistem › Pengaturan Perusahaan › Perusahaan › Logo** (PNG / JPG, dikecilkan otomatis, langsung tersimpan). Tampil di kiri bar judul untuk semua user dan semua cabang; tanpa logo = inisial perusahaan. Isian **Logo** di Master Cabang dihapus.
- **Server email (SMTP) diatur di aplikasi**: grup baru **Server email (SMTP)** di Pengaturan Perusahaan › Perusahaan (server, port, SSL, pengirim, user, password). Dipakai untuk ringkasan mingguan via email; password disimpan terenkripsi dan tidak pernah ditampilkan lagi. Dikosongkan = memakai pengaturan email di server (bila ada). Pesan gagal kirim kini menunjuk ke tempat mengisinya.
- **Menu Persediaan & Sistem disusun ulang** satu baris per kelompok, dari yang paling sering dipakai. Persediaan: Kartu Stok · Item · Satuan · Rak | Item Masuk · Item Keluar · Stok Opname | Transfer Masuk · Transfer Keluar | Rakitan / Produksi · Pecah Stok | Rekalkulasi. Sistem: Import Data | Integrasi Quinos · Daftar Pemetaan | Data Terhapus · Bersihkan Data | Pengaturan Perusahaan · Cabang · User · Jabatan · Izin Backdate · Pengaturan Cetak | Jenis PPN · Penomoran Dokumen · Template Cetak.

### Perlu diperhatikan
- Logo cabang yang pernah dipasang tidak dipakai lagi; pasang ulang sebagai logo perusahaan.
- Jam kerja dihitung dari aplikasi yang terbuka, bukan absensi: PC yang mati / tidur atau tanpa jaringan tidak terhitung. Sesi dicatat pada hari mulainya. Laporan Jam Kerja Karyawan bawaan hanya untuk Admin; jabatan lain diberi hak di **Jabatan & Hak Akses**.

## 1.0.22 (27 Oktober 2026)

### Baru
- **Sistem › Penomoran Dokumen** (baru): atur format nomor tiap jenis dokumen (faktur penjualan & pembelian, retur, pelunasan, stok, kas, jurnal, dan lainnya). Yang bisa diatur: **awalan**, **pemisah** (/ - . atau tanpa), **kode cabang** (tanpa kode cabang, semua cabang memakai satu urutan), **tahun** (tanpa, 2 atau 4 digit), **bulan**, **panjang nomor urut**, **kapan urutan mulai dari awal** (tiap bulan, tiap tahun, atau tidak pernah), dan **nomor awal**. Kolom **Contoh Nomor** langsung berubah saat diisi. Bawaan tetap `AWALAN/CABANG/YYMM/0001`. Format hanya berlaku untuk dokumen baru; nomor yang sudah terbit tidak berubah.
- **Hak akses** baru **Penomoran Dokumen** di grup Sistem: **Lihat** untuk membuka menu, **Ubah** untuk menyimpan format. Bawaan hanya Admin; jabatan lain tidak otomatis mendapatkannya.

### Perlu diperhatikan
- Mengganti hanya "kapan urutan mulai dari awal" pada jenis dokumen yang sudah punya nomor ditolak, karena nomor baru bisa kembar dengan yang lama. Ubah juga awalan, pemisah, kode cabang, atau tahun / bulan di nomor.

## 1.0.21 (27 Oktober 2026)

### Baru
- **Laporan & Analisa**: setiap laporan dan analisa kini dibuka di **tab sendiri**. Tab **Laporan** (tombol **Menu Laporan**) dan tab **Analisa** berisi daftar laporan beserta keterangannya; klik sekali untuk melihat keterangannya, **klik dua kali** (atau tekan **Enter**) untuk membukanya di tabnya sendiri, dan bila tabnya sudah terbuka Anda langsung dipindah ke tab itu. **Klik dua kali** baris, titik grafik, atau kartu yang membuka laporan rinci (mis. Tren Penjualan ke Laba Jual) selalu membuka **tab baru** (Laba Jual, Laba Jual #2, …), jadi laporan asal beserta hasilnya tetap terbuka dan tidak tertimpa.
- **Analisa › Harga Beli per Item**: kolom baru **Status** (Cek input, Fluktuasi tinggi, Naik, Turun, Sekali beli, Stabil; berwarna, yang perlu dicek paling atas), **Harga Tengah**, **Fluktuasi %** (selisih harga tertinggi dan terendah dibanding harga tengah), **Terakhir vs Rata-rata %**, dan **Harga Janggal** (jumlah pembelian yang harganya 3× lipat atau lebih, atau ⅓ atau kurang, dari pembelian lain item itu: kemungkinan salah ketik satuan atau qty). Status bisa dibaca tanpa periode pembanding. Batas "fluktuasi tinggi" diatur di isian **Ambang Fluktuasi %** (bawaan 20).
- **Analisa › Harga Beli per Item › Fluktuasi Tidak Normal** (pilihan laporan baru): daftar pembelian yang harganya menyimpang dari harga tengah item itu melebihi ambang, dikelompokkan per item, dengan Selisih, Selisih %, dan Kali Harga Tengah. Harga janggal diberi warna merah. Klik dua kali baris untuk membuka faktur pembeliannya.

- **Analisa › Analisa Belanja** (baru, bagian Pembelian): tujuh pilihan untuk melihat ke mana uang belanja pergi. **Efek Harga vs Qty** (per item dan per kategori) memisahkan kenaikan belanja karena harga naik dari karena beli lebih banyak. **Potensi Hemat** menghitung selisih bila item dibeli dari supplier termurah. **Supplier Kecil (Tail Spend)** menandai supplier kecil yang sering dipakai sebagai kandidat digabung. **Langsung vs Tidak Langsung** membandingkan belanja barang untuk dijual atau diolah dengan belanja operasional (non-stok, jasa, kas keluar ke beban). **Ketepatan Bayar Supplier** menunjukkan tepat waktu %, telat, bayar terlalu awal, dan sisa lewat jatuh tempo. **Pembelian di Luar Kebiasaan** mendaftar pembelian tanpa supplier, kas keluar untuk barang, supplier di luar kebiasaan, dan harga di atas harga biasa. Klik dua kali baris membuka laporan rinci atau dokumennya.
### Perbaikan
- **Jendela Pembaruan** (saat aplikasi memperbarui diri): kini berukuran dialog biasa, dan huruf, bilah progres serta tombolnya ikut ukuran font aplikasi.
- **Analisa**: panduan **Cara membaca** di kanan bawaannya disembunyikan, jadi grafik dan tabel lebih lebar. Buka dengan tombol **Tampilkan Panduan**.
- **Analisa › Harga Beli per Item**: **Harga Jual** dan **Margin Sekarang** kini dihitung dari rata-rata harga **penjualan sebenarnya** di periode itu (per satuan beli). Bila item tidak terjual di periode itu, harga master dipakai, dan kolom **Sumber Harga Jual** menunjukkan yang mana. Item yang tidak dijual (bahan baku, perlengkapan) atau tanpa harga master dibiarkan kosong, dan **HPP Sekarang** kosong untuk item Non-stok/Jasa.
- **Analisa › Harga Beli per Item**: bila periode pembanding tidak ada pembelian, keterangan di bawah tabel kini menjelaskan kenapa Harga Pembanding dan Selisih kosong. Grafik yang tidak punya nilai untuk digambar menampilkan keterangan, bukan sumbu kosong.

## 1.0.20 (26 Oktober 2026)

### Baru
- **Sistem › Daftar Pemetaan** (setelah Integrasi Quinos): semua pemetaan kode Quinos → item Pilar dalam satu daftar, dengan kolom **Kemiripan (%)** antara nama Quinos dan nama item Pilar (terendah di atas, filter "Hanya kemiripan < 50%"), plus tombol **Hapus Pemetaan**.
- **Integrasi Quinos › Item Quinos**: kolom **Kemiripan (%)** di grid pemetaan (merah bila < 50%). Kemiripan hanya informasi; **Cocokkan Otomatis** tetap hanya mengisi nama yang persis sama dan kini melaporkan berapa baris yang kemiripannya rendah.
- **Master Item › Duplikat**: tombol baru di samping Ubah — membuka item baru berisi salinan item terpilih (jenis, satuan & konversi, harga, resep / komponen, pecah stok, akun). Kode otomatis, barcode dikosongkan, nama diberi "(salin)".
- **Integrasi Quinos › Struk**: centang **Tampilkan Struk Detail** (bawaan mati) — baris item di bawah tiap struk hanya dibuat bila dicentang, supaya tidak memakan banyak memori.

### Perbaikan
- **Integrasi Quinos**: tombol 1. Buka, 2. Cek, 3. Simpan Pemetaan sejajar dengan pilihan tanggal, 4. Import rata kanan di bawahnya; isian tanggal diperkecil.

## 1.0.19 (26 Oktober 2026)

### Baru
- **Persediaan › Rekalkulasi Stok & HPP**: menu Rekalkulasi HPP kini sekaligus memeriksa **stok**. Tombol **Cek** menambah tab **Saldo Stok** (saldo stok tersimpan yang berbeda dari jumlah mutasi kartu stok) dan **Pemeriksaan Stok** (saldo minus per hari, opname yang saldo akhirnya ≠ hitung fisik, dokumen bertanggal sama yang dibuat sesudah opname) untuk rentang tanggal satu hari atau satu bulan. **Rekalkulasi** menyamakan saldo stok dengan kartu stok lalu menghitung ulang HPP. Mutasi, dokumen & jurnal tidak dihapus. Selama berjalan tampil **daftar langkah** (periksa saldo stok, saldo minus, opname, muat dokumen, hitung ulang HPP, perbaiki dokumen & jurnal, simpan, susun hasil), masing-masing dengan batang kemajuan dan hitungannya; daftar tetap tampil sesudahnya sebagai rekam apa yang dikerjakan. **Cek** bisa dihentikan dengan tombol **Batal** (berhenti di langkah / butir berikutnya, tidak ada yang disimpan); Rekalkulasi yang sedang menyimpan tidak bisa dibatalkan.

- **Master Item › Koreksi satuan dasar**: satuan dasar item yang sudah punya transaksi kini bisa dikoreksi langsung lewat tombol **Koreksi…** di samping satuan dasar (perlu hak baru **Koreksi Satuan Dasar Item**, bawaan hanya Admin). Dua keadaan: **hanya namanya yang salah** (isi 1) — nama satuan diganti di semua transaksi, angka tetap; atau **angkanya juga salah** (mis. 1 box = 12 pcs) — stok, mutasi, baris penjualan / pembelian / retur / opname, resep, pecah stok dan promo ikut dikonversi (qty dibagi isi, harga per satuan dikali isi), sedangkan jumlah rupiah, HPP total dan jurnal tidak berubah. Ada pratinjau tabel yang akan berubah dulu, alasan wajib, dan tercatat di log aktivitas sebagai **Koreksi Satuan**. Angka yang tidak habis dibagi dibulatkan 4 desimal setelah Anda menyetujui pratinjau.

### Perbaikan
- **Nomor dokumen pertama bulan itu**: dua orang yang menyimpan dokumen pertama di bulan baru (atau cabang baru) pada saat yang sama tidak lagi membuat salah satunya gagal dengan pesan "bentrok dengan user lain"; yang kedua menunggu sebentar lalu tetap tersimpan dengan nomor berikutnya.
- **Ubah dokumen (penjualan, pembelian, retur, rakitan, pecah stok, item masuk/keluar, transfer, titipan)**: hanya item yang benar-benar berubah (qty, satuan, harga pokok atau tanggal) yang dibalik dan diposting ulang. Item yang tidak berubah tidak lagi meninggalkan pasangan mutasi "(ubah)" di kartu stok, dan saldo serta HPP rata-ratanya tidak disentuh.

## 1.0.18 (25 Oktober 2026)

### Baru
- **Stok Opname — edit langsung di grid**: opname yang sudah tersimpan kini diedit **per baris**. Begitu Anda pindah baris, baris yang diubah / ditambah langsung terkirim ke server (kolom **Status** menandai **Baru**, **Diubah**, atau **Gagal**), dan hapus baris langsung berlaku. Tombol **Simpan** hanya menyimpan header (tanggal, catatan, No. Referensi). Opname baru tetap diisi lalu disimpan sekaligus.
- **Dua orang mengedit opname yang sama**: bila baris atau header sudah diubah user lain, muncul pemberitahuan dan tawaran **Muat ulang**. Seluruh opname dimuat ulang; isian Anda di baris lain yang belum terkirim tetap dipertahankan.
- **Persediaan › Kartu Stok kini ringkas**: dokumen yang pernah diubah, dibatalkan, atau dihapus tampil **satu baris** (nilai bersihnya, dengan keterangan "diubah 3×"), dokumen yang akhirnya nol tidak tampil, dan baris **penyesuaian nilai** (tanpa perubahan stok) disembunyikan. Saldo tidak berubah. Centang **Semua mutasi** untuk melihat semuanya apa adanya, seperti log.

### Perbaikan
- **Stok Opname**: **stok sistem** baris yang sudah tersimpan tidak lagi bergeser tiap opname disimpan ulang. Sebelumnya dokumen lain bertanggal sama yang dibuat sesudah opname (mis. retur pembelian) ikut menggeser stok sistem dan selisihnya. Stok sistem baru dihitung ulang untuk baris baru, item yang diganti, atau bila tanggal opname diganti.
- **Stok Opname**: mengubah satu baris hanya membalik dan memposting ulang mutasi item itu; item lain tidak disentuh, jadi kartu stok tidak lagi penuh pasangan "(ubah)".
- Mengganti tanggal opname: mutasi pembalik kini bertanggal sama dengan mutasi aslinya, jadi stok di tanggal lama kembali bersih.

### Perlu diperhatikan
- Pesan "sudah diubah user lain" kini dikirim server dengan kode tersendiri (409) untuk semua dokumen; tampilannya di dokumen lain tidak berubah.

## 1.0.17 (25 Oktober 2026)

### Baru
- **Tampilan › Warna Aplikasi**: **50 tema warna baru** (total 66), dikelompokkan dalam lima rumpun — **Biru & Teal** (Deep Sapphire, Cyber Cyan, Nordic Ice, Aqua Matrix, Digital Horizon, Abyss Glow, Cobalt Cloud, Polaris Light, Hydro Stream, Steel Navy), **Hijau & Zaitun** (Sage Minimal, Forest Ranger, Matcha Latte, Bio Tech, Olive Garden, Aloe Vera, Jungle Canopy, Fern Eco, Neon Moss, Pistachio Clean), **Hitam, Putih & Abu-abu** (Obsidian Dark, Alabaster White, Concrete Jungle, Matte Charcoal, Titanium Silver, Zebra High-Contrast, Ghost Slate, Smoky Quartz, Pebble Beach, Inkwell), **Pastel & Gradasi Senja** (Bubblegum Pop, Sunset Glow, Apricot Breeze, Lilac Dream, Lemon Meringue, Cotton Candy, Melon Sorbet, Orchid Aura, Vanilla Cream, Dreamy Teal) dan **Hangat & Kontras Tinggi** (Crimson Bold, Amber Gold, Volcanic Orange, Bordeaux Wine, Burnt Clay, Solar Flare, Fiesta Red, Rust & Steel, Mustard Retro, Spicy Chili). Tiap tema tetap bergradasi lima warna.
- **Bar judul terang**: tema yang memang berlatar pucat — mis. Nordic Ice, Alabaster White, Ghost Slate, Sage Minimal, Lemon Meringue, Lilac Dream — kini memakai bar judul terang dengan **teks dan ikon gelap** (nama perusahaan, versi, akun, tombol jendela), bukan nada gelap bertulisan putih. Layar pembuka tetap gelap.
- Dialog **Warna Aplikasi** punya kotak **Cari tema** (nama, rumpun, atau kesan warna seperti "pastel", "hitam", "terang"; beberapa kata sekaligus) dan lebih tinggi supaya lebih banyak kartu terlihat.
- **Pembaruan aplikasi saat login kini jelas terlihat**: begitu ada versi baru, muncul **jendela Pembaruan** berhuruf besar — persen dan bilah progres, MB yang sudah diunduh, **nama file yang sedang diperbarui** ("file 2 dari 4"), daftar semua file yang diperbarui dengan tandanya, dan kotak **Yang baru di versi …** berisi ringkasan perubahannya. Selesai mengunduh muncul **"PilarErp berhasil di-upgrade dari versi A ke versi B. Silakan login kembali."** dengan tombol **OK**; sesudah OK aplikasi dibuka ulang dan jendela Pembaruan baru menghilang setelah layar login baru tampil, jadi tidak ada layar kosong yang membuat orang membuka aplikasi lagi atau mencoba login berkali-kali. Layar login yang baru terbuka menampilkan kotak hijau "berhasil di-upgrade dari versi … ke versi …, silakan login kembali". Jendela yang sama dipakai tombol **Perbarui sekarang** di jendela utama; bila pembaruan gagal, alasannya tampil di jendela itu (bukan kotak pesan kecil) dan login dilanjutkan dengan versi sekarang.
- **Pengaturan Perusahaan › Penjualan › Faktur yang sudah dibayar**: atur apakah **Faktur Penjualan** yang sudah dilunasi lewat Penerimaan Piutang boleh diubah / ditambah itemnya — **Tidak boleh** (hapus dulu pelunasannya), **Boleh, selama total tidak lebih rendah dari sebelumnya** (menambah item atau menaikkan qty / harga boleh, menurunkan total ditolak), atau **Boleh, selama total tidak di bawah yang sudah dibayar** (bawaan, seperti 1.0.16). Tambahan nilai otomatis jadi piutang lagi. Form **Faktur Penjualan** kini benar-benar terbuka untuk diubah sesuai pilihan itu — sebelumnya form tetap terkunci walau servernya sudah mengizinkan — dengan konsumen terkunci dan tulisan di judul "sudah dilunasi … total tidak boleh di bawah …". Konsumen tidak bisa diganti, tanggal faktur tidak boleh sesudah tanggal pelunasan, dan faktur yang sudah diretur tetap terkunci.
- **Pengaturan Perusahaan › Pembelian › Faktur yang sudah dibayar**: pilihan yang sama untuk **Faktur Pembelian** yang sudah dilunasi lewat Pembayaran Hutang, diatur terpisah dari penjualan (bawaan tetap **total tidak di bawah yang sudah dibayar**). Form **Faktur Pembelian** kini terbuka untuk diubah sesuai pilihan itu (sebelumnya masih terkunci), dengan supplier terkunci dan judul "sudah dibayar … total tidak boleh di bawah …". Tambahan nilai jadi hutang lagi; mengubah harga / qty tetap menghitung ulang HPP dan menampilkan pratinjau penyesuaian HPP sebelum simpan.
- **Pengaturan Perusahaan › Keamanan** (tab baru): **Panjang minimum password** (8 — bawaan, 10, 12 atau 16 karakter; sebelumnya 6) — panjang lebih penting daripada rumit: user biasa cukup panjang (huruf, angka, simbol, spasi semuanya boleh — kalimat panjang yang mudah diingat lebih aman), dengan pilihan centang **User biasa: password wajib berisi huruf, angka & simbol** bila perusahaan ingin lebih ketat (bawaan tidak). **Akun Admin selalu wajib panjang dan rumit, tanpa pilihan**: minimal 12 karakter (atau lebih bila panjang minimum perusahaan lebih besar) dan memuat huruf, angka, dan simbol — juga untuk password admin perusahaan baru, reset password oleh admin platform, dan saat user dinaikkan ke jabatan Admin (password baru diisi sekaligus). Password lama yang tidak memenuhi syarat baru tetap berlaku sampai diganti. **Ganti password tiap** (tidak pernah — bawaan, 3, 6, 9 atau 12 bulan): password yang sudah lebih tua dari pilihan itu tidak langsung masuk, melainkan meminta **password baru** di layar login (harus berbeda dari yang lama) lalu masuk otomatis; **Admin tidak wajib ganti berkala**; dihitung sejak password diganti terakhir (atau user dibuat), dan penolakan login karena ini tercatat di Log Login. **Kunci layar setelah tidak aktif** (tidak dikunci — bawaan, 15, 30, 60, 120 atau 240 menit): tanpa gerak mouse / ketikan selama itu, aplikasi di PC ini menutup layarnya sampai password dimasukkan lagi (diperiksa server, salah-benarnya tercatat di Log Login); isian yang belum disimpan tetap aman di baliknya dan tombol **Keluar (Sign Out)** tersedia. Dialog ganti password, user baru & reset password menampilkan panjang minimum yang berlaku.
- **Pengaturan Perusahaan › Akuntansi › Tanggal transaksi › Paling jauh ke depan** (tidak terbatas — bawaan, 7 hari, 14 hari, 1 bulan, 3 bulan, 6 bulan, 1 tahun): batas tanggal transaksi (penjualan, pembelian, persediaan, kas, jurnal, retur) untuk user selain Admin. **Admin tidak dibatasi** (cocok selama masa migrasi). Melewati batas: perlu persetujuan atasan Admin. Batas mundur tetap diatur per jabatan (batas backdate & izin backdate).
- **Pengaturan Perusahaan › Penjualan › Retur penjualan › Paling lambat setelah faktur** (tanpa batas — bawaan, 1, 2, 3, 6 atau 12 bulan): retur dengan faktur asal hanya diterima sampai sekian bulan setelah tanggal faktur. Retur tanpa faktur asal dan retur dari perusahaan grup tidak terkena batas; mengubah retur lama tanpa mengganti tanggalnya juga tidak.
- **Pengaturan Perusahaan › Penjualan › Potongan › Batas potongan tanpa persetujuan %** (0 = tidak dibatasi — bawaan, jadi belum ada yang berubah): potongan manual per baris (dibanding harga daftar; harga di bawah harga master juga dihitung) atau diskon faktur di atas batas itu perlu hak baru **Potongan di Atas Batas** (Sistem › Jabatan) atau persetujuan atasan. Admin selalu boleh; potongan dari promo dan baris yang tidak berubah tidak dicek. "Rumah"-nya sudah siap untuk saat operasional penuh.
- **Bersihkan Data › tab Rincian**: sesudah **Periksa** (dengan Jenis data tertentu) ada tab **Rincian** yang menunjukkan ISI tiap baris ringkasan, supaya jelas apa yang akan dihapus: daftar dokumen (nomor, tanggal, cabang, status Berlaku / Batal / Terhapus, konsumen / supplier, nilai), **mutasi stok** per item dengan qty dan jenisnya (mis. "Penjualan", "Penjualan (batal)", "Penjualan (hapus)"), jurnal (nomor JU, uraian, total), perubahan saldo stok per item ("stok 95 → 100") dan nomor dokumen yang disesuaikan ("nomor terakhir 0004 → mulai 0001 lagi"). Klik dua kali baris di Ringkasan membuka rincian jenis itu; klik dua kali baris dokumen / mutasi membuka dokumennya; daftar bisa dicari, disaring dan disalin / diexport lewat klik kanan. Tiap jenis dibatasi 1.000 baris (mutasi stok 3.000), sisanya disebut. Dialog **Hapus permanen** satu dokumen juga menampilkan mutasi stok & saldo stok yang akan hilang.

## 1.0.16 (25 Oktober 2026)

### Baru
- **Harga jual vs harga daftar** — pengingat sedini mungkin bila harga jual beda dari harga jual master item / satuan (salah ketik, harga master keliru, atau pemetaan Quinos salah). **Faktur Penjualan**: kolom baru **Harga Daftar**; harga yang beda berwarna oranye, dan saat Simpan muncul konfirmasi "Harga beda dari harga daftar … Tetap simpan?". **Kasir**: konfirmasi yang sama sebelum bayar. **Integrasi Quinos**: tab Item Quinos & Detail Penjualan punya kolom **Harga Quinos**, **Harga Pilar** & **Selisih %** (oranye bila beda), dan **2. Cek** memberi peringatan per kode + nama, mis. "MF-34 (ROTI BARU): Quinos 9.000, item Roti 25.000 (−64%) — cek pemetaan". **Import Data penjualan**: peringatan per baris saat Periksa. Semuanya hanya peringatan (tetap bisa disimpan); atur di **Pengaturan Perusahaan › Penjualan › Beda dari harga daftar** (aktif / tidak, **Toleransi %**, bawaan 0 = semua beda diingatkan). Promo, item berharga jual 0 & jual ke perusahaan grup tidak dibandingkan.
- Setiap baris penjualan kini **menyimpan harga daftar saat itu**, jadi perbandingan tetap benar walau harga master diubah kemudian.
- **Laporan Penjualan › Harga Jual vs Harga Daftar**: **Per Item** (harga daftar, harga rata-rata / terendah / tertinggi per satuan dasar, baris beda harga, nilai selisih) dan **Detail Transaksi** (no faktur, sumber Faktur / Kasir / Quinos / Import, user, harga daftar, harga faktur, selisih %, nilai selisih) — bawaan hanya yang beda harga. Baris lama sebelum versi ini dibanding harga master sekarang (ditandai perkiraan). Hak lihat diberikan ke jabatan yang boleh melihat Laba Jual.
- **Analisa › Laba & Harga › Kepatuhan Harga Jual**: % baris yang sesuai harga daftar per bulan, per sumber (Kasir / Faktur / Import / Quinos) dan per user, serta **Item Selisih Terbesar** — tanda awal pemetaan Quinos atau harga master yang salah.
- **Sistem › Bersihkan Data per jenis data**: selain membersihkan semua transaksi, kini bisa memilih **Jenis data** tertentu saja — mis. hanya **Penjualan** (juga hasil import Quinos / Kasir), Pembelian, Penerimaan piutang, Pembayaran hutang, Retur, Kas & bank, Jurnal umum, Koreksi / transfer / titipan stok, Rakitan, Pecah stok, Stok opname atau Saldo awal piutang / hutang — boleh dengan **rentang tanggal**. Dokumen yang dipilih (termasuk yang sudah batal / terhapus) dihapus **permanen** bersama mutasi stok, jurnal dan log aktivitasnya, jadi **tidak ada baris "batal" yang tersisa di Kartu Stok**; pelunasan & retur yang menunjuknya ikut dihapus. Stok sekarang dikurangi mutasi yang dihapus (sama dengan buku stok), nomor dokumen kembali ke nomor terbesar yang masih ada (semua penjualan dibersihkan = nomor mulai 0001 lagi), dan dokumen jenis lain, periode serta master tidak berubah. Periksa dulu menampilkan jumlah per jenis dan penghalangnya: bulan yang periodenya sudah ditutup, pelunasan yang juga melunasi dokumen lain di luar pilihan, transfer yang penerimaannya di cabang lain, atau penjualan yang sudah diterima perusahaan grup. Bila pembelian / stok masuk ikut dihapus, jalankan **Persediaan › Rekalkulasi HPP** agar harga pokok rata-rata dihitung ulang. Khusus admin perusahaan.
- **Hapus permanen satu dokumen**: di menu **Lainnya ▾** daftar Penjualan, Pembelian, Rakitan, Pecah Stok, Stok Opname, Jurnal Umum (jurnal buatan sendiri), Kas & Bank, Retur, Penerimaan Piutang / Pembayaran Hutang, Saldo Awal dan Item Masuk / Keluar / Transfer / Titipan ada butir merah **Hapus permanen…** (khusus admin perusahaan). Muncul dulu ringkasan apa yang akan hilang (dokumen, mutasi stok, jurnal, log) lalu minta **alasan**; dokumennya — apa pun statusnya, juga yang sudah batal atau terhapus — lenyap total bersama mutasi stok (tidak ada baris batal / hapus di Kartu Stok), jurnal dan log aktivitasnya, stok sekarang disesuaikan, dan nomor dokumen dipakai lagi bila ia yang terakhir. Dokumen yang masih punya pelunasan atau retur tidak bisa dihapus permanen sebelum pelunasan / returnya dihapus; periode yang sudah ditutup juga menolak. Satu baris **Hapus Permanen** (alasan + jumlah data yang hilang) tetap tercatat di Log Aktivitas. Hapus biasa (soft delete, bisa dipulihkan) tetap ada seperti sebelumnya.
- **Integrasi Quinos › Hapus permanen (bukan batal)**: centang baru di samping Abaikan selisih total (aktif bawaan untuk admin perusahaan). **Update / Batalkan** kini menghapus **permanen** faktur lama beserta bukti pelunasan, mutasi stok & jurnalnya — tidak ada baris "batal" di Kartu Stok dan nomor faktur lama dipakai lagi — dan satu baris **Hapus Permanen** tercatat di Log Aktivitas (alasan + daftar nomor faktur). Hilangkan centang untuk membatalkan seperti sebelumnya (jejak batal tetap ada). Pelunasan / retur lain yang dibuat manual atas faktur itu, periode yang dikunci / ditutup, dan penjualan yang sudah diterima perusahaan grup tetap menolak.
- **Pilihan daftar panjang berupa tabel**: pemilih konsumen / supplier / penitip (Penerimaan Piutang, Pembayaran Hutang, Saldo Awal, Retur, Stok Titipan), faktur asal retur, akun (Kas & Bank, Akun lawan stok, Akun induk, akun & rak di Master Item), item hasil Rakitan, item Kartu Stok, dan pemilih kode di filter laporan kini membuka tabel (Kode · Nama …) dan tetap bisa diketik: ketik sebagian kode / nama (bagian tengah kata juga cocok), daftar tersaring, Enter memilih. Isian nama konsumen / supplier baru di faktur dan kategori item tetap ketik bebas; Kolom item / akun di baris faktur, stok, opname, pecah, rakitan, retur, promo, master item, jurnal, dan kas juga memakai tabel ini; mengetik langsung di sel dan Enter tetap seperti biasa.
- **Integrasi Quinos › Item Quinos**: kolom **Item Pilar** kini berupa pilihan bertabel dengan **kotak cari** (Kode · Nama · Kategori · Satuan), jadi item yang namanya mirip mudah dibedakan. Klik sel → daftar langsung terbuka, ketik sebagian kata dari kode / nama / kategori mana pun (hasil yang cocok disorot), lalu pilih barisnya.
- **Integrasi Quinos › Item Quinos**: pemetaan kini selalu terikat **kode + nama Quinos**, karena kode Quinos bisa dipakai ulang untuk barang lain (mis. MF-34 untuk roti & kue acak). Nama baru untuk kode yang sudah dipetakan tidak lagi ikut item lama diam-diam: barisnya berstatus **Saran — konfirmasi** (oranye, diisi item kode itu sebelumnya) dan **4. Import** terkunci sampai saran disetujui (**Konfirmasi Saran**, lalu **3. Simpan Pemetaan**) atau diganti item lain. **Kode umum** — kode yang dipakai bergantian untuk barang acak — tidak diberi saran sama sekali: diisi pola di isian **Kode umum** (mis. `MF*`), atau otomatis bila kode punya 3 nama atau lebih / nama-namanya ke item berbeda. Pemetaan lama otomatis diikat ke nama yang tercatat saat dipetakan. Hari yang sudah diimport dengan pemetaan keliru: perbaiki pemetaannya lalu **Update** hari / struk itu.
- **Integrasi Quinos › Item Quinos**: kolom **Catatan** kini berdiri sendiri tepat sebelum band **Pemetaan ke Pilar**, dan band pemetaan (Status + Item Pilar) **dibekukan di kanan**, jadi tetap terlihat saat tabel digeser ke samping untuk melihat kolom Quinos yang lebar.
- **Tampilan › Warna Aplikasi**: pilih tema warna aplikasi dari 16 pilihan — **Pilar Hijau** (bawaan) dan 15 lainnya dalam rumpun Biru (Ocean Breeze, Midnight Blue, Classic Navy), Hijau (Mint Cream, Emerald Corporate, Cyber Green), Hitam & Abu-abu (Deep Onyx, Urban Slate, Nordic Frost), Pastel (Lavender Mist, Peach Sorbet, Blush & Sky) dan Hangat & Kontras (Tangerine Navy, Cyberpunk Neon, Coral Warmth). Setiap tema bergradasi **lima warna** di bar judul dan layar pembuka, dan mengganti warna utama (tombol aksi, judul kelompok, garis judul form) baik di tampilan terang maupun gelap. Klik kartu untuk langsung mencoba di seluruh aplikasi, **Simpan** untuk menyimpannya bagi user Anda — ikut ke komputer mana pun Anda login; **Bawaan** mengembalikan hijau. Terang / gelap tetap diatur di **Tampilan › Tema**.

### Perbaikan
- **Jurnal saat dokumen diubah**: mengubah transaksi (faktur penjualan / pembelian, retur, pelunasan, kas & bank, mutasi stok, opname, rakitan, konversi, saldo awal) kini **memposting ulang jurnal yang sama** — nomor JU tetap (kecuali tanggal pindah bulan), isinya diganti angka baru. Sebelumnya setiap ubah membuat jurnal Batal + jurnal baru bernomor lain, sehingga daftar jurnal penuh jurnal batal. Isi jurnal lama → baru tercatat di **Riwayat** jurnal dan ikut tampil di Riwayat dokumennya (bagian "Jurnal"). Membatalkan dokumen tetap membuat jurnalnya **Batal**; laporan (Buku Besar, Neraca, Laba Rugi) tidak berubah.
- **Faktur Penjualan** & **Pembelian** yang sudah dibayar lewat **Penerimaan Piutang** / **Pembayaran Hutang** kini bisa diubah tanpa menghapus pembayarannya dulu, selama total baru tidak kurang dari yang sudah dibayar — mis. menambah item yang ketinggalan (sisanya jadi piutang / hutang lagi). Yang tetap ditolak: menurunkan total di bawah yang sudah dibayar, mengganti konsumen / supplier, atau memundurkan tanggal faktur ke sesudah tanggal pembayaran — untuk itu hapus / ubah dulu pembayarannya. Faktur yang sudah diretur, dan membatalkan faktur yang sudah dibayar, tetap seperti sebelumnya.
- **Salin sel / baris / semua** (klik kanan di tabel mana pun) kini menghasilkan angka mentah dan tanggal yang benar saat ditempel ke **Excel**: angka tanpa pemisah ribuan (mis. `1500,5`, bukan `1.500,5` yang di laptop berformat English terbaca 1,5), dengan pemisah desimal sesuai pengaturan Windows laptop itu; tanggal berbentuk `2026-10-03` (bukan `03/10/2026` yang bisa tertukar jadi 10 Maret). Tampilan di layar tidak berubah.

## 1.0.15 (24 Oktober 2026)

### Baru
- **Integrasi Quinos › Item Quinos**: kode Quinos yang dipakai untuk beberapa barang (mis. MF-34 untuk 20 jenis roti & kue) kini tampil satu baris **per deskripsi** dan dipetakan per deskripsi ke itemnya masing-masing, jadi stok, HPP & laporan per item benar. Kode biasa tetap satu baris per kode.

### Perbaikan
- **Integrasi Quinos (cara Harian)**: struk yang tarif layanan / PB1-nya lain dari tarif kebanyakan struk hari itu (mis. satu struk dine in layanan 2%, struk lain 3%) kini jadi **faktur harian tambahan** sendiri (nomor asal "…-T2", catatan "struk tarif lain: layanan 2%") dengan tarifnya sendiri, bukan disamakan lewat Pembulatan. Layanan & PB1 setiap faktur sama persis dengan Quinos. Hari yang sudah diimport satu faktur tampil **Beda** ("1 faktur → 2 faktur") dengan saran **Update** — Update membatalkan faktur lama dan membuat faktur-faktur baru.
- **Integrasi Quinos**: selisih **PB1** Rp 100 atau lebih antara hitungan Pilar dan Quinos kini jadi error saat **2. Cek** (pajak tidak boleh disamakan lewat Pembulatan); selisih layanan / diskon tetap boleh lewat Pembulatan seperti sebelumnya.
- **Integrasi Quinos**: faktur hasil import kini mengisi **No. Referensi** dengan nomor struk Quinos — cara **Per struk** mis. "KNO #85", cara **Harian** rentang nomor struk per store hari itu, mis. "KNO #1–134 · KNO-TR #1–72" (struk void / kosong tidak ikut). Catatan faktur tetap berisi struk, jenis penjualan, meja & kasir. Faktur yang sudah diimport sebelumnya mendapat No. Referensi bila di-**Update**.

## 1.0.14 (24 Oktober 2026)

### Baru
- **Integrasi Quinos › tab Struk**: tiap struk bisa dibuka (tanda **+** di kiri baris) untuk melihat **item struk**-nya — kode & deskripsi Quinos, qty, harga, jumlah, diskon item beserta nama diskonnya (mis. "Disc 100% Item"), bagian diskon struk, kena PB1 / layanan dan bagian layanan & PB1 menurut Pilar, item Pilar hasil pemetaan, dan catatan baris yang akan masuk ke faktur. Struk void / kosong hanya menampilkan angka Quinos.
- **Tab form** di bawah menu kini tampil semua dalam beberapa baris (tidak lagi satu baris dengan panah geser ◂ ▸), paling banyak **3 baris**. Bila tab lebih banyak lagi, tab yang sedang dibuka selalu terlihat; baris lainnya bisa digulir dengan **roda mouse** di atas tab, atau dipilih lewat tombol daftar tab di kanan / **Ctrl+Tab**. Tinggi baris ikut ukuran font.

## 1.0.13 (24 Oktober 2026)

### Baru
- **Daftar transaksi** (Faktur Penjualan, Kasir, Pembelian, Retur, Penerimaan Piutang, Pembayaran Hutang, Kas & Bank, dan daftar transaksi lain yang berhalaman): baris **summary** di bawah tabel berisi **jumlah baris** dan jumlah tiap kolom angka (Subtotal, DPP, PPN, Biaya Layanan, PB1, Total, Dibayar, Diretur, Sisa, HPP, …) dari baris yang tampil di halaman itu, dan langsung berubah saat kolom tabel disaring. Untuk menjumlah lebih banyak dokumen sekaligus, besarkan **Per halaman** (sampai 100).
- **Tabel baris** di form transaksi (Faktur Penjualan, keranjang Kasir, Pembelian, Retur, Pelunasan, Kas & Bank, Mutasi Stok, Opname, Rakitan, Konversi, Jurnal, Saldo Awal): baris summary yang sama — jumlah baris, Qty, Jumlah, Pot. Rp, DPP, Layanan, PB1, Debit / Kredit, selisih opname, … (harga, persen & stok tidak dijumlah). Baris yang ditandai hapus (dicoret) tidak dihitung; summary ikut berubah saat isian baris diubah.
- **Mode DEV**: bila aplikasi berjalan sebagai build pengembangan atau tersambung ke server di PC sendiri (localhost), bar judul menampilkan **[DEV]** di samping versi (juga di judul taskbar), bar judul & layar pembuka bergradasi **maroon**, dan warna utama hijau di semua form (tombol utama, judul, garis) menjadi maroon — supaya tidak tertukar dengan aplikasi produksi (tetap hijau).
- **Bar judul** aplikasi produksi kini bergradasi hijau (tua di kiri → terang di kanan), senada dengan layar pembuka.
- **Catatan per baris** di **Faktur Penjualan** dan **Pembelian**: kolom **Catatan** di tabel item untuk mencatat hal penting per item (maks. 500 huruf), mis. kemasan rusak atau kondisi aneh saat import. Ikut tersimpan, tampil lagi saat dokumen dibuka, dan ikut tersalin ke pembelian dari penjualan grup. **Import Data** penjualan & pembelian punya kolom baru **Catatan Baris** (opsional).
- **Integrasi Quinos**: baris faktur hasil import otomatis diberi catatan bila kondisinya tidak biasa di Quinos — item gratis / diskon item (dengan nama diskonnya, mis. "Disc 100% Item"), item bebas pajak (mis. PAPER BAG), item tanpa service charge di struk yang kena service charge, item tanpa kode, kode yang hanya ada di struk, dan pada cara **Harian** struk yang tarif layanan / PB1-nya lain dari tarif faktur (mis. "struk layanan 2% (faktur 3%) #85"), lengkap dengan nomor struknya. Faktur yang sudah diimport baru mendapat catatan bila di-**Update**.
- **Integrasi Quinos**: kolom **No Transaksi** di tab **Item Quinos** dan **Detail Penjualan** — nomor struk Quinos yang berisi item itu (mis. "#3, #17, #25"; beberapa hari: "11/09 #3, #17 · 12/09 #5"), supaya struknya mudah dicari di Quinos saat memetakan kode yang aneh. Struk void / kosong tidak ikut.
- **No. Referensi** di header semua transaksi (Faktur Penjualan, Pembelian, Retur, Penerimaan Piutang, Pembayaran Hutang, Kas Masuk / Keluar / Transfer, Mutasi Stok & Titipan, Opname, Rakitan, Konversi, Jurnal Umum, Saldo Awal Piutang / Hutang): isian untuk nomor dokumen dari **lawan transaksi** — mis. no. faktur / nota supplier, PO konsumen, no. bukti transfer, surat jalan (maks. 100 huruf). Letaknya di kiri **Catatan**, satu baris di bawah header. Ikut tampil sebagai kolom di daftar transaksi, bisa dicari lewat kotak cari daftar, ada di rekap laporan (Pembelian, Penjualan, Retur, Mutasi Stok, Opname, Kas & Bank), tercatat di Riwayat, dan bisa dicetak (isian **NoReferensi** di template; template bawaan mencetak "No. Referensi: …" bila terisi). Terima dari / retur ke perusahaan grup otomatis terisi nomor dokumen perusahaan asal.
- **Import Data**: kolom baru **No Referensi** (opsional) di semua import transaksi. Import **Pembelian** tanpa No Referensi memakai **No Faktur** (nomor faktur supplier) sebagai No. Referensi.
- **Faktur Penjualan** dan **Pembelian**: daftar **Pelunasan** dan **Retur** di panel kanan kini masing-masing punya accordion sendiri (tidak lagi satu baris "Pelunasan / retur" di dalam **Pembayaran**). Bagian yang tidak punya dokumen disembunyikan; saat dilipat, judulnya menampilkan jumlah dokumen dan totalnya.

### Perbaikan
- **Integrasi Quinos (cara Harian)**: tarif biaya layanan & PB1 faktur harian kini tarif yang dipakai mayoritas struk hari itu (mis. layanan 3%, PB1 10%), bukan rata-rata hari itu. Sebelumnya satu struk dengan tarif lain (mis. struk dine in layanan 2%) membuat tarif faktur jadi 2,9848% sehingga layanan setiap item sedikit lebih kecil dari Quinos dan tampil berselisih di **Detail Penjualan**. Selisih total dari struk bertarif lain disamakan lewat Pembulatan (total faktur tetap sama dengan Quinos) dan disebut di tab **Pesan**. Hari yang sudah diimport dengan tarif rata-rata disarankan **Update**. Cara **Per struk** tetap memakai tarif masing-masing struk.

## 1.0.12 (24 Oktober 2026)

### Baru
- **Bar judul aplikasi** disusun ulang: kiri **logo cabang** | nama perusahaan | pilihan cabang, tengah logo **Pilar ERP** | **versi aplikasi** (mis. v1.0.12), kanan tetap (akun, minimize, maximize). Versi juga tampil di judul taskbar.
- **Master Cabang › Ubah › Logo**: pasang logo per cabang (PNG / JPG, otomatis dikecilkan ke 256 px) dengan **Pilih Gambar…** atau hapus dengan **Hapus Logo**; terkirim setelah **Simpan**. Logo tampil di kiri bar judul saat cabang itu dipilih; cabang tanpa logo memakai lencana inisial cabang. Cabang baru: simpan dulu, lalu **Ubah** untuk memasang logo.

### Perbaikan
- **Faktur Penjualan** (outlet restoran): kolom **Layanan** dan **PB1** per baris kini dalam rupiah utuh bila pembulatan "Biaya layanan & PB1" di **Pengaturan Perusahaan › Penjualan** ke rupiah (bawaan: terdekat). Sebelumnya bagian per baris tampil dengan sen (mis. 11.342,3) walaupun totalnya sudah dibulatkan, terutama di faktur hasil import Quinos yang tarif layanannya tidak bulat (mis. 2,9848%). Jumlah per baris tetap sama dengan Biaya layanan & PB1 faktur; total faktur tidak berubah.

## 1.0.11 (24 Oktober 2026)

### Perbaikan
- **Integrasi Quinos**: struk batal di Quinos (baris item qty 0 lalu −1, total 0) tidak lagi membuat **2. Cek** gagal dengan "Qty harus lebih dari 0" / "Potongan Rp tidak boleh minus". Baris qty 0 / minus hanya jejak void dan dilewati, sama seperti subtotal struk & laporan Item Sales Quinos; struk yang tinggal tanpa item jadi **Struk kosong**.
- **Integrasi Quinos**: diskon khusus item ("Disc 100% Item", ditulis Quinos tepat setelah item-nya) kini jadi potongan baris item itu, bukan dibagi rata ke semua baris struk; diskon struk ("disc 10% All item", "Disc Owner") tetap jadi Diskon Faktur. Faktur harian memisahkan baris per store (kode yang sama bisa berpajak di KNO tetapi tidak di KNO-TR). Item yang hari itu bebas pajak di Quinos (mis. PAPER BAG sejak 24/09) tidak diberi PB1. Hasilnya diskon, layanan & PB1 per item sama dengan Quinos (diuji pada data 11–30/09, KNO & KNO-TR: semua item cocok), jadi peringatan "PB1 Quinos …, Pilar …" di tab Pesan hilang.
- **Integrasi Quinos**: item yang di Quinos tidak punya kode (mis. "LIDAH KUCING EDAM 292") tidak lagi hilang dari faktur. Deskripsinya dipakai sebagai kode di tab **Item Quinos**, jadi bisa dipetakan; sebelumnya nilainya hanya tertutup Pembulatan (atau Cek ditolak karena selisih).

### Perlu diperhatikan
- Faktur Quinos per struk yang diimport 1.0.9–1.0.10 dari struk berdiskon item akan disarankan **Update** (diskon kini di baris item); totalnya tidak berubah.

## 1.0.10 (24 Oktober 2026)

### Perbaikan
- **Integrasi Quinos**: modifier di struk Quinos (mis. HOT / ICE tanpa harga) tidak lagi diminta dipetakan. Sebelumnya **2. Cek** gagal dengan "kode Quinos 'MF-36' (HOT) belum dipetakan", padahal kodenya tidak ada di tab **Item Quinos**. Modifier tanpa harga kini dilewati (sama seperti laporan Item Sales Quinos); kode berharga yang hanya ada di struk tampil di tab **Item Quinos** dengan kategori "(hanya di struk)" supaya bisa dipetakan.

## 1.0.9 (24 Oktober 2026)

### Baru
- **Integrasi Quinos › Cara import per profil**: di **Kelola Profil** pilih **Harian** (satu faktur per hari, cara sebelumnya) atau **Per struk** (satu faktur per struk Quinos: jam, jenis penjualan, meja, kasir & nama pelanggan ikut; dibayar langsung di fakturnya, pembayaran kedua dan seterusnya jadi bukti Penerimaan Piutang). Profil yang sudah ada tetap Harian.
- **Integrasi Quinos**: angka diambil dari laporan struk Quinos (Transaction Detail) — biaya layanan hanya untuk menu yang di Quinos kena service charge (dine in), PB1 hanya untuk struk yang ada pajaknya, diskon struk ikut. Faktur harian kini dipisah per baris dine in / take away / tanpa PB1, jadi layanan & PB1 per item cocok dengan Quinos.
- **Integrasi Quinos › saran tindakan** per struk (Per struk) atau per hari (Harian) setelah **1. Buka**: Baru → Import, Sama → Lewati, Beda → Update, void / kosong di Quinos → Batalkan, faktur yang struknya tidak ada di Quinos → Lewati, periode dikunci → Lewati. Kolom **Catatan** menjelaskan alasannya (mis. "Beda: total 88.900 → 98.515"). **Tindakan** bisa diganti per baris; tombol **Ikuti saran** dan **Update yang sama** (memaksa import ulang yang sudah sama); **Tampilkan** menyaring menurut saran / tindakan.
- **Integrasi Quinos › tab Struk**: daftar struk Quinos (jam, jenis, meja, kasir, layanan, PB1, pembayaran, void) beserta faktur Pilar-nya.
- **Integrasi Quinos › 1. Buka / 2. Cek / 4. Import** menampilkan batang kemajuan dengan tombol **Batal**; yang dibatalkan tidak menyimpan apa pun.
- **Integrasi Quinos**: ganti cara import untuk hari yang sudah diimport = satu paket per hari, faktur harian diganti faktur per struk (atau sebaliknya) sekaligus.
- **Import Data › Faktur Penjualan**: kolom **Jam** (jj:mm atau jj:mm:dd) dan **Layanan Kena PB1**.

### Perlu diperhatikan
- Hari yang diimport versi sebelumnya dikenali, tidak diimport dua kali. Bila pembagian barisnya beda (dine in & take away dulu satu baris), sarannya **Update** dengan catatan "pembagian baris … beda (import versi lama)"; pilih **Lewati** bila tidak ingin diganti.
- Update / Batalkan membatalkan faktur & pelunasan lama (hak **Batal** Penjualan & **Hapus** Piutang, alasan wajib). Setelah mengganti faktur tanggal yang sudah lewat, jalankan **Persediaan › Rekalkulasi HPP** bila sesudahnya ada pembelian.
- Centang **Force update** diganti kolom **Tindakan** (pakai **Update yang sama** untuk import ulang hari / struk yang sudah sama).

## 1.0.8 (23 Oktober 2026)

### Baru
- **Kena Layanan per baris**: centang **Kena Layanan** di tiap baris **Faktur Penjualan** (outlet restoran) — bawaannya ikut Kena PB1 item, hapus centang mis. untuk roti yang dibawa pulang: baris itu tetap kena PB1 tetapi tidak kena biaya layanan. **Integrasi Quinos** kini menandai baris sesuai Quinos (layanan hanya untuk item yang di Quinos kena service charge, PB1 hanya untuk item yang kena pajak), jadi tarif layanan & PB1 faktur sama dengan Quinos (mis. layanan 1% minuman, PB1 10%) dan angka per baris cocok. **Import Data › Faktur Penjualan** punya kolom **Kena Layanan** (kosong = ikut Kena PB1). Faktur lama tidak berubah (semua baris yang kena PB1 tetap kena layanan).
- **Integrasi Quinos › 2. Cek / 4. Import**: baris yang biaya layanan / PB1-nya akan beda Rp 100 atau lebih dari Quinos dicatat sebagai peringatan di tab **Pesan**, mis. "22/10/2026 KNO KNO0247 (DOPPIO): PB1 Quinos 6.000, Pilar 8.223 (selisih -2.223)" — biasanya item yang di Quinos pajaknya bukan 10%. Peringatan tidak menghalangi Import; total hari tetap sama dengan Quinos.
- **Integrasi Quinos › Detail Penjualan**: centang **Hanya baris berselisih** menyaring tabel ke baris yang biaya layanan / PB1 Pilar-nya beda Rp 1 atau lebih dari Quinos.

### Perlu diperhatikan
- Faktur Quinos yang diimport sebelum versi ini masih memakai tarif rata-rata (layanan ikut terbagi ke item yang di Quinos tidak kena layanan). Totalnya tetap sama dengan Quinos; supaya per baris juga cocok, import ulang hari itu dengan **Force update**. Tarif PB1 tetap satu per faktur, jadi item yang pajaknya di Quinos bukan 10% (mis. ada transaksi tanpa pajak) masih bisa sedikit berselisih per baris.

## 1.0.7 (23 Oktober 2026)

### Baru
- **Integrasi Quinos › Force update (import ulang)**: hari yang sudah diimport bisa diimport ulang, mis. bila PB1 / biaya layanan fakturnya salah. Centang **Force update (import ulang)**, **2. Cek**, lalu **4. Import** dan isi alasannya: pelunasan hasil import Quinos hari itu dihapus dan fakturnya dibatalkan, lalu diimport lagi dengan nomor faktur baru — semuanya sekaligus, satu error saja = tidak ada yang berubah. Hari di periode yang sudah dikunci / ditutup dilewati (dokumennya tetap). Butuh hak **Batal** Penjualan dan **Hapus** Piutang; alasan tercatat di Log Aktivitas.
- **Integrasi Quinos › Detail Penjualan**: biaya layanan & PB1 tiap baris menurut Quinos dan menurut Pilar, beserta selisihnya (merah bila Rp 1 atau lebih). Hari yang sudah diimport diambil dari fakturnya, hari lain perkiraan hasil import. Judul tab menyebut jumlah baris yang berselisih.
- **Integrasi Quinos**: tabel Per Hari, Item Quinos, Pembayaran, dan Detail Penjualan memakai judul kelompok kolom (**Quinos** · **Pilar** · **Selisih** · **Pemetaan ke Pilar**), jadi angka Quinos dan Pilar mudah dibandingkan.
- **Faktur Penjualan** (outlet restoran): kolom **Layanan** dan **PB1** di tiap baris — bagian biaya layanan & PB1 faktur untuk baris itu; jumlahnya sama dengan Biaya Layanan & PB1 di panel kanan.
- Klik kanan › **Salin semua** di tabel yang kolomnya berkelompok: judul kolom diberi nama kelompoknya (mis. "Pilar · Layanan").

### Perbaikan
- **Integrasi Quinos**: hari tanpa biaya layanan (atau tanpa PB1) di Quinos dulu diimport dengan tarif bawaan cabang (mis. layanan 5%), lalu selisihnya ditutup Pembulatan. Sekarang tarif 0 dipakai apa adanya. Faktur yang terlanjur salah bisa diperbaiki dengan **Force update**.

### Perlu diperhatikan
- Tarif biaya layanan & PB1 faktur hasil import Quinos adalah rata-rata satu hari, jadi item yang di Quinos tidak kena layanan tetap tampil berselisih per baris walaupun total hari itu sama dengan Quinos.
- Setelah **Force update** untuk tanggal yang sudah lewat, jalankan **Persediaan › Rekalkulasi HPP** (klik Cek dulu) mulai tanggal itu bila sesudahnya ada pembelian.

## 1.0.6 (23 Oktober 2026)

### Baru
- **Laporan › Analisa**: kini menu **Analisa** sendiri di pita Laporan, terpisah dari **Menu Laporan** (tab sendiri, tidak tercampur dengan laporan biasa), dan bertambah menjadi 41 analisa dengan **grafik di atas tabel**, dikelompokkan per bagian (Ringkasan & Cabang, Penjualan, Laba & Harga, Persediaan, Pembelian, Keuangan, Operasional & Kontrol), di antaranya: **Ringkasan Eksekutif** (kartu penjualan, transaksi, laba kotor, margin, nilai stok, stok mati, item habis / kritis, piutang, hutang, kas & bank, dengan garis 12 bulan), **Tren Penjualan** (per hari / minggu / bulan, semua cabang atau per cabang), **Komposisi Penjualan** (per kategori, jenis item, cabang, kategori per bulan), **Item Terlaris & Pareto** (peringkat penjualan / qty / laba kotor dengan kelas ABC, dan item yang tidak terjual), **Margin per Item & Kategori** (termasuk margin bila dijual dengan HPP sekarang), **Nilai & Komposisi Stok** (per kategori / cabang / jenis dan tren 12 bulan), **Perputaran & Hari Persediaan**, **Stok Mati & Lambat** (termasuk umur stok), dan **Perkiraan Habis & Saran Order** (status Habis / Kritis / Segera, jumlah order dalam satuan beli, per supplier).
- Analisa lainnya: **Jam & Hari Ramai** (peta panas jam × hari, per jam, per hari dalam minggu, per tanggal; jumlah transaksi atau nilai penjualan; bisa disaring per kanal Kasir / Faktur / Import), **Retur & Pembatalan** (per bulan, per item, per alasan batal / hapus, per user), **Selisih Opname (Susut)** (kurang & lebih per bulan, kategori, cabang, item), **Tren Pembelian & Supplier** (per bulan, supplier utama dengan hari bayar rata-rata, per kategori, pembelian dibanding HPP terjual), **Harga Beli per Item** (kenaikan harga, perbandingan harga antar supplier, tren harga satu item), **Analisa Piutang** (tren umur piutang & DSO, konsumen telat, kebiasaan bayar), **Hutang & Jatuh Tempo** (yang harus dibayar 7 / 14 / 30 hari ke depan dibanding saldo kas & bank, per supplier, tren umur hutang & DPO), **Arus Kas Bulanan** (uang masuk & keluar per sumber, per akun kas / bank, per akun lawan seperti gaji atau listrik), **Laba Rugi Tren & Rasio** (Laba Rugi per bulan dengan % pendapatan & pembanding tahun lalu, rasio margin / beban / laba bersih, per cabang), dan **Kartu Skor Cabang** (semua ukuran tiap cabang dalam satu tabel: terbaik hijau, terburuk merah; klik dua kali sel membuka analisanya untuk cabang itu).
- **Ringkasan Eksekutif** kini lengkap: kartu **Hutang Jatuh Tempo 30 Hari**, 3 grafik kecil (penjualan per hari dibanding pembanding, 10 item teratas, komposisi kategori), dan 5 tabel peringatan (item akan habis, stok mati terbesar, konsumen telat, hutang lewat jatuh tempo, susut opname terbesar). Klik dua kali grafik atau baris peringatan membuka analisanya; **Cetak / Preview** mencetak seluruh ringkasan.
- **Kasir** dan **Faktur Penjualan** mencatat **jam transaksi** dan **kanal penjualan** (Kasir / Faktur; hasil Import Excel, Integrasi Quinos, dan migrasi Ketoko ditandai sendiri) untuk analisa jam ramai dan filter kanal.
- Analisa untuk perencanaan: **Rata-rata Transaksi & Keranjang** (nilai rata-rata & median per struk, jumlah item per struk, sebaran nilai struk), **Cara Bayar** (porsi tunai / QRIS / EDC / transfer per akun kas / bank, biaya transfer / MDR), **Efektivitas Promo & Diskon** (potongan & item gratis per promo, penjualan item saat promo dibanding sebelum promo, potongan manual per user), **Konsumen Utama, Baru & Hilang** (Pareto konsumen, konsumen baru, konsumen rutin yang lama tidak beli), **Tren Laba Kotor** (margin tiap kategori per bulan, harga jual vs HPP satu item), **Harga Jual vs HPP Sekarang** (harga jual yang marginnya sudah di bawah ambang dan harga jual minimumnya, memperhitungkan PB1 / PPN yang termasuk harga), **Menu Engineering** (menu Star / Plowhorse / Puzzle / Dog dari laris tidaknya dan untung per porsi, dengan saran tindakan), **ABC Persediaan Silang** (stok besar yang jarang dipakai = uang mengendap), **Pemakaian Bahan Aktual vs Resep** (bahan terbuang / selisih opname dibanding yang seharusnya terpakai menurut resep), **Kinerja Titipan** (% laku barang penitip & barang kita di toko titipan, hutang / piutang titipan), **Keseimbangan Stok Antar Cabang** (saran transfer dari cabang yang kelebihan ke cabang yang hampir habis), **Kualitas & Ketergantungan Supplier** (retur %, hari bayar, kategori yang bergantung pada satu supplier), **Biaya per Akun Tren** (beban per bulan, kenaikan mendadak, % pendapatan, per transaksi), **Pajak per Bulan** (PB1, PPN keluaran & masukan, kurang / lebih bayar), **Produktivitas Kasir / User**, dan **Kontrol** (batal, hapus, ubah, jual di bawah harga master, input mundur, dan pola jamnya per user).
- **Target vs Realisasi**: isi target penjualan bulanan tiap cabang (dan target margin % bila perlu) di **Sistem › Pengaturan Perusahaan › tab Target** — pilih tahun, isi per bulan, atau pakai **Isi dari tahun lalu…** (penjualan bulan yang sama tahun lalu + kenaikan %, dibulatkan ke ribuan) dan **Samakan 12 bulan**, lalu **Simpan**. Banyak cabang sekaligus bisa lewat **Sistem › Import Data › Target Penjualan**. Analisa **Target vs Realisasi** menampilkan per cabang, per bulan, atau cabang × bulan: target, realisasi (penjualan neto seperti Laba Jual), % tercapai, kekurangan, **proyeksi akhir bulan** dari rata-rata penjualan per hari sejauh ini, hari tersisa, dan penjualan yang perlu dikejar per hari; merah bila proyeksi di bawah target, hijau bila sudah tercapai. Klik dua kali baris membuka Laba Jual per tanggal.
- Analisa tambahan: **Kalender Penjualan** (peta panas bulan × tanggal 1–31, libur nasional diberi bingkai merah, dan penjualan per tanggal dibanding rata-rata hari yang sama), **Sering Dibeli Bersama** (pasangan item dalam satu struk, % keyakinan & lift untuk ide paket, atau teman belanja satu item), **Perkiraan Penjualan & Pemakaian** (4 minggu ke depan per item / kategori dan penjualan per hari, memperhitungkan pola hari dalam minggu; stok yang tidak cukup ditandai merah), **Simulasi Harga** (ubah Harga Baru / HPP Baru di tabel atau **Ubah Harga Semua…** sekian persen: penjualan, laba & margin baru langsung terhitung, tanpa mengubah master item), dan **Titik Impas & Rasio Neraca** (BEP per cabang / bulan dan margin keamanan; rasio lancar, rasio cepat, kas / kewajiban lancar, utang / modal per akhir bulan).
- **Perkiraan Habis & Saran Order**: pilihan **Dasar Pemakaian** "Perkiraan pola hari" (akhir pekan yang ramai ikut terhitung), dan tombol **Buat Pembelian**: pilih satu baris lalu klik, faktur pembelian baru terbuka berisi semua saran order supplier itu (satuan beli, qty, harga beli terakhir) untuk diperiksa lalu disimpan.
- **Cetak / Preview** analisa selalu memuat grafiknya, juga saat grafik sedang disembunyikan, dan **Export Excel** analisa kini menyertakan gambar grafik di atas tabel.
- **Ringkasan Eksekutif mingguan via email**: isi alamat penerima (paling banyak 5), hari & jam di **Sistem › Pengaturan Perusahaan › Perusahaan › Ringkasan mingguan via email**; tiap minggu PDF Ringkasan Eksekutif minggu lalu (semua cabang, dibanding minggu sebelumnya) dikirim otomatis. Tombol **Kirim Sekarang** dan **Lihat PDF…** untuk mencoba. Server email diatur oleh pengelola Pilar ERP.

### Perbaikan
- **Buku Kas & Bank** lebih cepat untuk data yang banyak (saldo awal hanya dihitung dari akun kas / bank).

### Perlu diperhatikan
- **Pajak per Bulan** dihitung dari faktur yang terposting, bukan pengganti SPT: cocokkan dengan e-Faktur / laporan pajak daerah sebelum lapor.
- Jam transaksi diambil dari jam PC kasir saat transaksi bertanggal hari ini disimpan: pastikan tanggal & jam PC kasir benar. Faktur sebelum 1.0.6 memakai jam simpan bila tanggalnya sama; faktur input mundur dan hasil import tidak punya jam dan dihitung di baris **Tanpa jam**.
- **Laporan Analisa** punya hak akses sendiri per analisa di kelompok **Analisa** (Sistem › Jabatan & Hak Akses), terpisah dari kelompok Laporan, dengan tombol **Semua analisa** / **Kosongkan analisa**. Jabatan yang sudah boleh melihat **Laba Jual** otomatis mendapat semua analisa; jabatan bawaan **Gudang** mendapat analisa persediaan (Nilai Stok, Perputaran, Stok Mati, Saran Order, Selisih Opname, ABC Silang, Pemakaian Bahan, Titipan, Stok Antar Cabang) dan pembelian (Tren Pembelian, Harga Beli, Kualitas Supplier); jabatan lain tanpa analisa. Analisa **Kontrol** (aksi tiap user) seperti Laporan Sistem: hanya Admin dan jabatan yang boleh melihat **Log Aktivitas**. Analisa yang ditambahkan kemudian diberikan sekali dengan aturan yang sama; hak yang sudah dicabut admin tetap tercabut. Admin sebaiknya meninjau hak ini, terutama untuk jabatan Kasir yang dulu diberi hak Laba Jual. Analisa **Margin**, **Nilai & Komposisi Stok**, **Perputaran**, **Harga Beli per Item**, **Tren Laba Kotor**, **Harga Jual vs HPP Sekarang**, **Menu Engineering**, dan **ABC Persediaan Silang** juga butuh hak **Lihat harga pokok (HPP) di laporan**.

## 1.0.5 (23 Oktober 2026)

### Baru
- Tampilan jendela utama lebih segar: bar judul Windows diganti bar aplikasi sendiri berwarna hijau — **Pilar ERP | Nama Perusahaan | Cabang** di kiri, lingkaran inisial pengguna di kanan beserta ikon minimize dan maximize. Klik lingkaran / nama pengguna untuk melihat nama lengkap, jabatan, dan tombol **Ganti Password**, **Sign Out** (kembali ke layar login), dan **Keluar** (tutup aplikasi). Seret bar untuk memindahkan jendela, klik dua kali untuk maximize / restore; tepi jendela tetap bisa ditarik untuk mengubah ukuran, dan saat maximize taskbar tetap terlihat.
- Layar pembuka setelah login didesain ulang: latar gradasi hijau dengan tulisan **PILAR ERP** yang tegas, nama perusahaan, langkah yang sedang dikerjakan, versi aplikasi, dan hak cipta tahun berjalan.
- **Bantuan › Riwayat Versi** lebih ringkas: tiap versi menjadi satu bagian lipat, hanya versi terkini (yang terpasang) yang terbuka, dan daftar dibagi per 5 versi dengan nomor halaman di bawahnya, jadi tidak ikut panjang saat versi makin banyak.
- Isi **Riwayat Versi** kini ditampilkan sebagai Markdown sungguhan: judul, **tebal**, *miring*, `kode`, daftar bertingkat / bernomor, kutipan, tabel, dan tautan (dibuka di browser) tampil rapi mengikuti tema dan ukuran font aplikasi, bukan teks mentah.
- **Persediaan › Kartu Stok** kini menu sendiri (tidak lagi memakai laporan di Menu Laporan). Pilih item, periode, dan **Cabang** lalu **Tampilkan** (**F5**): mutasi stok item itu beserta saldo awal dan saldo berjalan (satuan dasar), jumlah masuk dan keluar di kaki tabel, serta **Export Excel** dan **Cetak / Preview**. **Cabang** = satu cabang (bawaan: cabang yang sedang dipilih) atau **Semua cabang** yang boleh Anda akses: saldo awal dan saldo berjalan digabung (transfer antar cabang saling meniadakan) dan kolom **Cabang** tampil. Pilihan Cabang tidak tampil bila Anda hanya punya satu cabang. Klik dua kali baris untuk membuka dokumen asalnya (faktur penjualan, pembelian, item masuk / keluar, transfer, titipan, rakitan, pecah stok, stok opname, retur) di form transaksinya, mode Lihat, di cabang dokumen itu; baris penyesuaian nilai membuka dokumen yang memicunya.
- **Laporan › Analisa**: grup baru **Laporan Analisa** di Menu Laporan (tombol **Analisa** di pita Laporan) berisi 9 analisa dengan **grafik di atas tabel**: **Ringkasan Eksekutif** (kartu penjualan, transaksi, laba kotor, margin, nilai stok, stok mati, item habis / kritis, piutang, hutang, kas & bank, dengan garis 12 bulan), **Tren Penjualan** (per hari / minggu / bulan, semua cabang atau per cabang), **Komposisi Penjualan** (per kategori, jenis item, cabang, kategori per bulan), **Item Terlaris & Pareto** (peringkat penjualan / qty / laba kotor dengan kelas ABC, dan item yang tidak terjual), **Margin per Item & Kategori** (termasuk margin bila dijual dengan HPP sekarang), **Nilai & Komposisi Stok** (per kategori / cabang / jenis dan tren 12 bulan), **Perputaran & Hari Persediaan**, **Stok Mati & Lambat** (termasuk umur stok), dan **Perkiraan Habis & Saran Order** (status Habis / Kritis / Segera, jumlah order dalam satuan beli, per supplier).
- Analisa bisa **dibandingkan** dengan periode sebelumnya, periode sama tahun lalu, atau periode pilihan sendiri: kolom **Pembanding**, **Selisih**, **Selisih %** dan garis putus-putus di grafik. Angkanya sama dengan laporan yang sudah ada (Laba Jual, Mutasi Stok, Umur Piutang / Hutang, Buku Kas & Bank).
- Di Laporan Analisa, **klik dua kali** baris tabel, titik grafik, atau kartu Ringkasan membuka laporan rincinya (mis. Laba Jual per tanggal atau per item, Mutasi Stok) dengan periode, cabang, dan item / kategori baris itu. Klik titik grafik memilih baris yang sama di tabel. Panel kanan **Cara membaca** menjelaskan rumus tiap analisa; tombol **Sembunyikan Grafik** dan **Sembunyikan Panduan** melebarkan tabel. **Cetak / Preview** ikut mencetak grafiknya.

### Perbaikan
- Form **Retur Penjualan** dan **Retur Pembelian** dirapikan: baris barang dan **Potong piutang / hutang** kini dua tab (**Item Retur** dan **Potong piutang konsumen / hutang ke supplier**), jadi grid barang memakai seluruh ruang form dan tidak terjepit lagi. Jumlah potongan tetap terlihat di panel **Total Retur** di kanan.

### Perlu diperhatikan
- **Laporan Analisa** punya hak akses sendiri per analisa (Sistem › Jabatan & Hak Akses, grup Laporan, awalan **Analisa ›**). Jabatan yang sudah boleh melihat **Laba Jual** otomatis mendapat semua analisa; jabatan bawaan **Gudang** mendapat analisa persediaan (Nilai Stok, Perputaran, Stok Mati, Saran Order); jabatan lain tanpa analisa. Admin sebaiknya meninjau hak ini, terutama untuk jabatan Kasir yang dulu diberi hak Laba Jual. Analisa **Margin**, **Nilai & Komposisi Stok**, dan **Perputaran** juga butuh hak **Lihat harga pokok (HPP) di laporan**.
- Hak akses Kartu Stok ditata ulang: hak laporan **Kartu Stok** di grup Laporan diganti hak menu **Kartu Stok** (Lihat) di grup **Persediaan** (Sistem › Jabatan & Hak Akses). Jabatan yang tadinya boleh melihat laporan itu otomatis mendapat hak menu barunya; jabatan yang haknya sudah dicabut tetap tanpa hak. Jabatan bawaan **Gudang** dan **Akunting** mendapat hak ini untuk perusahaan baru.
- Membuka dokumen asal dari Kartu Stok tetap butuh hak **Lihat** di menu dokumen itu (mis. faktur pembelian butuh hak Pembelian); tanpa hak, muncul pesan menu mana yang dibutuhkan. **Harga Pokok** dan **Nilai** hanya tampil bagi jabatan dengan hak Harga Pokok.
- Laporan **Kartu Stok** di Menu Laporan dihapus (isinya pindah ke menu di atas).

## 1.0.4 (23 Oktober 2026)

### Baru
- **Persediaan › Kartu Stok**: tombol baru di pita Persediaan yang langsung membuka laporan **Kartu Stok** (perlu hak laporan Kartu Stok). Klik dua kali baris mutasi untuk melihat dokumen asalnya (faktur penjualan, pembelian, item masuk / keluar, transfer, titipan, rakitan, pecah stok, opname, retur, saldo awal stok) di formnya, baca saja; baris penyesuaian nilai membuka dokumen yang memicunya. Dokumen hanya terbuka bila punya hak Lihat di menu dokumen itu (mis. hak laporan Kartu Stok saja tidak cukup untuk membuka faktur pembelian), dan dibuka di cabang dokumennya walau laporan menampilkan semua cabang.
- **Bantuan › Shortcut**: daftar pintasan keyboard dan klik cepat dalam bagian lipat (accordion), dikelompokkan per bidang kerja: pindah dan tutup tab (**Ctrl+Tab**, **Ctrl+W**, bolak-balik ke tab sebelumnya), ukuran huruf (**Ctrl+=**, **Ctrl+-**, **Ctrl+0**), **Kasir** (**F9** bayar, scan barcode + **Enter**, **Delete** hapus baris), form dokumen (**F9** simpan, **Esc** tutup, **Delete** hapus baris, **Enter** pindah kolom), daftar dan tabel (klik ganda, klik kanan), laporan (**F5**), template cetak, dan dialog.
- **Laporan › Detail Transaksi**: pilihan laporan baru di laporan yang berisi dokumen dengan barisnya: **Laporan Pembelian**, **Retur Pembelian**, **Laporan Penjualan**, **Retur Penjualan**, **Item Masuk**, **Item Keluar**, **Item Transfer**, **Stok Opname**, **Kas Masuk & Keluar**, dan **Laba Jual**. Isinya sama dengan **Detail per Faktur** (atau Detail per Dokumen / Retur) tetapi satu tabel rata tanpa kelompok per dokumen, dengan kolom **No Faktur**, **Tanggal**, **Kode**, **Nama Item**, dan seterusnya. Barisnya sudah berurutan menurut no dokumen, tanggal, kode item, lalu nama item, jadi hasil **Export Excel** bisa langsung dipakai tanpa diolah lagi. Retur di Laporan Pembelian, Laporan Penjualan, dan Laba Jual ikut sebagai baris minus, seperti di Detail per Faktur. Di Kas Masuk & Keluar, tiap baris juga memuat jenis dokumen dan akun kas / bank-nya.
- **Laporan**: filter semua laporan dirapikan menjadi bagian lipat (accordion) bertajuk sesuai isinya, mis. **Periode & Cabang**, **Dokumen**, **Pembuat & Pajak**, **Item**. Bagian utama terbuka; bagian pendukung (mis. **Item**, **Pembuat**, **Jenis & Status**) mulai dilipat dan, saat dilipat, judulnya merangkum filter yang sedang aktif, jadi area grid lebih luas dan filter tetap terlihat.

## 1.0.3 (22 Oktober 2026)

### Baru
- **Tampilan panduan seragam**: panduan bergaya Master Item (judul lipat berwarna tema, langkah bernomor, kotak contoh dan catatan) kini juga ada di dialog **Cabang**, **Akun** (COA), **Jenis PPN**, **Supplier**, **Konsumen**, dan tiap tab **Pengaturan Perusahaan**. Di dalam panduan, tiap bagian (mis. **Alur stok**, **Cara input**) dan tiap butir penjelasan bisa dilipat / dibuka sendiri, jadi panduan tetap ringkas.
- **Sistem › Pengaturan Perusahaan**: tampilan dirapikan, isian dikelompokkan dalam kotak seperti Master Item dengan label di kiri yang lurus di semua kotak.
- **Sistem › Jabatan & Hak Akses › Import Data**: hak menu baru untuk memakai **Sistem › Data › Import Data**. **Lihat** = membuka menu, mengunduh template, dan **Periksa** file (tidak ada yang disimpan); **Buat** = **Import** (menyimpan; tombolnya mati bila hanya punya hak Lihat). Tiap jenis import tetap butuh hak Buat di menu tujuannya (data master: Buat atau Ubah). Import **Item** yang membuat satuan, rak, atau stok awal baru juga butuh hak Buat di **Satuan**, **Rak**, atau **Stok Opname**, sama seperti input manual. Tanpa hak ini menu Import Data dan tombol **Import** di daftar Item tidak tampil. Jabatan bawaan Gudang dan Akunting mendapatkannya.
- **Persediaan › Rekalkulasi HPP**: hitung ulang harga pokok rata-rata **urut tanggal** sejak tanggal yang dipilih, untuk semua cabang dan item. Dipakai bila pembelian atau item masuk diinput belakangan (tanggal mundur) atau sempat diinput dengan harga sementara supaya kasir bisa menjual, sehingga HPP dan laba di faktur penjualan terlanjur salah. Tombol **Cek** menampilkan dulu dampaknya tanpa mengubah apa pun (ringkasan per cabang & bulan, HPP item sebelum/sesudah, daftar dokumen yang berubah, dan pemeriksaan: stok minus atau HPP 0 saat barang keluar, harga beli yang janggal). **Rekalkulasi** (perlu alasan) lalu memperbaiki HPP di penjualan, item keluar, transfer, titipan, rakitan, pecah stok, opname, retur, kartu stok, jurnalnya, penyesuaian nilai persediaan, dan saldo HPP item; qty tidak berubah. Di tanggal yang sama, pembelian/item masuk dihitung lebih dulu daripada penjualan. Ditolak bila ada periode yang sudah ditutup atau terkunci sejak tanggal itu. Hak menu baru **Rekalkulasi HPP** (Lihat = Cek, Buat = jalankan); jabatan Akunting mendapatkannya otomatis. Tercatat di Log Aktivitas, dan riwayat tiap dokumen menunjukkan HPP lama → baru.
- **Master Item › tab Konversi**: aturan **pecah stok** kini boleh lebih dari satu per item, mis. 1 dus → 12 pak **dan** 1 dus → 144 pcs. Satu aturan ditandai **Utama**. Di **Persediaan › Pecah Stok** kolom **Menjadi** bisa dipilih per baris dari aturan item itu (baris baru langsung memakai aturan Utama). Keterangan di atas tabel menjelaskan bedanya dengan satuan konversi. Di **Import Data**, kolom Pecah Ke / Isi Pecah (sheet Item) mengisi aturan Utama dan aturan lain tetap; sheet Pecah Stok punya kolom baru **Kode Item Hasil** (kosong = aturan Utama). Pengaturan pecah stok yang sudah ada otomatis menjadi aturan Utama.
- **Master Item**: isian dikelompokkan dalam kotak (Identitas, Jenis & kategori, Satuan & stok, Harga jual & barcode, Satuan konversi, Objek pajak, Pemakaian, Akun jurnal). **Kategori** dan **Satuan dasar** bisa ditambah langsung dengan tombol **+** di sampingnya. Satuan baru juga masuk master Satuan, jadi perlu hak Buat di menu **Satuan**. Tabel satuan konversi punya tombol **+ Satuan baru**.
- **Laporan › Laporan Master › Resep Menu & Produksi**: laporan khusus item **Menu** (resep) dan **Produksi** (komponen). Tiga pilihan: **Rincian Resep per Item** (tiap bahan beserta takaran, satuan, stok, HPP bahan, dan biaya, dengan jumlah biaya per item), **Rekap per Item** (jumlah bahan, harga jual, estimasi HPP resep, laba, margin %, serta stok dan HPP stok untuk Produksi), dan **Pemakaian per Bahan** (item mana saja yang memakai suatu bahan). Bisa disaring menurut kode, kategori, jenis (Menu/Produksi), cabang, dijual, dan aktif; item yang belum punya resep ikut ditampilkan supaya mudah dilengkapi. Kolom HPP, laba, dan margin hanya terlihat jabatan dengan hak **Lihat harga pokok (HPP) di laporan**. Hak laporan ini perlu dicentang di Jabatan (Gudang bawaan sudah mendapatkannya untuk perusahaan baru).

### Perbaikan
- Menu klik kanan di grid (Salin kode / sel / baris / semua, Riwayat) kini mengikuti ukuran font yang dipilih; sebelumnya tetap kecil.

### Perlu diperhatikan
- **Import Data** kini butuh hak menunya sendiri. Jabatan yang sebelum pembaruan sudah bisa memakai salah satu jenis import otomatis diberi hak Import Data (Lihat + Buat) saat server diperbarui, jadi tidak ada yang berhenti bekerja. Admin sebaiknya meninjau dan mencabutnya dari jabatan yang tidak perlu (mis. Kasir yang boleh membuat penjualan ikut mendapatkannya) di **Sistem › Jabatan & Hak Akses**; hak yang sudah dicabut tidak diberikan lagi.

## 1.0.2 (21 Oktober 2026)

### Baru
- **Master Item**: panel kanan berisi panduan tiap jenis item — kapan stok terpotong, contoh, dan cara input — supaya **Menu** (tanpa stok, bahan resep terpotong saat dijual) dan **Produksi** (dibuat dulu lewat Rakitan, disimpan sebagai stok, lalu dijual) tidak tertukar. Tab **Resep** untuk Menu (oranye, takaran per porsi) dan tab **Komponen** untuk Produksi (biru, isi per satuan hasil) kini dibedakan tampilannya, dan pilihan Jenis menampilkan keterangan singkat.
- **Persediaan › Rakitan / Produksi**: jenis **Bongkar** untuk memecah lagi item Produksi yang tidak jadi dijual, mis. parcel sisa Natal: stok parcel berkurang, isinya kembali ke stok dengan nilai yang sama (tanpa laba/rugi). Tombol **Isi dari komponen** mengisi isi parcel × qty; jumlah yang dibongkar tidak boleh melebihi stok. Bukti cetaknya berjudul **Bukti Bongkar Rakitan**.
- **Penanda proses**: setelah login tampil layar pembuka dengan langkah yang sedang dikerjakan sampai jendela utama siap dipakai. Selama data dimuat, disimpan, dihapus, dibatalkan, atau laporan disiapkan, tab atau jendela yang sedang bekerja diredupkan dengan lingkaran berputar dan keterangannya (mis. "Memuat data…", "Menyimpan…", "Menyiapkan laporan…"), dan bar atas menampilkan penanda kecil. Membuka menu, form, laporan, pratinjau, dan cetakan yang berat menampilkan kursor tunggu dan lingkaran berputar.
- **Master Item › Harga & Satuan**: **satuan bawaan** beli, jual, dan stok untuk item yang boleh konversi satuan. Contoh kopi dengan satuan dasar gram dan satuan konversi kg: begitu kopi dipilih di Pembelian, Kasir, Faktur Penjualan, retur, dokumen stok, atau Stok Opname, barisnya langsung dalam kg dengan harga per kg (masih bisa diganti per baris). Tombol item di Kasir menampilkan harga satuan jual bawaannya, mis. "290.000 / kg". Rakitan, resep, dan pecah stok tetap memakai satuan dasar (gram). Bisa diisi juga lewat **Import Data** (kolom Satuan Beli, Satuan Jual, Satuan Stok di sheet Item).

### Perbaikan
- Tombol **Simpan** (juga F9 / Ctrl+S) tidak bisa terpicu dua kali selama dokumen sedang disimpan, jadi dokumen tidak tersimpan dobel.
- Pembaruan aplikasi saat **Masuk**: pemeriksaan file sebelum mengunduh tidak lagi membuat layar login berhenti bergerak.

### Perlu diperhatikan
- **Satuan dasar item terkunci** begitu item sudah punya transaksi (termasuk yang dibatalkan atau dihapus), atau dipakai di resep, pecah stok, atau promo item lain. Stok, HPP, dan takaran resep tercatat dalam satuan dasar dan tidak ikut dikonversi, jadi menggantinya akan membuat stok 5 kg terbaca 5 gram. Untuk satuan dasar lain, buat item baru lalu pindahkan stoknya lewat **Pecah Stok**. Berlaku juga di Import Data.
- **Import Data** transaksi: kolom Satuan yang kosong tetap berarti satuan dasar, walau item punya satuan bawaan lain. Saat Periksa muncul peringatan sekali per item supaya tidak salah baca (mis. 2 terbaca 2 gram, bukan 2 kg).

## 1.0.1 (21 Oktober 2026)

### Baru
- **Sistem › Data › Integrasi Quinos**: tarik penjualan harian dari Quinos Cloud (pilih tanggal, lalu **Buka**), petakan kode item dan jenis pembayaran Quinos ke master Pilar (tersimpan, cukup sekali), lalu **Cek** dan **Import** menjadi satu faktur penjualan per hari beserta pelunasan per jenis pembayaran. Login Quinos disimpan sebagai **profil** (email, password terenkripsi, store, cabang tujuan); satu perusahaan boleh punya banyak profil untuk beberapa email atau store, dikelola lewat tombol **Kelola Profil** (Baru · Ubah · Hapus); di layar cukup pilih profil dan tanggal. Pemetaan kode item per store (kode Quinos bisa beda per store, bahkan kode yang sama dipakai barang lain); kode dan nama yang sama dengan item Pilar langsung dipakai, cukup memetakan yang beda. Tombol Import baru aktif setelah Cek tanpa error. Total faktur disamakan dengan total Quinos; hari yang sudah diimport tidak bisa diimport dua kali.

## 1.0.0 (20 Oktober 2026)

### Baru
- Rilis pertama Pilar ERP untuk restoran, toko, dan oleh-oleh: banyak cabang dalam satu perusahaan.
- **Penjualan**: layar Kasir, Faktur Penjualan, pembayaran sebagian, piutang dan pelunasannya.
- **Pembelian**: faktur pembelian langsung menambah stok, hutang dan pelunasannya, koreksi harga beli.
- **Persediaan**: stock opname per rak, koreksi stok, transfer antar cabang, pecah stok, rakitan/resep, barang titipan.
- **Titipan › Setoran ke Penitip**: barang titipan cukup dicatat qty-nya saat masuk (harga titip boleh kosong, hanya perkiraan); hutang ke penitip baru tercatat saat setoran, sebesar barang yang sudah laku dengan harga yang disepakati saat itu. Daftar barang laku yang belum disetor terisi sendiri, dan selisih harga masuk ke HPP.
- **Pajak**: jenis PPN, PB1 dan biaya layanan untuk resto, pembulatan total.
- **Akuntansi**: jurnal otomatis dari setiap transaksi, jurnal umum, kunci periode dan tutup buku, tahun buku.
- **Kas & Bank**: kas masuk, kas keluar, dan transfer kas (setor tunai, pencairan EDC/QRIS beserta potongannya) tanpa perlu debit/kredit, cetak bukti kas, saldo awal akun.
- **Tutup buku**: kunci transaksi cabang dulu sementara pencatatan kas & jurnal tetap jalan; sebelum tutup ada pemeriksaan dan pratinjau laba rugi; laba tahun berjalan pindah otomatis ke laba ditahan di akhir tahun buku.
- **Laporan**: penjualan, pembelian, laba jual, mutasi stok, hutang/piutang, buku besar, neraca, laba rugi.
- **Cetak**: template nota dan faktur dengan atau tanpa harga untuk kertas A4, setengah A4, thermal, dan dot-matrix.
- **Sistem**: hak akses per jabatan dan cabang, import data dari Excel, log aktivitas, pulihkan data terhapus.
- Aplikasi memperbarui dirinya sendiri saat tombol **Masuk** ditekan; hanya file yang berubah yang diunduh.
- **Pengingat versi baru**: aplikasi yang dibiarkan terbuka tetap memeriksa versi baru (tiap 15 menit) dan menampilkan bar kuning dengan tombol **Perbarui sekarang** atau **Nanti**; **Bantuan → Periksa Pembaruan** untuk memeriksa langsung. Bila penyedia aplikasi mewajibkan versi tertentu, bar berubah merah dan data baru bisa disimpan setelah diperbarui (membuka data dan laporan tetap bisa).
- **Beranda → Ucapan & Berita**: ucapan atau info dari penyedia aplikasi tampil sebagai tab tersendiri setelah login (satu tab per ucapan) untuk semua user; tab ucapan baru muncul tanpa mengganggu layar yang sedang dipakai dan tertutup sendiri setelah masa tayangnya habis. Gambar ucapan hanya disimpan di PC selama masih tayang.
- Setelah **Masuk** ditekan, layar login menampilkan langkah yang sedang berjalan dengan progress bar: menghubungi server, memeriksa pembaruan, memeriksa user & password, dan memeriksa ucapan & berita. Bila gagal, langkahnya ditandai beserta alasannya.
- **Promo**: diskon periode / happy hour (tanggal, hari, jam, per cabang) dan beli X gratis Y; potongan dan item gratis terisi sendiri di Kasir dan Faktur Penjualan.
- **Persetujuan atasan**: bila hak user kurang (batal, hapus, ubah dokumen, tanggal mundur, ubah harga atau potongan di Kasir), atasan cukup login di layar yang sama; namanya tercatat di log aktivitas.
- **Kasir**: scan barcode atau ketik kode item lalu Enter; laci kas terbuka otomatis; struk bisa dicetak 1–3 rangkap dengan teks kaki sendiri dan nomor telepon / WhatsApp cabang.
- Peringatan atau penolakan **harga jual di bawah HPP**, dengan minimum laba yang bisa diatur.
- **Kode otomatis** untuk item, supplier, dan konsumen: kosongkan kode, nomor berikutnya diisi sendiri.
- **Saldo Awal Stok** sebagai menu sendiri (juga lewat import), **Item Keluar** untuk menu beresep, laporan **Stok Minimum** dan **Cek Konsistensi Stok**.
- Stock opname menghitung stok sistem pada tanggal opname, jadi opname yang diinput belakangan tetap benar.
- **Tutup sampai bulan ini**: beberapa bulan ditutup sekaligus.
- Akun kas bawaan per cabang, data perusahaan (alamat, telepon, email), masa simpan log, dan **Bantuan → Informasi Sistem**.
- Data yang sedang dibuka tidak lagi tertimpa diam-diam: bila user lain sudah mengubahnya lebih dulu, simpan ditolak dengan nama user dan jamnya.
- Menu disusun ulang: **Kas & Bank** jadi tab sendiri (Kas Keluar juga ada di Beranda), keempat **Saldo Awal** (akun, stok, piutang, hutang) dikumpulkan di tab Akuntansi, **Jenis PPN** pindah ke Sistem di samping Pengaturan Perusahaan; daftar hak akses jabatan dan Import Data dikelompokkan sama seperti menu.
- **Pengaturan → Fitur**: Titipan, Transfer Antar Cabang, Rakitan / Produksi, Pecah Stok dan Promo bisa dimatikan bila tidak dipakai; menunya hilang untuk semua user, data lama tetap ada di laporan.
- **Beranda → Mulai Pakai**: daftar 12 langkah menyiapkan perusahaan baru (pengaturan, cabang, akun, user, item, saldo awal, kunci periode) dengan tanda selesai otomatis; terbuka sendiri setelah login selama belum ada penjualan.
- Pintasan tab: **Ctrl+Tab** memunculkan pemilih tab dengan pratinjau (tahan Ctrl, tekan Tab untuk memilih, lepas Ctrl untuk membuka); **Ctrl+`** (tombol di atas Tab) bolak-balik ke tab sebelumnya; **Ctrl+W** menutup tab aktif (tetap ditanya bila belum disimpan). Tombol ▾ di ujung deretan tab menampilkan daftar semua tab.
- **Daftar transaksi per halaman** (penjualan, pembelian, persediaan, kas, pelunasan, saldo awal, jurnal, promo): 10 / 25 / 50 / 100 baris per halaman (bawaan 25; pilihan disimpan per user dan berlaku di semua menu, juga di PC lain) dengan nomor halaman per kelompok 10 (1–10, lalu … ke 11–20, dst.), tombol « ‹ › » dan isian nomor halaman, serta keterangan **baris aktif · jumlah baris · total data**, jadi daftar sebulan penuh tetap cepat dibuka. Kotak cari mencari di seluruh rentang tanggal (no. dokumen, nama konsumen / supplier, akun, catatan, pembuat), bukan hanya di halaman yang tampil.
- **Rincian pembayaran**: di daftar Faktur Penjualan, Pembelian, dan daftar penjualan di Kasir, nominal kolom **Dibayar** bisa diklik untuk melihat rinciannya (dibayar di faktur, tiap pelunasan, sisa, dan status bayar). Nomor pelunasan (Penerimaan Piutang / Pembayaran Hutang) di rincian itu dan di panel **Pembayaran** faktur bisa diklik untuk membuka dokumennya di tab baru; setelah pelunasan itu disimpan, daftar atau faktur langsung menampilkan angka terbaru.
- **Retur Penjualan** dan **Retur Pembelian** (menu Penjualan / Pembelian): pilih konsumen / supplier lalu faktur asalnya, atau klik **Cari No Transaksi** untuk membuka jendela pilih transaksi (menurut rentang tanggal, nomor transaksi, nama konsumen / supplier atau barang; hanya transaksi berstatus Posted yang tampil, yang sudah habis diretur berwarna abu-abu dan tidak bisa dipilih; transaksi di periode yang sudah ditutup tetap bisa diretur), kemudian isi qty yang dikembalikan. Harga, potongan, pajak dan pembulatan mengikuti faktur, dan retur bertahap tidak bisa melebihi qty faktur. Nilai retur memotong piutang / hutang faktur itu (bisa juga faktur lain atau saldo awal milik konsumen / supplier yang sama); sisanya dikembalikan tunai atau transfer. Barang kembali ke stok dengan HPP saat dijual, retur pembelian keluar dengan harga beli fakturnya; laporan penjualan, pembelian, laba, piutang / hutang dan kartu stok ikut menyesuaikan.
- Barang yang fakturnya tidak ada di Pilar ERP (mis. sebelum mulai memakai aplikasi) bisa diretur **tanpa faktur asal** dengan harga diisi sendiri; retur penjualan tanpa faktur butuh hak ubah harga atau persetujuan atasan.
- Dari daftar Faktur Penjualan / Pembelian: **Lainnya ▾ → Buat retur**. Faktur yang sudah diretur menampilkan nomor returnya (bisa diklik) di panel Pembayaran dan nilai di kolom **Diretur**; faktur itu tidak bisa diubah atau dibatalkan sebelum returnya dibatalkan.
- **Laporan › Retur Penjualan** dan **Retur Pembelian**: rekap per retur (faktur asal, potong piutang / hutang, uang yang dikembalikan, HPP barang yang kembali ke stok), detail per retur, rekap per pelanggan / supplier dan rekap per item, dengan filter tanggal, nomor, pelanggan / supplier, cabang, user dan item. Laporan Penjualan, Pembelian dan Laba Jual sudah dikurangi retur: per faktur retur tampil sebagai baris minus, sedangkan rekap per pelanggan / supplier, per item, per tanggal dan per cabang menampilkan kolom **Penjualan (atau Pembelian) · Retur · Neto** (per item juga qty jual, qty retur, qty neto) serta **Jml Faktur** dan **Jml Retur** terpisah.
- **Cetak nota retur**: tombol **Cetak** di daftar Retur Penjualan / Pembelian dan klik kanan nomor retur. Tersedia Nota Retur (dengan harga, ringkasan pajak, potong piutang / hutang per faktur dan uang yang dikembalikan) serta bukti barang retur / surat jalan retur (tanpa harga), masing-masing untuk A4, setengah A4, thermal 80 / 58 mm dan dot-matrix; bisa diubah di **Sistem › Template Cetak**. Hak cetaknya mengikuti cetak penjualan / pembelian.
- **Import Data › Retur Penjualan / Retur Pembelian**: satu baris = satu item yang diretur, No Retur sama = satu retur. Isi **Faktur Asal** (nomor faktur, atau nomor faktur lama hasil import) + kode item + qty — harga, potongan dan pajak mengikuti faktur dan qty dibatasi sisa yang bisa diretur — atau kosongkan Faktur Asal dan isi harga untuk retur tanpa faktur. Nilai retur otomatis memotong faktur asal (bisa diganti lewat **Potong Faktur** / **Jumlah Potong**), sisanya dikembalikan lewat **Akun Kas/Bank**. File yang sama tidak bisa diimport dua kali.
- **Retur antar perusahaan satu grup usaha**: perusahaan pembeli membuat Retur Pembelian dari pembelian yang diterima dari grup, lalu perusahaan penjual membuka **Retur Penjualan → Terima retur dari grup** — barang dan totalnya mengikuti retur pembeli persis sehingga piutang dan hutang kedua perusahaan tetap sama. Retur pembelian yang sudah diterima terkunci sampai retur penjualannya dibatalkan.
- **Klik kanan di semua grid** (daftar, laporan, baris dokumen, bagan akun): **Salin nomor** (atau kode) baris itu, **Salin sel**, **Salin baris** dan **Salin semua** baris yang tampil beserta judul kolomnya, dipisah tab sehingga langsung tertempel per kolom di Excel; pilihan **Riwayat…** tetap ada.
- **Klik kanan nomor di form dokumen** (saat melihat atau mengubah): menu **Salin nomor**, **Ubah**, **Simpan**, **Reset**, **Muat ulang**, **Riwayat**, **Cetak** dan **Tutup** (hanya yang berlaku saat itu; sama dengan tombol di baris judul). Nomor pelunasan / retur di panel **Pembayaran** faktur dan di popup **Rincian pembayaran** juga bisa diklik kanan: salin, buka, ubah, atau lihat riwayatnya. Dokumen asal di combo dan isi jendela **Detail** di Kasir bisa disalin lewat klik kanan.
