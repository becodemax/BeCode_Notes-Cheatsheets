
## What is DNS?

The Domain Name System (DNS) is the phonebook of the Internet. Humans access information online through [domain names](https://www.cloudflare.com/learning/dns/glossary/what-is-a-domain-name/), like nytimes.com or espn.com. Web browsers interact through [Internet Protocol (IP)](https://www.cloudflare.com/learning/network-layer/internet-protocol/) addresses. DNS translates domain names to [IP addresses](https://www.cloudflare.com/learning/dns/glossary/what-is-my-ip-address/) so browsers can load Internet resources.

Each device connected to the Internet has a unique IP address which other machines use to find the device. DNS servers eliminate the need for humans to memorize IP addresses such as 192.168.1.1 (in IPv4), or more complex newer alphanumeric IP addresses such as 2400:cb00:2048:1::c629:d7a2 (in IPv6).

## A Record

**A (address) records** are one of the most basic and commonly used DNS record types. They translate domain names and store them as IP addresses. A records can only hold IPv4 addresses.

An example of an A record is:

| Domain Name           | Record Type | Value       | TTL   |
|-----------------------|-------------|-------------|-------|
| example-website.com @ | A           | 192.168.0.1 | 14400 |
|                       |             |             |       |
|                       |             |             |       |

In the example above, the record is made up of the following elements:

-   **Domain name:** Contains the domain name of the website. The "@" symbol indicates that the record contains the root domain name.
-   **Record type:** Indicates the usage of an A record type.
-   **Value:** Contains the IP address associated with the domain name.
-   **TTL:** Lists the record's TTL (Time to Live) in seconds. The default value is 14400, which means the record expires after 14400 seconds (240 minutes).

## CNAME Record

A **CNAME (canonical name) record** is used instead of an A record if a domain is an alias for another domain. Because of this, all CNAME records point to a domain instead of an IP address.

For example, in a domain called **alias-domain.com** which works as an alias for **real-domain.com**, a CNAME record for would look like this:

| Domain Name        | Record Type | Value           | TTL   |
|--------------------|-------------|-----------------|-------|
| alias-domain.com @ | CNAME       | real-domain.com | 14400 |
|                    |             |                 |       |
|                    |             |                 |       |

This record contains:

-   **Domain name:** Contains the alias domain name. The "@" symbol shows that this is a root domain name.
-   **Record type:** Shows that this is a CNAME record.
-   **Value:** Contains the real domain name that the alias domain is pointing to.
-   **TTL:** Time left until the record expires.

CNAME records usually contain subdomains that point to a domain's A or AAAA record. This prevents having to create an extra A or AAAA record for each subdomain.

It is not recommended to have CNAME records pointing to other CNAME records, as this creates unnecessary steps to the DNS lookup process.

## Installation and Configuration (bind9)

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