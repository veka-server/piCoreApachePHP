# piCoreApachePHP
une image de tinyCore pour raspberry pi avec Apache 2.4 et PHP 7


# CONFIG

```
/usr/local/etc/httpd
```


# SOURCES

```
/home/www/
```

# EXEC

```
/etc/init.d/services/apache2 start|stop|status
```


# CREATE IMG

```
sudo dd bs=4M if=/dev/sdb of=piCore-9.0.3_backupMySDCard.img
```

