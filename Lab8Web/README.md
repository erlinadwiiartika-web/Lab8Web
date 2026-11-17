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

<img width="663" height="430" alt="Screenshot 2026-11-17 201432" src="https://github.com/user-attachments/assets/a8a64579-36e2-46b3-b3ec-fb53d6ff8f9d" />


### 2. Membuat Database, Tabel, dan Data Awal
Di phpMyAdmin (tab SQL) jalankan `CREATE DATABASE latihan1;`, lalu `CREATE TABLE data_barang (...)`, kemudian `INSERT INTO ...` (lihat `database.sql`).

<img width="875" height="433" alt="image" src="https://github.com/user-attachments/assets/c593799d-92b5-4c38-9dcf-67996d255065" />


### 3. Membuat Folder Project
Buat folder `lab8_php_database` di `htdocs`, sub-folder `gambar`, serta file `koneksi.php`, `index.php`, `tambah.php`, `ubah.php`, `hapus.php`, `style.css`.


### 4. koneksi.php
`mysqli_connect()` menghubungkan PHP ke database `latihan1` (host `localhost`, user `root`, tanpa password).

<img width="940" height="263" alt="image" src="https://github.com/user-attachments/assets/c9d32bd0-131b-40fd-93c7-588a1cafebdb" />


### 5. index.php (Read)
Menjalankan `SELECT * FROM data_barang` dan menampilkan hasilnya dalam tabel menggunakan `while` + `mysqli_fetch_array()`.

<img width="940" height="525" alt="image" src="https://github.com/user-attachments/assets/1921c048-fc9e-4780-884f-cc263ed0d66b" />


### 6. tambah.php (Create)
Form `method="post"` dengan `enctype="multipart/form-data"`. Data disimpan dengan `INSERT` (prepared statement) dan gambar dipindahkan ke folder `gambar/` memakai `move_uploaded_file()`.

<img width="940" height="568" alt="image" src="https://github.com/user-attachments/assets/c0b72a13-8cec-4c06-a8f0-3fef90a77813" />
<img width="940" height="500" alt="image" src="https://github.com/user-attachments/assets/15d6c008-6152-4059-af69-b470a0d0af6e" />


### 7. ubah.php (Update)
Mengambil data berdasarkan `id` (`$_GET`), menampilkannya di form, lalu menyimpan perubahan dengan `UPDATE`.

<img width="940" height="410" alt="image" src="https://github.com/user-attachments/assets/1e9811b1-cfb2-495b-896b-1eb3c7f74537" />
<img width="940" height="515" alt="image" src="https://github.com/user-attachments/assets/940a38e1-fd91-4e13-801c-f97a499d6a31" />


### 8. hapus.php (Delete)
Menghapus data berdasarkan `id` dengan `DELETE`, didahului konfirmasi JavaScript.

<img width="940" height="428" alt="image" src="https://github.com/user-attachments/assets/4ecdf45c-10ee-45d9-ad18-78589bca5565" />


## Perbaikan dari Kode Modul
- Urutan header Harga Beli / Harga Jual disamakan dengan isi tabel.
- Ditambahkan tautan **Tambah Barang**, **Ubah**, dan **Hapus** di `index.php`.
- Path gambar diperbaiki (database hanya menyimpan nama file; folder `gambar/` ditambahkan di `index.php`).
- `enctype="multipart/formdata"` diperbaiki menjadi `multipart/form-data` di `ubah.php`.
- Fungsi `is_select()` membandingkan dengan nilai opsi yang benar.
- Query memakai *prepared statement* untuk mencegah SQL Injection.

## Kesimpulan
Aplikasi CRUD Data Barang berhasil dibuat dan seluruh operasi Create, Read, Update, dan Delete berjalan dengan baik.
