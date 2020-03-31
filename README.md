# piCoreApachePHP
une image de tinyCore pour raspberry pi avec Apache 2.4 et PHP 7

#INSTALL 
1. installer l'image avec belena etcher

2. Se conencter en SSH  defaut user = tc  defaut_password = piCore

3. Expand the /dev/mmcblk0p2 Partition:

1 Start fdisk partitioning tool as root, using the following command –

```sudo fdisk -u /dev/mmcblk0```

2 Now list partitions with ‘p‘ command and write down the starting and
ending cylinders of the second partition.

3 Delete the second partition with ‘d‘ command and then enter ‘2‘ as ‘Partition Number’.

4 Create a new partition using ‘n‘ command. Select ‘p’ for ‘Primary Partition‘ and ‘2‘ for ‘Partition Number’. For ‘First Cylinder’ use the same value as you had in the original partition (you made note of this value in step # 6.2). You may use the default value for ‘Last Cylinder’ or may use the smaller value if you want to create more partitions (for ex: swap disk).

following is the screenshot for steps 6.1 to 6.4 –

piCore_fdisk

5 Reboot the system using the following command –

```sudo reboot```

6 After the system boots up, expand the ‘/dev/mmcblk0p2‘ partition using the “sudo resize2fs /dev/mmcblk0p2” command –

```
sudo resize2fs /dev/mmcblk0p2
```

# search paquet
``` 
tce-ab
```
# Télécharger depuis les serveurs et installer le logiciel (option -w):
``` 
tce-load -w -i nom_du_paquet.tcz
```
# Télécharger et installer la liste des mirroirs réseaux:
```
tce-load -w -i mirrors.tcz
```

# Mise à jour:
```
tce-update
```

# install apache 2.4 et PHP 7.1
```
tce-load -w -i apache2.4
tce-load -w -i apache2.4-mod-php7.1
```

# DEFINE DATE

I spent days fiddling with this also.

Here's what I do.

1. Get timezone string from here: http://wiki.openwrt.org/doc/uci/system#time.zones
2. Set $TIMEZONE equal to tz string
3. echo "TZ="$TIMEZONE > /etc/sysconfig/timezone
4. echo "etc/sysconfig/timezone" >> /opt/.filetool.lst
5. backup or sudo filetool.sh -b
6. reboot

Seems to works well for Sydney TZ=EST-10EST,M10.1.0,M4.1.0/3.


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

