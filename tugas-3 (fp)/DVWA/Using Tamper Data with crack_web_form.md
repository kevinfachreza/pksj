# Lesson 5 - Using Tamper Data with crack_web_form.pl

##Mengatur Tamper Data

1. Buka Firefox, lalu pilih Add-ons.
2. Lalu enable **Tamper data**.
![1 add_on](https://user-images.githubusercontent.com/17487644/34213281-4e72211e-e5d1-11e7-85a3-3156a2dd679c.png)
3. Restart Mozila anda.


##Mengambil Data HTTP-POST Menggunakan Tamper Data
1. Setelah merestart Mozila, Buka DVWA yang sudah di host Fedora, menggunakan IP fedora (pada tutorial ini 192.168.3.13):
	* http://<IP Fedora>/dvwa/login.php
2. Nyalakan Tamper Data
![2 tamper data](https://user-images.githubusercontent.com/17487644/34213282-4ea8b864-e5d1-11e7-9580-ba8e357145e3.png)
3. Klik Start **Tamper** pada window *Tamper Data* yang baru saja muncul
4. Lalu login DVWA
	* username: "admin"
	* password: "password"
	* klik login
5. Dialog *Tamper with request?* akan muncul
	* jangan centang *Continue with Tampering*
	* lalu klik submit
![3 uncheck dialog tamper](https://user-images.githubusercontent.com/17487644/34213284-4eded0c0-e5d1-11e7-88e4-521e9f19b497.png)
6. Hentikan Tamper data
7. Dapatkan data *post* dari Tamper data
	* pilih data POST pertama pada hasil tamper
	* klik kanan pada POSTDATA, lalu klik copy
![5 post data](https://user-images.githubusercontent.com/17487644/34213287-4f6ee390-e5d1-11e7-96a3-600452c4dcf8.png)
8. Salin pada notepad
	* buka notepad
![6 buka notepad](https://user-images.githubusercontent.com/17487644/34213288-4fa902e6-e5d1-11e7-97fe-0cbb6e1eede1.png)
	* lalu *paste* pada notepad
![7 hasil notepad](https://user-images.githubusercontent.com/17487644/34213289-4ff34d10-e5d1-11e7-866b-22b1126beebb.png)

9. Logout dari DVWA dan coba login salah
	* logout dari dvwa
	* lalu coba login lagi menggunakan password yang salah
![8 wrong password](https://user-images.githubusercontent.com/17487644/34213291-50c79372-e5d1-11e7-9dc4-dc2a2cd26b54.png)
	* copy tulisan "Login failed" pada bawah halaman

10. Salin pada notepad
	* tambahkan pada notepad yang sebelumnya
	* lalu save dengan nama "dvwa-post-data.txt"
![9 save notepad](https://user-images.githubusercontent.com/17487644/34213292-512afb1a-e5d1-11e7-94c5-db37f2c80b09.png)

##Mengatur dan Menjalankan crack_web.pl
1. Buat direktori
	* mkdir /pentest/passwords/cwf
![10 mkdir pentest](https://user-images.githubusercontent.com/17487644/34213294-51603456-e5d1-11e7-9527-8c66716c38fa.png)
2. Download file CWF
	* buka mozila
	* lalu masukan url:
		*http://www.computersecuritystudent.com/SECURITY_TOOLS/DVWA/DVWAv107/lesson5/cwf.tar.gz*
	* pilih "save file", lalu klik ok
[11. download tar.gz](https://github.com/kevinfachreza/pksj/files/1575933/11.download.tar.gz)
3. extrak
	* extrak pada folder yang telah dibuat tadi:
		/pentest/passwords/cwf
	* dengan menggunakan command:
		1. tar xovfz cwf.tar.gz*
		2. chmod 700 crack_web_form.pl
![12 untar](https://user-images.githubusercontent.com/17487644/34213297-52af75ce-e5d1-11e7-8876-bc796b621f08.png)

4. MenggunakanCrack Web
	1. *./crack_web_form.pl -help*
		*untuk mendapatkan bantuan tentang crack_web_form*
![13 crack web func](https://user-images.githubusercontent.com/17487644/34213301-5340702e-e5d1-11e7-8512-55c070c0e8c0.png)
	2. ./crack_web_form.pl -U admin -P password.txt -http "http://<IP fedora>/dvwa/login.php" -data "username=USERNAME&password=PASSWORD&Login=Login" -M "Login failed"
		*isi dengan ip fedora yang ada dvwa-nya*
![14 crack command](https://user-images.githubusercontent.com/17487644/34213302-53914292-e5d1-11e7-9050-dd0e1bc5e75a.png)
	3. dilakukan 239 kali percobaan untuk memecahkan password
![15 successfull crack](https://user-images.githubusercontent.com/17487644/34213278-4db791fa-e5d1-11e7-9bef-4e0b98b407a7.png)


##Bukti Selesai Lesson 5
![16 bukti lesson](https://user-images.githubusercontent.com/17487644/34213280-4e39f212-e5d1-11e7-8db8-36593b7e90d8.png)