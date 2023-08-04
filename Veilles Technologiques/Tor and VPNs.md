- What is Tor?
- How does it work?
- What's the difference with a VPN?
- Pros and cons?
- Is it illegal?
- How can I use it?

## What is Tor?

- Network service / Browser
- Open Source and free to use
- Clever way to enhance anonymity
- Allow access to classic web and dark web
	- Dark Web = Web non indexed on classic web

## How does it work?

- Onion routing
	- Messages are encapsulated in layers of encryption
- Passing through multiple volunteer servers = relays
- Entry node
	- Guard
	- Receive data and peels off the first layer of encryption
	- Knows your IP and the IP of the next relay
	- Doesn't know which site you're visiting or your identity
- Exit node
	- Last layer of encryption
	- IP showed to the website you're visiting

## What's the difference with a VPN?

- Same principle as a VPN : hide your IP to the website you're visiting
- Process is different though :
	- VPN :
		- Single server
		- Single layer of encryption (end-to-end)
		- Sees website you're visiting (logs)
	- TOR :
		- Multiple servers (at least 3)
		- Encryption peeling of as you travel from server to server
		- Separate the knowledge of who you are and the website you are visiting

## Pros and cons

Pros :
- Anonymity
- Security
- Web accessibility even in really closed country

Cons:
- *R e a l l y  s l o w*
- Have to trust the nodes (relays)
- Potential leaks possible in the exit node
	- e.g HTTP, SSL Stripping

## Is it illegal?

- Same as VPN
	- No legal problems unless you do something bad

## How can I use it?

- Tor Browser can be used alone
- Tor + VPN configs :
	- Onion over VPN :
		- Connect to VPN, then Tor
		- Home network only sees VPN address
		- First Tor relay only sees VPN address
		- VPN can't see which sites you're visiting
	- VPN over Onion :
		- Less anonymity than above config
		- Protect you from MiTM attacks on the exit node