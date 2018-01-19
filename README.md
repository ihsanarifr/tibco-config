# Konfigurasi TIBCO Asyst (Ubuntu)
TIBCO di perusahaan ASYST Garuda Group

## Software yang akan di install
* TibcoRv (TIBCO Renderzveous 8.4.0)
* TibcoBw (TIBCO ActiveMatrix BusinessWorks 5.11)
* TibcoTra (TIBCO Runtime Agent 5.8.0)
* TibcoEMS (TIBCO Enterprise Message Service 7.1.0)
* TibcoHawk
* TibcoAdmin (TIBCO Administrator 5.8.0)

## Software pendukung
* JDK Oracle 1.8
* Oracle Database
* SQL Developer

## Install java (jika belum ada)
* Download JDK Oracle 1.8.0
* Extract dan copy satu folder tersebut ke tempat yang diinginkan misal di `/opt/jdk/java-oracle-8/`
* Perintah `cp java-oracle-8 /opt/jdk/`
* edit file ~/.bashrc dengan perintah `nano ~/.bashrc`
* tambahkan perintah dibawah ini di paling bawah filter sebut
* `export JAVA_HOME=/opt/jdk/java-oracle-8`
* `export PATH=$PATH:$JAVA_HOME/bin`
* Save dan close terminal
* Buka kembali terminal dan ketik perintah `echo $JAVA_HOME`
* jika sudah ada ketik perintah `java -version`
* Jika sudah keluar informasi java maka sudah terinstal java

## Install Oracle Database
* Pilih file `oracle-xe_11.2.0-2_amd64.deb`
* Execute file dengan perintah `sudo dpkg -i oracle-xe_11.2.0-2_amd64.deb`

## Cara Instalasi TIBCO
### Install TIBCORv
* Pilih fail `TIB_rv_8.4.0_linux26gl23_x86.tar.gz`
* Extract fail dengan perintah `tar -vxzf TIB_rv_8.4.0_linux26gl23_x86.tar.gz` 
* Execute fail `./TIBCOUniversalInstaller-lnx-x86.bin -console` (mode `console`)
* Jika terdapat error lihat di tanya jawab

### Install TIBCOBw
* Pilih fail `TIB_bw_5.11.0_linux26gl23_x86_64.zip`
* Extract fail dengan perintah `unzip TIB_bw_5.11.0_linux26gl23_x86_64.zip`
* Execute fail `./TIBCOUniversalInstaller-lnx-x86-64.bin`

### Install TIBCOTra
* Pilih fail `TIB_tra_5.8.0_linux26gl23_x86_64.zip`
* Extract fail dengan perintah `unzip TIB_tra_5.8.0_linux26gl23_x86_64.zip`
* Execute fail `./TIBCOUniversalInstaller-lnx-x86-64.bin`

### Install TIBCOEMS
* Pilih fail `TIB_ems_7.0.1_linux_x86.tar.gz`
* Extract fail dengan perintah `tar -vxzf TIB_ems_7.0.1_linux_x86.tar.gz`
* Execute fail `./TIBCOUniversalInstaller-lnx-x86.bin -console` (mode `console`)

### Install TIBCOHawk
* Pilih fail `TIB_hawk_5.0.0_linux26gl23_x86_64.zip`
* Extract fail dengan perintah `unzip TIB_hawk_5.0.0_linux26gl23_x86_64.zip`
* Execute fail `./TIBCOUniversalInstaller-lnx-x86-64.bin`

### Install TIBCOAdmin
* Pilih fail `TIB_TIBCOAdmin_5.8.0_linux26gl23_x86_64.zip`
* Extract fail dengan perintah `unzip TIB_TIBCOAdmin_5.8.0_linux26gl23_x86_64.zip`
* Execute fail `./TIBCOUniversalInstaller-lnx-x86-64.bin`

## Tanya Jawab
### Saat install TIBCORv terdapat error `Bundled JRE is not binary compatible with host OS/Arch or it is corrupt. Testing bundled JRE failed.` Bagaimana cara mengatasinya?
Solusinya simple yaitu tambahkan arsitektur i386 dengan ikuti perintah dibawah
* `sudo dpkg --add-architecture i386`
* `sudo apt-get update`
* `sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386`

### Saat install JDK perintah `echo $JAVA_HOME` tidak muncul apa-apa
Saat melakukan edit `~/.bashrc` lihat apakah saat user `root` atau tidak? Usahakan tidak menggunakan user `root` agar JDK bisa terbaca di user biasa saja. Jika sudah diedit close terminal dan coba kembali perintah `echo $JAVA_HOME`

### Perintah `echo $JAVA_HOME` sudah bisa tetapi saat peritah `java -version` belum bisa
Coba lihat kembali path yang benar yan menghubungkan jdk, usahakan path untuk jdk java ini mengacu di `/opt/jdk/java-orancle-8`

### Bagaimana cara menambah kapasitas memory swap?
Caranya ada di [tutorial disini](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04).
* melihat swap yang ada `sudo swapon --show`
* melihat kapasitas memory yang sedang running `free -m`
* membuat file swap `sudo fallocate -l 1G /swapfile` -> 1G menunjukkan 1 Giga
* melihat file swap yang sudah dibuat `ls -lh /swapfile`
* menambahkan hak akses file swap `sudo chmod 600 /swapfile`
* create swap `sudo mkswap /swapfile`
* tambahkan ini untuk mengaktifkan `sudo swapon /swapfile`

### Bagaimana cara menambah kapasitas memory swap permanent?
Ini ada aturan dan rekomendasi kapasistas swap pada sistem bisa di baca [disini](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/installation_guide/s2-diskpartrecommend-ppc#id4394007) untuk yang memakai distro linux Ubuntu penjelasannya [disini](https://help.ubuntu.com/community/SwapFaq)
* ketik perintah `echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab`
* lalu `cat /proc/sys/vm/swappinest`
* edit file `/etc/sysctl.conf` dengan perintah `sudo nano /etc/sysctl.conf`
* tambahkan kode ini dibawah <code>vm.swappiness=10</code>
