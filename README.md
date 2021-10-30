# Jarkom-Modul-2-A07-2021
Laporan resmi berisi dokumentasi soal Jarkom Modul 2.
---
Kelompok A-07:
- [Arkan Aulia Farhan](): 05111940000128
- [Muchamad Maroqi Abdul Jalil](https://github.com/maroqijalil): 05111940000143
- [Syamil Difaul Haq Sukur](https://github.com/Syamil28): 05111940000196
---

## Soal praktikum:

Luffy adalah seorang yang akan jadi Raja Bajak Laut. Demi membuat Luffy
menjadi Raja Bajak Laut, Nami ingin membuat sebuah peta, bantu Nami
untuk membuat peta berikut:

![](.//media/image5.png)

EniesLobby akan dijadikan sebagai DNS Master, Water7 akan dijadikan DNS
Slave, dan Skypie akan digunakan sebagai Web Server. Terdapat 2 Client
yaitu Loguetown, dan Alabasta. Semua node terhubung pada router Foosha,
sehingga dapat mengakses internet (1).

Luffy ingin menghubungi Franky yang berada di EniesLobby dengan denden
mushi. Kalian diminta Luffy untuk membuat website utama dengan mengakses
**franky.yyy.com** dengan alias **www.franky.yyy.com** pada folder
kaizoku (2). Setelah itu buat subdomain **super.franky.yyy.com** dengan
alias **www.super.franky.yyy.com** yang diatur DNS nya di EniesLobby dan
mengarah ke Skypie(3). Buat juga reverse domain untuk domain utama (4).
Supaya tetap bisa menghubungi Franky jika server EniesLobby rusak, maka
buat Water7 sebagai DNS Slave untuk domain utama (5). Setelah itu
terdapat subdomain **mecha.franky.yyy.com** dengan alias
**www.mecha.franky.yyy.com** yang didelegasikan dari EniesLobby ke
Water7 dengan IP menuju ke Skypie dalam folder sunnygo(6). Untuk
memperlancar komunikasi Luffy dan rekannya, dibuatkan subdomain melalui
Franky dengan nama **general.mecha.frank.yyy.com** dengan alias
**www.general.mecha.franky.yyy.com** yang mengarah ke Skypie(7).

\(8) Setelah melakukan konfigurasi server, maka dilakukan konfigurasi
Webserver. Pertama dengan webserver
[**www.franky.yyy.com**](http://www.franky.com). Pertama, luffy
membutuhkan webserver dengan DocumentRoot pada /var/www/franky.yyy.com.
(9) Setelah itu, Luffy juga membutuhkan agar url
[**www.franky.yyy.com/index.php/home**](http://www.franky.com/index.php/home)
dapat menjadi menjadi
[**www.franky.yyy.com/home**](http://www.franky.com/home).

\(10) Setelah itu, pada subdomain
[**www.super.franky.yyy.com**](http://www.super.franky.com), Luffy
membutuhkan penyimpanan aset yang memiliki DocumentRoot pada
/var/www/super.franky.yyy.com .(11) Akan tetapi, pada folder /public,
Luffy ingin hanya dapat melakukan directory listing saja.(12) Tidak
hanya itu, Luffy juga menyiapkan error file 404.html pada folder /errors
untuk mengganti error kode pada apache . (13) Luffy juga meminta Nami
untuk dibuatkan konfigurasi virtual host. Virtual host ini bertujuan
untuk dapat mengakses file asset
**[www.super.franky.yyy.com/](http://www.super.franky.xxx.com/js)public/js**
menjadi
[**www.super.franky.yyy.com/js**](http://www.super.franky.xxx.com/js).

\(14) Dan Luffy meminta untuk web
[**www.general.mecha.franky.yyy.com**](http://www.mecha.franky.com)
hanya bisa diakses dengan port 15000 dan port 15500 (15) dengan
authentikasi username luffy dan password onepiece dan file di
/var/www/general.mecha.franky.yyy (16) Dan setiap kali mengakses IP
EniesLobby akan diahlikan secara otomatis ke
[**www.franky.yyy.com**](http://www.franky.xxx.com) (17). Dikarenakan
Franky juga ingin mengajak temannya untuk dapat menghubunginya melalui
website [w**ww.super.franky.yyy.com**](http://www.super.franky.com), dan
dikarenakan pengunjung web server pasti akan bingung dengan randomnya
images yang ada, maka Franky juga meminta untuk mengganti request gambar
yang memiliki substring "franky" akan diarahkan menuju franky.png. Maka
bantulah Luffy untuk membuat konfigurasi dns dan web server ini!

## Jawaban:

Karena kelompok kami adalah A07 maka kami menggunakan IP: 192.171.x.x

## no. 1
Konfigurasi Node

### Jawab
-   Foosha

Melakukan konfigurasi Foosha sebagai Router dari semua device nantinya.

![](.//media/image35.png)

Memasukkan perintah berikut agar node dapat terhubung internet.

![](.//media/image3.png)

-   Loguetown

Melakukan konfigurasi pada sesuai dengan alokasi IP yang diperuntukkan,
yaitu 192.171.1.2.

![](.//media/image10.png)


Uji koneksi pada node ini.

![](.//media/image21.png)


-   Alabasta

Melakukan konfigurasi pada sesuai dengan alokasi IP yang diperuntukkan,
yaitu 192.171.1.3.

![](.//media/image6.png)


Uji koneksi pada node ini.

![](.//media/image18.png)


-   EniesLobby

Melakukan konfigurasi pada sesuai dengan alokasi IP yang diperuntukkan,
yaitu 192.171.2.2.

![](.//media/image4.png)


Uji koneksi pada node ini.

![](.//media/image34.png)


-   Water7

Melakukan konfigurasi pada sesuai dengan alokasi IP yang diperuntukkan,
yaitu 192.171.2.3.

![](.//media/image12.png)


Uji koneksi pada node ini.

![](.//media/image29.png)


-   Skypie

Melakukan konfigurasi pada sesuai dengan alokasi IP yang diperuntukkan,
yaitu 192.171.2.4.

![](.//media/image24.png)


Uji koneksi pada node ini.

![](.//media/image16.png)


## no. 2
Membuat domain franky.A07.com dengan alias www

### Jawab
Menuliskan perintah-perintah yang digunakan ke dalam bash script di
EniesLobby. Perintah ini terdiri dari instalasi package bind9, kemudian
dilanjut dengan penambahan konfigurasi pada named.conf.local dan pada
kaizoku/franky.A07.com.

![](.//media/image14.png)

Untuk dapat memastikan pembuatan domain berhasil maka dilakukan ping
terhadap domain www.franky.A07.com dengan mengarahkan nameserver pada
EniesLobby.

![](.//media/image22.png)


## no. 3
Membuat domain super.franky.A07.com dengan alias www.super.franky.A07.com

### Jawab
Menuliskan perintah-perintah yang digunakan ke dalam bash script di
EniesLobby. Perintah ini adalah melakukan penambahan subdomain super
pada kaizoku/franky.A07.com.

![](.//media/image8.png)


Untuk dapat memastikan pembuatan subdomain berhasil maka dilakukan ping
terhadap domain www.super.franky.A07.com dengan mengarahkan nameserver
pada EniesLobby.

![](.//media/image23.png)


## no. 4
Membuat reverse domain utama

### Jawab
Menuliskan perintah-perintah yang digunakan ke dalam bash script di
EniesLobby. Perintah ini terdiri dari instalasi penambahan konfigurasi
pada named.conf.local untuk reverse domain dan pada
kaizoku/2.171.192.in-addr.arpa.

![](.//media/image26.png)


Untuk dapat memastikan pembuatan reverse domain berhasil maka dilakukan
pengecekan host pada IP 192.171.2.2 dengan mengarahkan nameserver pada
EniesLobby. Namun sebelumnya perlu dilakukan instalasi dnsutils dengan
mengarahkan nameserver pada router untuk mendapatakan akses internet.

![](.//media/image7.png)
![](.//media/image19.png)


## no. 5
Membuat DNS Slave dari EniesLobby ke Water7

### Jawab
-   EniesLobby

Menuliskan perintah-perintah yang digunakan ke dalam bash script di
EniesLobby. Perintah ini adalah melakukan penambahan konfigurasi pada
named.conf.local.

![](.//media/image17.png)


-   Water7

Lalu pada Water7 perlu dilakukan konfigurasi juga pada named.conf.local
namun dengan type slave.

![](.//media/image11.png)


Untuk dapat memastikan pembuatan dns slave berhasil maka dilakukan ping
terhadap domain.franky.A07.com dengan mengarahkan nameserver pada
EniesLobby dan Water7 namun EniesLobby dalam kondisi bind9 stop.

![](.//media/image32.png)


## no. 6
Melakukan delegeasi mecha.franky.A07.com ke Water7 dengan mengarahkan ke Skypie

### Jawab
-   EniesLobby

Melakukan penambahan konfigurasi untuk subdomain mecha.franky.A07.com
yang diarahkan ke IP Water7.

![](.//media/image33.png)


Mengubah konfigurasi pada named.conf.options.

![](.//media/image15.png)


Mengubah konfigurasi pada domain franky.A07.com di named.conf.local
dengan mengarahkan pada IP Water7.

![](.//media/image31.png)


Setelah selesai maka dilakukan restart pada bind9.

-   Water7

Mengubah konfigurasi pada named.conf.options.

![](.//media/image15.png)


Melakukan konfigurasi pada named.conf.local dengan menambahkan subdomain
mecha.franky.A07.com.

![](.//media/image30.png)


Terakhir menambahkan konfigurasi pada sunnygo/mecha.franky.A07.com,
kemudian restart bind9.

![](.//media/image20.png)


## no. 7
Membuat subdomain general.mecha.franky.A07.com di Water7 dengan mengarahkan ke Skypie

### Jawab
Melakukan penambahan konfigurasi untuk subdomain
general.mecha.franky.A07.com yang diarahkan ke IP Skypie, kemudian
restart bind9.

![](.//media/image28.png)


## no. 8

Setelah melakukan konfigurasi server, maka dilakukan konfigurasi Webserver. Pertama dengan webserver www.franky.yyy.com. Pertama, luffy membutuhkan webserver dengan DocumentRoot pada /var/www/franky.yyy.com

### Jawab

● Pada Skypie
1. Install paket yang diperlukan terlebih dahulu (Masukkan pada /root/.bashrc)
pada Skpie masukkan

``
 vim /root/.bashrc
``
kemudian copy

``
echo nameserver 192.172.122.1 > /etc/resolv.conf
apt-get update
apt-get install apache2 -y
apt-get install php -y
apt-get install libapache2-mod-php7.0 -y
apt-get install nano
apt-get install unzip -y
apt-get install wget -y
``
setelah itu jalankan menggunakan ``bash /root/.bashrc`` pada terminal Skypie

2. Masukkan perintah buat directory, download file yang ingin di download di command.sh, pindahkan file yang di download ke directory yang sudah ditentukan, dan lakukan copy pada 000-default.conf ke franky.a07.com.conf.
Pada terminal skypie jalankan perintah vim ``command.sh``
kemudian masukkan:
``
mkdir /var/www/franky.A07.com
wget https://raw.githubusercontent.com/FeinardSlim/Praktikum-Modul-2-Jarkom/main/franky.zip
unzip franky.zip
mv franky/home.html /var/www/franky.A07.com
mv franky/index.php /var/www/franky.A07.com
cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/franky.A07.com.conf
``
setelah itu pada terminal Skypie jalankan dengan perintah ``bash command.sh``

![](./images/Screenshot(217).png)

3. Lakukan edit franky.A07.com.conf, pada kasus ini kami buat script bernama general-script.sh dengan comand v``im franky.A07.com.conf`` dan melakukan perintah seperti berikut:
``
echo '<VirtualHost *:80>
 
            ServerAdmin webmaster@localhost
            ServerName franky.A07.com
            ServerAlias www.franky.A07.com
            DocumentRoot /var/www/franky.A07.com
 ErrorLog ${APACHE_LOG_DIR}/error.log
 CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>' > /etc/apache2/sites-available/franky.A07.com.conf
``
setelah itu jalankan dengan perintah bash ``franky.A07.com.conf``

4. Aktifkan konfigurasi franky.A07.com dengan menggunakan perintah 
``
cd /etc/apache2/sites-available
a2ensite franky.A07.com.conf
``
pada terminal Skypie
5. Restart apache2 pada terminal Skypie dengan commmand
``service apache2 restart``
● Pada Loguetown dan Alabasta
   1. install lynx dengan perintah ``vim /root/.bashrc`` yang kemudian masukkan commmand berikut di dalamnya
``
echo nameserver 192.172.122.1 > /etc/resolv.conf
apt-get update
apt-get install sudo
apt-get install nano
apt-get install dnsutils -y
apt-get install lynx -y
``
2. Buka franky.A07.com dengan perintah
``
lynx franky.A07.com
``

![](./images/Screenshot(216).png)

## no.9

Setelah itu, Luffy juga membutuhkan agar url www.franky.yyy.com/index.php/home dapat menjadi menjadi www.franky.yyy.com/home

### Jawab

● Pada Skypie
   1. Pada no9.sh di beri perintah terlebih dahulu dengan ``vim no9.sh``, setelah itu  edit .htaccess pada index.php di dalamnya.
``
echo '<VirtualHost *:80>
 
            ServerAdmin webmaster@localhost
            ServerName franky.A07.com
            ServerAlias www.franky.A07.com
            DocumentRoot /var/www/franky.A07.com
 
            <Directory /var/www/franky.A07.com>
            Options +FollowSymLinks -Multiviews
            AllowOverride All
            </Directory>
 ErrorLog ${APACHE_LOG_DIR}/error.log
 CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>' > /etc/apache2/sites-available/franky.A07.com.conf
 
echo 'RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^home$ /index.php/home
' > /var/www/franky.A07.com/.htaccess
``
kemudian jalankan dengan perintah bash ``no9.sh``

   2.  Setelah itu a2enmod franky.A07.com.conf
   3. Lakukan restart dengan service apache2 restart
● Pada Loguetown dan Alabasta
Lakukan ``lynx franky.A07.com/home``

![](./images/Screenshot(215).png)

## no. 10

Setelah itu, pada subdomain www.super.franky.yyy.com, Luffy membutuhkan penyimpanan aset yang memiliki DocumentRoot pada /var/www/super.franky.yyy.com

### Jawab

● Pada Skypie
   1. Pada command2.sh beri perintah vim command2.sh, dengan langkah membuat directory terlebih dahulu, setelah itu mendownload file zip dan meng unzip file tersebut.Lalu dilakukan pemindahan data dari super.franky ke super.franky.A07.com. Setelah itu lakukan copy pada 000-default.conf dengan command berikut
`` 
mkdir /var/www/super.franky.A07.com
wget https://raw.githubusercontent.com/FeinardSlim/Praktikum-Modul-2-Jarkom/main/super.franky.zip
unzip super.franky.zip

mv super.franky/error /var/www/super.franky.A07.com
mv super.franky/public /var/www/super.franky.A07.com
cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/super.franky.A07.com.conf
``
kemudian jalankan dengan ``bash comman2.sh``
1. Edit file franky.A07.super dengan perintah ``vim franky.A07.super`` kemudian masukkan kode berikut ke dalam franky.A07.super tersebut
``
echo '<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName super.franky.A07.com
    ServerAlias www.super.franky.A07.com
    DocumentRoot /var/www/super.franky.A07.com
 ErrorLog ${APACHE_LOG_DIR}/error.log
 CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>' > /etc/apache2/sites-available/super.franky.A07.com.conf
kemudian dijalankan dengan perintah bash franky.A07.super
``
2. Setelah itu lakukan ``a2ensite super.franky.A07.com`` pada terminal Skypie
3. restart node dengan comand ``service apache2 restart``
● Pada EniesLobby
   1. Lakukan konfigurasi pada zone super.franky.A07.com
   2. Lakukan restart bind9 dengan command
   ``
        Service bind9 restart
    ``
● Pada Loguetown dan Alabasta
   1. Lakukan ``lynx www.super.franky.yyy.com``
   
![](./images/Screenshot(214).png)

## no. 11

Akan tetapi, pada folder /public, Luffy ingin hanya dapat melakukan directory listing saja

### Jawab

 ●       Pada Skypie
1. Lakukan edit pada super.franky.A07.com.conf dengan command ``vim super.franky.A07.com.conf`` kemudian  tambahkan kode berikut
   
    ``
        <Directory /var/www/super.franky.A07.com/public>
            Options +Indexes
        </Directory>
    ``
2. Lakukan ``a2ensite super.franky.A07.com.conf``
3. Lakukan perintah service apache2 restart
 
●       Pada Loguetown dan Alabasta
1. lynx super.franky.A07.com/public

![](./images/Screenshot(213).png)

## no. 12

Tidak hanya itu, Luffy juga menyiapkan error file 404.html pada folder /error untuk mengganti error kode pada apache

### Jawab

●       Pada Skypie
1. Lakukan edit pada super.franky.A07.com.conf dengan command ``vim super.franky.A07.com.conf`` kemudian  tambahkan kode berikut
   ``ErrorDocument 404 /error/404.html``
2.   Lakukan ``a2ensite super.franky.A02.com.conf``
3.   Lakukan perintah ``service apache2 restart``
●       Pada Loguetown dan Alabasta
1. kemudian lakukan ``lynx super.franky.A07.com/(apapun yang salah)``

## no. 13

Luffy juga meminta Nami untuk dibuatkan konfigurasi virtual host. Virtual host ini bertujuan untuk dapat mengakses file asset www.super.franky.yyy.com/public/jsmenjadi www.super.franky.yyy.com/js

### Jawab

●       Pada Skypie
1. Lakukan edit pada super.franky.A07.com.conf dengan command vim super.franky.A07.com.conf kemudian  tambahkan kode berikut
``
    	Alias "/js" "/var/www/super.franky.A07.com/public/js"
``
2. Lakukan ``a2ensite super.franky.A07.com.conf``
3. Lakukan perintah ``service apache2 restart``
●       Pada Loguetown dan Alabasta
4. lakukan ``lynx super.franky.A07.com/js``

![](./images/Screenshot(212).png)

## no. 14

Luffy meminta untuk web www.general.mecha.franky.yyy.com hanya bisa diakses dengan port 15000 dan port 15500.

### Jawab

Pertama-tama di skypie, pada folder `/etc/apache2/sites-available`, copy file `000-default.conf` ke file bernama `general.mecha.franky.A07.com.conf`. Lalu file `general.mecha.franky.A07.com.conf` ditambahkan `<VirtualHost *:15000 *:15500>`, `ServerName general.mecha.franky.A07.com`, `ServerAlias www.general.mecha.franky.A07.com`, dan `DocumentRoot /var/www/general.mecha.franky.A07.com`. 

![](./images/Picture1.png)

Kemudian tambahkan port 15000 dan 15500 pada file `/etc/apache2/ports.conf` dengan menambahkan:

```
    Listen 15000
    Listen 15500
```

![](./images/Picture2.png)

Kemudian digunakan command `mkdir /var/www/general.mecha.franky.A07.com` untuk membuat directory baru dengan nama `general.mecha.franky.A07.com` pada `/var/www/`. lalu copy isi dari folder `general.mecha.franky` ke `/var/www/general.mecha.franky.A07.com`. Setelah itu general.mecha.franky tadi perlu di a2ensite dengan command `a2ensite general.mecha.franky.A07.com` lalu di `service apache2 restart`

untuk mencobanya di LogueTown, digunakan command `lynx http://192.172.2.4:15000` dan `lynx http://192.172.2.4:15500`. Hasilnya dengan kedua port tersebut akan terakses general.mecha.franky.A07.com tersebut.

![](./images/Picture3.png)

## no. 15

dengan authentikasi username luffy dan password onepiece dan file di /var/www/general.mecha.franky.yyy

### Jawab

Untuk authentikasi login, pertama jalankan command `htpasswd -c /etc/apache2/.htpasswd luffy` untuk menyimpan username dan password kedalam file `/etc/apache2/.htpasswd` dengan user `luffy`, lalu akan muncul prompt untuk memasukkan dan mengkonfirmasi password.

Kemudian, edit file `/etc/apache2/sites-available/general.mecha.franky.A07.com.conf` dengan menambahkan:

```
    <Directory /var/www/general.mecha.franky.A07.com>
        Options +FollowSymLinks -Multiviews
        AllowOverride All
    </Directory>
```
hal ini berguna untuk mengoveride default sitenya.

![](./images/Picture4.png)

Lalu, edit file `/var/www/general.mecha.franky.A07.com/.htaccess` menjadi:

```
    AuthType Basic
    AuthName "Restricted Content"
    AuthUserFile /etc/apache2/.htpasswd
    Require valid-user
```
Dengan ini, sebelum site terakses, akan diminta username yang dinama disini dipakai "luffy" dan password "onepiece"

![](./images/Picture5.png)


## no. 16

Dan setiap kali mengakses IP EniesLobby akan diahlikan secara otomatis ke www.franky.yyy.com

### Jawab

pertama-tama edit file `/var/www/html/.htaccess` dengan menambahkan:

```
    RewriteEngine On
    RewriteBase /
    RewriteCond %{HTTP_HOST} ^192\.172\.2\.4$
    RewriteRule ^(.*)$ http://www.franky.A07.com [L,R=301]
```

![](./images/Picture6.png)

Kemudian, edit file `/etc/apache2/sites-available/000-default.conf` dengan menambahkan:

```bash
    <Directory /var/www/html>
        Options +FollowSymLinks -Multiviews
        AllowOverride All
    </Directory>
```
hal ini berguna untuk mengoveride default sitenya.

![](./images/Picture7.png)

untuk mencobanya di LogueTown, digunakan command `lynx http://192.172.2.4` lalu akan terakses franky.A07.com dari akses ip tersebut.

![](./images/Picture8.png)

## no. 17

Dikarenakan Franky juga ingin mengajak temannya untuk dapat menghubunginya melalui website www.super.franky.yyy.com, dan dikarenakan pengunjung web server pasti akan bingung dengan randomnya images yang ada, maka Franky juga meminta untuk mengganti request gambar yang memiliki substring “franky” akan diarahkan menuju franky.png.

### Jawab

Pertama, edit file `/etc/apache2/sites-available/super.franky.A07.com.conf` dengan menambahkan:

```
    <Directory /var/www/super.franky.A07.com>
        Options +FollowSymLinks -Multiviews
        AllowOverride All
    </Directory>
```

![](./images/Picture9.png)

Kemudian, edit file `/var/www/super.franky.A07.com/.htaccess` dengan menambahkan:

```
    RewriteEngine On
    RewriteRule ^(.*)franky(.*)(jpg|gif|png)$ http://super.franky.A07.com/public/images/franky.png [L,R]
```

![](./images/Picture10.png)

untuk mencobanya di LogueTown, digunakan command `lynx www.super.franky.A07.com/public/images/franky.jpg` dan semua image di `www.super.franky.A07.com/public/images/` akan
terakses ke `lynx www.super.franky.A07.com/public/images/franky.jpg`.

![](./images/Picture11.png)

