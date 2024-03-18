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




## Bangun Aplikasi Pertama
### **Static Pages**




