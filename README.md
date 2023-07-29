## Gevyndo Gunawan 18221076,
### PHP with Laravel

Monolith
Ini adalah aplikasi e-commerce monolith yang terdiri dari komponen frontend (FE) dan backend (BE). Aplikasi ini memungkinkan pengguna untuk melakukan registrasi, login, menjelajahi katalog produk, melihat detail produk, membeli produk, dan melihat riwayat pembelian.

Frontend (FE)
Frontend dari aplikasi ini bertanggung jawab untuk menyediakan antarmuka yang ramah pengguna dan memfasilitasi interaksi dengan pengguna. Frontend dibangun menggunakan PHP dengan bantuan blade.

1 Halaman Registrasi
Halaman registrasi memungkinkan pengguna untuk membuat akun dengan data yang dibutuhkan berikut:

Nama lengkap (nama depan dan nama belakang)
Username
Email
Password
Selama proses registrasi, FE akan memvalidasi data sebelum mengirimkannya ke backend untuk diproses lebih lanjut. Backend akan memastikan bahwa email dan username yang diberikan adalah unik, dan jika tidak, pesan kesalahan yang sesuai akan dikirim kembali ke FE untuk ditampilkan.

2 Halaman Login
Halaman login memungkinkan pengguna untuk masuk ke akun mereka menggunakan email atau username bersama dengan password. FE akan memvalidasi kredensial login sebelum mengirimkannya ke backend untuk proses autentikasi. Jika kredensial benar, backend akan menghasilkan JSON Web Token (JWT) dan mengirimkannya kembali ke FE. FE akan menyimpan token ini, dan untuk setiap permintaan API selanjutnya, token akan disertakan dalam header "Authorization" menggunakan metode Bearer token.

3 Halaman Katalog dan Halaman Detail Produk
Halaman katalog menampilkan daftar produk yang tersedia untuk dibeli oleh pengguna. Setiap produk dalam katalog akan menampilkan nama, harga, dan stok saat ini. Untuk mencegah tampilan data yang terlalu banyak dalam satu halaman, dilakukan implementasi pagination baik pada frontend atau backend.

Ketika pengguna mengklik produk dalam katalog, mereka akan diarahkan ke halaman detail produk. Halaman ini akan menyediakan informasi lebih rinci tentang produk, termasuk nama, harga, dan stok saat ini. Dari halaman ini, pengguna juga dapat memulai proses pembelian produk.

4 Halaman Beli Produk
Halaman beli produk akan menampilkan detail produk yang dipilih, dan pengguna dapat memasukkan jumlah produk yang ingin dibeli. Halaman ini akan menampilkan total biaya yang harus dibayarkan berdasarkan jumlah yang dipilih dan harga produk.

Untuk melanjutkan pembelian, FE akan mengirimkan permintaan pembelian ke backend. Backend akan memvalidasi permintaan pembelian, memastikan bahwa jumlah yang diminta tidak melebihi stok yang tersedia. Jika pembelian berhasil, backend akan memperbarui stok produk di database dan mencatat pembelian dalam riwayat pembelian.

5 Halaman Riwayat Pembelian
Halaman riwayat pembelian akan menampilkan daftar sederhana dari pembelian sebelumnya yang dilakukan oleh pengguna. Daftar akan mencakup nama produk yang dibeli, jumlah produk yang dibeli, dan total harga yang dibayarkan. Seperti halaman katalog, pagination akan diimplementasikan untuk mengatur jumlah data yang ditampilkan dalam satu halaman.

Backend (BE)
Backend aplikasi bertanggung jawab atas pemrosesan data, validasi, dan komunikasi dengan database. Backend dibangun menggunakan bahasa pemrograman server-side seperti Node.js dan menggunakan database untuk menyimpan informasi pengguna, data produk, dan riwayat pembelian.

1 Registrasi
Selama proses registrasi, BE akan menerima data registrasi pengguna dari FE. BE akan melakukan validasi data untuk memastikan bahwa email dan username yang diberikan adalah unik. Jika salah satu dari keduanya tidak unik, BE akan mengirimkan respons error ke FE.

Password yang diberikan oleh pengguna akan dihash sebelum disimpan di database. Metode hashing yang digunakan bersifat fleksibel dan dapat dipilih berdasarkan kebutuhan aplikasi.

2 Login
Ketika FE mengirimkan kredensial login (email/username dan password) ke BE, BE akan memvalidasi datanya. Jika kredensial benar, BE akan menghasilkan JWT dan mengirimkannya kembali ke FE, yang akan menyimpannya dengan aman. FE akan menggunakan token ini untuk otentikasi pada permintaan API selanjutnya.

3 Katalog dan Detail Produk
BE bertanggung jawab untuk menyediakan data yang diperlukan ke FE untuk halaman katalog. BE akan mengambil daftar produk dari database dan mengimplementasikan pagination untuk membatasi jumlah produk yang ditampilkan dalam satu halaman.

Ketika FE meminta detail produk tertentu, BE akan mengambil informasi produk dari database dan mengirimkannya kembali ke FE.

4 Pembelian Produk
BE akan berkomunikasi dengan database untuk memastikan bahwa permintaan pembelian pengguna valid. BE akan memeriksa apakah jumlah yang diminta tersedia dalam stok. Jika stok cukup, BE akan memperbarui stok produk di database dan mencatat pembelian dalam riwayat pembelian.

5 Riwayat Pembelian
Riwayat pembelian akan diambil dari database berdasarkan ID pengguna untuk memastikan data yang ditampilkan hanya milik pengguna yang diotentikasi. BE akan mengimplementasikan pagination untuk mengatur data yang ditampilkan pada halaman riwayat pembelian.

Database
Aplikasi ini memerlukan database untuk menyimpan informasi pengguna, data produk, dan riwayat pembelian. Database akan menyimpan password yang dihash untuk memastikan keamanan pengguna.

Deployment
Untuk mendeploy aplikasi e-commerce monolith, Anda perlu menyiapkan server untuk meng-host backend dan server web untuk meng-host frontend. Server backend akan menangani permintaan API dari frontend dan berkomunikasi dengan database untuk mengambil dan menyimpan data. Frontend akan melakukan permintaan API ke server backend untuk mengambil data dan melakukan aksi pengguna.

Pastikan untuk mengatur langkah-langkah keamanan yang tepat, seperti mengamankan endpoint API, menangani CORS, dan melindungi data sensitif pengguna. Selain itu, konfigurasi backup reguler untuk database untuk mencegah kehilangan data.

Adapun bonus yang dibuat adalah deployment dan searching
Dokumentasi API:
https://gsis2023.postman.co/workspace/Team-Workspace~a395a4bf-32da-4628-89c5-31b5add1cb2e/collection/25876048-733f2edd-6d2d-42bd-a9cf-d6c800f46d59?action=share&creator=25876048
