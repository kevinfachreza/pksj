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

1. Untuk install ssh server ketik
```
sudo apt-get install openssh-server
```

2. Cek jika install berhasil menggunakan command berikut
```
service ssh status
```

#### Install Tools Medusa, THC-Hydra, NCrack

1. THC-Hydra, NCrack, dan Medusa merupakan tools default Kali, sehingga tidak perlu install

### Brute Force Menggunakan Tools

#### Hydra

1. Hydra membutuhkan list password, maka dibuat file password bernama """""""
1. Jalankan Hydra
```
hydra -l [username] -P [text_password] [ip_target] -t [jumlah_thread] [tipe_protocol]
```

#### NCrack

1. Jalankan NCrack

```
ncrack -p [port] --user [username] -P [text_password] [ip_target] 
```

#### Medusa

1. Jalankan Medusa

```
medusa -u root -P list.txt -h 192.168.33.10 -M sshMedusa v2.2_rc3 [http://www.foofus.net] (C) JoMo-Kun / Foofus Networks <jmk@foofus.net> 
```


## Uji Penetrasi 2

1. Install fail2ban

```
sudo apt-get install fail2ban
```

2. Install Ip-tables persistent

```
sudo apt-get install iptables-persistent
```

3. Buka konfigurasi fail2ban

```
sudo nano /etc/fail2ban/jail.conf
```

4. Atur bantime. Bantime merupakan lamanya waktu jika host di ban
5. Atur maxretry. Max retry merupakan maksimal percobaan gagal
6. Atur findtime. Findtime merupakan waktu diantara percobaan gagal 1 dan terakhir.
7. Masukkan command berikut

```
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
sudo iptables -A INPUT -p tcp -m multiport --dports 80,443 -j ACCEPT
sudo iptables -A INPUT -j DROP
```

8. Cek Iptables

```
sudo iptables -S
```

9. Start fail2ban

```
sudo service fail2ban start
```

10. Lihat perubahan iptables

