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
- Can stop if in VMWare VMs
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

## Case

#### Unpatched server exchange

1. Initial Intrusion (discovering vulnerabilities for later lateral movement)
	1. cmd.exe -> ver & systeminfo (os infos)
	2. net.exe -> domain info (controllers, computers and admins)
	3. Finding credentials (password folder)
	4. Deleting all initial activity logs at the end
2. Initialising lateral movement
	1. Mounting a shared network
	2. Launching WMIC.exe (collect more infos and computers control)
	3. Check all hosts and their connectivity
	4. Collecting last sign-in events via Get-ADComputer
3. Multiple lateral movements in order to collect as much infos as they can
	1. Creating fake legitimate processes in background to collect those
	2. Collecting policies, groups, domains, etc.
4. Stealing intellectual properties for double extortion (taking days)
5. Encryption and ransom
	1. Two weeks after initial intrusion
	2. Distribution of payload via PsExec.exe

#### Prevent those incidents

1. Switch defensive strategies
	1. Accordingly to attackers TTPs
2. Avoid weak credentials
3. Keep all services and devices up to date
4. Set up or improve access monitoring
5. (Bonus) Microsoft 365 Defender can now detect suspicious activities related to BlackCat 