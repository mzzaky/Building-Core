# Building-Core
Minecraft plugin

Softdependencies:
1. WorldGuard
2. Placeholderapi
3. Vault

Jenis Bangunan <building_type>:
1. Toko
2. Apartemen

Command list:
1. /buildingcore admin create type <building_type> <building_id> <building_price_value> <building_tax_value> #untuk mendaftarkan region saat command dijalankan.
2. /buildingcore admin set tax <building_id> <value> #untuk mengganti harga pajak secara manual.
3. /buildingcore admin set owner <building_id> <player_name> #untuk mengeset pemilik bangunan secara manual.
4. /buildingcore admin set price <building_id> <value> #untuk mengganti harga jual bangunan secara manual.

Logika Bangunan Tipe Toko:
1. 






Berikut detailnya:
1. Admin akan mendaftarkan area wilayah sebagai aset pemerintah, menentukan ID, harga sewa, nama tampilan, dan harga pajak, yang semuanya dilakukan menggunakan perintah.

2. Sistem pajak bangunan akan secara otomatis memotong dana dari pemilik bangunan setiap 24 jam. Jika pemilik tidak memiliki dana yang cukup, bangunan akan memasuki masa penahanan. Selama fase ini, bangunan tidak akan lagi berfungsi dengan baik, dan pemilik asli akan dikenakan denda keterlambatan pembayaran sebesar 25% per hari. Jika pemilik gagal membayar denda dan pajak dalam 3 hari, akses akan dicabut paksa, dan pemain akan ditambahkan ke daftar hitam, mencegah mereka membeli bangunan selama beberapa hari.

3. Pemilik bangunan dapat menjual bangunan mereka kepada pemerintah, melelangnya, atau menyewakannya kepada pemain lain.
a. Jika pemain menjual kepada pemerintah, akses pemain akan dicabut sepenuhnya, dan bangunan akan kembali ke harga normal. Harga jual adalah 50% dari harga asli.
b. Sistem lelang melibatkan pengalihan kepemilikan, tetapi pemain dapat dengan bebas menentukan harganya. Setelah proses ini selesai, pembeli akan menjadi pemilik penuh bangunan tersebut.
c. Selama fase penyewaan, pemilik asli tetap membayar pajak kepada pemerintah, tetapi pemilik asli akan menerima biaya sewa (yang ditentukan oleh pemilik) setiap 24 jam dari penyewa.

4. Sistem jual-beli tidak menggunakan toko peti (karena terlalu primitif). Setiap bangunan akan memiliki satu karyawan NPC yang menjual barang-barang milik atau disediakan oleh pemilik asli. Prosedur penjualan akan sepenuhnya menggunakan GUI khusus (mulai dari pendaftaran barang, penentuan harga, dll.) untuk menyederhanakan proses bagi pemain.

5. Terdapat sistem peringatan langsung untuk setiap kejadian seperti pajak, lelang, transaksi di tempat karyawan, dll.

6. Terdapat sistem anti-grief yang mencegah pemilik mengubah atau memodifikasi bangunan sepenuhnya; pemilik hanya dapat mendekorasi area tertentu.

7. Fitur fast-travel memungkinkan pemilik untuk langsung berteleportasi ke lokasi bangunan toko mereka.

8. Sistem peringkat dan ulasan di mana semua pemain dapat memberikan poin ke lokasi bangunan tempat mereka berada saat ini. Peringkat dan ulasan membantu pemain menemukan toko yang bagus.

Informasi tambahan:
1. Setiap transaksi yang melibatkan fitur ini akan dicatat dalam log (sistem ini juga mencatat nama setiap pemilik, tanggal penjualan, dan informasi detail lainnya), yang dapat diakses dan dibaca oleh admin.
2. Fitur rumah lelang yang ada di server akan dihapus karena bentrok (berpotensi mengurangi penggunaan salah satu fitur) dengan fitur ini.
3. Administrator memiliki akses penuh ke fitur ini, artinya mereka dapat menghapus pemilik secara paksa dan melakukan modifikasi penuh tanpa izin.
