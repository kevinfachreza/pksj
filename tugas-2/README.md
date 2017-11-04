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

1. Download plugin CP Reservation Calendar 
```
wget https://downloads.wordpress.org/plugin/cp-reservation-calendar.1.1.6.zip
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/2.PNG?raw=true)

1. Unzip

```
unzip cp-reservation-calendar.1.1.6.zip
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/3.PNG?raw=true)

1. Jika belum terinstal Unzip maka Install Unzip 
```
apt-get install unzip
```

1. Setelah selesai, login ke dalam wordpress yang telah diinstall. Setelah itu, sidebar bagian Plugins, klik di bagian Installed Plugin. Klik Activate pada plugin Cp reservation calendar

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/4%20activate%20this.PNG?raw=true)
1. Agar dapat di injection, maka kita membuat konten CP Reservation calendar ke dalam wordpress agar dapat diakses. Buat post baru melalui posts -> add new

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/tanda%20activated.PNG?raw=true)
1. Setelah muncul halaman new post, klik add media dan tambahkan CP Reservation Calendar

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/ne%20post.PNG?raw=true)
1. Lalu klik publish
1. Seharusnya tampil post kira kira seperti ini

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/post%20this.PNG?raw=true)

# Plugin League Manager 3.9.1.1

1. Plugin Wordpress League Manager di https://wordpress.org/plugins/leaguemanager/developers/

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/league%20manager/dl.PNG?raw=true)
2. Masuk ke dashboard WP lalu klik add new pada Plugins

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/league/plugin2.PNG?raw=true)

3. Upload file yang telah di download, league manager tadi lalu klik install now

3.1 Karena bukan di locaalhost maka disini kita install ftp dahulu, kita install vsftpd

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/league%20manager/install%20ftp.PNG?raw=true)

3.2 Atur settingan vsftpd sebagai berikut

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/league%20manager/edit%20conf.PNG?raw=true)

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/league%20manager/conf.PNG?raw=true)

3.3 Restart vsftpd lalu klik upload dan install pada Admin Wordpress

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/league%20manager/restart.PNG?raw=true)

4. Setelah install berhasil, klik activate plugin

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/league%20manager/installed.PNG?raw=true)

5. Buat liga baru

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/league%20manager/add%20league.PNG?raw=true)

6. Buat Season Baru

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/league%20manager/add%20season.PNG?raw=true)

7. Buat team, dan isi keterangan

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/league%20manager/add%20team.PNG?raw=true)

8. Buat pertandingan

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/instalasi-plugin/league%20manager/add%20match.PNG?raw=true)

9. Hasil posting

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/SS/league/hasil2.PNG?raw=true)

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

# Pada tahap ini, kami melakukan uji penetrasi berikut :

1. Scan Vulnerable Plugins dengan WPScan

2. Plugin CP Reservation Calendar 1.1.6 dengan tool SQLMap

3. Plugin League Manager 3.9.1.1 dengan tool SQLMap

# Scan Vulnerable Plugins dengan WPScan
1. Lakukan scan pada wordpress yang kita install.

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/wpscan/1.PNG?raw=true)
2. Lihat versi plugin dan vulnerable version plugin. Disini kami terdapat banyak plugins vulnerable namun yang kita inject hanya 2

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/wpscan/2.PNG?raw=true)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/wpscan/3.PNG?raw=true)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/wpscan/4.PNG?raw=true)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/wpscan/5.PNG?raw=true)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/wpscan/6.PNG?raw=true)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/wpscan/9.PNG?raw=true)
3. Explore pada reference yang tercantum pada hasil wpscan.

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/wpscan/8.PNG?raw=true)

# Plugin CP Reservation Calendar 1.1.6 dengan tool SQLMap
1. Buka salah satu reference yang kita dapat dari WPScan, disini kami menggunakan exploit-db.

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/wpscan/8.PNG?raw=true)
2. Dari dasar teori yang kita dapat dari reference maka kita jalankan script sqlmap yang ada pada reference

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/calendar%20sqlmap/1.PNG?raw=true)
3. Hasil dari sqlmap

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/calendar%20sqlmap/2.PNG?raw=true)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/calendar%20sqlmap/3.PNG?raw=true)
4. Lakukan Penetrasi lagi, namun kali ini untuk penetrasi tabel user

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/calendar%20sqlmap/penet%20user%201.PNG?raw=true)
5. Maka akan muncul isi dari tabel tersebut pada log

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/calendar%20sqlmap/p-2.PNG?raw=true)
6. Lalu kita akan mencoba brute force password user, disini akan ada pilihan bagaimana kita akan membrute forcenya. Pada kali ini kita memilih dengan dictionary default namun telah disisipkan dengan password kami juga.

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/calendar%20sqlmap/p-3.PNG?raw=true)
7. Hasil dan dump dapat terlihat, dan password terlihat karena bruteforce berhasil.

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/calendar%20sqlmap/log.PNG?raw=true)

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/calendar%20sqlmap/uesr%20os.PNG?raw=true)
8. Pada log dibawah terdapat hasil bruteforce dictionary pada hash yang ada di DB berhasil. Hasilnya adalah password user admin wordpress kami.

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/calendar%20sqlmap/pass%20os.PNG?raw=true)

# Plugin League Manager 3.9.1.1 dengan tool SQLMap
1. Dengan cara yang hampir sama dengan sebelumnya, buka reference dan dapatkan teori serta bagian yang dapat diexploit

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/league%20sqlmap/base.PNG?raw=true)
2. Lakukan test penetrasi #1 dengan ?match=1

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/league%20sqlmap/syn1.PNG?raw=true)
3. Hasil penenetrasi #1

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/league%20sqlmap/1.PNG?raw=true)
4. Lakukan test penetrasi #2 dengan ?match=1 dan --dbs untuk mendapatkan list database 

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/league%20sqlmap/syn1.5.PNG?raw=true)
5. Hasil penetrasi #2

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/league%20sqlmap/1.5.PNG?raw=true)
6. Lakukan test penetrasi #3 dengan ?match=1 dengan tambahan nama DB yng ingin kita masuki dan --tables utk melihat daftar table

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/league%20sqlmap/syn2.PNG?raw=true)
7. Hasil penetrasi #3

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/league%20sqlmap/2%20tables.PNG?raw=true)
8. Lakukan test penetrasi #4 dengan ?match=1 dengan tambahan nama table yng ingin kita masuki dan --dump untuk mencatat log

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/league%20sqlmap/3%20wp_user.PNG?raw=true)
9. Pada penetrasi #4 terdapat user yang dapat kita brute force, dan kami memilih mem brute force password dengan small dictionary dari part sebelumnya. Pada gambar terlihat isi tabel dan hasil crack hash password kami.

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/league%20sqlmap/3-1.PNG?raw=true)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-2/assets/inject/league%20sqlmap/3-2.PNG?raw=true)
