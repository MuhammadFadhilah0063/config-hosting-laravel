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
4. Buka file index.php. Ubah pada bagian :
      require __DIR__ . '/../vendor/autoload.php';             =>  require __DIR__ . '/aplikasi/vendor/autoload.php';
      $app = require_once __DIR__ . '/../bootstrap/app.php';   =>  $app = require_once __DIR__ . '/aplikasi/bootstrap/app.php';

      Tambahkan kode ini, dibawah baris variable $app diatas :
         $app->bind('path.public', function () {
            return __DIR__;
         });
   catatan: penamaan folder aplikasi sesuaikan dengan nama folder yang dibuat.

==== Pengaturan database ====
1. Buat database baru, pada menu websites di bagian submenu databases -> management.
2. Buka phpmyadmin sesuai database yang dibuat.
3. Import file sql.
4. Ubah file .env, pada bagian :
      DB_DATABASE=db_aplikasi
      DB_USERNAME=username_db
      DB_PASSWORD=pass_db
   catatan: sesuaikan dengan nama db, username dan password yang dibuat tadi.
6. 
