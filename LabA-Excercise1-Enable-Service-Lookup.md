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