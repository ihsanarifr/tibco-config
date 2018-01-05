# Implement Perform Credit Check

## Modifikasi design.tra
* buka file menggunakan perintah `vi /home/ihsan/tibco/designer/5.8/bin/designer.tra`
* ketik perintah ini `java.extended.properties -XX:PermSize=256M -XX:MaxPermSize=512M` dibawah `tibco.env.HEAP_SIZE 256M`

## Tambahkan path oracle jdbc library
* cari path penyimpanan oracle jdbc lalu copy, saat ini pathnya berada di `/u01/app/oracle/product/11.2.0/xe/jdbc/lib`
* tambahkan path tersebut dibaris `tibco.env.CUSTOM_CP_EXT` (baris 37)
* jangan lupa tambahkan `:` sebelum pathnya
* simpan

## Buat project baru dengan nama <bebas>
* ambil template dari `/home/ihsan/BWEDU/Template/bwpXX.designertemplate`
* lalu buka projectnya

## Konfigurasi Global Variables (BW)
* host.Name = `ihsan`
* jdbc.URL = `jdbc:oracle:thin:@localhost:1521:XE`
* user.Name = `ihsan`
* user.Password = `****`

## Test Koneksi OrderDB
* JDBC Drive = `oracle.jdbc.driver.OracleDriver(thin)`
* Pilih `Test Connection`