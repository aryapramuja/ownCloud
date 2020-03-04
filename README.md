<h1 id="top" align="center"><img src="https://upload.wikimedia.org/wikipedia/commons/f/f6/OwnCloud_logo_and_wordmark.svg"><br />Aplikasi Web ownCloud</h1>

Table of Content:

1. [Sekilas Tentang](#sekilas-tentang)
2. [Instalasi](#instalasi)
3. [Konfigurasi](#konfigurasi)
4. [Maintenance](#maintenance)
5. [Otomatisasi](#otomatisasi)
6. [Cara Pemakaian](#cara-pemakaian)
7. [Pembahasan](#pembahasan)
8. [Referensi](#referensi)

## Sekilas Tentang
[`^kembali ke atas^`](#top)

__ownCloud__ merupakan perangkat lunak open-source untuk menyimpan dan berbagi berkas dalam awan (internet). Sang pelopor, Frank Karlitschek, merasa bahwa dunia membutuhkan sesuatu yang mudah digunakan, aman, fleksibel dalam mengatur berkas, dan tanpa mengalami kemunduran pada tempat penyimpanannya.

## Instalasi
[`^kembali ke atas^`](#top)
### Prerequisites
Install `mysql`, `php`, dan `apache`.
```sh
sudo apt install apache2 php mysql-server
```
Install ekstensi `php` yang diperlukan
```sh
sudo apt install php-gd php-simplexml php-curl php-mbstring php-zip php-dom php-xmlwriter php-intl php-mysql
```
Enable module `headers`, `unique_id`, dan `php7.2` di apache2.
```sh
sudo a2enmod headers
sudo a2enmod unique_id
sudo a2enmod php7.2
```
### Instalasi ownCloud
Buat database untuk __ownCloud__, ganti `secret` sesuai password database yang akan digunakan.
```sh
sudo mysql -u root -ve "
  CREATE DATABASE owncloud;
  CREATE USER owncloud IDENTIFIED BY 'secret';
  GRANT ALL PRIVILEGES ON owncloud.* TO owncloud;"
```
Unduh tarball __ownCloud__ versi `10.3.2` dan ekstrak ke direktori webroot
```sh
wget "https://download.owncloud.org/community/owncloud-10.3.2.tar.bz2"
sudo tar -xjf owncloud-10.3.2.tar.bz2 -C /var/www
```
Konfigurasi apache untuk ownCloud
```sh
# tambah entri konfigurasi ownCloud di apache2
sudo tee /etc/apache2/sites-available/owncloud.conf << !
Alias /owncloud "/var/www/owncloud/"

<Directory /var/www/owncloud/>
  Options +FollowSymlinks
  AllowOverride All

 <IfModule mod_dav.c>
  Dav off
 </IfModule>
</Directory>
!
# enable ownCloud
sudo ln -sf /etc/apache2/sites-available/owncloud.conf /etc/apache2/sites-enabled/owncloud.conf
```
Buka laman [http://localhost:8000/owncloud](http://localhost:8000/owncloud) untuk meneruskan instalasi.
## Konfigurasi
[`^kembali ke atas^`](#top)

Buat akun admin dan isi folder untuk data.
<a href="https://ibb.co/72dyncM"><img src="https://i.ibb.co/4PnN8yv/Screenshot-2020-03-03-17-59-34.png" alt="Screenshot-2020-03-03-17-59-34" border="0" /></a><br/>
Isi konfigurasi database sesuai dengan database yang telah dibuat.
<a href="https://ibb.co/jvSbZrv"><img src="https://i.ibb.co/qMv7FrM/Screenshot-2020-03-03-17-59-53.png" alt="Screenshot-2020-03-03-17-59-53" border="0"></a><br/>

##  Maintenance
[`^kembali ke atas^`](#top)

Setting tambahan untuk maintenance secara periodik, misalnya:
- buat backup database tiap pekan
- hapus direktori sampah tiap hari
- dll


## Otomatisasi
[`^kembali ke atas^`](#top)

Skrip shell untuk otomatisasi instalasi, konfigurasi, dan maintenance.


## Cara Pemakaian
[`^kembali ke atas^`](#top)



## Pembahasan
[`^kembali ke atas^`](#top)

- Pendapat anda tentang aplikasi web ini
    - kelebihan
    - kekurangan
- Bandingkan dengan aplikasi web lain yang sejenis


## Referensi
[`^kembali ke atas^`](#top)

Cantumkan tiap sumber informasi yang anda pakai.
