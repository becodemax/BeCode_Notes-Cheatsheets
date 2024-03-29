### Security, compliance and identity (10-15%)

#### Security Compliance concepts and methodologies

**Zero Trust Security :**
- Verify explicitly, least privileges and assume breach
- Six Pillars (IDADIN) :
	1. Identities (authentication monitoring)
	2. Devices (infrastructure monitoring)
	3. Applications (usage and access monitoring)
	4. Data (classified, labeled and encrypted)
	5. Infrastructure (versions, configs)
	6. Networks (segmentation, encryption and monitoring)

**Shared Responsibility :**
- Depends on the services provider
- SaaS, PaaS or IaaS
	- Software as a Service
	- Platform as a Service
	- Infrastructure as a Service
- *Always retained by you*
	- Data
	- Endpoints
	- Account
	- Access Management

**Defense in depth :**
- = Defense in multiple layers

**Common threats :**
- Data Breach
- Dictionary attack
- Ransomware
- Disruptive attack

**Encryption/Hashing :**
- Encryption - At rest / In transit
	- Storing data
	- Transiting data
- Hashing
	- Storing hashed passwords

**CIA :**
- Confidentiality
- Integrity
- Availability

**Cloud Adoption Framework for Azure (CAF) :**
- = Methodology to implement cloud computing and technology for a business
- Lifecycle :
1. Strategy
2. Plan
3. Ready
4. Adopt
5. Govern
6. Manage

#### Concepts of Identity

**Identity as primary security :**
1. Administration
2. Authentication
3. Authorization
4. Auditing

**Identity providers :**
- Create, maintain and manage identities
- Provides authentication services to apps
- External users with Azure AD can automatically connect to infrastructure
	- B2B - Between to Business
	- B2C - Between to Customers

**AD - Active Directory :**
- Hierarchical structure that stores infos about objects on the network
- AD DS - Active Directory Domain Services :
	- Storing directory data and making this data available to network users and admins
- Informations about users accounts :
	- names, passwords, phone numbers, etc.

**Federated services :**
- Allowing user to access services of another trusted domain with the same identity
- "Shared credentials"

**Identity attacks :**
- Passwords bruteforce
- Phishing
- Spear phishing

### Microsoft Identity and Access Management Solutions (30-35%)

**Azure AD Identities :**
- *User* - employees or guests
	- Groups - multiple users with same access needs
- *Service Principal* :
	- Identity used by applications to access Azure resources
- *Managed Identity* -> Identities provided and managed by Azure
- *Device* -> Piece of hardware and infos related to it (type, owner, etc.)

**Hybrid Identity :**
- Password Hash Synchronization (PHS)
	- User connect remotely, synchronizing pwd hash to pwd hash of user's instance on-premises
- Pass-through authentication (PTA)
	- Authenticating directly against Azure AD
- Federated Authentication
	- Degree of trust may vary

**Authentication methods :**
- Best = Windows Hello

**SSPR (Self-Service Password Reset) :**
- Allow user to reset password without admin or helpdesk

**Password protection and management capabilities :**
- Global banned password list (most known weak passwords)
- Custom banned password list (key words like enterprise name, location, etc.)
- Password spray (same)
- Hybrid security (integrated Azure AD password security)

**Windows Hello :**
- Best authentication method
- Credentials are tied to a device and use biometric or PIN
- Windows Hello Convenience PIN :
	- Not backed by asymetric or certificate 
- Windows Hello for Business :
	- Backed by asymetric or certificate

### Microsoft Security Solutions (35-40%)

**Network security groups :**
- Provide list of allowed/denied communications between networks and subnets
- Isolate applications between environment, tiers and services

**Azure DDoS protection :**
- Volumetric attack
	- Substantial amount of seemingly legitimate traffic
	- UDP floods, amplification floods, and other spoofed-packet floods
- Protocol attack
	- Weakness on layer 3 and 4
	- SYN flood attacks, reflection attacks, and other protocol attacks
- Resource (application) layer attacks
	- Web application
	- HTTP protocol violations, SQL injection, cross-site scripting, and other layer 7 attacks

**Azure Firewall :**
- Cloud Based
- High availability and unrestricted scalability 
- Protection for non-HTTP/S protocols :
	- RDP, SSH, FDP, etc.

**Azure Bastion :**
- Provides seamless secured SSH and RDP connectivity
- Using Azure Portal (TLS = Transport Layer Security), passing through firewall
	- Protection against port scanning
	- Protection against zero-day exploits
- HTML5 Based
- No public IP required

**Web Application Firewall :**
- Simpler way to secure a web application against SQLi, XSS, etc.

**Azure Encryption :**
- Azure Storage Service Encryption
	- Protect data at rest
- Azure Disk Encryption
	- Protect OS
- Transparent data encryption
	- Protect Azure SQL database and data warehouse
	- Real time encryption and decryption
	- Automatic backups and transaction log files without changes in the application

**Azure Key Vault :**
- Centralized cloud service for storing your application secrets
- Secure access, permissions control, access logging capabilities

**Defender for Cloud :**
- Monitoring service tool that provides threats protection
- Includes incident response and implemented recommendations
- Features :
	- Compliance dashboard
	- Security alerts
	- Secure score
	- Resource security hygiene

**Azure Defender :**
- Enhanced features (paid)
	- Microsoft Defender for Endpoint
	- Vuln scan for VMs and containers
	- Multi-cloud security
	- Hybrid security (across different workloads)
	- Threat protection alerts
	- Access and application controls

**Cloud security posture management (CSPM) :**
- Tools and services in a cloud environment to monitor and prioritize security enhancements and features
- Automatic alerts to security staff
- Features :
	- Zero Trust-based access control
	- Real-time risk scoring
	- Threat and vulns management (TVM)
	- Discover sharing risks
	- Technical policy
	- Threat modeling systems and architecture
	- Hardening guidance

**Azure Sentinel :**
SIEM, SOAR and XDR
- SIEM - Security information and event management
- SOAR - Security orchestration and automated response
- XDR - Extended detection and response

Azure Sentinel = SIEM + SOAR

**Microsoft 365 Defender :**
Services :
- Defender for Identity
- Defender for Office 365 Apps
- Defender for endpoints
- Cloud App Security (between cloud user and cloud provider)

**Microsoft Intune :**
- Cloud-based service
- Focus on MDM & MAM
	- Mobile Device Management
	- Mobile Application Management

### Microsoft Compliances Solutions (25-30%)

**Offerings of Service Trust Portal :**
- Compliance Manager
- Trust Documents
- Industries and Regions
- Trust Center
- Resources
- My Library

**Microsoft Privacy Principles (6) :**
- Control
- Transparency
- Security
- Strong legal protections
- No content-bases targeting (advertising)
- Benefits to customer

**Data Classification Capabilities :**
- Sensitive information types
	- Server, airport code, emails, etc.
	- = Regex
- Trainable classifiers -> Machine Learning
	- Pre-trained or not

**Activity/Content Explorer :**
Activity explorer panel 
- Allow admins to see what's being summarized, labeled and all changes across the organization
Content explorer
- Allow admins to see content that has been summarized

**Sensitive labels :**
- Applied if sensitive data inside a file
- In the metadata
- Can be customized by the admins

**Retention policies :**
- Define the time in which a file will be retained, and will be deleted afterwards
- Reduce risks if breach

**Data loss prevention (DLP) :**
- Set of conditions that content must match before applying rules
- Actions to take if conditions match
- Locations where those rules are applied

**Insider Risk Capabilities in Microsoft 365 :**
- Helps organization by setting code-of-conduct for policy violations
- Features (to help the admin):
	- Information barriers
	- Privilege access management
	- Customer lockbox

**eDiscovery :**
- Identifying and delivering electronic information that can be used in legal cases
- Content search tool capabilities
	- Search in Exchange Online, OneDrive for business, SharePoint Online, Teams, emails, sites, etc.
- Regroup all of that information into a log file (.csv) for later audits
- Advanced audits
	- Increased log retention for advanced investigation and forensic
	- Require specifics Office 365 licenses

