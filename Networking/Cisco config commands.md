# Cisco config commands

### Router config commands :

- Enter config (select interface) :
```
interface <interface> <123>
```
- Configure the network of the interface (ip) :
```
ip address 1.2.3.4 255.255.255.0
```
- Configure the gateway :
```
ip default-gateway 5.6.7.8
```
- Give a description :
```
description Link to LAN-10
```
- Restart the interface :
```
no shutdown
```

- Check the config :
```
show ip interface brief
show ip route
show interfaces
show ip interface
```


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
