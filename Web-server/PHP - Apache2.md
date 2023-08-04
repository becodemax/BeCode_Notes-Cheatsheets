```
sudo apt install apache2
```
```
sudo apt install php libapache2-mod-php
```
```
sudo nano /etc/php/8.1/apache2/php.ini
```
```
sudo apt install php8.1 libapache2-mod-php8.1 php8.1-common php8.1-gmp php8.1-curl php8.1-intl php8.1-mbstring php8.1-xmlrpc php8.1-mysql php8.1-gd php8.1-imap php8.1-ldap php-cas php8.1-bcmath php8.1-xml php8.1-cli php8.1-zip php8.1-sqlite3 php8.1-apcu php8.1-bz2
```
```
file_uploads = On   
allow_url_fopen = On   
short_open_tag = On   
memory_limit = 256M   
upload_max_filesize = 100M   
max_execution_time = 360   
max_input_vars = 1500   
date.timezone = Europe/Paris
```
```
sudo nano /var/www/html/phpinfo.php
```