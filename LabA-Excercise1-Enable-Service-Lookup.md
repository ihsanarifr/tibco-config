# Enable Service Lookup

## Requirement
* Aktifkan Tibco EMS
* Aktifkan Tibco TRA Domain
* Aktifkan Tibco Administrator
* Aktifkan Database Oracle

## Aktifkan EMS
* masuk ke folder dengan perintah `cd /home/ihsan/tibco/ems/7.0/bin`
* execute perintah ini `./tibemsd64 =-config /home/ihsan/tibco/tibco/cfgmgmt/ems/data/tibemsd.conf`

## Aktifkan TRA Domain
* masuk ke folder dengan perintah `cd /home/ihsan/tibco/tra/domain/ihsan/`
* execute perintah `./hawkagent_ihsan`

## Aktifkan Administrator
* masuk ke folder dengan perintah `cd /home/ihsan/tibco/administrator/domain/ihsan/bin`
* execute perintah `./tibcoadmin_ihsan`

## Cara Akses Administrator
* Akses dengan browser <code>http://ihsan-optiplex-3020m:9090</code>
* username : <code>ihsan</code>
* password : <code>1234567890</code>

## Mengaktifkan service
* Configuration -> Advanced
* cari konfigurasi seperti `bw.platform.services.retreiveresources.Enabled` valuenya diganti menjadi <code>True</code>
* dan cari konfigurasi `bw.platform.services.retreiveresources.enableLookups` valuenya diganti menjadi <code>true</code>

## Masih error ketika
* poin 5 test and debug CreditCheckService
* <code>http://localhost:8010/inspection.wsil</code>
* seharusnya keluar
```{r, tidy=FALSE, eval=FALSE, highlight=FALSE }
http://localhost:8010/BWP.Core/Services/CreditCheck/Interface/intPerformCreditCheck-service.serviceagent?wsdl
```
