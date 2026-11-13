# Riwayat Versi Pilar ERP

Catatan perubahan tiap versi aplikasi desktop Pilar ERP. Installer: [Releases](https://github.com/NaviaAng/pilar-erp-installer/releases/latest) atau https://app.pilarsukses.com/unduh/.

## 1.0.87 (13 November 2026)

### Perbaikan
- **Situs web (harga paket)**: harga paket dinaikkan menjadi jutaan dan tertulis per bulan: Mulai Rp5.900.000, Tumbuh Rp9.900.000, Bercabang Rp11.900.000, dengan catatan S&K berlaku (versi Indonesia dan Inggris).

## 1.0.86 (13 November 2026)

### Perbaikan
- **Penjualan › Closing Harian**: kolom Cabang kini langsung tersaring ke cabang aktif tab itu saat dibuka. Filter bisa dihapus dari header kolom untuk melihat semua outlet.

## 1.0.85 (12 November 2026)

### Baru
- **Integrasi Quinos › cara Harian**: profil yang mencakup beberapa store (mis. KNO dan KNO-TR) kini menghasilkan **satu faktur harian per store (outlet)** memakai kolom store dari struk,
  bukan satu faktur gabungan. Profil satu store tidak berubah. Dengan begitu **Closing Harian › Penjualan › Penerimaan per akun** terpisah per outlet.
- **Closing Harian › Uang per Shift › Kas keluar / kas masuk**: kolom **No. Referensi** (nomor faktur / nota; ketik manual bila bukan pembayaran utang, otomatis dari faktur untuk Bayar faktur)
  dan kolom **Dokumen** (nomor Kas Keluar / Kas Masuk / Pembayaran Utang yang dibuat Posting Kas dari baris itu). No. Referensi ikut ke dokumen yang dibuat.

### Perbaikan
- **Uang per Shift**: keterangan "Utang usaha (dicatat saja)" pada jenis Bayar faktur diganti "Utang usaha (Pembayaran Utang)": sejak 1.0.82 baris itu benar-benar menjadi Pembayaran Utang saat Posting Kas.

### Perlu diperhatikan
- Hari-hari Quinos cara Harian yang sudah diimport sebagai satu faktur gabungan untuk profil beberapa store tampil **Beda** ("1 faktur → 2 faktur") di Integrasi Quinos. Tidak berubah sampai Anda
  memilih **Update** untuk hari itu; yang belum diupdate tetap tampil gabungan di Penerimaan per akun.
- Perubahan database: kolom baru `outlet_moves.ref_no` (migrasi otomatis saat API start).

## 1.0.84 (12 November 2026)

### Baru
- **Penjualan › Faktur Penjualan, Pesanan Penjualan, Kasir** dan **Pembelian › Faktur Pembelian, Pesanan Pembelian**: tombol **Muat ulang item**
  (atau **F5**) memuat ulang daftar item dari server, jadi item yang baru ditambah di Item (oleh user lain atau di PC lain) langsung bisa dipilih tanpa
  menutup form. Baris yang sudah diisi tidak berubah; tombol menampilkan sebentar berapa item baru yang masuk.
  - Daftar item juga dimuat ulang sendiri saat tab faktur / pesanan dibuka kembali setelah lebih dari 2 menit.
  - Di **Kasir**, barcode atau kode yang dipindai dan tidak ditemukan memuat ulang daftar otomatis lalu mencari lagi.
- **Persediaan › Stok Opname, Item Masuk / Item Keluar, Transfer Keluar, Rakitan / Produksi, Pecah Stok, Permintaan Transfer**, **Titipan** (Titip Masuk dari penitip,
  Titip Keluar ke toko) dan **Akuntansi › Saldo Awal Stok**: tombol **Muat ulang item** (atau **F5**) di judul form memuat ulang daftar item dari server, jadi item yang
  baru ditambah di Item (oleh user lain atau di PC lain) langsung bisa dipilih tanpa menutup form. Sama seperti di Penjualan dan Pembelian. Baris yang sudah diisi tidak
  berubah; tombol menampilkan sebentar berapa item baru yang masuk. Tombolnya hanya tampil saat form bisa diisi.
  - Daftar item juga dimuat ulang sendiri saat tab form dibuka kembali setelah lebih dari 2 menit.
  - **Stok Opname**: item baru ikut **Muat semua item**, dengan stok sistem dari server; stok sistem baris yang sudah diisi tidak dihitung ulang.
  - **Rakitan**: item hasil yang sudah dipilih tetap terpilih dan komponen yang sudah diisi tidak berubah.
  - **Pecah Stok**: item yang baru diberi aturan pecah (tab Konversi di Item) muncul di pilihan **Item dipecah**.

### Perbaikan
- **Persediaan › Koreksi Stok › Daftar Opname**: item yang sudah ada di daftar kini bisa dikeluarkan. Form daftar (Baru dan Ubah) punya tombol **Hapus item**;
  **Ctrl+Delete** juga bekerja saat sel sedang diketik (sebelumnya Delete diam saja begitu sel diklik), dan **Ctrl / Shift + klik** memilih beberapa item sekaligus.
  Perubahan baru tersimpan saat **Simpan (F9)**, dan dokumen Opname Harian yang sudah dibuat dari daftar itu tidak berubah.

### Diperbaiki
- **Laporan Setoran Harian (Tutup Hari › Cetak)** disamakan dengan lembar Excel kasir: Kas Keluar tampil positif, Kas Masuk nol tampil "-", baris **Pembulatan**
  (isian setoran di tab Kas dikurangi setoran hitung) ditambahkan, dan **TOTAL SETORAN** kini sama dengan isian tab Kas. Baris Lainnya yang nol tidak dicetak.

## 1.0.83 (12 November 2026)

### Baru
- **Closing Harian › Tutup Hari › Cetak ▾ › Laporan Setoran Harian** (struk thermal 80 mm): melaporkan uang yang akan disetorkan. Kolom **Sistem** (penjualan) dan **Settlement**
  (uang yang dihitung di Uang per Shift) untuk Tunai, tiap EDC, Lainnya, dan Total, lalu **Kas Keluar**, **Kas Masuk**, dan **Total Setoran**. Muncul bila fitur Laporan Outlet menyala.
- **Closing Harian › Penjualan › Import Quinos**: kolom **Outlet Quinos** menampilkan store Quinos yang dicakup tiap profil.
- **Closing Harian › Penjualan › Penerimaan per akun** kini grid parent-child: baris induk per outlet Quinos (dengan total), baris anak per akun. Penerimaan di luar import Quinos
  (Kasir, faktur, pelunasan manual) ada di baris **Di luar Quinos**.

### Perbaikan
- **Closing Harian › Penjualan**: kolom dibuat 50% / 50%; Import Quinos dan Retur dan pembatalan pindah ke kolom kiri, Penerimaan per akun ke kanan.

## 1.0.82 (11 November 2026)

### Baru
- **Closing Harian › Kas** disederhanakan: dua isian (**Kas fisik**, **Setoran** + tujuan) yang terisi dari Uang per Shift bila Laporan Outlet menyala, satu baris angka
  (Seharusnya, Selisih, Setoran, Sisa kas) dengan rumusnya, kotak **Dibuat saat Posting Kas**, accordion **Mutasi kas hari ini** (terbuka), dan **Hitung per pecahan** di paling bawah (tertutup).
- **Posting Kas** kini juga membuat dokumen dari kas keluar / kas masuk **Uang per Shift**: jenis Biaya menjadi **Kas Keluar / Kas Masuk**, jenis Bayar faktur menjadi
  **Pembayaran Utang**. Faktur yang sudah lunas membuat Posting Kas ditolak; yang sudah dibayar sebagian diberi keterangan. **Batalkan Posting Kas** membatalkan semuanya.
- Urutan tab Closing Harian mengikuti alur kerja: Opname, Penjualan, Uang per Shift, Setoran & Pencocokan, **Kas**, Tutup Hari.

### Perbaikan
- **Closing Harian › Uang per Shift › Kas keluar / kas masuk**: baris yang salah kini bisa dihapus lewat tombol **Hapus baris** (atau Ctrl+Delete), lalu **Simpan (F9)**.
- **Closing Harian › Uang per Shift**: panel kanan **Ringkasan hari** dan **Mode** dibuat 50% lebih lebar.

### Perlu diperhatikan
- Kas keluar / kas masuk Uang per Shift tidak lagi sekadar catatan: saat Posting Kas menjadi jurnal. Pembayaran faktur yang sudah dicatat di Uang per Shift **jangan diinput lagi**
  di menu Pembayaran Utang (Posting Kas akan menolak faktur yang sudah lunas).
- Sesudah Posting Kas, baris kas keluar / kas masuk Uang per Shift terkunci sampai **Batalkan Posting Kas**.

## 1.0.81 (11 November 2026)

### Perbaikan
- **Closing Harian › Kas › Seharusnya**: dihitung bersambung per hari: **sisa kas closing sebelumnya** (kas fisik − setoran; belum pernah mengisi kas = 0) + penerimaan tunai + kas keluar / masuk bertanda Closing Harian.
  Sebelumnya (1.0.79 dan 1.0.80) memakai saldo seluruh riwayat akun kas, yang tercampur setoran Akunting yang dicatat belakangan, sehingga selisih kas palsu (1.0.80: sampai ratusan juta).
  Dokumen Kas & Bank yang diinput langsung (Akunting) tetap tidak ikut closing.

### Perlu diperhatikan
- Hari pertama sebuah cabang mengisi kas memakai modal laci 0, jadi selisih hari itu sebesar modal laci sebenarnya; sisa kasnya otomatis menjadi modal hari berikutnya.
- Kas keluar laci yang hanya dicatat di Laporan Outlet (belum menjadi Kas Keluar bertanda **Bagian Closing Harian**) belum mengurangi Seharusnya.

## 1.0.80 (11 November 2026)

### Baru
- **Kas & Bank › Kas Masuk / Kas Keluar / Transfer Kas**: kotak **Bagian Closing Harian (kas outlet)** menandai dokumen sebagai bagian kas laci cabang. Kosong (bawaan) berarti input langsung dari Kas & Bank (Akunting). Daftar dokumen menampilkan kolom **Sumber**.
- **Closing Harian › Kas**: **Mutasi kas hari ini** dan **Kas seharusnya** hanya memuat dokumen bertanda Closing Harian (selisih kas dan setoran dari Posting Kas otomatis bertanda) serta penjualan tunai.
  Dokumen yang diinput Akunting langsung dari Kas & Bank (mis. bayar pajak) tidak lagi ikut closing operasional cabang.

### Perlu diperhatikan
- Dokumen kas yang dibuat Posting Kas sebelum rilis ini otomatis ditandai Closing Harian. Dokumen Kas & Bank lainnya dianggap input langsung Akunting, sehingga **Kas seharusnya** hari-hari yang belum diposting bisa berubah (tidak lagi memuat kas keluar / masuk Akunting). Closing yang kasnya sudah diposting tidak berubah.
- Kas keluar atau masuk laci yang dicatat dari menu Kas & Bank perlu dicentang **Bagian Closing Harian**, supaya ikut kas seharusnya.

## 1.0.79 (11 November 2026)

### Baru
- **Closing Harian › Kas › Setoran**: jumlah setoran terisi otomatis dari Setoran tunai Laporan Outlet (Tunai − Kas keluar + Kas masuk), tidak perlu diketik ulang. Angka yang diketik user tidak ditimpa.
- **Closing Harian › Uang per Shift › Lainnya**: terisi otomatis dari penerimaan sistem (akun di luar kas dan bank) di shift 1 pada hari yang belum tersimpan; ubah bila berbeda.
- **Closing Harian › Setoran & Pencocokan**: kolom **Sistem** sudah terisi sebelum isian disimpan (sebelumnya 0 sampai disimpan).

### Perbaikan
- **Closing Harian › Setoran & Pencocokan**: kolom **Sistem** kini ikut data penerimaan per akun di tab Penjualan walau akun bank belum dipetakan di Cabang › Bank EDC.
  Akun yang namanya memuat nama bank (mis. "QRIS/EDC/Transferan (BRI)") otomatis dihitung ke EDC bank itu, bukan lagi masuk **Lainnya**.
  Akun yang tetap tidak cocok dihitung sebagai Lainnya dan disebut di daftar Peringatan, lengkap dengan petunjuk untuk memetakannya.

### Perlu diperhatikan
- **Rilis**: gerbang CVE kini mengikuti ketentuan pembaruan komponen. Rilis keamanan .NET yang baru dan tidak serius ditunda 30 hari (Moderate) atau 90 hari (Low) (tidak menolak rilis); CVE serius yang dicatat pemilik repo atau paket High/Critical tetap menolak segera.

## 1.0.78 (11 November 2026)

### Diubah
- **Closing Harian › Uang per Shift**: **Pembayaran per shift** dan **Kas keluar / kas masuk** kini dua tab dalam satu tab group (bukan dua kotak bertumpuk), masing-masing memenuhi seluruh tinggi tab; judul tab kedua menampilkan jumlah baris, dan ringkasan setoran tunai tetap terlihat di bawahnya.

## 1.0.77 (10 November 2026)

### Diubah
- **Closing Harian › Laporan Outlet › Uang per Shift**: tampilan kini seperti kertas Laporan Harian, dengan **shift sebagai kolom** (baris Tunai, EDC tiap bank, Lainnya, Total pembayaran). Tunai dan Lainnya diketik langsung di sel; sel **EDC** (berlatar biru dengan ikon) diisi lewat popup **Rincian slip** (Debit, Kredit, QRIS, QRIS Tap; klik ganda, Enter, F2, atau tombol Rincian slip…). **Kas keluar / kas masuk** menjadi daftar datar dengan kolom Shift. Tanpa perubahan data di server.

## 1.0.76 (10 November 2026)

### Baru
- **Closing Harian**: judul tab kini memakai **ikon berwarna** (ceklis hijau selesai, seru kuning peringatan, silang merah penghalang atau gagal, lingkaran kosong belum diisi, setengah biru sebagian terisi), tetap benar di semua tema Warna Aplikasi. Arahkan mouse ke ikon untuk melihat arti dan alasannya, termasuk alasan Tutup Hari ditolak.
- **Closing Harian › Kas**: **Hitung fisik per pecahan** (lembar diketik, jumlah dihitung, boleh langsung mengetik total) dan **Mutasi kas hari ini** (Kas Masuk / Kas Keluar cabang itu tanggal itu); rincian pecahan tersimpan di closing.
- **Closing Harian › Laporan Outlet**: kolom kanan **Ringkasan hari** (persen tiap pembayaran, shift terisi, diisi oleh siapa dan jam), kotak **Peringatan (n)**, dan **Catatan laporan outlet** (memo bebas, satu per hari, tidak terkait selisih).
- **Laporan Outlet (sisi server)**: memo harian bebas per cabang per tanggal (maks. 1000 huruf) dan penanda "diisi oleh / kapan" (nama user dan waktu simpan
  terakhir). Memo tidak terkait pencocokan, catatan selisih, atau Mode Wajib: memo kosong tidak pernah menolak Tutup Hari. Fitur Laporan Outlet tetap harus
  dinyalakan di Pengaturan Perusahaan › Fitur.

### Perbaikan
- **Cabang › Laporan Outlet › Pilih akun…**: kotak centang akun kas / bank kini bisa dicentang (sebelumnya klik tidak mengubah apa pun, sehingga akun tidak bisa dikaitkan ke Bank EDC). Klik baris atau tekan Spasi untuk mencentang; daftar hanya akun Kas / Bank, urut kode.
- **Cabang › Ubah**: dialog dua kolom (isian cabang di kiri, kotak Laporan Outlet di kanan, tanpa gulir) dan satu tombol **Simpan** untuk cabang dan pengaturan Laporan Outlet; tombol "Simpan Laporan Outlet" yang terpisah dihapus.

### Diubah
- **Closing Harian**: semua tab memakai kotak berjudul standar (garis tipis, mengikuti tema Warna Aplikasi), tidak ada lagi bar judul berwarna atau akordeon.
- **Closing Harian › Laporan Outlet** dipecah menjadi dua tab: **Uang per Shift** (grid master-detail lebar) dan **Setoran & Pencocokan**. Urutan tab: Opname, Penjualan, Kas, Uang per Shift, Setoran & Pencocokan, Tutup Hari. Tetap tersembunyi bila fitur Laporan Outlet mati.
- **Closing Harian › Penjualan** didesain ulang: **Ringkasan penjualan** (Faktur, Total, Rata-rata per faktur, Diskon / PB1 / Layanan), **Penerimaan per akun** (akun, %, jumlah), **Import Quinos**, dan **Retur dan pembatalan**. Rincian per akun hanya di Penjualan; tab Kas hanya menyebut penerimaan tunai.

## 1.0.75 (10 November 2026)

### Baru
- **Web Outlet › Pilar ERP**: halaman web outlet kini bernama **Pilar ERP** dengan logo di halaman masuk dan di bar atas. Bar atas memuat nama cabang di kiri (tekan untuk memilih cabang) dan logo di kanan.
- **Web Outlet › Kartu pengguna**: tombol bulat di kanan bawah membuka kartu berisi nama, jabatan, perusahaan, cabang, versi, dan **Keluar**. Tombol Keluar di bar atas dihapus.
- **Web Outlet › Dashboard**: halaman pertama setelah masuk, berisi penjualan dan selisih kas hari ini, kiriman yang menunggu, opname yang berjalan, dan aksi cepat.
- **Web Outlet › Closing List**: tombol **Closing** membuka daftar 7 hari terakhir cabang terpilih (menggantikan Rekap semua cabang): nomor, penjualan, kas, selisih kas, opname, dan status. Tanggal dipilih dari list atau **Buka tanggal lain**.
- **Web Outlet › Hari closing**: tanggal di kiri dan **Ubah tanggal** di kanan; sub-tab Dashboard (kartu Opname, Selisih, Penjualan, Kas dan tombol Tutup Hari), Opname, Selisih, Penjualan, Kas, dan Atur. Hari ini diganti nama Dashboard, Hitung digabung ke Opname.

### Perubahan
- **Web Outlet**: status **Tersimpan** tidak lagi tampil; strip kuning **Menunggu sinyal** muncul hanya bila ada hitungan yang belum terkirim.

## 1.0.74 (10 November 2026)

### Baru
- **Closing Harian › Laporan Outlet** (tahap simulasi, bawaan mati): tab baru untuk mencatat uang harian outlet seperti di kertas Laporan Harian. Tunai dan Lainnya per shift diketik, **slip rekap EDC** per bank diketik per shift (hanya rupiah, tanpa nomor batch), lalu EDC, total pembayaran, dan **setoran tunai** (Tunai − Kas Keluar + Kas Masuk) dihitung otomatis. **Pencocokan dengan sistem** menandai selisih per bank dan menduga **salah gesek** bila dua bank berselisih sama besar berlawanan tanda. Hanya mencatat: tidak ada jurnal atau dokumen. Mode per cabang (Cabang › Laporan Outlet): Peringatan (bawaan, tidak menghalangi Tutup Hari) atau Wajib (Tutup Hari ditolak bila belum diisi atau ada selisih tanpa catatan). Nyalakan di Pengaturan Perusahaan › Fitur › **Laporan Outlet (simulasi)**.
- **Sistem › Master Pendukung › Jenis Kas Outlet**: master jenis kas keluar / kas masuk (arah, cara Biaya atau Bayar faktur, akun lawan) untuk Laporan Outlet. Tampil hanya bila fitur menyala.
- **Cabang**: isian **Jumlah shift**, **Mode Laporan Outlet** (Peringatan / Wajib), dan daftar **Bank EDC** (nama, TID / MID, akun kas / bank bank itu) untuk Laporan Outlet. Tampil hanya bila fitur menyala.

### Perbaikan
- **Penjualan › Opname Harian** dan **Persediaan › Stok Opname**: klik dua kali dokumen berstatus Release kini membuka dokumen dalam mode Ubah bagi yang boleh Buka Kembali, jadi tombol **Buka Kembali** langsung terlihat (sebelumnya dokumen Release terbuka sebagai Lihat tanpa tombol itu).

### Perlu diperhatikan
- Fitur **Laporan Outlet** bawaan **mati** untuk semua perusahaan: nyalakan di Pengaturan Perusahaan › Fitur › **Laporan Outlet (simulasi)**. Selama mati tidak ada yang berubah
  (tab, menu, dan isian Cabang tersembunyi; server menolak permintaannya). Fitur hanya mencatat dan mencocokkan: tidak membuat jurnal, Kas Keluar / Masuk, Transfer Kas, atau Pembayaran.
  **Mode Laporan Outlet** per cabang: Peringatan (bawaan, tidak pernah menolak Tutup Hari) atau Wajib (Tutup Hari ditolak bila belum diisi atau ada selisih pencocokan tanpa catatan);
  mode Wajib hanya berlaku bila fitur menyala. Migrasi `LaporanOutlet` menambah tabel kosong.

## 1.0.73 (9 November 2026)

### Baru
- **Web Outlet › menubar**: menubar jadi lima tombol: **Beranda**, **Penjualan**, **Pembelian**, **Persediaan**, dan **Closing** (Closing Harian). Layar di dalam tiap tombol dipilih lewat sub-tab.
- **Web Outlet › Beranda**: pintu masuk berisi kiriman yang menunggu diterima, opname yang berjalan, dan aksi cepat sesuai hak akun.
- **Web Outlet › Penjualan / Pembelian**: daftar transaksi 7 hari terakhir dengan rincian item (hanya melihat).
- **Web Outlet › Persediaan**: transfer keluar bisa **diubah** dan **dihapus** selama belum diterima; transfer masuk bisa diubah (tanggal, catatan) dan **dibatalkan terimanya**, dengan alasan wajib. Layar Pesanan Transfer untuk cabang penerima permintaan belum ada di web.
- **Web Outlet › Closing**: **Opname** (Opname Harian) kini paling depan di grup Closing.

### Perbaikan
- **Web Outlet › halaman masuk**: nomor versi tidak lagi memakai gaya inline yang diblokir kebijakan keamanan peramban.

## 1.0.72 (9 November 2026)

### Perbaikan
- **Web Outlet › Transfer Masuk / Transfer Keluar**: daftar "Diterima / Terkirim 7 hari terakhir" kini punya tombol **Lihat rincian** untuk melihat item dan qty tiap transfer (sebelumnya daftar tidak menampilkan item sama sekali).
- **Web Outlet › menubar**: menubar diringkas jadi 3 tombol grup — **Harian** (Hari ini, Opname, Hitung, Selisih, Penjualan, Kas, Tutup, Rekap sebagai sub-tab), **Transfer** (Masuk, Keluar), dan **Atur**. Sub-tab bisa digeser ke samping bila tidak muat.
- **Web Outlet › Transfer › Permintaan**: sub-tab baru untuk meminta barang ke cabang lain (Permintaan Transfer, nomor PTR) langsung dari web: pilih cabang, tanggal dibutuhkan, item dan qty. Daftar "Permintaan saya" menampilkan status, nomor transfer keluarnya, dan rincian terkirim/sisa. Perlu hak Permintaan Transfer.
- **Web Outlet**: nomor versi kini tampil di halaman masuk dan di header (di bawah nama pengguna).

## 1.0.71 (9 November 2026)

### Perbaikan
- **Penjualan › Closing Harian › tab Opname**: menu **Cetak ▾** kini juga menawarkan **Hasil Opname Stock Thermal 80 mm** untuk dokumen yang dicentang (yang sudah Release / Close, bagi pemegang hak Closing Harian); satu struk per dokumen dalam satu cetakan.
- **Penjualan › Closing Harian › tab Tutup Hari**: **Cetak ▾ › Hasil Opname Stock Thermal 80 mm** meminta konfirmasi **No Opname Harian** dulu (semua nomor yang sudah Release / Close dicentang), baru dicetak, satu struk per nomor.

## 1.0.70 (9 November 2026)

### Perbaikan
- **Penjualan › Closing Harian** dan **Laporan › Laporan Closing**: menu **Cetak** kembali menampilkan **Closing Harian Lengkap** dan **Ringkas** (A4 mendatar), di samping struk thermal.
- **Opname Harian / Closing Harian**: struk thermal 80 mm kini bernama **Hasil Opname Stock** (sebelumnya Laporan Persediaan Harian); judul di struknya **HASIL OPNAME STOCK**. Nama template lama di tiap perusahaan ikut diganti otomatis.

## 1.0.69 (9 November 2026)

### Baru
- **Persediaan › Koreksi Stok › Stok Opname** (menu baru, desktop): daftar dokumen Stok Opname berstatus (Draft → Open → Release → Close), **Baru…** (judul, tanggal opname, batas hitung, PIC, pilih item dari Semua / Tipe / Rak / Kelas / Excel), Open, Cetak, dan form dokumen dengan **Close (posting)**, Revisi, Ganti PIC, Buka Kembali, Batal. Menu lama diganti nama menjadi **Stok Opname Langsung**.
- **Halaman web HP**: menu Opname memuat dokumen Stok Opname berstatus (diberi label) untuk PIC dengan hak Hitung Stok Opname.
- **Stok Opname (berstatus) › Baru…**: centang **Pecah per rak** untuk membuat satu dokumen Draft per rak (judul "judul · rak", PIC sama; item tanpa rak satu dokumen sendiri). Aplikasi menyebut dokumen yang dibuat.
- **Stok Opname (berstatus) › Close…**: centang beberapa dokumen Release bertanggal opname sama lalu Close bersama menjadi **satu** Stok Opname (OP); buangan Expired / Waste digabung per alasan. Item yang sama di dua dokumen ditolak. Buka Kembali satu dokumen dari gabungan mengembalikan semua dokumen gabungan ke Release.
- **Sistem › Bersihkan Data**: jenis data baru **Stok Opname (berstatus)** (boleh per rentang tanggal opname) menghapus dokumen beserta hitungan, revisi, Stok Opname (OP), dan Item Keluar buangan hasil Close-nya. Bersihkan semua transaksi satu cabang juga ikut membersihkan dokumen Stok Opname berstatus; menghapus OP / Item Keluar hasil Close ikut menghapus dokumennya.
- **Persediaan › Laporan › Revisi Opname Harian**: kolom **Nilai Perubahan (Harga Jual)** di Rincian Revisi dan Rekap per Perevisi (perubahan qty × harga jual daftar item), serta **Nilai Perubahan (HPP)** bagi jabatan yang boleh melihat harga pokok.
- **Opname Harian › Cetak**: template **Hasil Hitung + Selisih** (A4 dan thermal 80 mm) dengan kolom Sistem dan Selisih dari Closing Harian, tombol **Hasil + Selisih ▾** di form dokumen. Hanya untuk pemegang hak Closing Harian; PIC tanpa hak itu tidak melihat template maupun angkanya.

### Perbaikan
- **Opname Harian**: Akun Expired / Waste tidak lagi wajib. Cabang yang belum punya akunnya tetap bisa Generate dokumen dan Open; kolom Expired / Waste
  saja yang tidak dipakai. Qty buangan lebih dari 0 tanpa akunnya tetap ditolak saat dicatat.
- **Persediaan › Opname Harian**: tombol Laporan Persediaan dipindah ke menu **Cetak ▾** dan namanya menjadi **Laporan Opname Harian Thermal 80 mm** (muncul sesudah dokumen di-Release).
- **Penjualan › Closing Harian** dan **Laporan › Laporan Closing**: menu **Cetak** kini hanya berisi **Laporan Opname Harian** (struk); cetakan A4 Closing Harian Lengkap dan Ringkas tidak ditawarkan lagi. Judul struknya **LAPORAN OPNAME HARIAN**.
- **Penjualan › Closing Harian** (desktop) dan **web outlet**: tab **Kas** kini menampilkan **Diterima per akun** (uang yang masuk hari itu, termasuk dari import Quinos) walau akun kas outlet belum dipilih, jadi atasan langsung melihat uangnya masuk ke akun mana.
- **Ekspor & Backup**: paket cabang kini memuat hitungan dokumen Stok Opname berstatus (sebelumnya terlewat karena tidak punya Closing Harian).
- **Opname Harian › wajib opname**: item berfrekuensi yang dihitung di dokumen Stok Opname berstatus kini terpenuhi setelah dokumen **Close** (bukan sejak Release), dan kembali jatuh tempo bila Close dibuka kembali.
- **Opname Harian › Ganti PIC…**: kini cukup dengan hak Closing Harian **Buat** (hak Tutup Hari), jadi kepala outlet yang boleh Tutup Hari bisa mengganti PIC. Generate, Open, dan Daftar Opname tetap butuh hak Ubah.

## 1.0.68 (8 November 2026)

### Baru
- **Cetak Hasil Hitung Opname Harian** (A4 dan thermal 80 mm) dari tombol **Cetak ▾** di daftar dan form Opname Harian: fisik sesudah revisi, Expired, Waste, catatan revisi per item, jumlah revisi, dan tanda tangan PIC dan Kepala outlet. Tanpa stok sistem, selisih, dan harga.
- **Laporan › Laporan Persediaan › Revisi Opname Harian**: Rekap per Perevisi dan Rincian Revisi (qty sebelum dan sesudah, alasan, perevisi, apakah PIC sendiri) untuk rentang tanggal opname dan outlet.
  Hak baru `lap_revisi_opname_harian`, diberikan ke jabatan yang boleh melihat Closing Harian.
- **Rekap Closing** (desktop dan web) mendapat kolom **Revisi** (jumlah revisi hitungan hari itu).
- Ringkasan **Salin untuk WhatsApp** menambahkan baris "Revisi hitungan: n item" beserta daftar ringkasnya bila ada.
- **Web outlet (/outlet/) › Transfer**: tab baru untuk terima kiriman cabang lain (**Masuk**) dan kirim barang ke cabang lain (**Keluar**) dari HP. Tampil sesuai hak
  Transfer Masuk dan Transfer Keluar akun.
- **Stok Opname berstatus (tahap 1, server)**: dokumen hitung periodik dengan status Draft → Open → Release → Close, nomor `SOH/…`, tanpa Closing Harian dan tanpa Daftar Opname. **Close** memposting Stok Opname (OP) per akhir tanggal opname dan buangan Expired / Waste sebagai Item Keluar; **Buka Kembali** dari Close membatalkan keduanya. Layar desktop dan label di HP menyusul di tahap berikutnya.
- Hak baru **Stok Opname (berstatus)** (atasan: Lihat, Buat, Ubah, Batal) dan **Hitung Stok Opname (PIC)** (Lihat, Buat), terpisah dari Opname Harian. Jabatan yang bisa membuat Stok Opname Langsung otomatis mendapatkannya.

### Perlu diperhatikan
- Migrasi basis data `StokOpnameBerstatus`: dokumen Opname Harian lama otomatis berjenis Harian.

## 1.0.67 (8 November 2026)

### Baru
- **Persediaan › Kartu Stok**: jenis mutasi kini jelas tanpa membuka dokumennya. Kolom **Jenis** membedakan **Penjualan umum** dan **Penjualan grup**
  (antar perusahaan satu grup), **Pembelian umum** dan **Pembelian grup**, serta **Opname lebih** dan **Opname kurang**. Kolom baru **Lawan** menyebut
  konsumen / supplier, alasan Item Masuk / Keluar (akun lawan), cabang tujuan Transfer Keluar ("→ Cabang") dan cabang asal Transfer Masuk ("← Cabang"),
  serta penitip / toko titipan.

## 1.0.66 (8 November 2026)

### Baru
- **Closing Harian (Web) › Stok › Selisih**: sub-tab baru di HP untuk pemegang hak Closing Harian. Menampilkan selisih stok dokumen Opname Harian yang sudah Release **sebelum Tutup Hari**
  (Sistem, Fisik, Selisih, filter Berselisih / Direvisi, pencarian) beserta riwayat revisi.
- **Revisi hitungan per item dari HP**: ketuk baris di tab Selisih, isi qty baru, alasan, serta username dan password yang merevisi (kode 2FA bila user itu memakainya),
  sama seperti di desktop. PIC melihat catatan revisi atas hitungannya di layar hitung.
- Menu bawah web HP diringkas: **Stok** memuat sub-tab Hitung dan Selisih, **Penjualan** memuat sub-tab Penjualan dan Kas.
- **Expired dan Waste selalu tampil** di layar hitung Opname Harian (desktop dan HP). Akun lawannya otomatis akun **5-1300 Susut, Rusak & Kedaluwarsa (Waste)** bila belum diatur di Closing Harian › Atur.
- Hak baru **Pengaturan Closing Harian** (Penjualan): Ubah = menyimpan Closing Harian › Atur (akun kas outlet, batas selisih kas, jam ganti hari, akun Expired / Waste, dan lainnya). Jabatan yang sebelumnya bisa menyimpan pengaturan (Closing Harian Buat) otomatis mendapatkannya.

### Perbaikan
- **Closing Harian / Opname Harian**: selisih opname kini selalu dibandingkan dengan stok akhir tanggal closing (awal + masuk − keluar − buangan),
  tidak lagi dengan stok pada jam hitung diinput. Hitungan yang diketik keesokan hari (dari lembar kertas) tidak lagi berselisih palsu karena kiriman
  atau penjualan tanggal berikutnya. Kolom dan peringatan *Mutasi Sesudah Hitung* / *Penjualan tanpa jam* dihapus.

### Perlu diperhatikan
- Closing yang sudah ditutup dengan selisih palsu tidak berubah sendiri (Stok Opname sudah diposting): **Buka Kembali** closing itu lalu **Tutup Hari** lagi.
- Cabang yang belum punya akun Expired / Waste dan perusahaannya tidak punya akun 5-1300 tidak bisa **Generate dokumen** dan **Open** Opname Harian sampai kedua akun diisi di Atur.

## 1.0.65 (8 November 2026)

### Baru
- **Closing Harian › Kas › Posting Kas**: kas fisik dan setoran kini langkah tersendiri, terpisah dari Tutup Hari. Kepala outlet boleh menutup hari tanpa mengisi kas;
  **Akunting** mengisi kas fisik dan setoran lalu menekan **Posting Kas** (membuat Kas Masuk / Keluar selisih kas dan Transfer setoran), juga **sesudah** Tutup Hari.
  Kas yang sudah diposting dikunci sampai **Batalkan Posting Kas…** (alasan wajib). Bila kas fisik sudah diisi sebelum Tutup Hari, Tutup Hari memostingnya otomatis seperti dulu.
- Hak baru **Kas Closing Harian** (Penjualan): Buat = isi kas dan Posting Kas, Batal = Batalkan Posting Kas.
- **Sistem › Jabatan & Hak Akses**: kolom Keterangan hak lintas-menu (harga modal, cetak, import, persetujuan, dan sebagainya) kini menyebut nama menu yang memakainya
  ("Dipakai di: …"), jadi hak mudah dicari lewat nama menu.

### Perlu diperhatikan
- **Buka Kembali closing tidak lagi membatalkan Kas Masuk / Keluar selisih dan Transfer setoran**; hanya Stok Opname dan Item Keluar buangan. Batalkan kas lewat
  **Batalkan Posting Kas…** bila perlu.
- Jabatan yang boleh mengisi kas (Closing Harian Buat) otomatis mendapat Kas Closing Harian Lihat + Buat, yang punya Closing Harian Batal juga Batal; jabatan bawaan Akunting
  mendapat ketiganya. Closing yang sudah ditutup sebelum pembaruan ini dianggap kasnya sudah diposting.

## 1.0.64 (8 November 2026)

### Perbaikan
- **Cetak thermal**: nama item di semua struk thermal (80 dan 58 mm) selalu satu baris; nama yang kepanjangan dipotong dan diakhiri "...", tidak turun ke baris bawah.

### Perlu diperhatikan
- **Buka Kembali** closing dan dokumen Opname Harian kini butuh hak baru **Buka Kembali Closing & Opname** (Penjualan), bukan lagi Closing Harian › Batal. Jabatan yang
  dulu punya Closing Harian › Batal otomatis mendapat hak baru ini, dan jabatan bawaan **Akunting** juga. Cabut dari kepala outlet di Jabatan & Hak Akses bila Buka Kembali
  hanya untuk pusat; tanpa hak itu, desktop meminta Persetujuan Atasan dan halaman web HP tidak menampilkan tombolnya. **Batal** dokumen tetap memakai Closing Harian › Batal.

## 1.0.63 (8 November 2026)

### Baru
- **Opname Harian › Revisi…**: hitungan yang sudah di-Release bisa direvisi per item sebelum Tutup Hari. Yang merevisi mengisi qty baru, alasan, username, dan
  password-nya sendiri (kode 2FA bila memakai 2FA). Kolom **Revisi** di grid menampilkan qty sebelum → sesudah, siapa, dan alasannya; **Riwayat revisi**
  menyimpan semuanya, termasuk user yang login di komputer saat itu. PIC ikut melihat revisi atas hitungannya.

### Perlu diperhatikan
- Hak baru **Revisi Hitungan Opname** (kelompok Persediaan). Jabatan yang boleh Tutup Hari (Closing Harian Buat) otomatis mendapatkannya; cabut di Jabatan & Hak Akses
  bila hanya kepala outlet yang boleh merevisi.

## 1.0.62 (8 November 2026)

### Baru
- **Closing Harian (Web)** dan **Opname Stock (Web)**: dua hak akses baru di Jabatan & Hak Akses untuk halaman web `/outlet/` di HP.
  Menu Hari ini, Penjualan, Kas, Tutup, Rekap, dan Atur mengikuti Closing Harian (Web); menu **Opname** mengikuti Opname Stock (Web).
- **Opname** di halaman web `/outlet/`: begitu login (akun dengan Opname Stock (Web) saja), tampil daftar dokumen opname yang **Draft**, **Open**, dan **Release**
  di semua tanggal; yang sudah Close tidak tampil. Ketuk satu dokumen untuk menghitung dan Release.

### Perlu diperhatikan
- Jabatan yang sudah punya hak Closing Harian atau Opname Harian otomatis mendapat kedua hak web baru ini, jadi tidak ada yang kehilangan akses. Cabut salah satunya
  di Jabatan & Hak Akses bila ingin memisahkan. Jabatan **Kasir** bawaan ikut mendapatkannya.
- **Closing Harian › Tutup Hari** kini hanya mengunci **transaksi** cabang pada tanggal itu: penjualan, retur, import Quinos, pembelian, dan dokumen stok.
  **Kas Masuk, Kas Keluar, Transfer Kas, pelunasan piutang / utang, dan biaya** bertanggal itu tetap bisa dibuat dan diubah Akunting sampai Tutup Periode.
- **Closing Harian**: hitung kas tidak wajib lagi untuk Tutup Hari. Kas dipegang Akunting; bila kas fisik diisi, selisih kas dan setoran tetap dibuat saat Tutup Hari.
- Pembelian yang telat diinput untuk tanggal yang sudah ditutup tetap harus lewat **Buka Kembali** closing, lalu Tutup Hari lagi, supaya stok tidak dobel.

## 1.0.61 (8 November 2026)

### Baru
- **Opname Harian › Cetak**: Lembar Hitung Opname kini punya template Thermal 80 mm. Satu baris per item (No, Nama, Sat, Fisik, Exp, Wst); nama item yang kepanjangan dipotong, tidak turun ke baris bawah.

## 1.0.60 (8 November 2026)

### Baru
- **Bantuan › Tutorial**: kotak cari kini mencari di isi semua topik. Topik yang cocok disaring di daftar, kata yang dicari disorot di halaman, dan **Enter** / **F3** (Shift = mundur) atau tombol ▲ ▼ pindah ke kecocokan berikutnya; **Ctrl+F** langsung ke kotak cari.
- **Bantuan › Tutorial**: panel **Bagian topik** (bookmark dari judul bagian) di kanan halaman. Klik untuk melompat ke bagian itu; butir yang menyala mengikuti bagian yang sedang dibaca. Tampil / sembunyikan dengan tombol **Bookmark** atau **Ctrl+B**.
- **Tutorial semua menu**: bagian **Hak akses** diseragamkan di tiap modul — hak yang dibutuhkan, tombol yang diatur masing-masing hak, hak tambahan (cetak, harga modal, import), dan jabatan bawaan.
- **Persediaan › Koreksi Stok › Opname Harian**: tombol **Cetak lembar hitung ▾** mencetak **Lembar Hitung Opname** (A4) untuk dokumen yang dicentang:
  item daftar dengan kolom Fisik, Expired, dan Waste kosong untuk ditulisi tangan, dikelompokkan per lokasi, tanpa stok sistem. Dua daftar dicentang
  menghasilkan dua lembar dalam satu cetakan, dan bisa dicetak sejak dokumen masih Draft. Cetakan yang sama ada di form hitung. Nomor baris di kertas
  sama dengan kolom **No** di form hitung, jadi menyalin dari kertas tinggal turun satu per satu.
- **Opname Harian**: daftar dokumen kini bisa dicentang banyak, ada tombol **Lihat**, **Ubah**, dan **Open** (untuk dokumen Draft yang dicentang).
  Lihat dan Ubah membuka form hitung sebagai dialog di atas daftar, tidak lagi pindah ke tab lain.
- **Penjualan › Closing Harian › Buka Closing**: form dibagi empat tab dengan tombolnya masing-masing: **Opname** (daftar dokumen Opname Harian: Generate,
  Open, Cetak lembar hitung, Lihat, Ubah), **Penjualan** (Import Penjualan, Pemetaan), **Kas** (Simpan, Atur kas outlet) dan **Tutup Hari** (Tutup Hari,
  Buka Kembali, Cetak, Salin WhatsApp). Judul tab memberi tanda ✔ / ⚠ / ○ untuk status tiap langkah. Bar atas tinggal Muat Ulang dan Tutup.

### Perbaikan
- **Akuntansi › Jurnal Umum**: kolom **No. Referensi** jurnal otomatis (penjualan, pembelian, kas, pelunasan, retur, stok, opname, penyusutan, dan lain-lain) kini terisi dari No. Referensi
  dokumen asalnya, mis. nomor closing `CLS/…` pada Stok Opname buatan Closing Harian. Mengubah No. Referensi di dokumen ikut mengubah jurnalnya. Jurnal lama dilengkapi otomatis saat
  aplikasi diperbarui. Kolom **Keterangan** dan jurnal manual tidak berubah.
- **Opname Harian**: tombol Cetak di form dokumen yang menghasilkan Laporan Persediaan (struk, setelah Release) diberi nama **Laporan Persediaan ▾**
  supaya tidak tertukar dengan lembar hitung.

### Perlu diperhatikan
- Migrasi database (`JurnalNoReferensi`): hanya mengisi kolom No. Referensi jurnal otomatis lama dari dokumen asalnya (satu perintah, tanpa kolom atau tabel baru).
- Tombol **Pemetaan & Kas ▾** di form closing kini bernama **Pemetaan ▾** (di tab Penjualan); pintasan Atur kas outlet pindah ke tab Kas.

## 1.0.59 (7 November 2026)

### Perbaikan
- **Installer**: gagal memasang di sebagian Windows 7 dengan pesan "Pemasangan file gagal: 11". Installer kini membawa pengekstrak 7-Zip sendiri
  (7za.exe, ikut tertanam di PilarErp-Setup.exe, bukan di folder aplikasi). Cukup unduh installer baru; PC yang sudah terpasang tidak terpengaruh.

## 1.0.58 (7 November 2026)

### Baru
- **Sistem › Data › Ekspor & Backup**: Paket Ekspor = salinan data **seluruh perusahaan** atau **satu / beberapa cabang** dalam satu berkas `.pilarpkg`,
  terenkripsi kata sandi paket (minimal 12 karakter). Dibuat di server sebagai pekerjaan latar dari satu potret data (kasir tetap bisa bekerja), lalu
  langsung diperiksa (SHA-256 & jumlah baris tiap tabel, rujukan, debit = kredit, saldo stok = mutasi) sebelum berstatus **Terverifikasi**.
- Paket cabang hanya berisi data cabang itu + master perusahaan lengkap; dokumen yang menyambung ke cabang / perusahaan lain (transfer, pelunasan,
  retur, grup usaha) ikut sebagai rujukan (id + nomor) dan tercantum di peringatan. Pilihan **Mulai tanggal**, **Excel ringkas**, **Log aktivitas**, **Log login**.
- Riwayat paket: **Unduh…**, **Periksa…**, **Buka Isi…** (salinan tanpa enkripsi untuk akuntan / auditor), **Periksa Berkas…** (paket di PC), **Hapus**.
- **Jadwal Otomatis** (admin perusahaan): paket seluruh perusahaan harian / mingguan / bulanan dengan masa simpan di server; paket jadwal ikut
  disalin backup harian server ke Google Drive / Object Storage penyedia.
- Tombol **Simpan Salinan Dulu** di **Bersihkan Data** dan **Tutup Periode**.
- Dasbor admin › **Backup** › **Paket per perusahaan**: jadwal, paket terakhir, status, ukuran, dan **Ekspor sekarang** atas permintaan perusahaan.
- **Penjualan › Daftar Harga Jual**: harga jual per kanal (mis. GoFood = Harga Dasar + 15%, dibulatkan ke 500), konsumen (grosir / reseller), cabang, dan
  periode, termasuk harga bertingkat menurut qty (mis. beli 12 lebih murah). Alat untuk mengisi dari Harga Dasar ± %, menyalin dari daftar lain, menaikkan /
  menurunkan harga sekaligus, import dan ekspor Excel; baris di bawah HPP ditandai.
- **Kasir** dan **Faktur Penjualan**: pilihan **Harga** (Kasir: tombol F8). Faktur otomatis memakai daftar konsumen, lalu daftar bawaan cabang; harga
  baris mengikuti daftar dan qty tanpa diketik. Daftar bertanda *Boleh dipilih* bisa dipilih kasir tanpa hak khusus.
- **Konsumen** (isian Daftar Harga) dan **Cabang** (Daftar Harga Jual Bawaan): memasang daftar harga.
- **Laporan Master › Daftar Harga**: isi daftar harga dengan Harga Dasar, selisih, HPP, dan margin. Filter **Daftar Harga** di Laporan Penjualan dan
  Harga Jual vs Harga Daftar (juga kolomnya), analisa Kepatuhan Harga Jual **Per Daftar Harga**.
- **Import Data › Daftar Harga Jual**, kolom **Daftar Harga** di import Konsumen dan Faktur Penjualan.
- **Kas & Bank › Biaya › Biaya Dibayar di Muka**: sewa setahun, premi asuransi, lisensi tahunan yang dibayar sekali dicatat sebagai aset lalu dibebankan
  rata tiap bulan. Asal: dibayar kas / bank, dari tagihan supplier (dibayar lewat **Pembayaran Utang**, ikut laporan utang & jatuh tempo), atau saldo
  awal / sudah tercatat (tanpa jurnal, dengan yang sudah dibebankan). Form menampilkan jadwal per bulan (beban, sudah dibebankan, sisa, status).
- **Kas & Bank › Biaya › Amortisasi**: satu dokumen pembebanan per cabang per bulan (AM/…), diposting berurutan, **Posting s/d bulan ini** untuk
  bulan yang tertinggal, batal hanya bulan terakhir. Mesinnya sama dengan Penyusutan: 10.000.000 / 12 bulan = 833.333, 833.334, 833.333, … tepat
  10.000.000.
- **Hentikan** di form Biaya Dibayar di Muka (kontrak putus / pindah tempat): sisa dibebankan sekaligus pada bulan pilihan, ke akun beban atau akun lain
  (mis. Piutang Lain-lain bila uang sewa dikembalikan); bisa dibatalkan selama amortisasi bulan itu belum diposting.
- **Tutup Periode** memposting amortisasi bulan itu yang belum diposting (tampil di pratinjau dan laba rugi sebelum jurnal penutup); buka kembali
  membatalkannya. Akun yang nonaktif = **Blokir**. Pemeriksaan baru **Biaya dibayar di muka sama dengan buku besar** (peringatan bila sisa per akun beda
  dengan saldo akunnya).
- **Menu Laporan › Laporan Biaya › Biaya Dibayar di Muka** per tanggal: rinci, rekap per akun / cabang, dan dibanding buku besar.
- Tutorial baru **Biaya Dibayar di Muka** dan **Amortisasi**.
- **Laporan › Menu Laporan › Laporan Penjualan › Laporan Closing**: closing harian satu outlet pada satu tanggal, dengan angka yang sama dengan layar Penjualan › Closing Harian.
  Pilihan laporan: Ringkasan (status, penjualan, pembayaran per akun, kas, stok, dokumen Tutup Hari, peringatan), Opname Harian (urut nilai selisih terbesar, termasuk mutasi
  sesudah hitung), Item Belum Dihitung, Pergerakan Stok, dan Pergerakan per Item. Bisa diekspor ke Excel dan dicetak; tombol **Cetak Closing ▾** mencetak Closing Harian
  Lengkap / Ringkas (A4 mendatar) atau Laporan Persediaan (thermal) untuk outlet mana pun yang boleh Anda lihat, tanpa pindah cabang.
- **Laporan › Menu Laporan › Laporan Persediaan › Selisih Stok Harian per Item**: dari closing yang sudah ditutup dalam rentang tanggal, item mana yang paling sering dan paling
  besar selisih opname hariannya per outlet (hari dihitung, hari selisih, lebih / kurang, selisih bersih dan terbesar, nilai HPP dan harga jual), untuk memeriksa resep yang salah
  atau barang hilang. Pilihan Rinci per Tanggal; klik dua kali baris membuka rincian item atau Laporan Closing hari itu.
- **Persediaan › Moving Index › Buat Daftar Opname**: dari kelas yang tampil (satu cabang, dengan filter kelas, tipe, kategori, supplier terakhir, dan cari yang sama),
  Daftar Opname baru terbuka dan dialog Generate langsung berisi kandidatnya.
- **Persediaan › Koreksi Stok › Daftar Opname › Generate…**: sumber baru **Kelas** Moving Index (centang satu atau beberapa kelas, boleh digabung dengan Tipe, Rak, dan cari)
  dan kolom **Kelas** di pratinjau, mis. daftar "Cepat laku" (Very Fast + Fast) dan "Stok diam" (Very Slow + Dead).
- **Penjualan › Closing Harian › Atur… › Frekuensi opname mengikuti Moving Index** (per cabang, bawaan mati): frekuensi wajib opname tiap item mengikuti kelasnya.
  Bawaan: Very Fast Mingguan, Fast 2 Mingguan, Medium Bulanan, Slow 3 Bulanan, Very Slow dan Dead 6 Bulanan, Baru Bulanan; tiap kelas bisa diubah. Item kelas ABC A
  naik satu tingkat (bisa dimatikan), yang paling sering menang atas isian Wajib opname di Master Item, dan jatuh tempo pertama disebar sepanjang satu siklus supaya
  Tutup Hari tidak terhalang ratusan item sekaligus. Tombol **Perkiraan beban** menampilkan rata-rata item yang harus dihitung per hari dan per minggu sebelum disimpan.
- **Master Item › Wajib opname** dan **Import Item › Wajib Opname**: pilihan baru **Mingguan** dan **2 Mingguan**.
- **Penerimaan Piutang** dan **Pembayaran Utang**: tab baru **Potongan & biaya** untuk selisih antara uang yang benar-benar masuk / keluar dan nilai faktur: PPh dipotong
  konsumen atau kita potong dari vendor, biaya admin bank, klaim, DP yang dipotongkan, denda, penghapusan piutang. Uang diterima / dibayar = nilai dokumen + pembulatan −
  potongan + biaya; tiap baris dijurnal ke akunnya. TOTAL BAYAR boleh 0 (penghapusan piutang, tanpa baris kas) bila semua selisih dijelaskan baris potongan. Isian
  **Uang di rekening** (opsional) dibandingkan dengan TOTAL BAYAR: selisih yang belum dijelaskan tampil merah dan tombol **Jadikan baris** membuatnya jadi baris potongan.
  Daftar pelunasan punya kolom **Potongan**; rincian pembayaran sebuah faktur menampilkan potongan yang dikenakan ke faktur itu.
- **Sistem › Master Pendukung › Jenis Potongan**: master jenis potongan (akun lawan, arah terhadap uang, dokumen pajak). Sebelas jenis bawaan dibuat sekali untuk setiap
  perusahaan: Biaya admin bank, PPh 23, PPh final 4(2), PPh final UMKM, PPh 22, PPN dipungut, Klaim, DP, Denda, Penghapusan piutang, Lainnya. Pembulatan tetap isian sendiri.
- **Laporan › Pajak** (hak baru **Pajak**): **Bukti Potong Diterima** (PPh yang dipotong konsumen, mana yang bukti potongnya belum diterima, rekap per masa) dan
  **Bukti Potong Dibuat** (PPh yang kita potong: bukti potong yang belum terbit, rekap potong & setor per masa dengan batas setor). Nomor & tanggal bukti potong diisi dari
  laporan (klik dua kali, atau pilih beberapa baris lalu Enter); tidak memposting ulang jurnal, boleh setelah periode ditutup, dan tercatat di Log Aktivitas.
- **Tutup Periode**: dua peringatan baru (bukan blokir): PPh dipotong konsumen yang bukti potongnya masih kosong lebih dari 30 hari, dan bukti potong yang kita terbitkan
  untuk bulan itu yang nomornya belum diisi.
- **Import Data › Penerimaan Piutang / Pembayaran Utang**: kolom baru **Jenis Potongan**, **Potongan**, **No Bukti Potong**, **Tgl Bukti Potong** (potongan kedua di baris
  tambahan tanpa Jumlah); sheet **Daftar Jenis Potongan** di template.
- **Akun (COA) › Template**: akun baru **2-1160 Utang PPh 4(2)** dan **4-1310 Potongan / Klaim Penjualan** (kontra pendapatan).
- **Pembelian › Daftar Harga Beli**: harga kesepakatan per supplier dengan periode, cabang, dan tingkat qty (mis. beli 12 lebih murah), plus kode barang di supplier.
  Daftar yang akan berakhir dalam 14 hari ditandai *Segera berakhir*. Alat untuk menyalin daftar periode lalu dengan ± % (harga Maret naik 3% untuk April),
  mengisi dari harga beli terakhir, menaikkan / menurunkan harga sekaligus, import dan ekspor Excel.
- **Pembelian**: setelah supplier dipilih, **Harga Beli** baris terisi harga kesepakatan (kolom baru **Harga Kesepakatan**); mengganti supplier, tanggal, satuan, atau
  qty menghitung ulang baris yang harganya tidak diketik sendiri. Harga yang beda dari kesepakatan berwarna oranye dan ditanya sebelum simpan (hanya peringatan).
  Jabatan tanpa hak melihat harga tetap mendapat harga otomatis dari kesepakatan, tanpa melihat angkanya.
- **Pengaturan Perusahaan › Pembelian › Beda dari harga kesepakatan**: pengingat aktif / mati dan toleransi %.
- **Laporan Pembelian › Harga Beli vs Kesepakatan** (per item dan detail transaksi) dan analisa **Pembelian › Perbandingan Supplier** (supplier termurah per item,
  selisih dari yang termurah). **Laporan Master › Daftar Harga** kini memuat daftar beli (dengan supplier) bagi yang boleh melihat harga pokok.
- **Import Data › Pembelian › Daftar Harga Beli**.
- **Faktur Penjualan › Cabang tujuan**: jual ke perusahaan satu grup usaha kini memilih cabang pembeli yang dituju. Hanya cabang itu yang melihat faktur
  di Pembelian › Import dari › Faktur dari perusahaan grup. Wajib dipilih bila pembeli punya lebih dari satu cabang yang boleh beli; pembeli satu
  cabang terisi otomatis; faktur dari Pesanan Masuk memakai cabang pemesan. Kolom **Kirim Grup** di daftar menyebut cabang tujuannya.
- **Pembelian › Import dari › Faktur dari perusahaan grup**: kolom **Catatan** (keterangan header penjual) dan **Cabang Tujuan**, serta isi faktur
  baris demi baris di bawah daftar (kode & nama item penjual, qty, harga, masalah tiap item).

### Perbaikan
- **Pembelian › Terima dari grup**: catatan yang diketik penjual di header faktur kini ikut tampil di jendela pilih dan masuk ke Catatan faktur
  pembelian (sebelumnya hilang, sehingga cabang tujuan tidak diketahui).
- **Akuntansi › Jurnal**: keterangan baris jurnal kini muat sampai 500 huruf (sebelumnya 200), sama dengan catatan baris dokumen sumber. Import Quinos dan dokumen dengan catatan baris panjang tidak lagi gagal tersimpan dengan pesan "value too long".

### Perlu diperhatikan
- Hak baru **Ekspor & Backup** (Sistem: Lihat / Buat / Hapus). Hanya jabatan bawaan **Akunting** yang otomatis mendapat Lihat + Buat (cabang yang boleh
  diaksesnya); jabatan lain diatur admin di Jabatan & Hak Akses. Paket seluruh perusahaan dan jadwal hanya untuk admin perusahaan.
- Paket tidak membawa hash kata sandi user, rahasia 2FA, kata sandi SMTP / Quinos, dan token sesi. Kata sandi SMTP tidak lagi dicatat di log aktivitas.
- Memulihkan data dari paket belum tersedia (menyusul); paket tidak menggantikan backup database server.
- Server: folder baru `/var/lib/pilar-erp/exports` (milik user API, 700) dan variabel `Export__Dir` dipasang `setup.sh`; sandbox API boleh menulis folder
  itu. Jalankan ulang `setup.sh` saat rilis. Migrasi database `PaketEkspor` (tabel baru `export_jobs` dan `export_schedules`).
- Fitur bawaan **mati**: nyalakan di **Pengaturan Perusahaan › Fitur › Daftar Harga**. Selama mati, harga tetap seperti sebelumnya.
- Harga daftar, pengingat beda harga, dan pemeriksaan hak Ubah Harga memakai daftar harga faktur, bukan selalu Harga Dasar. Memakai daftar yang tidak
  bertanda *Boleh dipilih* (atau Harga Dasar padahal ada daftar otomatis) butuh hak Ubah Harga & Potongan atau persetujuan atasan.
- Jabatan yang boleh mengubah master Item otomatis mendapat hak Daftar Harga Jual; laporan Daftar Harga untuk jabatan yang boleh melihat Laba Jual.
- Komputer kasir dan komputer pembelian perlu diperbarui ke versi ini sebelum fitur dinyalakan, supaya harga di layar sama dengan hitungan server.
- Hak baru **Biaya Dibayar di Muka**, **Amortisasi** dan laporan **Biaya Dibayar di Muka**: jabatan Akunting mendapatnya; jabatan lama yang boleh membuat
  Kas Keluar mendapat kedua menu sekali saat pembaruan, laporannya untuk jabatan yang boleh melihat Neraca.
- Biaya dibayar di muka yang dulu dicatat lewat Kas Keluar / Jurnal Umum ke 1-1530 bisa didaftarkan dengan asal **Saldo awal / sudah tercatat** supaya
  ikut dibebankan otomatis.
- Hak baru **Laporan Closing** dan **Selisih Stok Harian per Item** (Jabatan & Hak Akses › Laporan). Jabatan yang sudah boleh melihat Closing Harian otomatis mendapatnya.
  Hak laporan ini cukup untuk melihat stok sistem dan selisih semua outlet jabatan itu tanpa hak menu Closing Harian; nilai HPP tetap butuh hak Lihat harga pokok di laporan.
- Mencetak Laporan Closing kini boleh dengan hak Laporan Closing + Cetak Penjualan (sebelumnya hanya Closing Harian + Cetak Penjualan).
- Menyalakan frekuensi opname menurut kelas butuh hitungan Moving Index untuk cabang itu (buka menu Moving Index atau Hitung Ulang dulu). Item yang jatuh tempo tetap
  menghalangi Tutup Hari seperti Wajib opname biasa, jadi lihat **Perkiraan beban** sebelum menyalakannya.
- Cabang yang belum menyalakan setelan itu tidak berubah. Halaman web `/outlet/` (tab Atur) tidak mengubah setelan baru ini.
- Perusahaan yang dibuat sebelum ini belum punya kedua akun baru (dan mungkin akun PPh sektor lain): jenis potongan yang akunnya belum ada ditandai di kolom **Perhatian**
  dan belum bisa dipakai sampai akunnya diisi. Impor akunnya lewat **Akun (COA) › Template…**, lalu pilih di **Jenis Potongan**.
- Jabatan yang punya hak **Jenis PPN** otomatis mendapat hak **Jenis Potongan** yang sama; jabatan yang boleh melihat **Neraca** otomatis mendapat hak laporan **Pajak**.
- Kolom **No Faktur** dan **Jumlah** di template import pelunasan tidak lagi bertanda wajib karena baris potongan tambahan boleh tanpa keduanya; baris faktur biasa tetap
  harus mengisi keduanya (kesalahannya tetap ditunjuk per baris).
- Fitur **Daftar Harga Jual** di **Pengaturan Perusahaan › Fitur** kini bernama **Daftar Harga (jual & beli)**: satu centang untuk keduanya.
- Lembar data import daftar harga jual dan beli bernama **Harga Jual** / **Harga Beli**: unduh template baru bila Anda menyimpan template lama.
- Jabatan yang boleh membuat Pembelian otomatis mendapat hak Daftar Harga Beli; laporan Harga Beli vs Kesepakatan untuk jabatan yang boleh melihat Laba Jual.
- Faktur penjualan grup yang sudah ada tidak punya cabang tujuan: tetap muncul di semua cabang pembeli, seperti sebelumnya. Penjual yang mengubah faktur
  lama boleh memilih tujuannya; mengubah tanpa memilih tidak menghapus tujuan yang sudah ada.
- Klien Pilar ERP versi lama tidak bisa memilih cabang tujuan: membuat faktur grup baru ke pembeli beberapa cabang dari klien lama ditolak dengan
  pesan "Pilih cabang tujuan". Perbarui aplikasi dulu.

## 1.0.57 (7 November 2026)

### Perbaikan
- **Penjualan › Closing Harian**: closing yang dibuka kembali tidak lagi menampilkan selisih stok palsu. Stok Opname hasil Tutup Hari yang dibatalkan oleh Buka Kembali
  tadinya terbaca sebagai "mutasi sesudah jam hitung", sehingga tiap item berselisih sebesar opname lama (muncul juga di Laporan Persediaan Harian) dan Tutup Hari ulang
  memposting selisih itu ke stok lagi. Kini dokumen yang dibatalkan atau dihapus impas dengan pembaliknya.

## 1.0.56 (7 November 2026)

### Perbaikan
- **Integrasi Quinos › Import (Harian)**: hari dengan banyak catatan baris (diskon item, struk tarif lain) tidak lagi gagal disimpan karena "value too long for type character varying(200)". Catatan baris faktur harian tidak lagi memuat daftar nomor struk (sudah ada di No. Referensi faktur), dan memo baris jurnal dibatasi 200 huruf.

## 1.0.55 (7 November 2026)

### Baru
- **Pembelian › Pembayaran Utang** dan **Penjualan › Penerimaan Piutang**: tombol **Ribuan** / **Ratusan** di baris **Bulatkan** (panel kanan) mengisi
  **Pembulatan** otomatis supaya **Total Bayar** bulat ke ribuan / ratusan terdekat. Contoh: tagihan Rp 1.668.420 → klik **Ribuan** → Pembulatan −420,
  Total Bayar Rp 1.668.000. Pembulatan tetap bisa diubah sesudahnya.
- **Sistem › Import Data › Pembayaran Utang** dan **Penerimaan Piutang**: kolom baru **Pembulatan** (opsional, cukup diisi di baris pertama tiap
  No Bukti) dengan aturan yang sama dengan isian di form. Uang yang dibayar / diterima = jumlah faktur + pembulatan, faktur tetap **Lunas**, dan
  selisihnya ke akun **Selisih Pembulatan**. File lama tanpa kolom ini tetap bisa dipakai (pembulatan 0).
- **Persediaan › Item › tab Harga & Satuan › Harga perkiraan**: bahan yang belum pernah dibeli dan belum punya stok awal kini bisa diberi harga
  perkiraan per satuan dasar. Selama HPP rata-rata bahan masih 0, tab **Resep** memakai harga perkiraan itu untuk **Est. HPP** dan **margin** menu,
  dengan catatan abu-abu "PERKIRAAN" dan keterangan "(perkiraan)" di panel HPP & Margin. Begitu bahan dibeli atau diberi stok awal, HPP sebenarnya yang
  dipakai. Harga perkiraan hanya untuk melihat angka: tidak masuk stok, jurnal, HPP penjualan, maupun laporan. Hanya untuk item ber-stok (Bahan, Dagang,
  Produksi) dan jabatan dengan hak **Lihat Harga Modal di Pembelian & Item**.
- **Sistem › Import Data › Item**: kolom baru **Harga Perkiraan** (kosong = tidak diubah); ikut terisi di sheet Daftar Item template untuk jabatan yang
  berhak.
- **Akuntansi › Akun (COA)**: akun Kas/Bank punya isian **Wajib sebelum Tutup Periode** (Tidak / Saldo saja / Saldo + Rekonsiliasi Selesai) dan **Wajib mulai bulan**
  (terisi bulan berjalan saat dinyalakan, bisa diubah). Bawaannya Tidak; kolom **Wajib Rekonsiliasi** tampil di daftar akun. Saldo + Rekonsiliasi hanya bisa dipilih untuk
  akun yang sudah punya mutasi rekening koran hasil import.
- **Kunci & Tutup Buku › Tutup Periode**: akun yang diwajibkan diperiksa sendiri-sendiri (**Rekening koran wajib: …**). Saldo Rekening Koran yang belum diisi atau
  selisih tanpa penjelasan, dan untuk Saldo + Rekonsiliasi juga Rekonsiliasi Bank yang belum **Selesai**, menjadi **Blokir** (bukan lagi Peringatan) mulai Wajib mulai bulan.
  Klik dua kali barisnya membuka Saldo Rekening Koran / Rekonsiliasi Bank bulan dan akun itu. Akun yang tidak diwajibkan tetap Peringatan seperti sebelumnya.
- **Abaikan sekali**: pemegang hak baru **Abaikan Syarat Rekening Koran (Tutup Periode)** bisa mengabaikan syarat satu akun untuk satu bulan (mis. rekening koran
  terlambat dari bank) lewat tombol **Abaikan sekali…** di Tutup Periode. Alasan wajib dan tercatat di Log Aktivitas; syarat akun dan bulan berikutnya tidak berubah;
  **Batalkan abaikan…** memberlakukannya lagi selama periode belum ditutup.
- **Saldo Rekening Koran**: kolom **Wajib Sebelum Tutup**; akun yang diwajibkan selalu perlu diisi (juga tanpa saldo dan mutasi, isi 0).
- **Import Data › Akun (COA)**: kolom **Wajib Rekonsiliasi** dan **Wajib Mulai Bulan** (mis. 11/2026).
- **Laporan › Laporan Kendaraan › Daftar Kendaraan**: daftar kendaraan per tanggal (rinci per kendaraan, rekap per jenis / cabang) dengan pemegang, no. rangka
  & mesin, harga perolehan, akumulasi, nilai buku Aset Tetap tertaut, biaya sampai tanggal itu, dan dokumen terdekat; bisa dicetak dan diekspor.
- **Laporan › Laporan Kendaraan › TCO per Kendaraan**: total biaya kepemilikan per kendaraan (operasional, pajak & asuransi, sewa & leasing, penyusutan),
  dalam satu periode atau sejak perolehan, beserta TCO per bulan.
- **Biaya per Kendaraan › Dibanding Buku Besar**: pemeriksaan otomatis per akun, biaya ber-kendaraan + tanpa kendaraan = mutasi akun di Buku Besar.
- **Kas & Bank › Biaya Rutin**: kolom **Kendaraan** per baris jadwal (cicilan leasing, asuransi, sewa per kendaraan); Kas Keluar, Tagihan Biaya, atau Jurnal
  Umum yang dicatat membawa kendaraannya.
- **Kendaraan › Dokumen Kendaraan**: tombol **Simpan & Catat Biaya** (dokumen baru / perpanjangan) dan **Catat Biaya** mencatat biaya perpanjangan STNK, pajak,
  KIR, atau premi asuransi sebagai Kas Keluar / Tagihan Biaya ber-kendaraan; nomornya tampil di kolom **Biaya Dicatat** dan tidak bisa tercatat dua kali.
- **Kendaraan › Kendaraan**: **Cetak Kartu** / **Cetak** di Kartu Kendaraan: Kartu Kendaraan A4 (identitas, pemegang & SIM, Aset Tetap, dokumen aktif,
  ringkasan biaya per kategori).
- **Akuntansi › Buku Besar**: kolom **Kendaraan** (no. polisi) di baris biaya kendaraan; klik no. polisinya membuka Kartu Kendaraan, kotak cari juga
  mencari no. polisi.
- **Sistem › Import Data**: kelompok **Kendaraan** dengan import **Pengemudi** dan **Kendaraan** dari Excel (dicocokkan lewat kode / no. polisi, merek &
  model baru dibuat otomatis).
- **Menu akun › Refresh Menu Akses** (klik nama Anda di kanan atas): menarik ulang semua hak akses, daftar cabang, dan pengaturan perusahaan (fitur yang
  dipakai, format angka, kunci layar, nama perusahaan) dari server tanpa keluar aplikasi. Menu disusun ulang, tab daftar yang sedang terbuka dibuat ulang
  supaya tombolnya (Baru, Ubah, Hapus, dan lainnya) mengikuti hak terbaru, dan tab yang haknya dicabut ditutup. Pesan hasilnya menyebut menu yang bertambah
  atau dicabut. Form dokumen yang sedang terbuka tidak disentuh, jadi isiannya aman.
- **Persediaan › Moving Index**: kelas pergerakan setiap item ber-stok di setiap cabang, Very Fast, Fast, Medium, Slow, Very Slow, dan Dead (ditambah
  Baru dan Tidak aktif), dari seberapa sering item keluar dalam 90 hari terakhir. Hari stok kosong tidak menurunkan kelas, transfer keluar ke outlet
  dihitung sebagai permintaan gudang, buangan Expired / Waste dan retur pembelian tidak dihitung. Tab **Ringkasan** menampilkan tabel cabang × kelas
  (jumlah item, % item, atau nilai stok) dengan grafik; klik dua kali angkanya untuk melihat itemnya. Tab **Rincian** memuat frekuensi, hari bergerak,
  hari stok kosong, rata-rata keluar per hari, hari persediaan, kelas ABC, dan supplier terakhir; klik dua kali membuka Kartu Stok item itu. Tab
  **Antar Cabang** menunjukkan stok mati yang bisa ditransfer ke cabang yang laku, dan tab **Perubahan** menunjukkan item yang naik / turun kelas.
  Kelas dihitung otomatis tiap tanggal 1 pukul 02.00 (bisa diatur Mingguan atau Manual saja) atau lewat tombol **Hitung Ulang**, dan riwayat tiap
  hitungan disimpan. **Kunci Kelas** menetapkan kelas secara manual (mis. parcel musiman, item promosi, bahan cadangan) dengan alasan dan batas tanggal.
- **Pengaturan Perusahaan › Persediaan › Moving Index**: jendela, ambang kelas, Hari Dead, masa item Baru, pembagi minimal, abaikan hari stok kosong, jadwal.
- **Master Item** (tab Item) dan **Kartu Stok** menampilkan kelas Moving Index item itu per cabang.

### Perbaikan
- **Persediaan › Item › tab Resep / Komponen**: bahan yang HPP-nya masih 0 di cabang aktif (belum dibeli atau belum diberi stok awal) kini diberi
  catatan merah "HPP 0" beserta nama bahannya dan petunjuk mengisinya lewat Pembelian, Saldo Awal Stok, atau Harga perkiraan. Sebelumnya Est. HPP
  menu diam-diam kurang tanpa penjelasan. Catatan tidak tampil untuk jabatan tanpa hak Lihat Harga Modal.
- **Tutorial › Item**: penjelasan dari mana HPP menu berasal, dengan contoh menu baru sebelum bahannya dibeli.
- **Import Data › Akun (COA)**: memperbarui akun Kas/Bank lewat import tidak lagi menghapus centang **Minta nomor kartu**.
- **Biaya Kendaraan Tanpa Kendaraan**: jurnal penutup (Tutup Buku) tidak lagi ikut dihitung sebagai biaya tanpa kendaraan.
- **Kendaraan › Kategori Biaya**: akun template kendaraan yang diimpor belakangan lewat **Akun (COA) › Template…** (mis. 6-1640 … 6-1990 di perusahaan
  lama) langsung terpetakan ke kategorinya.
- Perubahan **Fitur** perusahaan (Pengaturan Perusahaan) dan hak akses yang diberikan saat sebuah tab sudah terbuka kini bisa sampai ke PC lain tanpa login ulang,
  lewat **Refresh Menu Akses**. Sebelumnya menu atau tombol yang baru diberi hak kadang tidak muncul sampai user keluar dan masuk lagi.
- **Web /outlet/**: tab yang dibuka lagi keesokan harinya (mis. dipulihkan Chrome di HP) tidak lagi masih memegang tanggal kemarin, yang membuat isian **Hitung** terkunci atau halaman Stok kosong. Tanggal yang dibuka kini hanya diingat sampai hari kerja berganti; sesudahnya halaman mulai dari **Pilih tanggal**.
- **Opname Harian**: tanda **Terlambat** kini mengikuti **jam ganti hari** cabang, sama dengan aturan penolakan hitungan. Dokumen kemarin yang dihitung
  sesudah tengah malam tetapi sebelum jam ganti hari (bawaan 06.00) tidak lagi ditandai terlambat di dokumen, Closing Harian, dan Laporan Closing.
  Sebelumnya hitungan itu diterima walau batas hitung terlambat 0 dan layar PIC tidak memberi peringatan, tetapi barisnya tersimpan sebagai terlambat.

### Perlu diperhatikan
- **Riwayat** item menutup perubahan Harga perkiraan bagi jabatan tanpa hak Lihat Harga Modal di Pembelian & Item. **Koreksi Satuan Dasar**
  mengonversi harga perkiraan seperti harga jual (dikali isi).
- **Rekonsiliasi Bank**: untuk akun yang diwajibkan, mutasi dan bulan sebelum Wajib mulai bulan tidak lagi ikut daftar belum cocok dan tidak dihitung di aturan
  **Selesai berurutan**, jadi riwayat mutasi lama yang pernah di-import tidak menghalangi.
- Hak **Abaikan Syarat Rekening Koran** tidak diberikan otomatis ke jabatan mana pun (juga tidak ke Akunting); Admin selalu boleh. Atur di Jabatan & Hak Akses bila perlu.
- Kendaraan yang masih disebut jadwal Biaya Rutin tidak bisa dihapus sebelum kendaraannya dikosongkan di jadwal itu.
- Jabatan yang boleh melihat menu Kendaraan otomatis mendapat hak laporan baru **Daftar Kendaraan** dan **TCO per Kendaraan**.
- Hitungan yang tersimpan sebelum pembaruan ini tidak diubah: baris yang terlanjur bertanda terlambat tetap begitu. Koreksi stok sistem tidak berubah.
- Hak baru **Moving Index** (Lihat = menu, Ubah = Hitung Ulang & Kunci Kelas). Jabatan yang sudah boleh melihat analisa Stok Mati otomatis mendapat Lihat;
  nilai keluar & nilai stok tetap butuh hak Lihat harga pokok di laporan.
- Hitungan pertama dibuat saat menu Moving Index pertama kali dibuka sesudah pembaruan (tanggal hitung akhir bulan lalu).
- **Bersihkan Data** satu cabang ikut menghapus hasil hitung dan Kunci Kelas cabang itu.
- Migrasi database tata letak (`UrutanKolomGrupClosing`, `UrutanKolomTanpaDefault`): tabel `customers`, `closing_settings`, `sales`, `sale_lines`,
  dan `expense_bills` dibangun ulang supaya kolom yang ditambah belakangan (aturan harga grup, closing mundur, rujukan pesanan penjualan, akun utang
  tagihan biaya) berada sebelum kolom audit, dan nilai bawaan database yang tersisa di 60 kolom lain dibuang (nilai selalu diisi aplikasi). Hanya
  tata letak tabel yang berubah; data, index, dan relasi tetap. Update server pertama kali sedikit lebih lama, sebanding dengan jumlah faktur penjualan.
- Migrasi database lain di versi ini (berjalan otomatis saat server diperbarui): `HargaPerkiraan` (kolom `items.estimated_cost`, awal 0),
  `Kendaraan5` (kendaraan di baris Biaya Rutin, biaya tercatat di Dokumen Kendaraan), `SyaratRekonsiliasi` (syarat per akun di `accounts` dan tabel
  `bank_recon_waivers`), dan `MovingIndex` (tabel `moving_runs`, `moving_items`, `moving_locks`, serta pengaturan Moving Index di `company_settings`).

## 1.0.54 (6 November 2026)

### Baru
- **Pembelian › Pembayaran Utang** dan **Penjualan › Penerimaan Piutang**: sekarang bisa mencatat **Pembulatan** bila uang yang dibayar / diterima
  dibulatkan. Contoh: sembilan tagihan berjumlah Rp 1.668.420 dibayar Rp 1.668.000 → isi **Pembulatan** −420 di panel kanan. Semua tagihan tetap
  **Lunas**, dan selisih Rp 420 dibukukan otomatis ke akun **Selisih Pembulatan**. Panel kanan kini menampilkan **Nilai dokumen**, **Pembulatan**, dan
  **Total Bayar** (uang yang benar-benar keluar / masuk kas atau bank). Daftar pelunasan punya kolom **Pembulatan**.
- **Penjualan › Konsumen**: harga jual ke perusahaan satu grup usaha (konsumen `GRP-…`) kini bisa diatur per konsumen, tidak lagi selalu sama dengan
  harga modal. Admin membuka **Ubah** pada konsumen grup, memilih **Dasar Harga Jual**: **Harga modal (HPP) + markup** (mis. HPP + 5%) atau
  **Harga jual item − diskon** (mis. harga jual − 10%), lalu mengisi **Persen**. Harga faktur dihitung otomatis saat disimpan dan tidak pernah di
  bawah HPP, termasuk faktur dari Pesanan Masuk. Kolom baru **Harga Jual Grup** di daftar konsumen meringkas aturannya. Perusahaan pembeli tidak perlu
  mengatur apa pun.

### Perbaikan
- **Akuntansi › Jurnal Umum**: keterangan jurnal otomatis kini ikut memuat catatan dari dokumen asalnya, setelah nomor dokumen (mis.
  `Penjualan PJ/… · meja 5`), sehingga alasan transaksi langsung terbaca saat memeriksa jurnal. Berlaku untuk Penjualan, Pembelian, Retur, Item Masuk /
  Keluar, Transfer, Titipan, Pelunasan, Saldo Awal, Rakitan, Pecah Stok, dan Opname. Catatan per baris Penjualan / Pembelian juga muncul di **Memo**
  baris jurnal akun terkait (catatan beberapa baris yang masuk ke akun yang sama digabung). Hanya untuk dokumen yang disimpan atau diubah mulai versi
  ini; jurnal lama tidak berubah.
- **Sistem › Pengaturan Perusahaan**: blok **Contoh** (pembulatan, format angka, qty, jurnal, PPN, layanan / PB1) kini tampil rapi di kolom kanan, di
  samping isiannya, dengan pola angka sebelum → sesudah. Contoh berubah langsung saat pilihan diganti, jadi efek tiap pengaturan langsung terlihat. Di
  tab Penjualan dan Pembelian, contoh total, layanan / PB1, dan PPN kini satu blok. Bila jendela sempit, contoh pindah ke bawah isian dan tidak terpotong.

### Perlu diperhatikan
- **Total** pelunasan sekarang berarti uang yang benar-benar dibayar / diterima, sudah termasuk pembulatan. Angka ini yang dipakai laporan Kas & Bank,
  Closing Harian, dan Analisa. Pelunasan lama tidak berubah (pembulatannya 0).
- Konsumen grup yang sudah ada otomatis memakai **Harga modal (HPP) + 0%**, sama seperti sebelumnya, jadi harga faktur tidak berubah sampai Admin
  mengganti aturannya. Faktur lama tidak ikut berubah; faktur yang belum diterima pembeli dihitung ulang dengan aturan baru bila disimpan lagi.
- Potongan baris dan diskon faktur ke perusahaan grup tetap tidak bisa dipakai; untuk memberi potongan, pakai aturan **Harga jual item − diskon**.
- Faktur grup berdasar HPP tetap butuh hak **Lihat HPP / Harga Modal di Penjualan**; dasar **Harga jual item − diskon** tidak butuh hak itu.
- Dengan markup, penjual mencatat laba dan stok pembeli bernilai harga markup. Laporan laba gabungan grup belum ada, jadi laba antar perusahaan belum
  dieliminasi.
- Migrasi database (berjalan otomatis saat server diperbarui): kolom baru `rounding` di tabel `payments` (`PembulatanPelunasan`), serta
  `group_price_basis` dan `group_price_percent` di tabel `customers` (`HargaGrup`).

## 1.0.53 (6 November 2026)

### Baru
- **Web /outlet/**: halaman pertama sekarang **Pilih tanggal**. Pilih tanggal, tekan **Buka**, baru masuk ke halaman isian (PIC yang hanya berhak menghitung
  langsung ke Stok). Sesudah dibuka, tanggal terkunci dan hanya tampil sebagai label; tombol ‹ › dan kolom tanggal di bar atas dihapus. Untuk pindah tanggal,
  tekan **Ganti tanggal** di bawah halaman Hari ini. Tanggal yang sudah dibuka tidak hilang saat halaman dimuat ulang.
- **Closing Harian › Petakan yang belum**: kolom **Terdekat** menampilkan item Pilar yang namanya paling mirip dengan nama Quinos, dan tiga kandidat teratas
  tampil di bawah tabel untuk baris yang dipilih. Tombol **Pakai terdekat baris ini** mengisi satu baris, dan **Isi saran terdekat (≥ 80%)** mengisi semua baris
  kosong yang kemiripannya 80% ke atas dan jelas unggul dari kandidat kedua (kandidat kembar dan pilihan yang sudah Anda isi dilewati). Baru tersimpan setelah
  **Simpan**.

### Perbaikan
- **Closing Harian › Petakan yang belum**: kolom **Item Pilar** tidak lagi menyempit menjadi "K00 Bak…" saat dialog dibuka.
- **Web /outlet/ › Stok (Opname Harian)**: tampilan HP dibuat lebih ringkas. Tiap baris memuat nama dan kode item di kiri (lokasi stok tetap tampil bila ada)
  serta isian **Hitung** di kanan; keterangan wajib / terlambat / di luar daftar per baris dan hitungan "item wajib belum" di kepala dokumen tidak
  ditampilkan lagi.
- **Web /outlet/ › Stok**: filter Semua / Belum dihitung / Sudah dan kolom cari item menempel di bawah layar, tepat di atas menubar, sehingga terjangkau
  jempol saat daftar panjang digulir.
- **Web /outlet/ › Stok**: kalimat kemajuan di kepala dokumen tidak lagi menempel dengan kalimat sesudahnya.
- **Persediaan › Opname Harian**: baris di daftar dokumen kini berwarna menurut status: Draft teks abu-abu, Open kuning, Release hijau, Close hijau muda, dan
  Batal merah seperti dokumen batal di daftar lain. Sebelumnya semua baris tampil polos sehingga dokumen Batal sulit dibedakan.

### Perlu diperhatikan
- **Opname Harian › hak akses**: PIC (jabatan dengan hak **Opname Harian** tanpa **Closing Harian**) tidak lagi bisa membuka riwayat lama. Dokumen yang sudah
  Release / Close hanya terlihat dari hari ini sampai **batas hitung terlambat** (Closing Harian › Atur…); dokumen yang masih Open tetap terlihat. Di web
  /outlet/ pilihan tanggalnya ikut dibatasi, dan server menolak lewat jalan lain (desktop maupun web). Atasan dan admin (hak Closing Harian) tetap melihat
  semua tanggal.

## 1.0.52 (6 November 2026)

### Baru
- **Persediaan › Opname Harian › Cetak ▾**: dokumen yang sudah di-Release (atau Close) bisa mencetak **Laporan Persediaan** (struk 80 mm) yang formatnya sama dengan di
  Closing Harian, tetapi hanya memuat item di dokumen itu: awal, masuk, keluar, fisik, dan selisih. Kepala struk mencantumkan nomor dokumen dan nama daftarnya.
  Tombol tampil bagi yang punya hak Closing Harian dan Cetak Penjualan (selisih tidak ditampilkan kepada penghitung buta).
- **Closing Harian**: tombol **Pemetaan & Kas** membuka Daftar Pemetaan item, Integrasi Quinos (bila punya hak Quinos), dan Atur kas outlet tanpa keluar dari closing. Siapa pun yang boleh mengimpor (hak Buat Closing Harian) bisa memakai pemetaan dan pengaturan kas, tanpa hak tambahan.
- **Closing Harian › Atur…**: isian **Closing mundur (hari)**. Diisi N, maka import penjualan dan Tutup Hari untuk tanggal yang sudah lewat sampai N hari tidak lagi kena batas backdate jabatan (tanpa izin backdate / persetujuan atasan). 0 = ikut batas jabatan seperti sebelumnya. Hanya berlaku untuk closing; transaksi lain dan periode yang dikunci tidak berubah.
- **Closing Harian › Petakan yang belum**: item dan jenis pembayaran Quinos yang belum dipetakan bisa dipetakan langsung dari closing, tanpa membuka Integrasi Quinos. Setelah import berhenti karena pemetaan, form menawarkan memetakan sekarang lalu mengulang import. Dialog menampilkan saran item dan kemiripan nama (merah di bawah 50%) seperti Integrasi Quinos. Cukup hak Closing Harian (Buat); hak Quinos, Item, dan Akun tidak diminta.

### Perbaikan
- **Closing Harian › Import Penjualan**: PIC outlet tidak lagi ditolak "tidak punya hak Buat di menu Penerimaan & Saldo Awal Piutang". Import Quinos, termasuk import ulang (Update / Batalkan), cukup memakai hak Closing Harian.

### Perlu diperhatikan
- Migrasi database: kolom baru pengaturan closing (`ClosingMundur`).

## 1.0.51 (5 November 2026)

### Perbaikan
- **Closing Harian › Laporan Persediaan (thermal 80 mm)**: tiap item kini **satu baris** dengan kolom Aw, Ms, Kl, Fs, Sl sejajar di kanan nama; nama yang kepanjangan turun ke baris bawahnya.
  Judul kolom diulang di tiap halaman, dan di dalam kelompok nama ditulis ` - Abon Manis` tanpa kata pertamanya.

## 1.0.50 (5 November 2026)

### Baru
- **Closing Harian › Cetak ▾ › Laporan Persediaan (thermal 80 mm)**: struk khusus pergerakan stok hari closing. Per item: **Awal**, **Masuk**, **Keluar**, **Fisik** (hasil opname) dan **Selisih**.
  Masuk dan Keluar hanya mutasi yang berpengaruh: pembelian, transfer, retur, item masuk / keluar, rakitan, dan penjualan. Dokumen yang dibatalkan atau diubah tidak menggelembungkan angka,
  dan dokumen buatan Tutup Hari tidak dihitung. Memuat item closing dan item lain yang bergerak hari itu; item yang tidak dihitung tidak punya Fisik dan Selisih. Tanpa harga pokok.
  Item yang kata pertama namanya sama dikelompokkan di bawah satu judul (mis. ROTI › Abon Manis, Abon Parmesan); item yang kata pertamanya unik tidak dikelompokkan.
  Closing yang belum ditutup bertanda ** DRAFT ** di kepala struk.
- **Login & Pembaruan**: progres langkah dan rincian log kini tampil di samping (dua kolom), tidak lagi memanjang ke bawah. Namanya ditulis "Pilar Erp".

### Perbaikan
- Cetak Laporan Closing Lengkap: kolom Awal / Masuk / Keluar kini memakai efek bersih tiap dokumen, jadi dokumen yang dibatalkan atau diubah tidak membuat Masuk dan Keluar sama-sama membengkak.
- **Kode cabang**: selain huruf dan angka, kini boleh memakai tanda minus (mis. `TP-2`), asal tidak di awal atau akhir kode.

## 1.0.49 (5 November 2026)

### Baru
- **Penjualan › Closing Harian › Cetak ▾**: Laporan Closing bisa dicetak dari form closing dan dari daftar Closing Harian, satu kali cetak untuk semuanya: penjualan
  dan status import Quinos, pembayaran per akun, kas (seharusnya, fisik, selisih, setoran, pecahan uang), opname harian (stok awal, masuk, keluar, sistem, fisik,
  selisih, nilai selisih menurut harga jual), item belum dihitung, pergerakan stok hari itu, dokumen yang dibuat Tutup Hari, dan kotak tanda tangan.
  Dua template bawaan di **Sistem › Template Cetak**, keduanya **A4 mendatar** dan **tanpa harga pokok**: **Closing Harian Lengkap** (semua item, beberapa halaman,
  utama) dan **Closing Harian Ringkas** (satu halaman: hanya 6 item selisih terbesar, jumlah belum dihitung, pergerakan per jenis).
- Closing yang **belum ditutup** dicetak dengan watermark **DRAFT** dan catatan peringatan. Closing yang **sudah ditutup** dicetak dengan catatan final: ditutup oleh siapa dan
  kapan, angka dikunci, perubahan hanya lewat Buka Kembali, riwayat buka kembali bila ada, nomor dokumen sumber, dicetak oleh siapa, dan Halaman n dari N.
- **Template Cetak**: ukuran kertas baru **A4 mendatar**, dan satu dokumen cetak kini boleh memuat beberapa tabel berurutan (dipakai Laporan Closing; template buatan sendiri
  dari Duplikat atau Desain mengikutinya).

### Perlu diperhatikan
- Mencetak Laporan Closing butuh hak **Cetak Penjualan** dan **Closing Harian (Lihat)**. Jabatan yang hanya punya Hitung Stok Harian tidak bisa mencetaknya
  (laporan memuat stok sistem dan selisih). Beri hak **Cetak Penjualan** di Jabatan dan Hak Akses bagi atasan outlet yang belum memilikinya.

## 1.0.48 (5 November 2026)

### Baru
- **Cetak**: semua dokumen (A4, setengah A4, dot matrix, struk thermal) kini selalu mencetak "Jumlah Item" dan "Total Qty" di bawah tabel barang.
  Total harga tidak diulang di baris ini karena sudah ada di ringkasan total. Bukti Kas tanpa Total Qty. Field `TotalQty` kini juga tersedia di data cetak
  Stok Opname, Rakitan, dan Pecah Stok.
- **Sistem › Pengaturan Perusahaan**: setiap isian format angka, pembulatan, dan desimal (Tampilan nominal, pembulatan total / layanan & PB1 / PPN
  penjualan dan pembelian, Desimal qty, Pembulatan jurnal) kini menampilkan baris **Contoh** yang langsung berubah mengikuti pilihan, sebelum disimpan.

### Perbaikan
- **Penjualan › Closing Harian › Import Penjualan**: import ulang hari yang sudah pernah diimport (data Quinos berubah) tidak lagi gagal dengan
  "Alasan wajib diisi untuk Update / Batalkan": faktur lama dibatalkan dan diganti, alasannya diisi sistem di log aktivitas.
- **Closing Harian › Import Penjualan**: hasilnya tampil sebagai tabel (Tanggal / Struk, Item, Masalah, Pesan, Tindakan) dengan petunjuk sesuai error yang
  terjadi, bukan lagi kalimat umum "mis. item yang belum dipetakan". Web outlet (HP) ikut menampilkan tindakan per pesan.
- **Sistem › Integrasi Quinos**: tab **Pesan** mendapat kolom Tanggal / Struk, Item, Masalah, dan Tindakan.
- **Integrasi Quinos / Closing Harian**: harga dan diskon dari Quinos dipakai apa adanya. Import tidak lagi meminta hak Ubah Harga & Potongan, batas potongan
  (Pengaturan kebijakan), atau persetujuan atasan untuk diskon dan harga di bawah HPP, karena diskon sudah diputuskan di kasir Quinos.
- **Opname Harian**: kolom **Fisik** kini bisa diisi di desktop (sebelumnya sel tidak bisa diedit sama sekali). Hal yang sama diperbaiki di grid
  **Daftar Opname** (Item, Lokasi, Urutan) dan kolom **Pilih** di Generate.
- **Opname Harian**: kolom Wajib tidak ditampilkan lagi (semua item daftar wajib; yang belum dihitung tetap merah). Frekuensi dan Jatuh Tempo hanya muncul bila
  ada item berfrekuensi, Terlambat hanya bila ada hitungan terlambat.
- **Opname Harian**: semua item yang masuk daftar kini otomatis **wajib** dihitung sebelum Selesai hitung (Release), juga di cabang yang mencentang
  "Opname hanya dari Daftar Opname yang di-Generate". Sebelumnya item itu tampil "Tidak perlu" dan boleh dikosongkan begitu saja.
- **Opname Harian**: bila ada item wajib yang memang tidak sempat dihitung, Release bisa dilanjutkan dengan **alasan**; alasan dan jumlah item yang dilewati
  dicatat di Catatan dokumen.
- **Daftar Opname**: tombol **Simpan** kini bisa diklik (sebelumnya klik tidak berbuat apa-apa dan hanya F9 yang menyimpan).
- **Pengaturan Perusahaan**: kotak isian (GroupBox) dirapatkan, jarak antar kotak dan kotak centang lebih kecil sehingga muat lebih banyak tanpa menggulir.

## 1.0.47 (4 November 2026)

### Baru
- **Kas & Bank › Tagihan Biaya**: isian baru **Akun utang**. Dulu semua tagihan otomatis masuk ke Utang Usaha. Kini bawaannya tetap Utang Usaha, tetapi bisa diganti ke
  **Utang Lain-lain**, **Beban Yang Masih Harus Dibayar**, atau akun Kewajiban lain bila tagihannya bukan utang dagang (misalnya jasa dari perusahaan satu grup).
  Jurnal tagihan mengkredit akun itu. Daftar Tagihan Biaya punya kolom **Akun Utang**.
- **Pembelian › Pembayaran Utang**: tagihan biaya yang akun utangnya bukan Utang Usaha melunasi akun itu (debit akun tersebut, bukan Utang Usaha). Satu pembayaran boleh
  melunasi tagihan ke akun utang yang berbeda.
- **Kas & Bank › Biaya Rutin**: jadwal dengan hasil Tagihan Biaya punya isian **Akun utang** yang sama, dan tagihan yang dicatat darinya memakai akun itu.
- **Kas & Bank › Saldo Rekening Koran**: isi saldo akhir bulan tiap akun kas / bank menurut rekening koran (kas tunai: hasil hitung), lihat selisihnya dengan saldo buku
  semua cabang, dan beri penjelasan untuk selisih yang wajar. Bisa juga lewat **Import Data › Saldo Rekening Koran**. Bulan yang periodenya sudah ditutup terkunci.
- **Laporan Rekonsiliasi › Kas & Bank vs Rekening Koran**: saldo buku vs rekening koran per bulan dan per akun (12 bulan terakhir). **Ringkasan Rekonsiliasi** memuat satu baris
  *Kas & Bank (Rekening Koran)*.
- **Kunci & Tutup Buku**: pratinjau tutup periode memberi peringatan bila ada akun kas / bank yang saldo rekening korannya belum diisi atau selisih tanpa penjelasan.
- **Persediaan › Daftar Opname**: daftar item yang dihitung tiap hari, banyak per cabang, masing-masing dengan **PIC** (satu item satu daftar). Isi daftar
  lewat **Generate…** (Semua item, Tipe, Rak, cari, atau Tempel dari Excel) dengan pratinjau dan centang, atau manual.
- **Persediaan › Opname Harian**: dokumen hitungan per daftar per tanggal (nomor **OPH**). Atasan **Generate dokumen** lalu **Open**; PIC menghitung **buta**
  (stok sistem & selisih tidak pernah tampil), bisa **Tambah item** di luar daftar (penambahnya dicatat), lalu **Selesai hitung (Release)**. Atasan bisa
  **Buka Kembali** (Release → Open) atau **Batal** dokumen, keduanya dengan alasan. Juga di HP lewat **/outlet/** tab Stok.
- **Master Item › Wajib opname**: frekuensi Tidak perlu / Harian / Bulanan / 3 Bulanan / 6 Bulanan / Tahunan. Item berfrekuensi jatuh tempo sejak hitungan
  terakhirnya (Opname Harian atau Stok Opname) dan muncul di dokumen saat jatuh tempo. Import Item: kolom **Wajib Opname**.
- **Closing Harian › Atur…**: **Batas hitung terlambat** (bawaan 0 = hitungan sesudah tanggal pelaksanaan ditolak); hitungan terlambat ditandai dan stok
  sistemnya dikoreksi mutasi sampai jam hitung.
- **Import Data › Mutasi Rekening Koran**: tempel mutasi dari internet banking ke template (per akun kas / bank; baris SALDO AWAL dan kolom Saldo opsional). Saldo berjalan
  diperiksa, import ulang rentang yang sama mengganti (tidak menggandakan), dan saldo akhir bulan terisi otomatis di **Saldo Rekening Koran**.
- **Laporan Rekonsiliasi › Kas & Bank vs Rekening Koran**: pilihan baru **Per Hari** (mutasi dan saldo akhir hari menurut bank vs buku, dengan penanda hari pertama selisih)
  dan **Mutasi Rekening Koran** (daftar hasil import), dengan filter akun.
- **Rekonsiliasi Bank (server)**: mutasi rekening koran hasil import dicocokkan dengan baris jurnal akun kas / bank itu (semua cabang) per akun per bulan: saran otomatis
  (nominal sama, tanggal ±3 hari), satu mutasi ↔ banyak baris jurnal (setoran QRIS / EDC) dan sebaliknya, dua mutasi yang saling meniadakan, **Catat Selisih** (Kas Masuk / Kas Keluar
  otomatis untuk biaya admin, bunga, MDR) lalu cocok, **Selesai** per bulan secara **berurutan** (syarat: semua mutasi cocok dan saldo rekening koran cocok / dijelaskan) dan **Buka Kembali**
  (bulan Selesai terakhir, dengan alasan).
- Dokumen yang barisnya sudah dicocokkan tidak bisa dibatalkan, dihapus, atau diubah (faktur, kas, pelunasan, jurnal umum; juga bila baris kasnya tidak berubah) sampai pencocokannya dilepas.
  Bulan Selesai, dan bulan-bulan sebelumnya, juga mengunci import ulang mutasi dan perubahan Saldo Rekening Koran.
- **Kas & Bank › Rekonsiliasi Bank**: cocokkan mutasi rekening koran (hasil **Import Data › Mutasi Rekening Koran**) dengan baris jurnal akun kas / bank itu (semua cabang), per akun per bulan.
  Centang mutasi di kiri dan baris jurnal di kanan; jumlahnya sama → **Cocokkan** (satu mutasi boleh dengan banyak baris dan sebaliknya, misalnya satu setoran QRIS untuk beberapa hari penjualan).
- **Saran Otomatis** memasangkan mutasi dan baris jurnal yang nominalnya sama (tanggal berdekatan, referensi atau nama cocok); pasangan bisa diterima sebagian atau semua.
- **Catat Selisih…** membuat **Kas Masuk** / **Kas Keluar** sebesar selisih (biaya admin, bunga, potongan MDR, atau mutasi yang tidak punya pasangan) ke akun lawan pilihan Anda, lalu mencocokkan semuanya.
- **Klik dua kali** baris jurnal membuka dokumen asalnya (faktur, kas, pelunasan, jurnal umum, …) di cabang dokumen itu, seperti Buku Besar; kolom **No. Dokumen** menyebut nomornya.
- **Lepas Cocok** membatalkan pasangan yang salah. **Selesai** mengunci rekonsiliasi bulan itu bila semua syaratnya terpenuhi, **Buka Kembali** (alasan wajib) membukanya.
- Topik Tutorial baru **Rekonsiliasi Bank**; tombol **?** dan **F1** di layar ini membuka topiknya sendiri walau hak aksesnya sama dengan Saldo Rekening Koran.
- **Opname Harian › kolom Expired dan Waste**: PIC mencatat barang expired / rusak yang dibuang per item (desktop dan HP **/outlet/**), terpisah dari kolom
  Fisik. Saat **Tutup Hari**, closing membuat **Item Keluar** sendiri (satu untuk Expired, satu untuk Waste) dengan akun beban masing-masing, **sebelum**
  Stok Opname gabungan dibuat, jadi buangan tidak ikut terhitung sebagai selisih. Nomor Item Keluar tampil di Closing Harian; **Buka Kembali** closing
  menghapusnya bersama Stok Opname.
- **Closing Harian › Atur…**: **Akun Expired** dan **Akun Waste / Rusak** (akun beban lawan Item Keluar). Dikosongkan = kolomnya tidak muncul di layar hitung.
- **Closing Harian › Atur… › Opname hanya dari Daftar Opname yang di-Generate**: bila dicentang, frekuensi **Wajib opname** per item (Master Item) diabaikan di
  cabang itu. Tidak ada item yang otomatis jatuh tempo, wajib, atau menghalangi Tutup Hari; item dihitung hanya bila ada di Daftar Opname yang di-Generate
  menjadi dokumen, dan Release tidak lagi menolak item yang belum dihitung (cukup konfirmasi). Frekuensi di Master Item tidak berubah dan berlaku lagi bila
  pengaturan dimatikan.

### Perbaikan
- **Persediaan › Rekalkulasi Stok & HPP › Pemeriksaan**: item yang stoknya minus atau HPP-nya 0 saat barang keluar kini tampil **satu baris per item**, bukan satu baris
  per penjualan. Kolom **Baris** menunjukkan jumlah penjualan yang terdampak, dan keterangannya memuat rentang tanggal serta saldo terendah. Item yang paling banyak terdampak
  ada di atas. Dulu bahan yang pembeliannya tidak pernah dicatat menghasilkan ribuan baris untuk belasan item.
- **Closing Harian**: hasil hitung dan selisih diambil dari dokumen Opname Harian yang sudah Release; Tutup Hari membuat satu Stok Opname gabungan dan
  dokumennya menjadi Close. Form closing menampilkan status dokumen, pengingat item wajib yang belum punya dokumen, dan tombol Generate dokumen.
- **/outlet/**: pesan daftar kosong tidak lagi menunjuk menu yang tidak ada.
- **Bersihkan Data (semua cabang)** kini ikut membersihkan Saldo Rekening Koran dan mutasinya.

### Perlu diperhatikan
- Akun utang tidak bisa diganti setelah tagihan ada pembayarannya (pembayaran sudah mendebit akun itu). Sebelum dibayar boleh diganti dan jurnalnya ikut pindah.
- Tagihan ke akun selain Utang Usaha tetap tampil di laporan **Utang** per supplier, tetapi tidak dihitung di **Utang vs Neraca** dan pemeriksaan buku bantu saat Tutup Periode,
  karena perbandingan itu hanya untuk akun Utang Usaha. Saldo akun utang lainnya dilihat di **Buku Besar**. Tagihan yang sudah ada tidak berubah (tetap Utang Usaha).
- Ada migrasi database (kolom `payable_account_id` di tabel `expense_bills`).
- Laporan **Kas & Bank vs Neraca** diganti nama menjadi **Kas & Bank: Dokumen vs Jurnal** (isinya sama): laporan itu membandingkan angka Pilar ERP dengan dirinya sendiri,
  sedangkan pembandingnya untuk tutup bulan sekarang rekening koran.
- Menu baru: jabatan yang sudah boleh membuat Jurnal Umum otomatis mendapat hak **Saldo Rekening Koran**, dan jabatan yang boleh melihat Neraca mendapat laporan barunya.
  Menu ini butuh akses ke semua cabang karena saldo akun kas / bank dihitung semua cabang.
- Migrasi database: satu tabel baru (`bank_statements`).
- **Tutup Hari** sekarang ditolak selama ada dokumen Opname Harian **Draft / Open**, atau item wajib opname yang jatuh tempo tetapi belum dihitung.
- Daftar Hitung Harian lama tiap cabang dipindah menjadi Daftar Opname **Utama** (tanpa PIC), dan hitungan closing lama menjadi dokumen Opname Harian pindahan
  (nomor **OPH-** + nomor closing). Kolom Fisik di form Closing Harian desktop tidak lagi bisa diisi: hitung lewat Opname Harian.
- Hitungan dari HP versi lama yang masih tertahan di antrean (belum terkirim) dibuang saat halaman /outlet/ baru dibuka.
- Migrasi database: satu tabel baru (`bank_statement_lines`). Mutasi rekening koran bukan dokumen akuntansi: tidak ada jurnal dan tidak ikut kunci periode per cabang,
  tetapi import ke bulan yang periodenya sudah ditutup ditolak.
- Migrasi database: tiga tabel baru (`bank_match_groups`, `bank_matches`, `bank_reconciliations`).
- Periode akuntansi yang sudah ditutup tidak menghalangi pencocokan (sisa mutasi di bulan lama tetap bisa dirapikan); yang ditolak hanya dokumen kas baru, import mutasi, dan perubahan saldo.
- **Hapus Permanen** dan **Bersihkan Data** melepas pencocokan rekening koran yang menyentuh jurnal yang dihapus (mutasi bank tetap ada).
- Hanya user yang boleh mengakses semua cabang yang bisa memakai Rekonsiliasi Bank.
- Tidak ada hak akses baru: layar ini memakai hak menu **Saldo Rekening Koran**. **Catat Selisih…** juga butuh hak **Buat** di Kas Masuk (selisih positif) atau Kas Keluar (selisih negatif).
- Buangan mengikuti kebijakan stok minus perusahaan seperti Item Keluar biasa: bila stok minus dilarang dan buangan melebihi stok, Tutup Hari ditolak.
- Closing Harian ditolak bila ada buangan tetapi akun Expired / Waste-nya belum diatur.

## 1.0.46 (4 November 2026)

### Baru
- **Bantuan › Tutorial**: diagram alur dan urutan kini bisa **diperbesar, diperkecil, dan digeser**. **Ctrl + roda mouse** atau tombol **− / +** di atas diagram memberi zoom
  (20%–400%) di sekitar penunjuk; **seret** atau **Shift + roda mouse** menggeser; **klik dua kali** atau tombol **Pas** menampilkan seluruh diagram; tombol **100%**
  kembali ke ukuran asli. Tombol **Layar besar** membuka diagram di jendela sendiri (roda mouse langsung zoom, **+ −** zoom lewat keyboard, **0** memuat seluruh diagram,
  tombol panah menggeser, **Esc** menutup). Roda mouse tanpa Ctrl tetap menggulir halaman. Pintasannya tercatat di **Bantuan › Shortcut**.
- **Bantuan › Panduan › Tutorial**: topik baru untuk menu Sistem yang belum punya panduan: **Import Data**, **Integrasi Quinos**, **Daftar Pemetaan**,
  **Data Terhapus**, **Bersihkan Data**, dan **Admin Platform**, masing-masing berisi fungsi, langkah, alur, contoh kasus, aturan, dan hak akses.
- **Bantuan › Panduan › Tutorial**: 13 topik baru untuk menu Beranda (Dashboard, Tim, Ucapan & Berita), Tampilan (Mode Tab / Jendela,
  Susun Jendela, Ukuran Font, Warna Aplikasi, Switch UI), dan Bantuan (Tutorial, Shortcut, Periksa Pembaruan, Informasi Sistem, Riwayat Versi),
  masing-masing berisi fungsi, cara, alur, dan contoh kasus. Tombol **?** dan F1 di menu-menu itu membuka topiknya.
- **Bantuan › Tutorial**: sembilan topik baru untuk menu **Persediaan**: Kartu Stok, Item Masuk dan Item Keluar, Stok Opname, Permintaan Transfer, Pesanan Transfer,
  Transfer Keluar dan Transfer Masuk, Rakitan / Produksi (termasuk bongkar), Pecah Stok, dan Rekalkulasi Stok & HPP. Tiap topik berisi fungsi, langkah, diagram alur,
  contoh kasus dengan angka, aturan, dan hak akses. Dibuka dengan tombol **?** / **F1** di menu itu.
- **Bantuan › Panduan › Tutorial**: topik baru untuk **Kas Masuk**, **Kas Keluar**, **Transfer Kas**, **Jurnal Umum**, **Buku Besar**, **Saldo Awal Akun**,
  **Saldo Awal Stok**, dan **Kunci & Tutup Buku**. Tiap topik berisi fungsi, langkah, diagram alur, contoh kasus berangka dengan jurnalnya, aturan, dan hak akses.
  Tombol **?** atau F1 di menu itu membuka topiknya.
- **Bantuan › Panduan › Tutorial**: topik untuk menu Pembelian (**Pesanan Pembelian**, **Pembelian**, **Retur Pembelian**, **Saldo Awal Utang**) dan seluruh
  menu **Titipan** (**Titip Masuk**, **Retur ke Penitip**, **Setoran ke Penitip**, **Titip Keluar**, **Kembali dari Toko**, **Laku Titipan**, ditambah
  **Alur Titipan**). Tiap topik berisi fungsi, langkah, diagram alur, contoh kasus dengan angka, aturan, dan hak akses; buka dengan tombol ? atau F1.
- **Bantuan › Panduan › Tutorial**: topik untuk seluruh menu **Laporan** dan **Analisa**. Menu Laporan (cara membuka laporan, filter accordion, ekspor / cetak, hak akses dan hak lihat harga pokok),
  satu topik per grup laporan (Master, Pembelian, Penjualan, Utang, Piutang, Persediaan, Laba Jual, Kas & Bank, Buku Besar, Keuangan, Rekonsiliasi, Aset Tetap, Kendaraan, Sistem)
  dengan alur memilih laporan dan contoh kasus berangka, termasuk cara membaca dan menelusuri selisih di Laporan Rekonsiliasi. Analisa: topik pengantar dan satu topik per bagian
  (Ringkasan & Cabang, Penjualan, Laba & Harga, Persediaan, Pembelian, Keuangan, Operasional & Kontrol).

### Perbaikan
- **Bantuan › Tutorial**: diagram yang lebar tidak lagi dikecilkan mengikuti lebar jendela sampai teksnya tak terbaca. Di halaman, diagram tidak lebih kecil dari 80%; bagian yang
  melewati bingkai digeser, atau lihat utuh dengan **Pas**. Bingkai ikut meninggi saat diagram diperbesar.
- **Bantuan › Tutorial**: semua topik kini memakai susunan yang sama: **Fungsi** (menu ini untuk apa dan kapan dipakai), **Alur** (diagram gambaran
  besar), **Cara pakai** (langkah per tugas), dan **Contoh kasus**, lalu bagian rujukan seperti Isian, Aturan, dan Hak akses. Topik Tagihan Biaya,
  Pembayaran Utang, dan Biaya Rutin mendapat diagram alur dan contoh kasus; Jabatan & Hak Akses serta topik gambaran besar (Alur Penjualan, Alur
  Titipan, Alur Biaya Bulanan) mendapat langkah pemakaian.
- **HPP rata-rata** selalu dihitung 4 desimal. Dulu, bila desimal harga pokok diatur 0, sisa pembulatan ke rupiah utuh langsung dijurnal ke HPP
  (Penyesuaian nilai persediaan) saat pembelian, misalnya Beras 60.000 g @ 15,3667 tersimpan 15 dan 22.002 masuk HPP sebelum ada yang terjual.
- **Persediaan › Rekalkulasi Stok & HPP** tidak lagi membuat penyesuaian nilai persediaan karena HPP dibulatkan ke rupiah utuh: yang lama dibatalkan
  tanpa pengganti. Yang dibuat ulang hanya selisih nilai sungguhan (stok minus, retur/batal berharga tetap saat stok habis) dan sisa pembulatan 4 desimal
  bila mencapai Rp 1 per dokumen.
- **Laporan › Persediaan vs Neraca › Selisih per Dokumen**: selisih di bawah Rp 5 diberi keterangan "Pembulatan harga pokok", ditaruh paling bawah, dan
  tidak dihitung sebagai dokumen berselisih.

### Perlu diperhatikan
- **Pengaturan › Persediaan**: isian *Desimal harga pokok* dihapus.
- Perusahaan yang dulu memakai desimal harga pokok kurang dari 4 sebaiknya menjalankan **Rekalkulasi Stok & HPP** dari tanggal dokumen paling awal supaya
  penyesuaian nilai karena pembulatan hilang dan nilai persediaan kembali sesuai harga beli.

## 1.0.45 (3 November 2026)

### Baru
- **Bantuan › Panduan › Tutorial**: jendela bantuan kini bernama **Tutorial** dan punya tombol sendiri di menu **Bantuan › Panduan** (juga di Menu Classic
  dan kotak Cari menu). Tombol itu membuka daftar isi semua topik; tombol **?** di judul menu dan **F1** tetap langsung membuka topik menu itu.
- **Laporan › Laporan Rekonsiliasi › Ringkasan Rekonsiliasi**: semua pemeriksaan rekonsiliasi dalam satu laporan, dengan hasil **Cocok / Selisih** per
  pemeriksaan: Persediaan, Piutang Usaha, Utang Usaha, Utang Titipan, Titipan Belum Ditagih, Kas & Bank, Aset Tetap (harga perolehan dan akumulasi) vs
  Neraca, dan Dokumen vs Jurnal (temuan bulan berjalan). **Per Cabang** = keadaan per tanggal laporan; **Per Bulan (12 Bulan Terakhir)** = selisih tiap akhir
  bulan, untuk melihat sejak bulan apa selisih muncul. Kolom **Laporan Rinci** menyebut laporan yang merinci penyebabnya.
- **Laporan › Laporan Rekonsiliasi › Kas & Bank vs Neraca**: mutasi akun kas / bank menurut dokumen (penjualan dan pembelian yang dibayar di faktur,
  penerimaan dan pembayaran, kas masuk / keluar / transfer, refund retur, perolehan dan pelepasan aset) ditambah jurnal lain (jurnal umum, saldo awal akun)
  dibandingkan saldo di Neraca. Tiga pilihan: **Per Akun** (dengan saldo terendah di periode), **Saldo Minus** (rentang hari saat saldo kas / bank minus), dan
  **Selisih per Dokumen**.
- **Laporan › Laporan Rekonsiliasi › Aset Tetap vs Neraca**: harga perolehan dan akumulasi penyusutan menurut daftar Aset Tetap dibandingkan akun aset dan
  akumulasi di Neraca, per cabang. **Selisih per Dokumen** menunjuk jurnal perolehan, penyusutan, dan pelepasan yang nilainya beda, serta jurnal umum ke
  akun aset tanpa data asetnya. Aset **Sudah dijurnal** dicocokkan dengan jurnal sumbernya lewat no. sumber.
- **Tutorial Penjualan**: 9 topik baru di jendela bantuan (tombol **?** / **F1**), kelompok **Penjualan**: Alur Penjualan (mulai di sini), Kasir,
  Pesanan Penjualan, Faktur Penjualan, Pesanan Masuk, Retur Penjualan, Penerimaan Piutang, Saldo Awal Piutang, dan Closing Harian Outlet.
  Tiap topik berisi langkah, diagram alur, aturan yang berlaku, efek ke stok dan jurnal, serta contoh kasus resto, kafe, dan toko oleh-oleh.
- **Bantuan › Tutorial**: panduan lengkap semua menu Master, tiap topik berisi fungsi menu, isian, langkah, **contoh kasus**, dan **alur** (diagram): Item,
  Koreksi Satuan Dasar, Satuan, Rak, Konsumen, Promo, Supplier, Akun (COA) beserta Template, Aset Tetap, Kelompok Aset, Penyusutan, Pelepasan Aset,
  Kendaraan, Pengemudi, Merek & Model, Dokumen Kendaraan, Kategori Biaya, Pengaturan Perusahaan (9 tab), Cabang, User, Jabatan & Hak Akses, Izin Backdate,
  Pengaturan Cetak, Jenis PPN, Penomoran Dokumen, Template Cetak, dan Mulai Pakai. Buka dengan tombol **?** di judul menu atau **F1**.
- **Dialog master** (Supplier, Konsumen, Satuan, Rak, Jenis PPN, Cabang, User, Akun, Template Cetak) punya tombol **?** di samping tombol Simpan dan bisa
  dibuka dengan **F1**; **Akun (COA) › Template…** punya tombol **?** di bar atasnya.

### Perbaikan
- **Laporan**: tombol **?** tidak lagi tampil di **Menu Laporan**, **Analisa**, dan tab tiap laporan (sebelumnya membuka halaman "Belum ada panduan khusus").
  **F1** di tab laporan membuka daftar isi Tutorial.
- **Form dan dialog**: panel panduan di kanan form dihapus (Item, Akun, Template Akun, Cabang, Aset Tetap, Kelompok Aset, Ubah Estimasi, Penyusutan, Pelepasan
  Aset, Kendaraan, Pengemudi, Merek & Model, Dokumen Kendaraan, Catat Biaya, dan tiap tab Pengaturan Perusahaan). Isiannya jadi selebar form; isi panduannya
  pindah ke Tutorial. Penjelasan singkat per isian tetap ada sebagai tooltip.
- **Item**: panel HPP & Margin di kanan hanya tampil untuk item ber-resep / komponen; item lain memakai lebar penuh.

### Perlu diperhatikan
- Jabatan yang sudah boleh melihat Neraca otomatis mendapat hak tiga laporan baru ini. **Aset Tetap vs Neraca** hanya tampil bila fitur Aset Tetap dipakai.
- Di Ringkasan Rekonsiliasi, angka Persediaan hanya tampil bagi yang punya hak Lihat harga pokok (HPP); hasil Cocok / Selisih tetap tampil.
- Panduan yang dulu muncul di kanan form kini hanya ada di Tutorial (tombol **?** atau **F1**).

## 1.0.44 (3 November 2026)

### Baru
- **Kendaraan › biaya per kendaraan**: kolom **Kendaraan** (pilih no. polisi) di baris **Kas Keluar / Kas Masuk**, **Tagihan Biaya**, **Jurnal Umum**, dan **Pembelian**
  (hanya baris item Non-stok, mis. oli, ban, tol, parkir). Jurnalnya mencatat kendaraan di baris biayanya, jadi biaya tiap kendaraan bisa dipisahkan di buku besar.
  Kolom ini hanya tampil bila fitur Kendaraan dipakai dan jabatan Anda punya hak Kendaraan.
- **Persediaan › Item Keluar**: pilihan **Kendaraan** di kepala dokumen. Nilai barang yang keluar (mis. suku cadang) menjadi biaya kendaraan itu di **Akun lawan**
  (akun lawan wajib dipilih bila kendaraan diisi).
- **Aset Tetap › Penyusutan**: aset yang sudah ditautkan ke kendaraan dijurnal terpisah per kendaraan (total beban dan akumulasi penyusutan tetap sama).
- **Retur Pembelian** atas faktur yang berkendaraan mengkredit biaya ke kendaraan yang sama.
- Mengubah **hanya** kendaraan di baris dokumen memposting ulang jurnalnya, dan tercatat di Riwayat dengan no. polisinya.
- **Rekalkulasi HPP** mempertahankan kendaraan di jurnal Item Keluar.
- **Tombol Cetak ▾ di dalam dokumen**: menu yang punya tombol **Cetak** di daftarnya (Penjualan, Pembelian, Pesanan Pembelian, Retur, Kas, Stok Opname, Rakitan, Pecah Stok,
  Item Masuk / Keluar, Transfer, Titipan) kini punya tombol **Cetak ▾** juga di baris judul dokumen yang dibuka dengan **Lihat** (atau Ubah), di samping Ubah / Simpan / Tutup.
  Pilihan template dan hak cetaknya sama dengan di daftar. Dokumen yang isiannya belum disimpan diminta disimpan dulu. Tombol ini tidak ada di dokumen baru.
- **Penjualan › Kasir › Daftar › Detail**: jendela Detail (header dan baris) kini punya tombol **Cetak ▾** untuk mencetak dokumen yang sedang dilihat.
- **Kendaraan › Kartu Kendaraan** (tombol **Kartu** atau klik dua kali kendaraan di daftar): biaya kendaraan per kategori (bulan ini, 12 bulan, sejak awal), nilai buku bila tertaut Aset Tetap,
  dokumennya, dan baris biayanya. Klik dua kali baris biaya membuka dokumen asalnya (Kas Keluar, Tagihan Biaya, Jurnal, …). Angkanya sama dengan Buku Besar.
- **Kendaraan › Catat Biaya** (dari Kartu atau daftar kendaraan): pintasan mencatat BBM, servis, tol, pajak, dan sejenisnya untuk satu kendaraan. Dibayar sekarang membuat **Kas Keluar**,
  utang ke supplier membuat **Tagihan Biaya**, keduanya dengan kolom Kendaraan terisi.
- **Kendaraan › Kategori Biaya**: akun beban mana yang dihitung sebagai biaya kendaraan dan masuk kategori apa (BBM & pelumas, servis & perawatan, suku cadang & ban, tol & parkir, pajak & STNK,
  asuransi, sewa & bunga leasing, denda & tilang, penyusutan). Pemetaan awal terisi dari akun template.
- **Laporan › Laporan Kendaraan**: **Biaya per Kendaraan** (rekap per kendaraan, per kategori, rinci per jurnal) dan **Biaya Kendaraan Tanpa Kendaraan** (biaya di akun kendaraan yang kolom
  Kendaraannya masih kosong, supaya bisa dilengkapi di dokumen asalnya).
- **Akun (COA)**: akun template baru untuk perusahaan baru: 6-1640 Beban BBM & Pelumas Kendaraan, 6-1650 Servis & Perawatan Kendaraan, 6-1660 Suku Cadang & Ban Kendaraan,
  6-1670 Tol, Parkir & Derek Kendaraan, 6-1990 Denda & Tilang Kendaraan, 1-1360 Piutang Klaim Asuransi.
- **Laporan › Laba Rugi**: pilihan laporan **Per Bulan (N Bulan Terakhir)**: satu kolom per bulan untuk 3 / 6 / 12 / 24 / 36 bulan terakhir s/d tanggal yang dipilih, plus kolom Total.
- **Kas & Bank › Tagihan Biaya**: tombol **Bayar** di daftar dan di form tagihan yang sudah tersimpan. Tombol itu membuka **Pembayaran Utang** baru yang sudah berisi supplier dan tagihannya
  (kolom Bayar = sisa), tinggal pilih akun kas / bank lalu Simpan. Sebelumnya tagihan hanya bisa dibayar dengan membuka Pembayaran Utang sendiri di tab Pembelian.
- **Bantuan di dalam aplikasi**: tombol bulat **?** di judul tiap menu (dan tombol **F1**) membuka jendela bantuan terpisah, bukan tab. Isinya penjelasan, langkah, dan diagram alur,
  lengkap dengan daftar topik dan kotak cari. Topik pertama: **Alur Biaya Bulanan**, **Biaya Rutin**, **Tagihan Biaya**, dan **Pembayaran Utang**. Menu yang belum punya topik menampilkan daftar semua topik.
- **Penampil Markdown** (bantuan dan Riwayat Versi) kini menampilkan **gambar**, diagram **Mermaid** (flowchart dan sequence diagram), dan tautan antartopik.
- **Laporan › Laporan Rekonsiliasi › Persediaan vs Neraca**: satu laporan untuk mencocokkan nilai persediaan dari sisi barang (sama dengan **Analisa › Nilai Stok**)
  dengan saldo akun persediaan di Neraca, per tanggal dan cabang. Tiga pilihan: **Per Cabang** (ringkasan), **Per Akun Persediaan** (akun Persediaan dan akun
  persediaan khusus item), dan **Selisih per Dokumen** (dokumen yang nilai stoknya tidak sama dengan jurnal persediaannya, selisih terbesar dulu, untuk mencari
  penyebab). Selisih di bawah Rp 100 dianggap pembulatan harga pokok, sama dengan pemeriksaan **Tutup Periode**. Angkanya butuh hak Lihat harga pokok (HPP) di laporan.
- **Laporan › Laporan Rekonsiliasi** (grup baru, setelah Laporan Keuangan): laporan untuk mencocokkan buku bantu dengan buku besar / Neraca. Isinya
  **Persediaan vs Neraca**, **Piutang vs Neraca**, **Utang vs Neraca**, dan **Dokumen vs Jurnal**.
- **Laporan › Laporan Rekonsiliasi › Piutang vs Neraca**: saldo piutang menurut dokumen (faktur kredit, laku titipan, saldo awal piutang, dikurangi penerimaan
  dan retur; sama dengan Laporan Piutang) dibandingkan saldo akun Piutang di Neraca, per tanggal dan cabang. Tiga pilihan: **Per Cabang**, **Per Akun**, dan
  **Selisih per Dokumen** (dokumen yang efeknya tidak sama dengan jurnalnya, termasuk jurnal umum atau saldo awal akun yang langsung ke akun Piutang).
- **Laporan › Laporan Rekonsiliasi › Utang vs Neraca**: sama untuk Utang Usaha (faktur pembelian kredit, tagihan biaya, saldo awal utang, dikurangi pembayaran
  dan retur), Utang Titipan, dan Titipan Belum Ditagih. Selisih = buku bantu − Neraca; di bawah Rp 0,01 dianggap cocok.
- **Laporan › Laporan Rekonsiliasi › Dokumen vs Jurnal**: memeriksa periode dan cabang yang dipilih. Pemeriksaannya: dokumen terposting tanpa jurnal, jurnal ganda untuk
  satu dokumen, tanggal atau cabang jurnal beda dengan dokumennya, jurnal yang dokumen sumbernya sudah dibatalkan / dihapus, dan jurnal yang debit-kreditnya tidak
  seimbang. **Rekap per Pemeriksaan** menunjukkan jumlah temuan; **Daftar Temuan** menunjuk dokumen dan jurnalnya. Jenis dokumen yang diperiksa: Penjualan,
  Pembelian, Penerimaan Piutang, Pembayaran Utang, Retur, Saldo Awal Piutang / Utang, Tagihan Biaya, dan Kas Masuk / Keluar / Transfer.

### Perbaikan
- **Laporan › Neraca, Laba Rugi, dan Analisa (Laba Rugi Tren, Akun × Bulan)**: baris akun induk (mis. 6-5000 Beban Pemilik) kini tebal, sama seperti di daftar **Akun (COA)**. Sebelumnya hanya judul bagian dan total yang tebal.
- **Penulisan "Hutang" diganti "Utang"** di seluruh tampilan: menu **Pembelian › Pembayaran Utang**, **Saldo Awal Utang**, laporan dan analisa Utang, pesan, bantuan, nama akun di template akun, dan template import.
  Kunci hak akses tidak berubah (nama akun lama: lihat bagian Perlu diperhatikan). File import lama yang memakai judul kolom "Potong Hutang" / "Sisa Hutang" tetap bisa dibaca.

### Perlu diperhatikan
- Dokumen lama tidak berubah: kolom Kendaraan kosong. Penyusutan bulan-bulan lalu tidak dijurnal ulang per kendaraan.
- Barang ber-stok yang dibeli tidak bisa langsung diberi kendaraan di Pembelian: barang masuk persediaan dan baru menjadi biaya kendaraan saat dikeluarkan lewat **Item Keluar**.
- Kendaraan yang sudah dipakai di dokumen biaya tidak bisa dihapus lagi (ubah statusnya menjadi Dijual / Dikembalikan, atau nonaktifkan).
- Biaya Rutin, laporan **Biaya per Kendaraan**, dan **Kartu Kendaraan** menyusul.
- Perusahaan yang sudah berjalan tidak mendapat akun baru otomatis: tambahkan lewat **Akun (COA) › Template**, lalu atur kategorinya di **Kendaraan › Kategori Biaya**.
- Jabatan yang boleh melihat menu Kendaraan otomatis boleh membuka Laporan Kendaraan.
- Biaya per km dan biaya total kepemilikan (TCO) menyusul bersama catatan meter.
- Pembaruan ini mengganti kata "Hutang" di **nama akun** yang sudah ada (mis. "Hutang Usaha" menjadi "Utang Usaha") lewat migrasi database. Hanya kata utuh di nama akun;
  keterangan jurnal lama dan log aktivitas tidak diubah. Akun yang namanya sudah Anda ubah sendiri tetap mengikuti aturan yang sama bila memuat kata "Hutang".
- Tombol **Bayar** hanya muncul bagi pengguna yang boleh membuat **Pembayaran Utang**.
- Jabatan yang sudah boleh melihat Neraca otomatis mendapat hak laporan **Persediaan vs Neraca**.
- **Persediaan vs Neraca** pindah dari Laporan Keuangan ke Laporan Rekonsiliasi. Hak laporannya tidak berubah.
- Jabatan yang sudah boleh melihat Neraca otomatis mendapat hak tiga laporan rekonsiliasi yang baru.

## 1.0.43 (2 November 2026)

### Baru
- **Persediaan › Kartu Stok**: kolom baru **Nilai Saldo** (nilai stok setelah tiap mutasi, dihitung dari nilai saldo awal ditambah kolom Nilai), dan **total Nilai** di baris Total
  (sama dengan nilai stok akhir). Nilai stok akhir juga tampil di ringkasan di atas tabel. Kolom ini ikut ke ekspor Excel dan cetak.
  Seperti Harga Pokok dan Nilai, kolom ini hanya tampil bagi yang punya hak **Harga Pokok**; tanpa hak itu kolomnya tidak tampil dan angkanya tidak dikirim ke aplikasi.

## 1.0.42 (2 November 2026)

### Baru
- **Kendaraan › Kendaraan**: daftar kendaraan per cabang. Isinya no. polisi (dirapikan otomatis, mis. B1234XYZ menjadi B 1234 XYZ, dan tidak boleh kembar),
  jenis, merek / model, tahun, warna, no. rangka & mesin, kepemilikan (Milik, Leasing, Sewa, Pinjam), pemegang, meter awal, dan status (Siap, Rusak,
  Dikembalikan). Kendaraan Milik / Leasing bisa ditautkan ke satu **Aset Tetap** (nilai buku dan penyusutan tetap di Akuntansi › Aset Tetap).
- **Kendaraan › Pengemudi**: daftar pengemudi cabang dengan telepon, NIK, golongan, nomor, dan masa berlaku SIM. Pengemudi dipilih sebagai pemegang kendaraan.
- **Kendaraan › Merek & Model**: daftar merek, model, dan varian yang dipilih di form Kendaraan.
- **Pengaturan Perusahaan › Fitur › Kendaraan**: menyalakan menu Kendaraan.
- Kendaraan, pengemudi, dan merek / model tercatat di log aktivitas dan bisa dipulihkan lewat **Sistem › Data Terhapus**.
- **Kendaraan › Dokumen Kendaraan**: STNK, pajak tahunan, KIR, asuransi, dan BPKB per kendaraan, dengan no. dokumen, tanggal terbit, berlaku s/d, penerbit,
  lokasi fisik dokumen (mis. BPKB ditahan leasing), dan biaya (catatan). Sisa hari berwarna: merah = lewat atau ≤ 7 hari, kuning = ≤ 30 hari. **Perpanjang**
  membuat dokumen baru dan menjadikan yang lama *Diganti* (riwayatnya tetap tersimpan). Satu dokumen aktif per jenis per kendaraan.
- **Kendaraan › Kendaraan**: kolom **Dokumen Terdekat** (mis. "STNK · 45 hari lagi") yang berwarna, dan tombol **Dokumen Baru**.
- **Kendaraan › Pengemudi**: tanggal SIM yang hampir kedaluwarsa diberi warna.
- **Beranda**: kartu **Dokumen kendaraan perlu perhatian** (lewat, ≤ 7 hari, ≤ 30 hari, ≤ 60 hari, termasuk SIM pengemudi) bagi perusahaan yang memakai fitur Kendaraan.
- Dokumen kendaraan tercatat di log aktivitas dan bisa dipulihkan lewat **Sistem › Data Terhapus**.

### Perbaikan
- **Persediaan › Transfer Antar Cabang**: menu dipisah menurut arah barang dan namanya dibuat jelas. Kelompok **Masuk dari Cabang Lain** berisi
  **Permintaan Transfer** (cabang peminta membuat permintaan) lalu **Transfer Masuk** (cabang peminta menerima barang). Kelompok **Keluar ke Cabang
  Lain** berisi **Pesanan Transfer** (cabang asal melihat permintaan yang masuk sebagai pesanan) lalu **Transfer Keluar** (cabang asal mengirim barang).
  Di menu klasik kedua kelompok dipisah garis dan judul. Sebelumnya menu kedua bernama Permintaan Transfer Masuk, dan Transfer Masuk berada sebelum
  Transfer Keluar.
- **Persediaan › Rekalkulasi HPP**: pembelian (dan dokumen stok lain) yang pernah diubah dengan **menghapus satu baris** atau **mengubah sebagian barisnya** tidak lagi
  dianggap batal atau terlewat. Sebelumnya seluruh isi dokumen itu hilang dari hitungan: HPP rata-rata semua item di dalamnya menjadi 0, HPP penjualan atas item itu
  ikut ditulis ulang menjadi 0 (di Kartu Stok kolom Harga Pokok kosong saat terjual), dan jurnal HPP-nya ikut berubah. Kini setiap item dihitung dari mutasinya sendiri.
  Item yang HPP-nya sudah terlanjur 0 karena kejadian ini pulih dengan menjalankan **Rekalkulasi HPP** satu kali sejak tanggal dokumen paling awal yang pernah diubah.

### Perlu diperhatikan
- Fitur **Kendaraan** mati untuk perusahaan yang sudah ada; nyalakan di Pengaturan Perusahaan › Fitur. Perusahaan Pengangkutan baru langsung menyala.
  Jabatan Akunting otomatis mendapat hak Kendaraan; jabatan lain diatur di Jabatan & Hak Akses (grup Kendaraan).
- **Akuntansi › Aset Tetap**: aset yang tertaut ke kendaraan tidak bisa dihapus. **Bersihkan Data** jenis Aset tetap hanya melepas tautannya; kendaraan tidak ikut dihapus.
- Hak **Kendaraan** yang sudah ada otomatis berlaku untuk Dokumen Kendaraan. Biaya di dokumen hanya catatan: pengeluarannya tetap dicatat lewat Kas Keluar / Tagihan Biaya.
- Pengingat lewat email belum ada (menyusul); ambang pengingat tetap 7 / 30 / 60 hari.
- Hak akses tidak berubah: **Pesanan Transfer** tetap memakai hak **Transfer Keluar**, **Permintaan Transfer** memakai hak Permintaan Transfer.
- Bila Kartu Stok sebuah item menunjukkan penjualan tanpa HPP padahal pembeliannya ada, dan dokumen pembeliannya pernah diubah (baris dihapus atau sebagian baris
  diubah), jalankan **Rekalkulasi HPP** (Cek dulu) sejak tanggal pembelian itu setelah versi ini terpasang.

## 1.0.41 (2 November 2026)

### Baru
- **Tampilan › Switch UI**: menu utama bisa diganti antara **Ribbon Menu** (bawaan) dan **Menu Classic**, yaitu menu turun
  Beranda · Penjualan · Pembelian · … di bawah bar judul seperti aplikasi desktop biasa. Isi menunya sama: hak akses, fitur perusahaan,
  dan kotak **Cari menu** berlaku di keduanya. Beralih tidak menutup tab yang sedang terbuka, dan pilihannya diingat di PC ini
  (sampai kembali dipilih lagi); pilihan juga bisa dicari lewat **Cari menu** ("Switch UI").
- **Sistem › Jabatan & Hak Akses**: hak baru **Switch UI (Ribbon Menu / Menu Classic)** di kelompok Sistem. Jabatan tanpa hak ini tidak melihat
  pilihan Switch UI dan menu utamanya tetap Ribbon Menu (pilihan yang sudah tersimpan di PC itu tidak terhapus, berlaku lagi bila haknya diberikan).

### Perlu diperhatikan
- Hak **Switch UI** otomatis diberikan ke semua jabatan yang sudah ada (selain Admin, yang selalu boleh) dan ke jabatan bawaan Kasir, Gudang,
  dan Akunting di perusahaan baru, jadi tidak ada yang kehilangan pilihannya. Untuk membatasinya, hapus centang **Switch UI** di jabatan terkait.

## 1.0.40 (2 November 2026)

### Baru
- **Satu faktur dari beberapa pesanan**: **Pembelian › Import dari › Pesanan Pembelian** kini memakai kotak centang, jadi beberapa pesanan supplier yang
  sama (dengan jenis PPN yang sama) bisa dijadikan satu faktur pembelian: satu baris per baris pesanan, diskon pesanan yang belum pernah difakturkan ikut.
  Di **Faktur Penjualan** ke perusahaan grup, kotak **Dari pesanan** kini tombol **Pilih…** untuk beberapa pesanan dari perusahaan dan cabang pemesan yang
  sama (✕ melepas pesanan). Kolom **Pesanan** di daftar Pembelian / Penjualan memuat semua nomor pesanan. Tiap pesanan menghitung statusnya sendiri
  (Terbuka / Sebagian / Selesai) dan menyebut faktur itu.
- **Penjualan › Closing Harian** (desktop): **Rekap Closing** semua outlet × tanggal (hari yang belum di-closing merah), **Buka Closing** untuk satu hari (kolom
  **Fisik** bisa diisi langsung, stok sistem, mutasi sesudah hitung, selisih & nilainya; ringkasan Penjualan, Kas & Stok di kanan; **Import Penjualan**, **Simpan (F9)**,
  **Tutup Hari**, **Buka Kembali**, **Salin WhatsApp**) dan **Atur…** untuk Daftar Hitung Harian, akun kas outlet, batas selisih kas dan jam ganti hari.
- **Closing Harian outlet** (halaman web untuk HP di `/outlet/`, login dengan akun Pilar ERP): staf outlet menghitung stok dari HP, atasan mengimpor
  penjualan Quinos hari itu, menghitung kas & setoran, lalu **Tutup Hari**.
  - **Hitung stok**: item **Daftar Hitung Harian** per outlet (diatur atasan di tab **Atur**: item & lokasi seperti Chiller / Gudang). Hitung buta: staf
    tidak melihat stok sistem, boleh beberapa orang sekaligus, satu item boleh dihitung di beberapa lokasi (dijumlah). Hitungan tersimpan di HP bila
    sinyal hilang dan terkirim saat tersambung lagi.
  - **Penjualan & kas**: tombol **Import penjualan** menjalankan import Quinos hari itu; kas fisik dihitung per pecahan atau total, selisih terhadap
    saldo buku akun kas outlet, lalu setoran ke bank / kas pusat.
  - **Tutup Hari** membuat **Stok Opname** per akhir hari, **Kas Masuk / Keluar** selisih kas (akun baru **Selisih Kas**) dan **Transfer Kas**
    setoran dalam satu langkah, lalu **mengunci tanggal itu untuk outlet itu**: penjualan, pembelian, persediaan, kas & bank, dan pelunasan outlet
    itu bertanggal itu tidak bisa dibuat / diubah / dibatalkan (Jurnal Umum tetap bisa). Import Quinos melewati hari yang sudah di-closing.
  - **Penjualan & mutasi selama menghitung** tidak terbaca sebagai selisih: stok sistem dihitung pada **jam hitung** item (penjualan Quinos *Per struk*
    menurut jam struk; dokumen lain menurut jam input). Penjualan tanpa jam (import *Harian*) tidak bisa dikoreksi dan diberi peringatan.
  - **Buka kembali** (atasan, alasan wajib) membatalkan Stok Opname & kas buatan closing dan melepas kunci; hitungan tetap ada. **Rekap** semua outlet 7
    hari terakhir dan **Salin untuk WhatsApp** untuk ringkasan closing.
- **Sistem › Penomoran Dokumen**: jenis baru **Closing Harian** (CLS). **Sistem › Bersihkan Data**: jenis baru **Closing harian**.
- **Penjualan › Import dari ▾**: tombol baru di samping **Baru** di daftar Faktur Penjualan, dan di form Faktur Penjualan baru. Faktur baru diisi dari:
  - **Pesanan Masuk…** (jumlah yang menunggu tertulis di menu): satu atau beberapa Pesanan Pembelian perusahaan grup dari perusahaan dan cabang pemesan
    yang sama (dulu kotak **Dari pesanan**).
  - **Faktur penjualan lain**: salinan konsumen, jenis PPN, potongan, dan baris faktur lama untuk pesanan rutin yang sama. Promo yang berlaku hari ini
    diterapkan lagi, potongan yang diketik ikut. Faktur dari pesanan grup tidak bisa disalin.
  - **Teks (tempel)…**, **File teks / CSV…**, **Excel…**: pesanan konsumen dari WhatsApp, nota, atau file. Item dicocokkan lewat barcode, kode, lalu nama dan
    diperiksa dulu di pratinjau; tanpa harga = harga jual item. Konsumen boleh dipilih di pratinjau.
  Faktur belum tersimpan: periksa, ubah bila perlu, lalu Simpan. Sumbernya tampil di judul form ("Dari pesanan …", "Salinan PJ/…", "Dari teks (12 baris)").
- **Penjualan › Pesanan Penjualan (SO)**: pesanan konsumen biasa (pre-order, katering, parsel, pesanan rutin kantor) dengan qty, harga, potongan, jenis PPN, dan
  tanggal kirim yang disepakati. Tidak mengubah stok, jurnal, atau piutang. Nomor **SO**, hak akses **Pesanan Penjualan** per jabatan.
  - Daftar: **Baru**, **Import dari ▾**, **Lihat**, **Ubah**, **Salin untuk WhatsApp** (teks konfirmasi ke konsumen), **Lainnya ▾** (Riwayat, Tutup, Batalkan,
    Pulihkan, Hapus). Bawaan menampilkan pesanan yang belum selesai.
  - **Import dari ▾** di pesanan baru: **Pesanan penjualan lain** (pesanan rutin), **Faktur penjualan lain**, **Teks**, **File teks / CSV**, **Excel**.
  - Status **Terbuka / Sebagian / Selesai / Ditutup / Batal** dihitung dari faktur yang memakainya. Pesanan yang sudah difakturkan tidak bisa diubah atau
    dihapus, hanya ditutup (sisa tidak dipenuhi lagi).
  - Total pesanan memuat PPN saja; PB1 dan biaya layanan dihitung saat faktur dibuat.
- **Faktur Penjualan › Import dari ▾ › Pesanan Penjualan…**: faktur baru berisi sisa satu atau beberapa pesanan dari konsumen dan jenis PPN yang sama (jumlah
  pesanan yang menunggu tertulis di menu). Konsumen, jenis PPN, harga, dan potongan pesanan terisi; harga boleh diubah, qty melebihi sisa ditanyakan saat
  simpan, baris di luar pesanan boleh ditambah. Promo tidak menimpa harga pesanan. Kolom **Pesanan** di daftar Faktur Penjualan menampilkan nomor SO-nya.

### Perbaikan
- **Pembelian › Import dari ▾** kini tombol sendiri di samping **Baru**, tidak lagi tersembunyi di dalam **Lainnya ▾**. Isinya sama (Pesanan
  Pembelian, faktur perusahaan grup, Faktur pembelian lain, Teks, File teks / CSV, Excel). **Lainnya ▾** kini hanya untuk pembelian terpilih
  (Riwayat, Buat retur, Batalkan, Hapus).
- **Bersihkan Data › Pesanan pembelian**: bila satu faktur berasal dari beberapa pesanan dan hanya sebagian yang dibersihkan, faktur tetap ada dan tetap
  terhubung ke pesanan yang tersisa (dulu semua rujukan pesanan faktur itu dilepas).

### Perlu diperhatikan
- Sumber **Penjualan dari Grup (pengguna Pilar ERP)** di Import dari kini bernama **Faktur dari perusahaan grup**. Cara kerjanya tidak berubah.
- Pesanan asal sebuah faktur ditentukan saat faktur dibuat: pesanan lain tidak bisa ditambahkan ke faktur yang sudah tersimpan. Pemesan hanya bisa
  menerima satu faktur di satu cabang, jadi pesanan dari cabang pemesan yang berbeda tidak digabung dalam satu faktur penjualan grup.
- Hak baru **Closing Harian** (Penjualan; Lihat = ringkasan, stok sistem & selisih, Buat = import / kas / Tutup Hari, Ubah = pengaturan, Batal = Buka kembali)
  dan **Hitung Stok Harian** (Persediaan; khusus staf yang hanya menghitung, tanpa stok sistem). Hak diberikan admin per jabatan; jabatan Kasir bawaan
  perusahaan baru mendapat Hitung Stok Harian. Import penjualan dari closing juga butuh hak Penjualan & Penerimaan Piutang (Buat).
- Staf tetap menghitung dari HP (halaman web); atasan memakai aplikasi desktop atau halaman web, keduanya ke data yang sama. Item yang dihitung di lebih dari
  satu lokasi hanya bisa dilihat (tidak diubah) di desktop.
- Kotak **Dari pesanan** di form Faktur Penjualan sudah tidak ada: pilih lewat **Import dari ▾ › Pesanan Masuk…**. **Penjualan › Pesanan Masuk › Buat Faktur**
  tetap membuka faktur berisi pesanan itu.
- Import teks / file untuk Penjualan tidak mengingat pilihan item dan pemetaan kolom (tidak ada peta item konsumen); kolom file yang judulnya tidak dikenali
  diatur lewat **Kolom…** setiap kali.
- Hak **Pesanan Penjualan** (Lihat / Buat / Ubah / Hapus / Batal) dibagikan sekali ke jabatan yang boleh membuat **dan** menghapus Faktur Penjualan; jabatan lain
  (termasuk Kasir) tidak mendapatkannya sampai diatur di Jabatan & Hak Akses. Admin selalu boleh.
- Cetak template Pesanan Penjualan (A4 / thermal / dot-matrix) belum ada; untuk saat ini kirim konfirmasi lewat **Salin untuk WhatsApp**.
- Faktur yang dibuat dari Pesanan Penjualan tidak bisa disalin lewat **Faktur penjualan lain**; pakai Import dari › Pesanan Penjualan.
- **Bersihkan Data** punya jenis **Pesanan penjualan**: faktur yang berasal dari pesanan yang dibersihkan tetap ada, tanpa rujukan pesanan.

## 1.0.39 (31 Oktober 2026)

### Baru
- **Akuntansi › Buku Besar**: hasil dibagi per halaman seperti daftar transaksi (pilihan **Per halaman** 10 / 25 / 50 / 100 di bawah tabel,
  sama dengan menu lain), jadi buku besar semua akun untuk periode panjang tampil cepat. Saldo berjalan tetap dihitung dari seluruh periode.
  **Ctrl+F** mencari no. jurnal, no. dokumen, jenis, keterangan, cabang atau akun di semua halaman. Jumlah debit / kredit di kaki tabel =
  halaman yang tampil; **Export Excel** dan **Cetak / Preview** tetap berisi semua baris.
- **Persediaan › Stok Opname**: kolom **Harga Jual** (harga jual / pricelist di Master Item, per satuan baris) dan **Nilai Jual** (selisih ×
  harga jual), plus **Selisih harga jual** di ringkasan kanan. Harga jual dicatat saat baris dibuat atau item / satuannya diganti, jadi opname
  lama tidak berubah walau harga master naik. Item berharga bebas (harga jual 0) kolomnya kosong.
- **Cetak ▾** di Stok Opname: template baru **Selisih Opname Harga Jual** (A4, setengah A4, thermal 80 / 58 mm, dot matrix) untuk membebankan
  selisih stok ke karyawan dengan harga jual: kolom harga jual & nilai jual, ringkasan selisih lebih / kurang / bersih menurut harga jual,
  tanda tangan Dihitung oleh · Karyawan · Disetujui. Tanpa harga pokok, jadi bisa dicetak jabatan yang hanya boleh cetak tanpa harga.
- **Persediaan › Permintaan Transfer**: cabang meminta item & qty ke cabang lain (mis. outlet ke dapur pusat / gudang), dengan tanggal dibutuhkan
  dan catatan. Nomor **PTR**. Status Terbuka / Sebagian / Selesai mengikuti pengirimannya; sisa yang tidak perlu dikirim bisa **Tutup permintaan**.
- **Persediaan › Permintaan Transfer Masuk**: cabang asal melihat permintaan ke cabangnya beserta item, terkirim & sisa, lalu **Buat Transfer
  Keluar**: cabang tujuan & sisa item terisi otomatis, qty boleh dikurangi (kirim sebagian). Barangnya diterima seperti biasa di **Transfer Masuk**.
- **Transfer Keluar › Dari permintaan**: permintaan juga bisa dipilih langsung di form Transfer Keluar baru. Qty tidak boleh melebihi sisa
  permintaan; item lain boleh ditambah sebagai baris di luar permintaan.
- **Dasbor admin › Kesehatan server › Kerentanan (.NET)**: API memantau celah keamanan pada runtime .NET yang ikut di paketnya (seperti
  Node2Shell, CVE-2026-111497) dengan membaca daftar rilis keamanan Microsoft sekali sehari. Runtime API atau desktop yang tertinggal dari
  rilis keamanan terbaru memunculkan peringatan merah di Kesehatan server dan Ringkasan, lengkap dengan versi dan nomor CVE-nya. Tombol
  **Cek sekarang** mengecek ulang saat itu juga.
- **Rilis**: `release.ps1` menolak rilis bila ada paket NuGet yang rentan atau runtime .NET hasil publish lebih tua dari rilis keamanan
  terbaru (dicek sebelum apa pun dikirim ke server). Tanpa internet hanya memberi peringatan; `-AbaikanCve` untuk keadaan darurat.
- **Dasbor admin › Server › Ubuntu Pro**: status Ubuntu Pro (terpasang, esm-apps, Livepatch) dan paket yang tambalan keamanannya tertahan
  karena Pro belum terpasang (caddy, rclone). `setup.sh` bisa memasangnya dengan `PRO_TOKEN`; token tidak disimpan di mana pun.

### Perbaikan
- **Stok Opname**: opname yang selisih lebih dan kurangnya sama besar di akun persediaan yang sama (mis. item A +2, item B −2 dengan harga
  pokok sama) tidak bisa disimpan / diubah ("Jurnal tidak punya baris"). Kini tersimpan tanpa jurnal, seperti rakitan dan pecah stok.

### Perlu diperhatikan
- Baris opname yang sudah ada diisi harga jual master saat pembaruan dipasang (harga master hari itu).
- Menu **Cetak ▾** dokumen persediaan kini berjudul **Dengan harga pokok** / **Tanpa harga pokok**; template Selisih Opname Harga Jual ada di
  kelompok sendiri **Harga jual (tanpa harga pokok)**. Template utama opname tidak berubah.
- **Buku Besar**: pratinjau cetak kini jendela modal (tutup pratinjau dulu sebelum kembali ke Buku Besar).
- Hak baru **Permintaan Transfer** (kelompok Persediaan). Jabatan yang sudah boleh membuat Transfer Keluar / Masuk otomatis mendapatkannya.
  Permintaan Transfer Masuk & Transfer Keluar dari permintaan memakai hak **Transfer Keluar**.
- Permintaan yang sudah dikirim tidak bisa diubah, dibatalkan atau dihapus lagi, hanya ditutup.
- **Bersihkan Data** punya jenis baru **Permintaan transfer**; transfer keluar yang dibuat dari permintaan yang dihapus tetap ada, tanpa rujukan
  permintaan.
- Runtime .NET baru sampai ke pengguna lewat **rilis Pilar ERP baru** (API di server dan pembaruan otomatis desktop). Dasbor hanya memberi
  tahu; pembaruan Ubuntu tidak menambal runtime ini.
- Ubuntu Pro belum terpasang di server sebelum pemilik menjalankan `setup.sh` dengan `PRO_TOKEN` (langkah di `deploy/linux/README.md`).

## 1.0.38 (31 Oktober 2026)

### Baru
- **Pembelian › Lainnya › Import dari**: faktur pembelian baru diisi dari **Pesanan Pembelian**, **Penjualan dari Grup**, atau **Faktur pembelian
  lain** (salinan supplier, jenis PPN, potongan & baris faktur lama, untuk belanja rutin yang sama). Faktur belum tersimpan: periksa, ubah bila
  perlu, lalu Simpan. Tombol **Import dari ▾** yang sama ada di form Pembelian baru.
- Label menu Import dari menyebut jumlah yang menunggu, mis. **Penjualan dari Grup (2)**. Daftar Pembelian menampilkan bar info bila ada
  penjualan perusahaan grup yang menunggu diterima, dengan tombol **Terima…**.
- **Profil Saya › 2FA** (aplikasi) dan **Profil › 2FA** (dasbor admin): verifikasi dua langkah dengan aplikasi authenticator di HP (Google /
  Microsoft Authenticator, Authy, 1Password). Nyalakan dengan memindai kode QR (atau mengetik kuncinya), lalu simpan 10 kode cadangan yang
  hanya ditampilkan sekali. Bisa membuat kode cadangan baru dan mematikan 2FA (password + kode).
- **Layar login** aplikasi dan dasbor: akun dengan 2FA aktif diminta **Kode 2FA** sesudah password (6 angka dari aplikasi, atau satu kode
  cadangan). Kode salah dihitung pembatas login dan tercatat di Log Login ("Kode 2FA salah"); satu kode hanya bisa dipakai sekali.
- **Master User › Reset 2FA** dan **Sistem › Admin Platform › Reset 2FA**: mematikan 2FA user yang kehilangan HP (tercatat di log aktivitas).
  Kolom **2FA** di daftar user.
- **Keamanan server**: layanan aplikasi dan web server kini berjalan terkurung. Bila suatu celah keamanan sampai dibobol, penyerang tetap
  tidak bisa mengambil alih server, mengubah sistem, atau melihat program lain.
- **Dasbor admin › Server › Layanan**: kolom **Sandbox** menampilkan seberapa terkurung tiap layanan (0 = terkunci rapat, 10 = bebas).
- **Pembelian › Lainnya › Import dari › Teks (tempel)**: tempel daftar item dari WhatsApp / nota, mis. "Kopi 10 pcs x 1.500", "Gula 2 kg @15rb",
  "Telur 3 kg = 75.000". Nomor urut, salam, total, PPN & ongkir dilewati. Teks **Salin untuk WhatsApp** dari Pesanan Pembelian juga terbaca.
- **Import dari › File teks / CSV** dan **Excel**: file faktur / daftar harga supplier (.csv, .txt, .xlsx, .xls). Judul kolom dikenali sendiri
  walau ada kop perusahaan di atasnya; file tanpa judul cukup diatur kolomnya sekali per supplier (**Kolom…**). File template **Import Data ›
  Pembelian** berisi beberapa faktur: pilih satu, No Faktur-nya jadi No. Referensi.
- Item dicocokkan otomatis lewat **peta item supplier**, barcode (juga barcode satuan dus), kode, lalu nama item. Hasilnya diperiksa dulu di
  jendela pratinjau: baris yang belum cocok dipilih itemnya, baris lain boleh diabaikan, lalu **Isi faktur**.
- Item yang dipilih sendiri diingat untuk supplier itu (**Ingat untuk supplier ini**, bawaan menyala), termasuk satuannya: faktur berikutnya dari
  supplier yang sama langsung cocok. Peta dilihat, diubah & dihapus di **Master Supplier › Peta Item** (hak Ubah Supplier).

### Perbaikan
- **Server › batas permintaan**: lonjakan permintaan dari satu user atau satu IP kini tidak melebihi batas yang diatur (`RateLimit__*`).
  Sebelumnya, setelah beberapa detik tidak dipakai, lonjakan berikutnya bisa lolos lebih banyak dari batas.

### Perlu diperhatikan
- Kotak **Terima dari grup** dan **Dari pesanan** di header form Pembelian dihapus; pilihannya pindah ke **Import dari**. Faktur yang sudah
  tersimpan menulis sumbernya (pesanan / penjualan grup) di judul form.
- **Lainnya ▾** di daftar Pembelian kini bisa dibuka tanpa memilih faktur; tanpa faktur terpilih isinya Import dari saja.
- **Admin penyedia aplikasi (admin platform) wajib 2FA.** Sebelum 2FA aktif, dasbor admin hanya membuka Profil › 2FA dan menu Admin Platform
  menampilkan petunjuk; setelah dinyalakan langsung terbuka tanpa masuk ulang. User lain tidak terpengaruh (2FA opsional).
- **Dasbor › Server**: perubahan server kini dikonfirmasi dengan **kode 2FA**, bukan ketik ulang password. Satu kode untuk satu perubahan.
- Server: jalankan ulang `setup.sh` setelah rilis ini supaya dasbor bisa membuka Profil › 2FA (jalur `/api/auth/2fa` di Caddy). Admin platform
  yang kehilangan HP dan kode cadangan: `sudo bash reset-2fa.sh <KODE> <user>` di VPS (lihat `deploy/linux/README.md`).
- Saat pengaturan server diperbarui, layanan aplikasi dimulai ulang bila perlu: PC kasir terputus sebentar (±5–30 detik) lalu tersambung
  lagi.
- Tanpa hak Lihat harga di Pembelian, harga di teks / file tidak dipakai: harga diisi otomatis seperti input biasa.
- Baris tanpa harga di teks / file diisi harga beli otomatis seperti memilih item di form (harga beli terakhir / HPP).

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
