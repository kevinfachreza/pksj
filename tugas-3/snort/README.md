<b> TUGAS 3 PKSJ </b>
# SNORT

## Anggota Kelompok :
1. Aldi Febriansyah - 5114100015
1. Trastian Satria W - 5114100016
1. Kevin A Fachreza - 5114100128

## Dasar Teori :
#### OS
##### 1. Ubuntu
Ubuntu  merupakan salah satu distribusi Linux yang berbasiskan Debian dan didistribusikan sebagai perangkat lunak bebas.
(https://id.wikipedia.org/wiki/Ubuntu).

##### 2. Snort
Salah satu aplikasi Linux yang dapat dipakai untuk meningkatkan keamanan komputer adalah Snort. ... Akan tetapi berbeda dengan Wireshark, Snort dapat dipakai sebagai komponen NIDS dengan menjalankannya pada Network Intrusion Detection System (NIDS) mode.
(https://thesolidsnake.wordpress.com/2011/06/05/pengenalan-snort/).


## Installasi 

1. Menyiapkan server, install library yang dibutuhkan dengan script berikut

```
sudo apt install -y gcc libpcre3-dev zlib1g-dev libpcap-dev openssl libssl-dev libnghttp2-dev libdumbnet-dev bison flex libdnet
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/1.JPG)

2. Sebelum install snort, mari kita buat folder terlebih dahulu

```
mkdir ~/snort_src && cd ~/snort_src
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/2.JPG)

3. Snort menggunakan Data Acquisition Library (DAQ) untuk membuat panggilan abstrak ke paket yang ter-capture.
Download & Ekstrak snort DAQ

```
wget https://www.snort.org/downloads/snort/daq-2.0.6.tar.gz
tar -xvzf daq-2.0.6.tar.gz
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/3.JPG)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/4.JPG)

4. Pindah ke direktori snort yang baru saja di ekstrak

```
cd daq-2.0.6
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/5.JPG)

5. Compile dan install DAQ Snort

```
./configure && make && sudo make install
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/6.JPG)

6. Kembali ke folder snort_src

```
cd ~/snort_src
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/7.JPG)

7. Download snort terbaru

```
wget https://www.snort.org/downloads/snort/snort-2.9.11.tar.gz
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/8.JPG)

8. Extract file

```
tar -xvzf snort-2.9.11.tar.gz
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/9.JPG)

9. Pindah ke direktori file yang telah di ekstrak

```
cd snort-2.9.11
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/10.JPG)

10. Konfigurasi dengan sourcefire, dan install

```
./configure --enable-sourcefire && make && sudo make install
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/11.JPG)


## Konfigurasi

1. Update shared libraries

```
sudo ldconfig
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/12.JPG)

2. Buat symbolic link ke direktori snort

```
sudo ln -s /usr/local/bin/snort /usr/sbin/snort
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/13.JPG)

3. Buat username dan group untuk snort

```
sudo groupadd snort
sudo useradd snort -r -s /sbin/nologin -c SNORT_IDS -g snort
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/14.JPG)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/15.JPG)

4. Buat struktur folder untuk konfigurasi SNORT

```
sudo mkdir -p /etc/snort/rules
sudo mkdir /var/log/snort
sudo mkdir /usr/local/lib/snort_dynamicrules
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/16.JPG)

5. Atur permissions direktori

```
sudo chmod -R 5775 /etc/snort
sudo chmod -R 5775 /var/log/snort
sudo chmod -R 5775 /usr/local/lib/snort_dynamicrules
sudo chown -R snort:snort /etc/snort
sudo chown -R snort:snort /var/log/snort
sudo chown -R snort:snort /usr/local/lib/snort_dynamicrules
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/17.JPG)

6. Buat file untuk menampung black list dan white list

```
sudo touch /etc/snort/rules/white_list.rules
sudo touch /etc/snort/rules/black_list.rules
sudo touch /etc/snort/rules/local.rules
```


![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/18.JPG)

7. Copy file konfigurasi dari folder download

```
sudo cp ~/snort_src/snort-2.9.9.0/etc/*.conf* /etc/snort
sudo cp ~/snort_src/snort-2.9.9.0/etc/*.map /etc/snort
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/19.JPG)

8. Download rules community

```
wget https://www.snort.org/rules/community -O ~/community.tar.gz
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/20.JPG)

9. Ekstrak rules dan copy ke folder konfigurasi

```
sudo tar -xvf ~/community.tar.gz -C ~/
sudo cp ~/community-rules/* /etc/snort/rules
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/21.JPG)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/22.JPG)

10. Comment rules rules yang tidak penting pada file konfigurasi

```
sudo sed -i 's/include \$RULE\_PATH/#include \$RULE\_PATH/' /etc/snort/snort.conf
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/23.JPG)

11. Edit file konfigurasi

```
sudo gedit /etc/snort/snort.conf
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/25.JPG)

12. Edit dengan konfigurasi sebagai berikut

```
# Setup the network addresses you are protecting
ipvar HOME_NET <server public IP>/32
```

```
# Set up the external network addresses. Leave as "any" in most situations
ipvar EXTERNAL_NET !$HOME_NET
```

```
# Path to your rules files (this can be a relative path)
var RULE_PATH /etc/snort/rules
var SO_RULE_PATH /etc/snort/so_rules
var PREPROC_RULE_PATH /etc/snort/preproc_rules
```

```
# Set the absolute path appropriately
var WHITE_LIST_PATH /etc/snort/rules
var BLACK_LIST_PATH /etc/snort/rules
```

```
# unified2
# Recommended for most installs
output unified2: filename snort.log, limit 128
```

13. Uncomment rules berikut

```
include $RULE_PATH/community.rules
```

14. Validasi konfigurasi

```
sudo snort -T -c /etc/snort/snort.conf
``` 

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/26.JPG)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/26-complete-result.JPG)

15. Buka local rules

```
sudo nano /etc/snort/rules/local.rules
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/28.JPG)

16. Tambahkan line berikut

```
alert icmp any any -> $HOME_NET any (msg:"ICMP test"; sid:10000001; rev:001;)
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/28.JPG)

17. Cek ip address

```
ip addr
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/29.JPG)

18. Perhatikan tipe koneksi anda jika eth0 maka masukkan eth0 , dalam kasus ini kami menggunakan enp0s3

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/29-result.JPG)

19. Masukkan konfigurasi berikut untuk memilih tipe koneksi

```
sudo snort -A console -i enp0s3 -u snort -g snort -c /etc/snort/snort.conf
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/30.JPG)

20. Download file PCAP pilih ekstensi file pcap.

```
panda.gtisc.gatech.edu/malrec/
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/31.JPG)

21. Baca file PCAP hasil download

```
snort -r <nama_file>
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/32.JPG)

22. Lihat hasil

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/snort/assets/33.JPG)