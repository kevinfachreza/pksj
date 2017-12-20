#### TUGAS 3 PKSJ

# CUCKOO

## Anggota Kelompok
1. Aldi Febriansyah - 5114100015
1. Trastian Satria W - 5114100016
1. Kevin A Fachreza - 5114100128

## Dasar Teori
1. Tools dan Malware 

<b>Cuckoo Sandbox 2.0.5<b> adalah sistem yang dibuat untuk tempat / wadah analisis malware secara otomatis. Sistem ini merupakan aplikasi open source. Sistem ini berjalan secara otomatis dan dapat menganalisa files serta mendapat hasil analisis yang komprehensif dari sebuah malware yang di analisa yang berjalan didalam sistem operasi yang ter isolir.

<b>Malware<b> adalah suatu file atau software yang disisipi dengan barisan kode yang malicious/berbahaya yang digunakan untuk mengambil data sensitif, atau mengganggu jalannya service/operasi komputasi, bisa juga mendapatkan akses akses yang memiliki hak akses khusus.

2. Malware yang Digunakan 

<b>Ransomware Locky<b> adalah ransomware yang disebarkan sebagai dokumen Word berbahaya yang melekat pada email spam. Email yang membawa Ransomware Locky biasanya berpura-pura memberikan faktur. dokumen Word berbahaya ini dapat segera mengeksekusi proses enkripsi berbahaya ketika macro Word diaktifkan. Jika tidak, teks Word ini muncul sebagai file yang rusak, dan juduldokumen menular ini mengatakan, “Enable macro if the data encoding is incorrect.” Anda tidak harus melakukan hal seperti yang diperintahkan!

## Instalasi
1. Install depedensi
```
sudo apt-get install python python-pip python-dev libffi-dev libssl-dev 
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/1.png)

2. Install libxml2-dev dan libslt-dev
```
sudo apt-get install libxml2-dev libxslt-dev
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/3.png)


3. Install cuckoo sandbox

```
pip install -u cuckoo
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/4.png)

4. Download VMWare
5. Buat user untuk cuckoo
```
sudo adduser cuckoo
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/8.png)


6. Install mongodb
```
sudo apt-get install mongodb
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/5.png)


7. Install TCPDump & Libcap2-bin

```
sudo apt-get install tcpdup
sudo apt-get install libcap2-bin
sudo setcap cap_net_raw,cap_net_admin=eip/usr/sbin/tcpdump
getcap /usr/sbin/tcpdump
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/9.png)


8. Install Volatility
```
sudo apt install git
git clone https://github.com/volatilityfoundation/volatility.git
cd /home/YourUserName/volatility
sudo python setup.py install
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/11.png)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/12.png)


9. Download Distrom3 <https://github.com/gdabah/distorm/releases>
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/13.png)


10. Ekstrak dan install distrop
```
tar -xvzf distorm-3.4.0.tar.gz
cd /home/<username>/Downloads/distorm-3.4.0
sudo python setup.py install
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/14.png)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/15.png)


11. Install AutoConf dan Libtool-bin
```
sudo apt-get install autoconf
sudo apt-get install libtool-bin
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/17.png)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/18.png)

12. Download Yara dan lakukan ekstrak serta install <https://github.com/VirusTotal/yara/releases>
```
tar -xvzf yara-3.5.0.tar.gz
cd /home/<username>/Downloads/yara-3.5.0
./bootstrap.sh
./configure --with-crypto --enable-magic --enable-cuckoo
make
sudo make install 
sudo -H pip install yara-python
```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/19.png)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/20.png)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/21.png)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/22.png)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/23.png)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/25.png)

13. Download dan Install PyCrypto <https://pypi.python.org/pypi/pycrypto>
```
tar -xvzf pycrypto-2.6.1.tar.gz
cd /home/<username>/Downloads/pycrypto-2.6.1
python setup.py build
sudo python setup.py install
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/27.png)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/28.png)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/30.png)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/31.png)

14. Install Mitmproxy
```
sudo pip3 install mitmproxy
mitmproxy
cd ~/.mitmproxy
cp mitmproxy-ca-cert.p12 /home/YourUserName/Downloads/cuckoo/analyzer/windows/bin/cert.p12 
mitmdump = /usr/local/bin/mitmdump
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/36.png)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/install/40.png)


15. Download ISO Windows 7 dan lakukan install windows 7 pada VM yang telah terinstall

## configurasi cuckoo
Lakukan edit file pada file file berikut 
direktori : .cuckoo/conf

1. Cuckoo.conf
```
machinery = virtualbox
ip = 192.168.56.1
port = 2042
memory dump = yes
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/config/13.png)


2. Auxiliary Conf
```
[sniffer]
enabled = yes

tcpdump = /usr/sbin/tcpdump
mitm = yes
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/config/2.png)

3. Virtualbox.conf
```
interface = vboxnet0
machines = windows7
[windows7]
label = windows7
platform = windows
ip = 192.168.56.10
snapshot = snapshot1
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/config/3.png)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/config/4.png)

4. Reporting.conf
```
[mongodb]
enabled = yes

html = yes
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/config/5.png)

5. Processing.conf
```
[memory]
enabled = yes
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/config/15.png)

6. Atur IPTables
```
sudo iptables -t nat -A POSTROUTING -o eth0 -s 192.168.56.0/24 -j MASQUERADE
sudo iptables -P FORWARD DROP
sudo iptables -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -s 192.168.56.0/24 -j ACCEPT
sudo iptables -A FORWARD -s 192.168.56.0/24 -d 192.168.56.0/24 -j ACCEPT
sudo iptables -A FORWARD -j LOG
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/config/7.png)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/config/9.png)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/config/10.png)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/config/11.png)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/config/14.png)

7. Atur routing pada cuckoo
```
etc/tor/torrc

TransPort 192.168.56.1:9141
DNSPort 192.168.56.1:5454
```

```
.cuckoo/conf/routing.conf

[tor]
enabled = yes
dnsport = 5454
proxyport = 9141

```

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/config/6.png)

8. Restart routing

```
/etc/init.d/tor restart
```

## configurasi windows 7
1. Install python 2.7 dan Adobe Reader DC

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/config/install_python_2.7.png)

2. Matikan Firewall
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/config/sett_fw.png)

3. Matikan Windows Update
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/config/sett_upd.png)

4. Matikan User Account Control (UAC)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/config/sett_uac.png)

5. Set static IP dan pakai DNS Google
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/config/konfig_ip.png)


## Uji Coba
1. Run Rooter Cuckoo
```
sudo cuckoo rooter -g cuckoo
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/run/5.png)



2. Run Cuckoo
```
cuckoo
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/run/2.png)

3. Run Cuckoo pada web server

```
cuckoo web runserver
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/run/1.png)

4. Akses 127.0.0.1:8000 pada browser
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/run/3.png)

5. Run Virtual Box
```
sudo virtualbox
```
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/run/4.png)

6. Download salah satu file malware di https://github.com/ytisf/theZoo/tree/master/malwares
kami mengambil salah satu file https://github.com/ytisf/theZoo/tree/master/malwares/Binaries/Ransomware.Locky

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/run/7.png)

7. Upload file ke web

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/run/6.png)

8. Maka nanti dari cuckoo akan otomatis membuka VM

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/run/8.png)

9. Dan akan muncul hasil pada terminal cuckoo

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/run/9.png)

10. Akan muncul pula hasil analisa pada web

![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/run/10.png)
![Alt text](https://github.com/kevinfachreza/pksj/blob/master/tugas-3/Cuckoo/assets/run/11.png)