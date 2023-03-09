# Network Layer

**The IP protocol on the network layer takes care of** :

- Destination address
- Encapsulation of PDU data from previous layer (such as dest and src ip)
- Routing path
- De-encapsulation of packets incoming

**The IP protocol on the network layer is** :

- Connectionless
- Not a protocol that will follow packets (no errors messages)
- Independent of the medium **but** adapts the size of the packet according to it

**IPV4 address headers** :

![IPV4 Headers Image](https://bravelearn.com/wp-content/uploads/2014/11/IPv4-headers.png)

- Version (of the IP address)
- DS (Different Service - prioritizing packets)
- Protocol (of previous layer)

**IPV4 limitations** :

- Number of IP addresses available/limited
	- Use of NAT needed
- Thus routing table filling up more and more until no address left

**Solution to IPV4 limitations = IPV6** :

- Address space of 128 bits (instead of 32 bits for IPV4)
- More efficient in terms of processing packets
- No need to use NAT anymore

**IPV6 address headers** :

![IPV6 Headers Image](https://networkel.com/wp-content/uploads/2017/01/IPv6_header_rv1.png)

- Traffic class : defines packets priority
- Flow label : specify that all packets with the same label should be processed the same way (increases efficiency)

**Routing** :

- Gateway : address that allow traffic to get through one network to another (remote)
- Routing table : associate a physical address to an IP address
- Routing line is composed by :
	- Method (static, enhanced or open shortest path)
	- Destination (ip)
	- Distance (of the route)
	- Metric (distance from the target)
	- Next leg (your router)
	- Route timestamp (last time the route was maintained)
	- Interface (destination)

**Routers** :

- Routers are like computers :
	- RAM (store information temporarily)
	- ROM (can't be modified, except by cisco)
	- Non-volatile RAM (use as storage, for config file for instance)
	- Flash memory (contains sys and logs)
	- Advanced integration module (offload cpu from heavy actions)
- Boot time :
	1. Sys in flash loaded in ram
	2. Execution of post-tests and startup program loading
	3. Loading IOS
	4. Locating and loading config file