# Building-Core
Minecraft plugin

Softdependencies:
1. WorldGuard
2. Placeholderapi
3. Vault

Jenis Bangunan <building_type>:
1. Toko
2. Apartemen

Admin Command list:
1. "/buildingcore admin create type <building_type> <building_id> <building_price_value> <building_tax_value> <building_tax_time>"
Fungsi: untuk mendaftarkan region (worldguard) menjadi bangunan.
2. "/buildingcore admin set owner <building_id> <value>"
Fungsi: value adalah <player_name>, untuk mengganti pemilik bangunan.
3. "/buildingcore admin set price <building_id> <value>"
Fungsi: value adalah <building_price_value>, untuk mengganti harga jual bangunan.
4. "/buildingcore admin set tax <building_id> <value>"
Fungsi: value adalah <building_tax_value>, untuk mengganti harga pajak.
5. "/buildingcore admin set tax_time <building_id> <value>"
Fungsi: value adalah <building_tax_time>, untuk mengganti waktu pembayaran pajak.
6. "/buildingcore admin set type <building_id> <value> #value adalah <building_type>"
Fungsi: untuk merubah tipe bangunan.
7. "/buildingcore admin remove <building_id>"
Fungsi: untuk menghapus bangunan
8. "/buildingcore admin teleport <building_id>"
Fungsi: untuk teleportasi ke lokasi bangunan
9. "/buildingcore admin building_list"
Fungsi: untuk melihat semua bangunan yang terdaftarkan, command ini memperlihatkan teks yang berisi informasi informasi dasar bangunan.
10. "/buildingcore admin reload"
Fungsi: untuk mereload plugin

Owner Command List:
1. "/buildingcore buy <building_id>"
Fungsi: untuk membeli bangunan yang tersedia
2. "/buildingcore sell governor <building_id>"
Fungsi: untuk menjual bangunan ke pemerintah, pemain langsung menerima uang (50% dari harga asli bangunan) dan kehilangan aksesnya.
3. "/buildingcore sell auction <building_id> <value>"
Fungsi: untuk menjual bangunan ke pemain lain, <value> adalah harga jual yang ditentukan pemain.
4. "/buildongcore tax pay <building_id>"
Fungsi: fungsi untuk membayar pajak lebih awal (manual).
5. "/buildingcore tax check <building_id>"
Fungsi: memberikan pesan teks ke pemain yang berisikan informasi kapan waktu pembayaran pajak selanjutnya.
6. "/buildingcore donation claim <building_id>"
Fungsi: mengambil semua uang donasi yang terkumpul.
7. "/buildingcore donation check <building_id>"
Fungsi: memerika uang donasi yang terkumpul, dan informasi log (mencakup waktu, donatur, dan jumlah donasi).
8. "/buildingcore tp <building_id>"
Fungsi: melakukan teleportasi ke koordinat bangunan

Owner Command List (bangunan tipe apartemen):
1. "/buildingcore rent claim <building_id>"
Fungsi: mengambil semua uang yang telah digenerasi oleh bangunan apartemen
2. "/buildingcore rent check <building_id>"
Fungsi: mengecek jumlah uang yang telah terkumpul oleh bangunan

Visitor Command:
1. "/buildingcore information <building_id>"
Fungsi: untuk melihat informasi tentang bangunan, 
2. "/buildingcore donate <building_id> <value>" 
Fungsi: melakukan donasi ke bangunan yang dituju.
3. "/buildingcore review <building_id> <value>"
Fungsi: melakukan penilaian ke bangunan, value adalah angka 1-10 (mendukung angka desimal), semua angka yang telah dikumpulkan akan dihitung kembali menjadi <building_rating>

Other Command:
1. "/buildingcore help"
Fungsi: mengirim pesan teks kepada main yang berisi daftar lengka command yang tersedia.
2. "/buildingcore version"
Fungsi: melihat informasi versi plugin.
3. "/buildingcore rating <building_id>"
Fungsi: memperlihatkan total rating yang dimiliki bangunan.

Logika Umum:
1. Sistem pajak bangunan akan secara otomatis memotong dana dari pemilik bangunan setiap beberapa waktu (yang telah didaftarkan oleh admin). Jika pemilik tidak memiliki dana yang cukup, bangunan akan memasuki <inactive_period>. Selama fase ini, bangunan tidak akan lagi berfungsi dengan baik, dan pemilik asli akan dikenakan denda keterlambatan pembayaran sebesar 25% dari harga bangunan per hari. Jika pemilik gagal membayar denda dan pajak dalam 3 hari, akses akan dicabut paksa, dan pemain akan ditambahkan ke daftar hitam, mencegah mereka membeli bangunan selama beberapa hari.
2. Selama masa pelelangan, bangunan akan memasuki <inactive_period> hingga masa lelang berakhir atau bangunan dibeli oleh pemain lain.
3. Terdapat sistem peringatan langsung untuk setiap kejadian seperti pajak, lelang, transaksi, dll.
4. Setiap transaksi yang melibatkan fitur ini akan dicatat dalam log (sistem ini juga mencatat nama setiap pemilik, tanggal penjualan, dan informasi detail lainnya), yang dapat diakses dan dibaca oleh admin.

Logika (bangunan tipe apartemen):
1. setiap bangunan menghasilkan uang (vault) diantara 25-30 perjamnya, data angka dapat distack dengan jumlah yang tak terbatas hingga pemain mengklaimnya menggunakan command.

Istilah:
1. <inactive_period>: bangunan yang berada dalam masa ini dinonaktifkan semua fungsinya secara keseluruhan, semua command terkait pemilik akan trigger pesan "bangunan sedang tidak dapat digunakan"
2. <building_rating>: adalah nilai angka yang telah diakumulasikan dari total nilai review pengunjung, hanya bangunan yang dimiliki pemain yang bisa memiliki atribut ini, rating akan direset setelah pemilik berpindah tangan atau dijual.

Perintah Tambahan:
1. pastikan plugin komtabible dengan versi 1.21.1, 1.21.2, 1.21.4, 1.21.5
2. optimasi plugin untuk mencegah lag saat dijalankan.
3. tambahkan sistem permission disetiap command untuk mencegah eksploitasi.
4. tambahkan sistem log, debugging, dan pesan error untuk mencatat informasi dan mempermudah proses pengembangan plugin.
5. semua waktu yang berada dalam plugini merujuk pada waktu minecraft, bukan waktu di dunia nyata
6. daftarkan (integrasikan) semua value penting ke placeholderapi, agar dapat terbaca jika saya menggunakannya pada custom GUI.
7. sertakan panduan pembuatan plugin ini dengan detail (karena saya adalah developer pemula).
