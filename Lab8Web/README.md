# Lab8Web — Praktikum 8: PHP dan Database MySQL

| | |
|---|---|
| **Nama** | Erlina Dwi Artika |
| **Kelas** | I252A |
| **NIM** | 312510039 |
| **Mata Kuliah** | Pemrograman Web |

Aplikasi CRUD sederhana **Data Barang** menggunakan PHP (MySQLi) dan MySQL/MariaDB (XAMPP).

## Isi Repository
| File | Fungsi |
|---|---|
| `database.sql` | Membuat database `latihan1`, tabel `data_barang`, dan 3 data awal |
| `koneksi.php` | Koneksi ke database |
| `index.php` | **Read** — menampilkan data barang |
| `tambah.php` | **Create** — menambah data barang (dengan upload gambar) |
| `ubah.php` | **Update** — mengubah data barang |
| `hapus.php` | **Delete** — menghapus data barang |
| `style.css` | Tampilan halaman |
| `gambar/` | Folder penyimpanan gambar barang |
| `screenshots/` | Screenshot hasil praktikum |

## Cara Menjalankan
1. Jalankan **Apache** dan **MySQL** di XAMPP Control Panel.
2. Salin folder project ke `C:\xampp\htdocs\` dan ubah namanya menjadi `lab8_php_database`.
3. Buka `http://localhost/phpmyadmin/`, pilih tab **Impor**, lalu impor `database.sql` (atau jalankan isinya pada tab **SQL**).
4. Buka `http://localhost/lab8_php_database/` di browser.

## Langkah Praktikum

### 1. Menjalankan Apache dan MySQL
Buka XAMPP Control Panel lalu klik **Start** pada Apache dan MySQL hingga berwarna hijau.

![XAMPP](screenshots/01_xampp_control.png)

### 2. Membuat Database, Tabel, dan Data Awal
Di phpMyAdmin (tab SQL) jalankan `CREATE DATABASE latihan1;`, lalu `CREATE TABLE data_barang (...)`, kemudian `INSERT INTO ...` (lihat `database.sql`).

![Database](screenshots/02a_buat_database.png)
![Tabel](screenshots/02b_buat_tabel.png)
![Insert](screenshots/02c_insert_data.png)

### 3. Membuat Folder Project
Buat folder `lab8_php_database` di `htdocs`, sub-folder `gambar`, serta file `koneksi.php`, `index.php`, `tambah.php`, `ubah.php`, `hapus.php`, `style.css`.

![Folder](screenshots/02d_struktur_folder.png)

### 4. koneksi.php
`mysqli_connect()` menghubungkan PHP ke database `latihan1` (host `localhost`, user `root`, tanpa password).

![Koneksi](screenshots/03_koneksi_berhasil.png)

### 5. index.php (Read)
Menjalankan `SELECT * FROM data_barang` dan menampilkan hasilnya dalam tabel menggunakan `while` + `mysqli_fetch_array()`.

![Index](screenshots/04_index_awal.png)

### 6. tambah.php (Create)
Form `method="post"` dengan `enctype="multipart/form-data"`. Data disimpan dengan `INSERT` (prepared statement) dan gambar dipindahkan ke folder `gambar/` memakai `move_uploaded_file()`.

![Form tambah](screenshots/05_form_tambah_kosong.png)
![Form tambah terisi](screenshots/06_form_tambah_isi.png)
![Setelah tambah](screenshots/07_index_setelah_tambah.png)

### 7. ubah.php (Update)
Mengambil data berdasarkan `id` (`$_GET`), menampilkannya di form, lalu menyimpan perubahan dengan `UPDATE`.

![Form ubah](screenshots/08_form_ubah.png)
![Setelah ubah](screenshots/09_index_setelah_ubah.png)

### 8. hapus.php (Delete)
Menghapus data berdasarkan `id` dengan `DELETE`, didahului konfirmasi JavaScript.

![Konfirmasi hapus](screenshots/10_konfirmasi_hapus.png)
![Setelah hapus](screenshots/11_index_setelah_hapus.png)

## Perbaikan dari Kode Modul
- Urutan header Harga Beli / Harga Jual disamakan dengan isi tabel.
- Ditambahkan tautan **Tambah Barang**, **Ubah**, dan **Hapus** di `index.php`.
- Path gambar diperbaiki (database hanya menyimpan nama file; folder `gambar/` ditambahkan di `index.php`).
- `enctype="multipart/formdata"` diperbaiki menjadi `multipart/form-data` di `ubah.php`.
- Fungsi `is_select()` membandingkan dengan nilai opsi yang benar.
- Query memakai *prepared statement* untuk mencegah SQL Injection.

## Kesimpulan
Aplikasi CRUD Data Barang berhasil dibuat dan seluruh operasi Create, Read, Update, dan Delete berjalan dengan baik.
