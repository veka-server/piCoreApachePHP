# piCoreApachePHP
une image de tinyCore pour raspberry pi avec Apache 2.4 et PHP 7

# SAVE
```
filetool.sh -b
```

# RESET LAST SAVE
```
filetool.sh -r
```

# CONFIG

```
/usr/local/etc/httpd/httpd.conf
```
ADD
```
LoadModule php7_module modules/libphp7.so

<FilesMatch \.php$>
    Sethandler application/x-httpd-php
</FilesMatch>

DirectoryIndex index.php
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

