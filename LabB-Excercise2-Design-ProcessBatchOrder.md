# Design ProcessBatchOrder

## setting ~/.bashrc
* masuk ke folder `/home/ihsan/tibco/ems/7.0/samples/java/`
* execute `./setup.sh`
* untuk mengakses sample java harus di compile terlebih dahulu maka coba
```{r, tidy=FALSE, eval=FALSE, highlight=FALSE }
TIBEMS_JAVA=/home/ihsan/tibco/ems/7.0/lib
CLASSPATH=${TIBEMS_JAVA}/jms.jar:${CLASSPATH}
CLASSPATH=.:${TIBEMS_JAVA}/tibjms.jar:${TIBEMS_JAVA}/tibjmsufo.jar:${TIBEMS_JAVA}/tibcrypt.jar:${TIBEMS_JAVA}/tibjmsadmin.jar:${TIBEMS_JAVA}/slf4j-api-1.4.2.jar:${TIBEMS_JAVA}/slf4j-simple-1.4.2.jar:${CLASSPATH}

export CLASSPATH
```

* compile java <code>javac -d . *.java</java>
