
Installer Virt Manager
1) Mettre à jour les répertoirs et paquets.
2) Installer les paquets : qemu virt-manager virt-viewer dnsmasq vde2 bridge-utils openbsd-netcat
3) Installer les paquets (si pas encore installés) : iptables ebtables
4) Installer le paquet : libguestfs
5) Activer le service : libvirtd.service
6) Lancer et vérifier le service : libvirtd.service
7) Ajouter l’utilisateur au groupe virt pour lancer sans root : 
```
$ usermod -a -G libvirt $(whoami)
```
9) Relancer le service : libvirtd.service