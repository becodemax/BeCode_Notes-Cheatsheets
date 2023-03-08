# Exploration

- LAN : Local Area Network
- WAN : Wide Area Network
- MAN : Metropolitan Area Network
- WLAN : Wireless Local Area Network
- SAN : Storage Area Network
- DHCP : Dynamic Host Configuration Protocol
- PDU : Protocol Data Unit

- Intranet : réseau interne possédé par une compagnie par exemple
- Extranet : permet à un réseau interne de communiquer avec l'extérieur

- traceroute / tracert : permet de suivre l'itinéraire des paquets de données

# IOS Configuration

- IOS : Internetwork Operating system
- Access via : terminal, ssh
- Commands modes :
	- User mode : monitoring, no configuration
	- Privileged mode : for configuration
	- Configuration mode : accessible through privileged mode
		- Device configuration
	- Line configuration mode
		- Command line (console) configuration
	- Interface configuration mode
		- Interface (network) configuration
- Device name :
	- Begin with a letter
	- Not contain spaces
	- End with a letter or a number
	- Less than 64 char
- Commands examples to change hostname of a switch
```
# configure terminal
# hostname SW-floor-1
```
- In order to secure a network :
	- Set passwords for priviliged user, user and remote access
	- Encrypt those passwords
	- Add legal notice


**Setting up password**

- Commands :
``` 
enable secret
```
(global configuration mode, privileged user)
``` 
password (online configuration mode, user)
```
(online configuration mode, user)

- for ssh, enter the vty configuration mode and use the same commands above
``` 
banner word #<message>#
```
(to setup a message that will displays at each connection)


**Configuration files**

- startup-config file
	- configuration is retained in RAM despite system shutdown
- running-config
	- configuration will reset when reboot
- Commands if something goes wrong with config file
``` 
reload
erase startup-config
```

**Setting up the interface's IP Address**

```
interface vlan1
ip address 192.168.0.12 255.255.255.0
no shutdown
```
(select vlan1, set ip add and mask, reboot)


# Protocol and network config

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

# Ethernet

### Protocol's layers location

- **Standard : protocol on layers 2 and 3**
	- Sub-layers :
		- LLC (communication between these 2 layers)
		- MAc (lower layer, hardware level)
- MAC :
	- Encapsulating data
		- Frame Delimitation (sync between 2 devices)
		- Physical addressing of the frame
		- Error detection
	- Controling access
		- Medium (hardware and software)
		- Possible collisions

### Frame Structure

- Fragments size between 64-1518 bytes
- Outside these values = collision fragment

|Preamble|Destination address|Source address|Type|Data|Frame check|
|---------|----------------------|--------------|----|-------|----------------|
|8 bits|6 bits|6 bits|2 bits|46 to 1.500 bits|4 bits|

- **Preamble** : sync between devices
- **Destination address** (allow uni, multi and broad)
- **Source address** (origin)
- **Type** (protocol of previous source)
- **Data** : encapsulated data of the previous layer
- **Frame check** : check for errors and end of the frame

### Hexadecimal

**Hexadecimal table :**

![Hexadecimal Table Image](https://camo.githubusercontent.com/32a4f082cd5f509732a4cb7be03000f7753f07d12cc37e03676036072dcc9302/68747470733a2f2f63727970746c6162732e636f6d2f77702d636f6e74656e742f75706c6f6164732f323032312f30372f315f506b484c683239366c70767945794a324b50786453772e706e67)

**Examples of protocols frames type in hex** :

- 0x800 (IPV4 address)
- 0x86DD (IPV6 address)
- 0x806 (ARP request)

**MAC Adresses** :

- In hexadecimal characters
- In pairs (separated by `:` or `-`)
	- 00-05-9A-3C-78-00
	- 00:05:9A:3C:78:00
- In quad (separated by `.`)
	- 0005.9A3C.7800
- Two parts of 24bits
	- One defined by IEEE
	- Other by manufacturer
- Unique for each device (worldwide)
- Non-volatile
	- But can be changed in OS (ram)

**Switches** :

- Method used by switches to transfer frames :
	- Cut-through (faster but no errors check)
	- Store and forward (slower but errors check)
- Buffers
	- Store data temporarily when data flow > data processing
	- Port-based
	- Memory-based

**ARP Protocol :**

- ARP protocol associates/resolves MAC addresses and IP and keep everything in a mapping table.
- The mapping table is contained in RAM.
- If a MAC address is not available, a ARP request is sended through the network.
- ARP request contains either the IP or the MAC address which must be completed
- Ethernet frame headers of a ARP request :
	- Broadcast MAC address (everyone can respond)
	- Source MAC address (origin of the request)
	- Frame type (0x806) = ARP request

**ARP spoofing attacks** :

- Denial Of Services (DoS)
	- Mutliple IP addresses attempting to connect to one MAC address at the same time, causing the device to be overwhelmed and probably crash.
- Session Hijacking
	- Stealing ID and passwords to gain access to private data for instance.
- Man In The Middle (MITM)
	- Intercepting and changing traffic data between victims.

