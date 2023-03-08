# Cisco config commands

### Switch config commands :

- Enter EXEC (privileged mode)

```
enable
```
- Enter config mode :
```
configure terminal
```
- Change hostname :
```
hostname <hostname>
```
- Assign password to priviliged EXEC (config mode) :
```
enable secret <password>
```
- Assign password to Telnet (config mode) :
```
line vty 0 15
password <password>
login
exit
```
- Assign password to console (config mode) :
```
line console 0
password <password>
login
exit
```
