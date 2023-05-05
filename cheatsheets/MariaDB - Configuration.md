```
sudo mysql -u root -p
```

## MariaDB >

```
create database glpi;
```
```
create user 'glpi'@'localhost' identified by 'password';
```
```
grand all privileges on glpi.* to 'glpi'@'localhost';
```
```
flush privileges;
```
```
exit
```

