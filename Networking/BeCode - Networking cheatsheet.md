# Exploration

- LAN : Local Area Network
- WAN : Wide Area Network
- MAN : Metropolitan Area Network
- WLAN : Wireless Local Area Network
- SAN : Storage Area Network

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
