## Sources :

- https://www.varonis.com/blog/blackcat-ransomware
- https://www.microsoft.com/en-us/security/blog/2022/06/13/the-many-lives-of-blackcat-ransomware/
- www.notifycyber.com

## What is it?

- Rebranding of BlackMatter
	- Successor of REvil and DarkSide
- BlackCat = ALPHV
- RaaS = Ransomware-as-a-Service
- Human-operated attack
- Increased activity since nov 2021
	- Recruiting ++
- Target large organizations across the entire world
	- Big ransoms : $400K - $3M
- Advertising (Russian)
	- Affiliates are enticed to join the group : up to 90% of the ransom returned.
- Triple extorsion
	- Data encrypted
	- Data leaks threats if not paid
	- DDoS if not paid

## What's inside?

- Rust-based
	- Fast
	- Cross-platform (Linux, Windows and VMWare instances)
	- Customizable
	- Evading detection
- Use Zeroise
	- Clears encryption secrets from compromised host
- Built-in privilege escalation
- Can propagate across the network
- Can stop VMWare VMs
- Command-line interface (--help)
- Multi-thread worker
- Masquerade_PEB (appearance of another process -> allow elevated operations)
- UAC bypass

## I mean... How?

1) Initial intrusion = tried and tested
	- Multiple entry points 
	- CVEs in network, weak creds, etc.
	- Changing Windows Defender settings and launching binaries through network
		- -> Using PsExec
3) Lateral movement once initial intrusion executed
	- Valuable data exfiltration and remembered for later encryption
4) Crafting the executable according to the victim's infrastructure
	- Encryption performance
	- Embedded victim's credentials
5) Injecting payload and starting the attack

## Cases

#### 1) Unpatched server exchange

- Exchange vulnerability leads to executing commands via cmd
	- Collecting infos about the system, domains, etc.
	- Discovering credentials
	- Deleting compromising activity files
	- Finding ways for potential lateral movement



