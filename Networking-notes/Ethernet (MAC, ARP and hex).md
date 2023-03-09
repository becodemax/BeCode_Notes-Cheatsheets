# Ethernet

### Protocol's layers location

- **Standard : protocol on layers 2 and 3**
	- Sub-layers :
		- LLC (communication between these 2 layers)
		- MAC (lower layer, hardware level)
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