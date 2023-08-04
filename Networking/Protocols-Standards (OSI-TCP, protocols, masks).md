# Protocols and network config

- Structure of elements between 2 computers (5 layers)
	- Emitter (machine)
	- Transmitter (interface)
	- Transmission (copper, air, fiber)
	- Receiver (interface)
	- Receiver (machine)

- Protocol = shared language between machines

- Coding : transforming the data to something the protocol can interpret and vice versa
	- ex : phone mic (vibration) transforming to signal / signal transforming to sound in the earing of the phone

- Encapsulation
	- Adding informations to the raw message as :
		- Destination
		- Protocol info
		- ...

- A message can be framed in order to respect the protocol max size of packets.

- Sync and frame management protocol (avoid collisions between packets)
	- -> Defines who talks and what to do if errors
	
	- Flow control system : give chance to each host to send data
	- Waiting time : when exceeded, will allow host to send error message (no responses given)

- **Sending Methods**
	- Unicast : to one host
	- Multicast : to multiple hosts
	- Broadcast : to all hosts

- **Network Protocols**
	- open : standard and can be used by everyone
	- proprietary : belong to a company for instance

- **Application protocols**
	- DNS : Domain Name System
	- BOOTP : allows a machine to know its ip on the network
	- DHCP
	- SMTP : Simple Mail Transfer Protocol
	- POP : Post Office Protocol (retrieve emails from mail server to host machine)
	- IMAP : same as above, but remote
	- FTP : File Transfer Protocol
	- TFTP : same as FTP, without acknowledgement
	- HTTP : HyperText Transfer Protocol (transfer data as media, text, graph over the web)
	- UDP : User Datagram Protocol (packets transfer without acknowledgement)
	- TCP : Transmission Control Protocol (more reliable)

- **Internet protocols**
	- IP : internet protocol (groups messages into packets and indicate destination address)
	- NAT : convert local address into global address (world network)
	- ICMP : Internet Control Message Protocol (for errors)
	- OSPF : Open Shortest Path First (route packets to the right direction)
	- EIGRP : Enhanced Interior Gateway Routing Protocol (cisco proprietary, protocol that gives an appropriate metric according to the bandwidth)

- **Network access protocols**
	- ARP : address resolution protocol (provides mapping between MAC and IP add)
	- PPP : Piont to Point Protocol (allows packets to be encapsulated)
	- Ethernet (cabling in signaling rules)
	- Interface Drivers (allows host to communicate with its network interface)

# Communication standards

- **OSI (7 layers)**
1. Physique
2. Liaison
3. Réseau
4. Transport
5. Session
6. Présentation
7. Application

![OSI and protocols](https://1.bp.blogspot.com/-sIzvnoBGNOc/Xnep1Z8C7UI/AAAAAAAAARM/alEV0at7DQcU_7aL1BV85npcJFrfFJxOgCLcBGAsYHQ/s1600/osi-model-7-layers-804x1024%2Bcopy.png)

- **TCP/IP (4 layers)**
1. Réseau
2. Internet
3. Transport
4. Application

![TCP/IP and Protocols](https://camo.githubusercontent.com/be754a45a8d7053944543101ac174fe8ceed200e8332715ebbf5024e70753b7b/68747470733a2f2f6d796265636f64652d66696c65732d70726f64756374696f6e2e73332d65752d776573742d312e616d617a6f6e6177732e636f6d2f62653238396539312d303065662d343938352d393266622d6530393863313333353066632d7463702d70726f746f636f6c2d737569742e706e67)

**Data Transfer**

- Segmentation (dividing data in several frames)
- Multiplexing (mixing packets)
- Frame transformation (encapsulation)
	- Dividing data into segments
	- Encapsulating those segments following protocols
	- Creating packets
	- Sending packets
- Decapsulation
	- Receiving packets
	- Decapsulating data (opposite direction of encapsulation)

**Network addresses**

- MAC (data link layer)
	- Physical address, network card, can't be used outside a local network
- IP (network layer)
	- Origin/Destination address, has a network part and host part

**Subnet mask charts :**

![Subnet masks chart](https://2.bp.blogspot.com/_KjNkTh3VA1Y/S8rCAPONZ4I/AAAAAAAAAPo/C76ssp9fsU0/s1600/subnetting_c.png)

![Subnet masks chart 2](https://www.auvik.com/wp-content/uploads/2014/07/common-subnet-masks-table-800x315.png)
