
Se connecter à GitHub en SSH sur linux : Guide

1) Installer OpenSSH
```
sudo apt install openssh-server
```
    
2) Générer les clés publiques et privées et les ajouter à l'agent SSH
```
ssh-keygen -t ed25519 -C «email@example.com»

eval «$(ssh-agent -s)»
> 	Agent pid ***

ssh-add ~/.ssh/id_ed25519
```

3) Ajouter la clé SSH publique au compte GitHub (voir sur le site dans les settings)

4) Tester la connexion avec la commande suivante :
```
ssh -T git@github.com
```