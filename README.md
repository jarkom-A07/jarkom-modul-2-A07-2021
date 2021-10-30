# jarkom-modul-2-A07-2021

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

