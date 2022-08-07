## PHP MULTIPLE VERSION INSTALL
```
sudo apt update && sudo apt upgrade
```
## FIRST START BY ADDING INSTALL DIFFERENT VERSION  // no need signle version
```
sudo apt install software-properties-common
```
## Again 
```
sudo add-apt-repository ppa:ondrej/php
```

## Now Update Apt pakage manager
```
sudo apt update 
```
## Install PHP VERSION php8.1
```
sudo apt install php8.1 
```
## Install PHP VERSION 7.4
```
sudo apt install php7.4
```

##  install PHP MODULES
```
sudo apt install php7.3-cli php8.0-xml php8.0-mysql
```

## Finally, verify your default PHP version used on your system like this
```
php -v 
```

## Set Default PHP Version in Ubuntu

------------ Set Default PHP Version 7.4 ------------
```
sudo update-alternatives --set php /usr/bin/php7.4
```

------------ Set Default PHP Version 8.0 ------------
```
sudo update-alternatives --set php /usr/bin/php8.0
```

## disable PHP VERSION
```
sudo a2dismod php7.4
```

```
sudo a2dismod php8.0
```

## Enable PHP VERSION
```
sudo a2enmod php7.4
```
```
sudo a2enmod php8.0
```
----------- Restart Apache Server ----------- 
$ sudo systemctl restart apache2

## After switching from one version to another, you can find your PHP configuration file, by running the command below.

------------ For PHP 7.4 ------------
$ sudo update-alternatives --set php /usr/bin/php7.4
$ php -i | grep "Loaded Configuration File"

------------ For PHP 8.0 ------------
$ sudo update-alternatives --set php /usr/bin/php8.0
$ php -i | grep "Loaded Configuration File"

----------- Restart Apache Server ----------- 
$ sudo systemctl restart apache2


## Fist check php verison then get will version and change version fist previous version a2dismod with enable new version and new version sudo update-alternative command use and run the apache server.

