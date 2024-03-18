# TUGAS 1 PBF Sheliya Triana WS-220302094

## Pengertian CodeIgniter
CodeIgniter adalah sebuah framework yang dikembangkan pada tahun 2006 oleh Rick Ellis. CodeIgniter berfungsi untuk web dan application development yang hadir dalam bentuk platform open-source. Framework ini diciptakan untuk para developer yang hendak membangun situs web maupun aplikasi menggunakan bahasa pemrograman PHP.

## Instalasi
CodeIgniter memiliki dua metode instalasi yang didukung: download manual, atau menggunakan Composer .

### **Instalasi Manual**
1. Download manual file CodeIgniter4 di web resminya [CodeIgniter](https://codeigniter.com/download)
   
2. Hasil download tadi akan berbentuk file ZIP.
Ekstrak file .zip tersebut pada direktori root web server kita. Jika menggunakan Laragon Server, ekstrak filenya di C:/laragon/www

3. Hasil ekstrak tadi akan menghasilkan sebuah folder, silahkan rename atau ganti namanya menjadi ci4.

4. Untuk menjalankan Codeigniter 4 kamu harus menggunakan terminal dan masuk ke folder ci4 tersebut. 
   Ketik perintah berikut pada terminal untuk menjalankan:
   ```shell
   $ cd ci4
   $ php spark serve
   ```
   
5. Perintah diatas akan menjalankan Codeigniter 4 di port 8080. Proses running akan terus berjalan sampai menekan tombol CTRL+C untuk memberhentikannya.
Untuk melihat hasilnya, buka browser dan ketikkan alamat http://localhost:8080/.
![image](https://github.com/sheliyatrn/TUGAS-1_PBF/assets/134477604/ccad96a0-17a2-4b86-a115-44b151229b6f)

### **Instalasi via Composer**
1. Buka terminal dan arahkan ke direktori root web server yang kita gunakan ke C:/laragon/www.
   Ketikan perintah berikut untuk mendownload dan menginstal Codeigniter 4:
   ```shell
   $ composer create-project codeigniter4/appstarter nama-projek
   ```
   ![image](https://github.com/sheliyatrn/TUGAS-1_PBF/assets/134477604/3a56d43f-c0e8-4781-9159-c0e0de0d663d)

2. Perintah di atas akan menghasilkan sebuah project Codeigniter 4 dengan nama ci4app. Cepat atau lambatnya proses tersebut dipengaruhi oleh koneksi internet.
   
3. Jika proses instalasi sudah selesai, arahkan terminal ke folder ci4app tersebut. Gunakan perintah: 
   ```shell
   $ php spark serve
   ```

4. Jika proses instalasi berhasil, secara otomatis Codeigniter 4 akan berjalan di port 8080. Untuk menghentikan proses, ketik CTRL+C pada terminal.
   
   ![image](https://github.com/sheliyatrn/TUGAS-1_PBF/assets/134477604/a9e8852d-bebf-4c62-bf00-8c98b5eeef1b)

6. Untuk melihat hasilnya, buka browser dan arahkan ke alamat http://localhost:8080/.
   ![image](https://github.com/sheliyatrn/TUGAS-1_PBF/assets/134477604/ccad96a0-17a2-4b86-a115-44b151229b6f)

## Konfigurasi
### **Konfigurasi Situs**
Melakukan konfigurasi dasar pada project melalui file dapat dengan `app/Config/App.php` atau `.env`

1. Menetapkan URL dasar pada **$baseURL (App.php) atau app.baseURL (.env)**
   ```php
   public string $baseURL = 'http://localhost:8080/'; // menggunakan file app.php
   app.baseURL = 'http://localhost:8080' // menggunakan .env
   ```
     
2. Menentukan index page
   Jika tidak ingin menyertakan **index.php** di URI situs setel `$indexPage`ke `''` pada **`app/Config/App.php`**.
   ```php
   public string $indexPage = '';
   ```

### **Konfigurasi Koneksi Database**
Melakukan konfigurasi database pada project dapat dengan melalui file `app/Config/Database.php` atau `.env`

1.  Ubah ke mode development
   setel `CI_ENVIRONMENT`yang defaultnya `production` ubah ke `development` dalam file **.env** untuk memanfaatkan alat debugging yang disediakan.

   ![image](https://github.com/sheliyatrn/TUGAS-1_PBF/assets/134477604/b0614a45-6043-40ed-b40e-4370e29282d0) -> ![image](https://github.com/sheliyatrn/TUGAS-1_PBF/assets/134477604/0251a323-9ce5-49a7-844c-c880bd54c97c)

# Bangun Aplikasi Pertama
### Eror

## **Static Pages**
### **Setting Routing**
Buka file route yang berlokasi di `app/Config/Routes.php` yang berisi
```shell
<?php

use CodeIgniter\Router\RouteCollection;

/**
 * @var RouteCollection $routes
 */
$routes->get('/', 'Home::index');
```
Tambahkan baris berikut, setelah arahan rute untuk '/' , untuk menyambungkan dengan `Pages.php. yang akan dibuat di Controllers.
```shell
use App\Controllers\Pages;

$routes->get('pages', [Pages::class, 'index']);
$routes->get('(:segment)', [Pages::class, 'view']);
```
### **Membuat Controller**
#### **Membuat Page Controller**
Buat file pages controllers di folder `app/Controllers/Pages.php` dengan kode berikut.
```shell
<?php

namespace App\Controllers;

class Pages extends BaseController
{
   //http://localhost:8080/pages menampilkan index() welcome_message
    public function index()
    {
        return view('welcome_message');
    }

    public function view($page = 'home')
    {
        // ...
    }
}
```

#### **Membuat Views**
Kita akan membuat 2 views, yaitu page header dan footer.

1. Header
   Buat file header di `app/Views/templates/header.php` dan isikan kode berikut :
   ```shell
   <!doctype html>
<html>

<head>
    <title>Tutorial CodeIgniter</title>
</head>

<body>

    <h1><?= esc($title) ?></h1>
    <!-- esc fungsi global yang disediakan oleh CodeIgniter untuk membantu mencegah serangan XSS -->
```
Header berisi kode HTML dasar yang ingin di tampilkan sebelum memuat tampilan utama, bersama dengan judul,serta menampilkan $title variabel, yang akan kita definisikan nanti di controller. Berikut tampilan header

2. Footer
   Buat file footer di `app/Views/templates/footer.php` dan isikan kode berikut :
``shell
<em>&copy; 2024</em>
</body>

</html>
```
### **Menambah Logika Controller**
#### **Membuat home.php & about.php**
Tambahkan folder `pages` di `app/Views/` lalu tambahkan dua file bernama `home.php` dan `about.php` pada `app/Views/pages/`.

1. File `home.php` dengan kode berikut :
```php
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Home Page</title>
</head>

<body>
    <h1>Selamat datang di Home Page</h1>
</body>

</html>
```
2. File `about.php` dengan kode berikut :
```shell
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About Page</title>
</head>

<body>
    <h1>Tentang saya</h1>
    <p>Hai semuanya. Nama saya Sheliya Triana WS, Mahasiswa Politeknik Negeri Cilacap</p>
</body>

</html>
```

3. Lengkapi controller pages
```shell
<?php

namespace App\Controllers;

use CodeIgniter\Exceptions\PageNotFoundException; //untuk mengimpor kelas PageNotFoundException
//CodeIgniter\Exceptions. tidak ada folder fisik yang secara langsung menampungnya di struktur proyek standar ini berasal dari default sistem ci

class Pages extends BaseController
{
    //http://localhost:8080/pages menampilkan index() welcome_message
    public function index()
    {
        // Menampilkan halaman utama (welcome_message.php)
        return view('welcome_message');
    }

    public function view($page = 'home')
    {
        // ...

        // Mengecek apakah halaman yang diminta ada
        if (! is_file(APPPATH . 'Views/pages/' . $page . '.php')) {
            // Whoops, we don't have a page for that!
            // Jika tidak ada, lempar PageNotFoundException
            throw new PageNotFoundException($page);
        }

        // Mengatur judul halaman berdasarkan nama halaman
        $data['title'] = ucfirst($page); // Capitalize the first letter

         // Memuat template header, halaman statis (home, about), dan footer
        return view('templates/header', $data)
            . view('pages/' . $page)
            . view('templates/footer');
    }
}
```

### **Jalankan**

1. Buka file home pada browser `localhost:8080/home`
   
2. Buka file about pada browser `localhost:8080/about`



