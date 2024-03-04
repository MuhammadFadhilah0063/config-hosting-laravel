Langkah-langkah hosting

==== Hosting ====
1. Buat subdomain baru, pada menu websites di bagian submenu domain -> subdomain.
2. Buka file manager, public_html, folder subdomain.
3. Upload file project (zip), dan ekstrak.
4. Lanjut langkah dibawah.

==== Pengaturan struktur folder ====
1. Bikin folder nama terserah, pada folder project. Misalnya folder aplikasi.
2. Pindahkan semua folder dan file pada folder project kecuali folder public, ke dalam folder yang baru dibuat tadi.
3. Pindahkan semua folder dan file pada folder public, ke luar folder public. Dan hapus folder publicnya.
4. Buka file index.php. Ubah pada bagian :<br/>
&ensp;&ensp;<code>require \_\_DIR\_\_ . '/../vendor/autoload.php';</code>&ensp;=>&ensp;<code>require \_\_DIR\_\_ . '/aplikasi/vendor/autoload.php';</code><br/>
&ensp;&ensp;<code>$app = require_once \_\_DIR\_\_ . '/../bootstrap/app.php';</code>&ensp;=>&ensp;<code>$app = require_once \_\_DIR\_\_ . '/aplikasi/bootstrap/app.php';</code><br/>

&ensp;&ensp;Tambahkan kode ini, dibawah baris variable $app diatas :<br/>
&ensp;&ensp;&ensp;<code>$app->bind('path.public', function () {</code><br/>
&ensp;&ensp;&ensp;<code>&ensp;&ensp;return \_\_DIR\_\_;</code><br/>
&ensp;&ensp;&ensp;<code>});</code><br/>
catatan: penamaan folder aplikasi sesuaikan dengan nama folder yang dibuat.

==== Pengaturan database ====
1. Buat database baru, pada menu websites di bagian submenu databases -> management.
2. Buka phpmyadmin sesuai database yang dibuat.
3. Import file sql.
4. Ubah file .env, pada bagian :<br/>
&ensp;&ensp;<code>DB_DATABASE=db_aplikasi</code><br/>
&ensp;&ensp;<code>DB_USERNAME=username_db</code><br/>
&ensp;&ensp;<code>DB_PASSWORD=pass_db</code><br/>
catatan: sesuaikan dengan nama db, username dan password yang dibuat tadi.

* Contoh struktur folder lihat susunan pada repository ini.
* Referensi: https://www.rumahweb.com/journal/cara-upload-laravel-ke-hosting-cpanel/
