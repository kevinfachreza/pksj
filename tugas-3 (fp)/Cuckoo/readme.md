#### TUGAS 3 PKSJ

# CUCKOO

## Anggota Kelompok
1. Aldi Febriansyah - 5114100015
1. Trastian Satria W - 5114100016
1. Kevin A Fachreza - 5114100128

## Instalasi
1. Install depedensi
```
sudo apt-get install python python-pip python-dev libffi-dev libssl-dev 
```

2. Install libxml2-dev dan libslt-dev
```
sudo apt-get install libxml2-dev libxslt-dev
```

3. Install cuckoo sandbox

```
pip install -u cuckoo
```

4. Download VMWare
5. Buat user untuk cuckoo
```
sudo adduser cuckoo
```

6. Install mongodb
```
sudo apt-get install mongodb
```

7. Install TCPDump

```
sudo apt-get install tcpdup
sudo apt-get install libcap2-bin
sudo setcap cap_net_raw,cap_net_admin=eip/usr/sbin/tcpdump
getcap /usr/sbin/tcpdump
```

8. Install Volatility
```
sudo apt install git
git clone https://github.com/volatilityfoundation/volatility.git
cd /home/YourUserName/volatility
sudo python setup.py install
```

9. Download Distrom3 <https://github.com/gdabah/distorm/releases>
10. Ekstrak dan install distrop
```
tar -xvzf distorm-3.4.0.tar.gz
cd /home/<username>/Downloads/distorm-3.4.0
sudo python setup.py install
```

11. Install AutoConf dan Libtool-bin
```
sudo apt-get install autoconf
sudo apt-get install libtool-bin
```

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

13. Download dan Install PyCrypto <https://pypi.python.org/pypi/pycrypto>
```
tar -xvzf pycrypto-2.6.1.tar.gz
cd /home/<username>/Downloads/pycrypto-2.6.1
python setup.py build
sudo python setup.py install
```

14. Install Mitmproxy
```
sudo apt-get install python3-pip python3-dev libssl-dev libtiff5-dev libjpeg8-dev zlib1g-dev libwebp-dev
sudo pip3 install mitmproxy
mitmproxy
cd ~/.mitmproxy
cp mitmproxy-ca-cert.p12 /home/YourUserName/Downloads/cuckoo/analyzer/windows/bin/cert.p12 
mitmdump = /usr/local/bin/mitmdump
```

15. Download ISO Windows 7 dan lakukan install windows 7 pada VM yang telah terinstall

## Konfigurasi
Lakukan edit file pada file file berikut 
direktori : .cuckoo/conf

1. Cuckoo.conf
```
machinery = virtualbox
ip = 192.168.56.1
port = 2042
memory dump = yes
```

2. Auxiliary Conf
```
[sniffer]
enabled = yes

tcpdump = /usr/sbin/tcpdump
mitm = yes
```

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

4. Reporting.conf
```
[mongodb]
enabled = yes

html = yes
```

5. Processing.conf
```
memory = yes
```

## Uji Coba

1. Run Cuckoo
```
cuckoo
```

2. Run Cuckoo pada web server

```
cuckoo web runserver
```

3. Akses 127.0.0.1:8000 pada browser
