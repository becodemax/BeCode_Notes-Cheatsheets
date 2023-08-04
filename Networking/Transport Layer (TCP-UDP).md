# Transport Layer

**Protocols** : 

- Establishing communication between 2 devices
- Following the exchange of applications on the network
- Segmenting the data and reconstituting it (thanks to headers)
- Identifying the applications and assigning a port to each of them
- TCP : reliable (packets tracing) but slower
- UDP : unreliable (no packets tracing) but faster (useful for stream or audio)

### TCP

**TCP Headers** :

![TCP Headers Image](https://i1.wp.com/networkustad.com/wp-content/uploads/2019/05/TCP-Header.png)
- Sequence number (ISN) : used for data reorganization 
- Acknowledgment number : indicate de receipt of data
- Window : the number of segments accepted at the same time
- Checksum : used to check segments errors

**Handshake** :

- Handshake is the way to establish a connection between 2 devices
	- Verifying the identity of the devices
	- Establishing the connection between them
- 3 steps are requiered = 3 way handshake
	- SYN - SYN - ACK
	![3way-handshake-image](https://camo.githubusercontent.com/9167c0b48c8b58590476820d2f2b47dcbc6ff1baa4d216349691f4f84ada1897/68747470733a2f2f6c696e757868696e742e636f6d2f77702d636f6e74656e742f75706c6f6164732f323032312f30352f696d616765322d332e706e67)
	- Outcomes :
		- No response (system not avaible or wrong protocol)
		- Rejected (system got the message, but refused the connection)
		- Accepted

**Requests types** :

- SYN : sync 
- FIN : end of connection (no data from the sender)
- URG : urgent packet
- ACK : acknowledgment
- PSH : push function
- RST : reset connection

### UDP

**UDP frames Headers** :

![UDP Header Image](https://www.csestack.org/wp-content/uploads/2017/02/UDP-header-format.png)

- All applications that use UDP protocol must have a function to reorganize all the data received.
	- DNS, SNMP, TFTP, VoIP, Television over IP, etc.