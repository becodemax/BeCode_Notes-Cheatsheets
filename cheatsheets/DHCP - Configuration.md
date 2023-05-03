The most common settings provided by a DHCP server to DHCP clients include:

-   IP address and netmask
    
-   IP address of the default-gateway to use
    
-   IP addresses of the DNS servers to use
    

However, a DHCP server can also supply configuration properties such as:

-   Hostname
    
-   Domain name
    
-   Time server
    
-   Print server

## Installation and configuration

sudo apt install isc-dhcp-server

nano /etc/dhcp/dhcpd.conf

```
# minimal sample /etc/dhcp/dhcpd.conf
default-lease-time 600;
max-lease-time 7200;
    
subnet 192.168.1.0 netmask 255.255.255.0 {
 range 192.168.1.150 192.168.1.200;
 option routers 192.168.1.254;
 option domain-name-servers 192.168.1.1, 192.168.1.2;
 option domain-name "mydomain.example";
}
```

nano /etc/default/isc-dhcp-server

```
INTERFACESv4="enp1s0"
```

sudo systemctl restart isc-dhcp-server.service