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

  ## Ethernet avec un hub

un hub permet un câblage physique en étoile. Il se comporte comme un bus partagé topologie logiques. Ses principales fonctions sont le travail au niveau de couche physique, reçoit contrôle et régénère les bits reçus et un bit reçu est retransmis sur tous les ports.  

La transmission sur un médium partagé permet une seule transmission à la fois, si deux stations transmettent en même temps, il y a collision. dans ce cas, le récepteur reçoit n'importe quoi. si on utilise ce protocole on a plus de 80% de perte. Pour éviter cela, la méthode CSMA est utilisé. Il y a le CSMA persistant et non-persistant. Le CSMA persistant consiste à écouter et transmettre dès que le canal est libre mais il y a possibilité que deux émetteur essaie de transmettre en même temps. Le CSMA non persistant résout un peu le problème  en introduisant un délai aléatoire d'attente pour chaque machine. Le Carrier Sense écoute si le canal est libre avant de transmettre. Le Multiple Access partage le canal de transmission. S'il y a collision il envoie 32 bits de jam de bourrage de donnée aléatoire. Le jam sert à dire à tous les récepteur qu'il y a collision.  Pour détecter la collision, un émetteur transmet et écoute en même temps, s'il voit que cela ne correspond pas à ce qu'il a envoyé , il arrête de transmettre. la trame ethernet est prévue pour transmettre pendant 50 ms au minimum.  Ethernet utilise CSMA persistant et wifi non persistant. 

L'algorithme CSMA/CD apporte une amélioration de détection de collision. Il essaie de transmettre le paquet 16 fois et après il arrête. Si une collision est détectée, on envoie un jam, on attend un délai aléatoire et on ressaie. après chaque essai, le temps aléatoire augmente de manière exponentiel pour désengorger le réseau. 

## Ethernet avec un switch 

Un switch travaille à la couche 2, il connaît le format des trames et peut interpréter les adesses MAC. Quand il reçoit une trame, il l'analyse et la retransmet si elle est correct. Topologie physique et logique en étoile. Ses principaux avantages sont la transmission en parallèle, et il transmet la trame en fonction de son adresse. Ses fonctions sont la commutation de trames, l'acheminement vers le destinataire, arbre recouvrant pour éviter les boucles. 

### Commutation de trames

Les ports sont composés d'un récepteur et d'un émetteur qui sont connecté à une matrice de commutation. Ils sont chacun indépendant. 

### ethernet full  et half duplex 

Effectue une transmissions simultanées dans les deux sens. Il n'y a pas de collisions possibles et CSMA/CD n'est pas nécessaire. 

Duplex veut dire qu'on transmet dans les deux sens. Le mode half duplex définit que soit on transmet ou on émet. Il est utilisé sur un hub connecté à un switch et le Switch utilise CSMA/CD. 

Le switch détecte un hub grâce  à des impulsions électrique qui identifie la vitesse. 

Le switch Ethernet fonctionne sans configuration. Il sait les adresses des machines branchées quand elles envoies des paquets. S'il ne sait pas, il envoie à tout le monde. Dès qu'il sait quelle machine est derrière quel port, il rempli sa table de filtrage. 

# Routage

Chaque paquet dispose de l'adresse de destination, cette dernière est interprétée par le routeur via sa table de routage. si elle n'y est pas, il utilise celle par défaut. si un paquet n'est pas routable, il l'écarte. 

- Acheminement : on a besoin du prochain routeur pour la résolution d'adresse MAC et parce que derrière il y peut-être un sous réseau. 
  - fonctionnalité du protocole IP
  - exécutée pour chaque paquet = rapide
  - Ip utilise la table de routage pour définir le prochain saut
- Routage: 
  - fonctionnalité des protocole de routage 
  - remplir les tables de routage avec les meilleures chemins
  - exécutée périodiquement

Une requête ARP sert à savoir l'adresse MAC. On sait qu'une machine est sur le même sous-réseau grâce à l'IP et au mask. 

## Remise direct

- destinataire sur le même sous réseau
- transmission sans passer par un noeud
- construit une trame Ethernet

## Remise indirect

- le destinataire est dans un autre réseau
- il faut passer par un nœud pour envoyer
- construit une trame Ethernet avec adresse MAC du prochain noeud

## Table de routage

### Statique

configuration manuellement, petit réseaux.

un routeur connaît les réseaux directement connecté, ll faut configurer les routes vers les autres réseaux. 

### Dynamique

protocole de routage pour l'échange d'information entre routeur, il calcul les routes et rempli la table de routage, s'adapte automatiquement aux pannes. 

trouve le meilleur chemin en échangeant les informations avec les autres routeurs

## Algorithme de Dijkstra

1) préparation de la représentation

2) Marquer chaque noeud par un doublet (distance source, noeud précèdent )

3) choisir le noeud avec le coût le plus bas et le marqué comme permanent

4) calculer le chemin de tous les voisins 

5) répéter 2 et 3 jusqu'à que la destination soit marquée permanent

## RIP

- Protocole de routage simple 
- petits réseaux
- calcul en nombre de sauts
- famille vecteur de distance 
- diamètre limité à 15 sauts
- mise à jour lente 

les méthodes pour accélérer les nouvelles routes en cas de pannes sont l'horizon éclaté, et l'horizon éclaté avec retour empoisonné. 

# Niveaux de routage

- routage à l'intérieur d'un AS 
  - calcul des routes optimales 
- routage à l'extérieur d'un AS
  - n'utilise pas de métrique
  - protocole BGP4 



