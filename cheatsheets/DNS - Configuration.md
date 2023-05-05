
## What is DNS?

The Domain Name System (DNS) is the phonebook of the Internet. Humans access information online through [domain names](https://www.cloudflare.com/learning/dns/glossary/what-is-a-domain-name/), like nytimes.com or espn.com. Web browsers interact through [Internet Protocol (IP)](https://www.cloudflare.com/learning/network-layer/internet-protocol/) addresses. DNS translates domain names to [IP addresses](https://www.cloudflare.com/learning/dns/glossary/what-is-my-ip-address/) so browsers can load Internet resources.

Each device connected to the Internet has a unique IP address which other machines use to find the device. DNS servers eliminate the need for humans to memorize IP addresses such as 192.168.1.1 (in IPv4), or more complex newer alphanumeric IP addresses such as 2400:cb00:2048:1::c629:d7a2 (in IPv6).

## Installation and Configuration

sudo apt install bind9

nano /etc/hostname

nano /etc/resolv.conf

	nameserver 192.168.100.143
	search ubuntu-server.local

cd /etc/bind

nano named.conf.local

```
zone "ubuntu-server.local" {
    type master;
    file "/etc/bind/direct";
};
```
```
zone "100.168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/reverse";
};
```

cp db.local direct

nano direct
```
;
; BIND data file for local loopback interface
;
$TTL	604800
@	IN	SOA	server1.ubuntu-server.local. root.server1.ubuntu-server.local. (
			      2		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	ubuntu-server.local.
@	IN	A	192.168.100.10
server1	IN	A	192.168.100.10
www	IN	CNAME	ubuntu-server.local.

```

cp direct reverse

```
;
; BIND data file for local loopback interface
;
$TTL	604800
@	IN	SOA	server1.ubuntu-server.local. root.server1.ubuntu-server.local. (
			      2		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	server1.ubuntu-server.local.
server1	IN	A	192.168.100.10
10	IN	PTR	server1

```

named-checkconf -z

cat /etc/resolv.conf

sudo systemctl restart bind9

sudo systemctl status bind9