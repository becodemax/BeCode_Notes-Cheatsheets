```
cd /tmp
```
```
wget https://github.com/glpi-project/glpi/releases/download/10.0.7/glpi-10.0.7.tgz
```
```
sudo mv glpi /var/www/glpi
```
```
sudo chown -R www-data:www-data /var/www/glpi/
```
```
sudo chmod -R 755 /var/www/glpi/
```
```
sudo nano /etc/apache2/sites-available/glpi.conf
```
```
<VirtualHost *:80>
     ServerAdmin admin@example.com
     DocumentRoot /var/www/glpi
     ServerName example.com
     ServerAlias www.example.com

     <Directory /var/www/glpi/>
        Options +FollowSymlinks
        AllowOverride All
        Require all granted
     </Directory>

     ErrorLog ${APACHE_LOG_DIR}/error.log
     CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
```
```
sudo a2ensite glpi.conf
```
```
sudo a2enmod rewrite
```
```
sudo systemctl restart apache2.service
```
```
`sudo rm /etc/apache2/sites-enabled/000-default.conf`
```
```
`sudo rm -rf /var/www/glpi/install/`
```
