# lab4web
<table bprder="1" cellpadding="5" cellspacing="0">
  <tbody>
  <tr>
  <td> Nama </td>
  <td> Ade maulani bilgis</td>
  </tr>
  <tr>
  <td>Prodi</td>
  <td>Teknik Informatika</td>
  </tr>
</table>

# modularisasi
Implementasikan konsep modularisasi pada kode program praktikum 3 tentang database, sehingga
setiap halamannya memiliki template tampilan yang sama.

* buatlah file **koneksi.php** untuk menghubungkan database
```
 <?php
$host = "localhost";
$user = ""; //username my sql kalian
$pass = ""; //pass my sql kalian
$db = ""; //nama database yang akan di hubungkan
$conn = mysqli_connect($host, $user, $pass, $db);
if ($conn == false)
{
echo "Koneksi ke server gagal.";
die();
} #else echo "Koneksi berhasil";
?> 
```

* lalu buatlah file **header.php** **home.php** **tambah.php** **hapus.php** dan jangan lupa untuk membuat file **footer.php**

# hasil 
! [image.png](https://github.com/forusig/lab4web/blob/fcae40774dcdce0f82f9fe0e446f5f380ae36678/gambar/img3.png)

## Membuat Routing
Routing digunakan untuk mempermudah akses halaman web agar SEO Friendly.
Langkah awal adalah menyiapkan file utama (index.php) yang berisi routing untuk mengakses banyak
halaman.
Contohnya:
* Halaman Home ( http://localhost/lab4web/lab4web/home.php )
* Halaman About ( http://localhost/lab4web/lab4web/tambah.php )

buuatlah file baru dengan nama **index.php**
```
<?php
$mod = $_REQUEST['mod'];
switch ($mod) {
case "home":
require("home.php");
break;
case "about":
require("about");
break;
else:
require("home.php");
}
?>
```
### aktuvasi mod_rewrite (.htaccess)
Mod_rewrite digunakan untuk mengubah URL dari query string menjadi SEO Friendly.
Langkah awal yang harus disiapkan adalah aktivasi mod_rewrite pada webserver Apache2 pada
configurasi **httpd.conf**.
Aktifkan LoadModule mod_rewrite dengan cara melakukan un-comment pada baris tersebut,
kemudian restart Apache2.
Langkah berikutnya adalah membuat file **.htaccess**
```
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /lab4/
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ index.php?mod=$1 [L]
</IfModule>
```

#Terimakasih !