<b> TUGAS 2 PKSJ </b>
# SQL Injection

## Anggota Kelompok :
1. Aldi Febriansyah - 5114100015
1. Trastian Satria W - 5114100016
1. Kevin A Fachreza - 5114100128



## 1. Install Wordpress pada Ubuntu Server
1. Install Linux, Apache, MySql, dan PHP
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/apache_install/1.PNG?raw=true)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/apache_install/2.PNG?raw=true)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/apache_install/3.PNG?raw=true)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/apache_install/4.PNG?raw=true)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/apache_install/5.PNG?raw=true)

1. Login ke Mysql root
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/make_sql_db/new1.PNG?raw=true)
1. Buat Database WP
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/make_sql_db/new2.PNG?raw=true)
1. Buat User WP
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/make_sql_db/new3.PNG?raw=true)
1. Beri Hak Akses
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/make_sql_db/new4.PNG?raw=true)
1. Flush Aturan Hak Akses
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/make_sql_db/new5.PNG?raw=true)

![Alt text]()
1. Download WP terbaru
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/install_wordpress/1.PNG?raw=true)
1. Ekstrak file
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/install_wordpress/2.PNG?raw=true)
1. Add Repository tambahan dan Download library tambahan seperti php7.0-gd, php7.0-cli, libssh2, php-ssh2
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/install_wordpress/5.PNG?raw=true)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/install_wordpress/7.PNG?raw=true)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/install_wordpress/8.PNG?raw=true)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/install_wordpress/9.PNG?raw=true)
1. Pindah ke direktori WP dan salin config sample WP
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/wp_conf/new1.PNG?raw=true)
1. Buka file konfigurasi dan ubah DB_NAME, DB_USER, dan DB_PASSWORD sesuai dengan value yang telah ditentukan
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/wp_conf/new2.PNG?raw=true)
1. Salin isi dari direktori wordpress ke /var/www/html/mywp
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/wp_conf/new3.PNG?raw=true)
1. Ubah hak kepemilikan file dan folder
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/wp_conf/new4.PNG?raw=true)
1. Buat sebuah folder bernama uploads dalam wp-content untuk tempat kita mengupload plugins dan ubah hak kepemilikan
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/wp_conf/new5.1.PNG?raw=true)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/wp_conf/new5.2.PNG?raw=true)
1.Set IP static ubuntu server agar IP tidak berubah dan akses ke WP tetap sama
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/wp_conf/set%20static%20ip.PNG?raw=true
)

1. Buka web browser dan masukkan IP Ubuntu Server yang terinstall wordpress. Seharusnya sudah tertampil dan Masukkan data data yang digunakan untuk membuat akun admin
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/wp_conf/6.PNG?raw=true)
1. Login ke WP menggunakan akun yang telah dibuat
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/wp_conf/8.PNG?raw=true)
1. Lalu akan masuk ke halaman kelola admin
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/wp_conf/new9.PNG?raw=true)

## 2. Install Plugin Wordpress
- Plugin CP Reservation Calendar 1.1.6
1. Di command line/terminal/SSH komputer webserver, pastikan anda berada di direktori wordpress anda dan Pindah ke folder plugins
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/1.PNG?raw=true)

2. Download plugin CP Reservation Calendar 
```
wget https://downloads.wordpress.org/plugin/cp-reservation-calendar.1.1.6.zip
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/2.PNG?raw=true)

3. Unzip

```
unzip cp-reservation-calendar.1.1.6.zip
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/3.PNG?raw=true)

4. Jika belum terinstal Unzip maka Install Unzip 
```
apt-get install unzip
```

5. Setelah selesai, login ke dalam wordpress yang telah diinstall. Setelah itu, sidebar bagian Plugins, klik di bagian Installed Plugin. Klik Activate pada plugin Cp reservation calendar
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/4%20activate%20this.PNG?raw=true)
6. Agar dapat di injection, maka kita membuat konten CP Reservation calendar ke dalam wordpress agar dapat diakses. Buat post baru melalui posts -> add new
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/tanda%20activated.PNG?raw=true)
9. Setelah muncul halaman new post, klik add media dan tambahkan CP Reservation Calendar
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/ne%20post.PNG?raw=true)
10. Lalu klik publish
11. Seharusnya tampil post kira kira seperti ini
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/post%20this.PNG?raw=true)

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

