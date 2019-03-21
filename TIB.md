# TIB

## Modèle de référence OSI

Il sert de modèle conceptuel de référence mais il n'est pas appliqué. Mais il définit les fonctionnalité. 

1. physique : le format du connecteur, la forme du signal, durée d'impulsion. elle sert à transporter des bits. 
2. liaison : Il fait la liaison entre deux points.  Le but de cette couche est de simuler une liaison parfaite pour les couches supérieur. Il ajoute une somme de contrôle. mais si le paquet est corrompu, il ne retransmet pas le paquet
3. réseau: interconnecter les sous-réseau de manière générale. acheminement de paquets entre la sources et le destinataire. adressage des nœuds réseaux. interconnexion de réseaux hétérogènes (fragmenter les paquets)
4. transport : la seule couche qui travaille avec les serveurs terminaux. Si le paquet n'est bien arrivée, c'est le serveur récepteur qui envoie au serveur émetteur. service fiable, pour la plupart des services, Ou service non fiable, pour l'audiovisuel, pour la lecture de vidéo pour fluidifier la transmission et la lecture. 
5. session: Permet d'établir des session entre les utilisateurs pour la transmission de grand fichier.  il enregistre le statut de la transmission. si la connexion tombe, elle reprend depuis son dernier statut. En général pas implémenter. 
6. présentation: s'occupe de la syntaxe des données transmises. comme par exemple entre big endian et little endian ou ASCII unicode. 
7. application: protocoles des applications. un email vers protocole SMTP. Elle est implémenter dans le système d'exploitation. 

## EXO modèle OSi 

fonctionnalité de transport: somme de contrôle, un numéro de séquence, si tout est correct, on quittance. si pas OK, il retransmet. établir une connexion. gère le débit de transmission. 

fonctionnalité de réseau: langage commun qui permet d'interconnecter les réseaux, le routage, la fragmentation de paquets. système d'adressage 

## Modèle TCP/IP

Ce modèle représente la pratique. 

1. hôte-réseau: ethernet, wifi, PPP
2. Internet. couche réseau du modèle OSI. IPv4 IPv6. ICMP (ping) si on fait un ping sur une adresse qui n'existe pas, le routeur fait un message d'erreur et il détruit le paquet. RIP est un protocole de routage.  
3. Transport: TCP réalise un service fiable pour la couche supérieur. UPD réalise un service non fiable.
4. Application: HTTP, SMTP pour envoyer des emails, DNS traduction de nom de domaine en adresse IP, SIP protocol pour VOip. 

### Adressage

Chaque couche a une adresse différente. Les adresses font partie des en-têtes de chaque couche. Dans une trame ethernet, il y a l'adresse MAC destinataire et source, Paquet ip, ype (IPv4, IPv6, etc), protocole (TCP ou UDP) et dans le paquet UDP il y a le port qui indique à quel application est destiné la trame. 

Les fonctionnalité de la couche liaison est de découper la donnée en plusieurs paquets, d'assurer une liaison parfaite pour la couche supérieur. La particularité de cette couche est qu'elle gère la connexion entre voisin. Le routage des paquets est fait par la couche réseau. 

# Réseau LAN 

Lan est utilisé dans les entreprises et à domicile. Ils interconnectent les PC, serveurs, les imprimantes à courte distance.  La technologie utilisée est Ethernet ou WIFI. Elle a comme particularité d'être à haut débit, Multicast/Broadcast (envoi de paquets en diffusion est important). Si on ne sait pas l'adresse d'un destinataire, on envoie un paquet ARP et après la machine répond. 

Sa connexion est principalement en étoile avec un Hub ou un switch qui interconnectent les stations. Le câblage ethernet UTP comprend 4 paires torsadées non blindées. sur 10 et 100Mb/s seulement deux 2 paires sont utilisés. Les câbles vont jusqu'à 100m et possède plusieurs catégories. Le connecteur est 8P8C (et pas RJ45), c'est le connecteur standard pour ethernet sur câble UTP. 

La paire de transmission de la source doit être la paire de la réception. cela implique un croisement des paires. Les hub et les switchs effectuent un croisement interne. L'autocross permet aux machines de se mette d'accord sur qui fait le croisement. 

Les trames ehternet existent sous deux formats incompatibles. Le format ethernet 2 et le 802.3. Les 8 premier octets sont pour la synchronisation T/R, ensuite vient l'adresse MAC de destination, adresse MAC source.  Pour ethernet 2 il a ensuite 2 bytes pour le type, pour 802.3 les 2 bytes sont pour la longueur des données. La taille minimum des données est 46 octets et le maximum 1500 octets. Ethernet n'effectue pas de retransmission de trames erronées. 

L'adresse physique d'une carte réseau  est en générale programmé dans la ROM et elle est unique. mais on peut changer deux machines peuvent avoir la même adresse pour faire une redondance. Les trois premiers octets correspond au constructeur de la carte.  Les trois derniers octets identifie la carte. 

Les adresses MAC de groupe sont signalé par le dernier bit du premier octet. S'il est paire c'est individuelle, sinon c'est une adresse de groupe. Les adresses de broadcast sont  utiliser pour les requêtes DHCP. 

  