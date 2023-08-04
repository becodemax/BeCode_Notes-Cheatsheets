### Nmap : Cheatsheet

-   man nmap/nmap -h

**Switches**

-   -sS
    -   Syn Scan
    -   « Half-open » 
    -   3-way handshake, n’établit pas de connexion entre l’hôte et l’attaquant et laisse le port ouvert.
-   -sU
    -   Scan UDP
-   -O
    -   Détection d’OS
-   -sV
    -   Scan des services et de leur version
-   -v / -vv
    -   verbose et verbose ++
-   -oA
    -   Output dans 3 formats majeurs
-   -oN
    -   Output en format normal
-   -oG
    -   Output en format grep
-   -A
    -   AGRESSIVE MODE !
-   -T(0-5)
    -   Timing (slower is safer)
-   -p
    -   Ports scan
    -   -p 123-456
    -   -p-
-   --script
-   -sn
    -   Ping Sweep
-   -Pn
    -   ping before scanning (firewall evasion)
-   -f
    -   Fragmenter les paquets (firewall evasion)
-   --mtu **"number"**
    -   Fragmenter les paquets (par multiple de 8)
-   --scan-delay "**time**"ms
    -   Aide pour les réseaux instables, permet dans certains cas de contourner le pare-feu.
-   --badsum
    -   Utilisé pour générer de faux paquets checksum (utiles pour détecter des erreurs durant la transmission d’un message par exemple).

**Scan Types**

-   -sT
    -   TCP connect scans  
-   -sS
    -   Half-open scans
-   -sU
    -   UDP scans
-   -sN, -sF, -sX
    -   TCP Null scans, FIN scans et Xmas scans
-   ICMP
    -   Internet Control Message Protocol
-   TCP Connect Scans
    - Nmap envoie une requête TCP sur un port spécifique à l’hôte, si l’hôte répond par un paquet TCP, alors le port est ouvert. Si l’hôte ne répond pas, alors le port est fermé.
        - La réponse formulée par l’hôte sera sous la forme SYN/ACK (synchronize and acknowledgment) qui tentera d’établir une connexion avec la machine attaquante.
        - Un port peut être protégé par un pare-feu et sera considéré comme « filtré ».
            - Configuration du pare-feu par iptables, ufw, etc.

-   Flags
	-   SYN : synchronize
	-   ACK : acknowlegdment
	-   RST : reset

-   SYN scan
	- Scan furtif. La machine attaquante envoie une requête SYN à la machine victime, cette dernière renvoie un paquet SYN/ACK à la machine attaquante, qui pour finir annule la tentative de connexion en envoyant un flag RST.
	- Permet de bypass les plus anciens systèmes de détection d’intrusions
	-  N’est souvent pas retenu dans les logs de connexions car la connexion ne sera pas entièrement établie.
	- La tentative de connexion n’aboutissant pas, le scan est plus rapide qu’un scan standard TCP.
	- Requiert les permissions sudo pour l’altération des paquets (RST)
	- Peut faire tomber certains services instables lors du scan

- UDP Scans
    - « UDP connections rely on sending packets to a target port and essentially hoping that they make it. »
    - Quand un paquet est envoyé par UDP, nmap n’attend pas de réponse. Si c’est le cas, nmap considéra le port comme ouvert/filtré (pare-feu).
        -   Dans le cas contraire, la cible répondra par un paquet ICMP (ping) qui dira que le port est inatteignable.  
    - Un scan UDP prend beaucoup plus de temps.
        -   Accélérer le scan : --top-ports 20
    - Nmap utilise des requêtes « vides »
    - Si l’on connaît un port et son service, on peut dès lors envoyer une requête spécifique contenant un payload, permettant d’obtenir une réponse plus ciblée.

- NULL, FIN and XMAS scans
    - Encore plus discrets que SYN scan. **«** **Firewall Evasion »**
    - NULL
        - Envoie une requête complètement vide, la cible répondra par un paquet RST si le port est fermé.
    - FINZ 
        - Presque similaire à NULL, à l’exception que ce type de requête est normalement utilisée pour terminer une connexion. La cible répondra par RST si le port est fermé.
    - XMAS
        - Consiste à envoyer un paquet TCP « malformé ». La cible répondra par RST si le port est fermé.
    - Attention, pour le protocle UDP, un port ouvert équivaut à un port filtré (dropping packets).
	- **Ces types de scans sont de nos jours, pour la plupart des systèmes, devenus obsolètes grâce à l’emploi de pare-feu bloquant l’accès aux paquets TCP entrant et contenant un flag SYN. Il est reste cependant possible de contourner cela, en envoyant une requête ne contenant pas NULLde flag SYN par exemple, mais il vaut mieux ne pas s’y fier à 100 %.**
    
-   Ping Sweep
    - NULL  Permet de découvrir l’architecture d’un réseau (hôtes disponibles)
        -   nmap -sn 192.168.0.1-254 
        -   nmap -sn 192.168.0.0/24
    -   ICMP echo request
    -   Envoie en plus à la cible les paquets suivants :
        -   TCP SYN sur le port 443
        -   TCP ACK sur le port 80 (si root)

**NSE Scripts (Nmap Scripting Engine)**

-   Scripts écrits en « Lua » qui permettent :
    -   Scan de vulnérabilités
    -   Automatisation des exploits
-   Catégories de scripts
    -   safe – n’affecte pas la cible
    -   intrusive – grande chance d’affecter la cible
    -   vuln – scan pour les vulnérabilités
    -   exploit – tente l’exploitation d’une vulnérabilité
    -   auth – tente de bypass l’authentification à un service
    -   brute – tente de bruteforce les indentifiants d’un service
    -   discovery – tente de récolter plus d’informations concernant les services présents
-   Scripts trouvables dans /usr/share/nmap/scripts
    -   Liste disponible dans /usr/share/nmap/scripts/script.db