<b> TUGAS 2 PKSJ </b>
# SQL Injection

## Anggota Kelompok :
1. Aldi Febriansyah - 5114100015
1. Trastian Satria W - 5114100016
1. Kevin A Fachreza - 5114100128



## 1. Install Wordpress pada Kali
1. Install Linux, Apache, MySql, dan PHP
1. Login ke Mysql root
1. Buat Database WP
1. Buat User WP
1. Beri Hak Akses
1. Flush Aturan Hak Akses
1. Keluar dari Mysql
1. Download WP terbaru
1. Ekstrak file 
1. Download library tambahan seperti php5-gd
1. Pindah ke direktori WP
1. Buka file konfigurasi dan ubah DB_NAME, DB_USER, dan DB_PASSWORD sesuai dengan value yang telah ditentukan
1. Salin isi dari direktori wordpress ke /var/www/html/
1. Ubah hak kepemilikan file dan folder
1. Buka web browser dan masukkan url wordpress. Seharusnya sudah tertampil
1. Masukkan data data yang digunakan untuk membuat akun admin
1. Login ke WP menggunakan akun yang telah dibuat

## 2. Install Plugin Wordpress
- Plugin CP Reservation Calendar 1.6
1. Di command line/terminal/SSH komputer webserver, pastikan anda berada di direktori wordpress anda
```
cd {direktori web server}/{nama folder}
cd /var/www/html/wordpress
```

2. Pindah ke folder plugins
```
cd wp-content
cd plugin
```

3. Download plugin CP Reservation Calendar 
```
wget https://downloads.wordpress.org/plugin/cp-reservation-calendar.1.1.6.zip
```

4. Unzip

```
unzip cp-reservation-calendar.1.1.6.zip
```

5. Install
```
apt-get install unzip
```

6. Setelah selesai, login ke dalam wordpress yang telah diinstall. Setelah itu, sidebar bagian Plugins, klik di bagian Installed Plugin.

7. Klik Activate pada plugin Cp reservation calendar

8. Agar dapat di injection, maka kita membuat konten CP Reservation calendar ke dalam wordpress agar dapat diakses. Buat post baru melalui posts -> add new

9. Setelah muncul halaman new post, klik add media dan tambahkan CP Reservation Calendar

10. Lalu klik publish

11. Seharusnya tampil post kira kira seperti ini


# Plugin League Manager

1. Plugin Wordpress League Manager di https://wordpress.org/plugins/leaguemanager/developers/

2. Masuk ke dashboard WP lalu klik add new pada Plugins

3. Upload file yang telah di download, league manager tadi lalu klik install now

4. Setelah install berhasil, klik activate plugin

5. Pindah ke menu League Manager, lalu buat pertandingan

6. Buat liga baru

7. Buat Season Baru

8. Masukkan tahun season dan jumlah pertandingan per matchday

9. Buat team, dan isi keterangan

10. Buat team lain

11. Buat pertandingan

12. Berikut adalah hasil dari buat tim dan pertandingan

13. Hasil akhir, akses vulnerability dengan paremeter /?match=1 dapat diakses

# Plugin Video Player

1. Download plugin Wordpress Video Player

2. Add New Plugins

3. Upload file plugin WP Video Player

4. Tampilan ketika plugin berhasil diinstall, klik Activate Plugin

5. Masuk ke plugin Video Player

6. Klik add a player

7. Masukkan prioritas, judul, desain, dan playlist kemudian klik save.

8. Tampilan player sudah tersimpan

9. Pilih post pada wordpress yang sudah terbuat

10. Untuk menambahkan Video Player, klik Insert Spider Video Player

11. Pilih player yang ingin ditampilkan

12. Video Player telah ditambahkan pada post

13. Tampilan Video Player pada Wordpress

## Uji Penetrasi SQL Injection

# . Plugin Video Player dengan tools WPScan dan Mitmproxy

