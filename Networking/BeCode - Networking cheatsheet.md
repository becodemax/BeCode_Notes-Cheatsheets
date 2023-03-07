# Exploration

- LAN : Local Area Network
- WAN : Wide Area Network
- MAN : Metropolitan Area Network
- WLAN : Wireless Local Area Network
- SAN : Storage Area Network
- DHCP : Dynamic Host Configuration Protocol

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

- **TCP/IP (4 layers)**
1. Réseau
2. Internet
3. Transport
4. Application

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



