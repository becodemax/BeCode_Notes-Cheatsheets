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


Setting up password

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
banner word #<message#
```
(to setup a message that will displays at each connection)


Configuration files

- startup-config file
	- configuration is retained in RAM despite system shutdown
- running-config
	- configuration will reset when reboot
- Commands if something goes wrong with config file
``` 
reload
erase startup-config
```

Setting up the interface's IP Address

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

- Sending Methods
	- Unicast : to one host
	- Multicast : to multiple hosts
	- Broadcast : to all hosts

- 