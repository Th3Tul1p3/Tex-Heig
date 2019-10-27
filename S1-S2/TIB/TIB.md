# Introduction

la téléinformation traite des Services et application, des Protocoles de communication et de l'infrastructure réseau. Des compétences sont transversales comme la sécurité et le développement logicies. Il y a trois principaux réeaux, l'internet qui contient l'internet des objets, les réseaux mobiles avec des réseaux personnels et les réseaux d'entreprises.

- père de la transmission radio longue distance.
- père de la théorie de l'information, base de la cryptographie.
- inventeur de la communication par paquets.
- théorie mathématique des réseaux à paquets, contributeur à l'ARPANET.
- Un des pères d'internet, promotion ipv6.
- inventeur du web, adressage web, HTTP.

# Réseaux

- bluetooth nfc, interconnexion entre périphérique. va de 1 à 10 m.
- réseau d'une entreprise ou d'un campus. ethernet et WIFI
- Réseau d'un opérateur dans une ville. fibres optiques, WiMax et Metro-Ethernet. très grande vitesse.
- Fibres optiques, Faisceaux hertziens et satellites. 10 à 1000km
- interconnexions de tous les réseaux.

Topoligie en Bus, Tous les noeuds sont connectés au même médium. Une seule transmission possible au même moment. distance de communication basse. limité à 1024. Le hub résout le problème, si une machine pose problème sur le bus, elle est éjecter du bus. Topologie en anneau, un segement de câble connecte deux stations. résilience contre les pannes. tokenring utilisait un système de jeton pour savoir qui transmet. Topologie en étoile, chaque station est connecté à un noeud central. Le noeud central transmet à toutes les stations.

Topologie maillée, interconnexion entre tous les noeuds. Bonne résilience utilisation

# Commutation

La commutation est le processus d'acheminement de données à travers un réseau. Il y a deux types de commutation: par circuit et par paquets.

## Commutation par circuit

Utilisés dans les réseaux téléphoniques. Mais cela n'est pas adapté aux réseaux informatiques. Car cela n'est pas assez rapide.

## Commutation par paquets

La source segmente le message à transmettre en paquets. Ensuite les paquets sont transmis de manières indépendante. Le destinataire trcombine les paquets reçus pour obtenir le message. Il y a plusieurs chemins. Si un paquet est perdu, on retransmet que le paquet. Conversion des formats possible et reroutage facile en cas de panne d'un lien. Mais le délai de transfert est variable et plus long. Pertes de paquets possibles. Noeuds intermédiaires doivent recevoir l'ensemble du paquet pour commencer à le transmettre. Si la file d'attente est trop longue, il se peut qu'on doive recommencer la transmission.

## Paramètres de performance

Délai, Vitesse, Longueur deonnées, Débit binaire et taux de perte.
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
# DNS
# Réseau IP + NAT
Les utilisateurs sont connectés via un ISP à internet. Les ISP tiers fournissent au niveau internationales et ils forment la Backbone. Ils sont interconnectés à des Internet eXange Point et elle s'appelle Peering qui est effectué par une LAN haute vitesse.
Ils utilisent tous le protocole IP pour la couche 3. 

- transmission sans connexion: aucun établissement de connexion avant l'envoi de donnée. Un paquet contient toutes les informations à son traitement. 
- Service non fiable: aucune garantie de transmission, les paquets peuvent être perdu ou arrivée en désordre. les paquets sont dans une file d'attente, si elle déborde le paquet est perdu. 
- Fragmentation et réassemblage : Il est possible que le paquet soit fragmenté par un routeur intermédiaires. Le destinataire réassemble le datagramme. 

- xDSL 1- 20 Mb/s

- Modem câble 1 - 100 Mb/s 

- Accès mobile  1 - 100 Mb/s 

- Fibre optique 100 Mb/s - 1 Gb/s 

  la taille de l'entête IPv4 est de 20 octets + 0 - 40 octets optionnels * 20 - 65535 octets de données. 

  | Nom                           | taille  | détail                                                  |
  | ----------------------------- | ------- | ------------------------------------------------------- |
  | Version                       | 4 bits  | v4 ou v6                                                |
  | IHL                           | 4 bits  | longueur d'entête pour les options                      |
  | DSCP                          | 6 bits  | qualité de services                                     |
  | ECN                           | 2 btis  | permet de signaler de congestion à une source           |
  | Longueur totale               | 16 bits | longueur des données                                    |
  | identification                | 16 bits | identificateur unique datagramme                        |
  | flags                         | 3 bits  | don't fragment et more fragment                         |
  | offset de fragmentation       | 13 bits | position du fragment dans le datagramme                 |
  | TTL                           | 8 bits  | permet d'éliminer les paquets dans une boucle de routag |
  | Protocole                     | 8 bits  | protocole de la couche supérieur                        |
  | checksum entête               | 16 bits | somme de contrôle                                       |
  | adresse source et destination | 64 bits |                                                         |
  | options                       |         | diverses options                                        |
  | bourrage                      |         | pour que la longueur de l'entête soit un multiple de 4  |

  fragmentation à partir de 1500 pour Ethernet et 7982 pour le wifi. chaque fragment est indépendant et peut être encore fragmenté. si un fragment est perdu on supprime le datagramme. 

  ## structure des adresses 

  sur 4 octets, Une partie identificateur réseau et une partie identificateur de machine. 

  - Classe A 255.0.0.0 126 réseaux 16 mio hôtes 1.0.0.0 - 127.255.255.255
  - Classe B 255.255.0.0 16k réseaux 64k hôtes 128.0.0.0 191.255.255.255
  - Classe C 255.255.255.0 2 mio réseaux 254 hôtes 192.0.0.0 -223.255.255.255
  - 224.0.0.0 - 239.255.255.255 multicast 
  - loopback 127.x.x.x
  - broadcast local 255.255.255.255
  - adresse réseau préfixe + des 0 
  - adresse broadcast réseau préfixe réseau + que des 255
Les sous réseaux permettent de subdiviser des plages d'adresse en plus petite. 
mettre exemple slide 32
CIDR permet de réduire les tables de routage en fusionnant desréseaux pour créer des super sous-réseaux. 
Pour palier au manque d'adresse, on utilise des adresses privées dans les sous réseaux. L'outil NAT permet de les traduire en adresse publique. NAT simple pool de plusieurs adresses. NATP utilise une adresse publique et le port TCP/UDP source 
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

## Niveaux de routage

- routage à l'intérieur d'un AS 
  - calcul des routes optimales 
- routage à l'extérieur d'un AS
  - n'utilise pas de métrique
  - protocole BGP4 
# IPV6
Les adresses IPv6 ont été crée pour faire face à la pénurie d'adresse IPv4. De plus, elles ont pour objectifs de rendre plus efficace le traitement des paquets par les routeurs. Mieux structurer les protocoles annexes. 
- Adresses sur 128 bits
- entête simplifié et extensibilité si besoin
- plus de fragmentation sur les routeurs
- Autoconfiguration d'adresses des machines sans DHCP
- ARP, ICMP, IGMP remplacés par ICMPv6
## Notation 
Par groupe de 4 chiffres héxa séparé par ':' . on peut simplifier s'il n'y a que des 0. 
## Adresses globales
l'adresse IPv6 est divisée en 3 parties:
- le préfixe de routage
- l'identificateur de sous-réseau
- l'identificateur de l'inferface sur 64 bits
l'utilisateur dispose de 8 - 16 bits pour créer des sous réseaux
l'adresse locale sert à communiquer sur le LAN et elle est obligatoire. l'adresse unicast globales sert pour la communication sur internet et elle est optionnelle. 
## Auto-configuration
L'ID est construit sur la base de l'adresse MAC. Avec la méthode EUI-64, on ajoute FFFE au milieu de l'adresse et on inverse le deuxième bit de boit faible du premier octet. 
- ::1 --> 127.0.0.1
- :: --> 0.0.0.0
## Remplacement du protocole ARP 
les messages ICMPv6 de sollicitations de voisins et d'annonce de voisin servent à remplacer ARP.
Lors de l'autoconfiguration, la machine constuit une adresse locale de lien avec le préfixe et l'ID. La machine fait ensuite un message Duplicate address detection pour savoir si la même machine à la même adresse. 
Même chose pour l'adresse globale mais la demande de préfixe se fait via le routeur. 
## En-tête IPv6 
La taille est désormais fixe, on peut rajouter des en-têtes à l'aide d'extensions. il n'y a plus de somme de contrôle. 
- la classe de traffic 8 bits : sert à effectuer des services différencier 
- identificateur de flux 20 bits: meilleur traitement des flux de paquets
- longueur de donnée 16 bits : avec une option pour plus de donnée
- en-tête suivant 8 bits : indique le type de l'en-tête suivante. 
- nombre de saut 8 bits : 
Les en-têtes d'extension sont examinés seulement par le destinataire final. 
La fragmentation se fait uniquement par la source. si trop grand le paquet est retourné à la source
S'il est fragmenté, le paquet contient une en-tête de fragmentation. 
## Méthode de transition
- Double-pile IPv4 et IPv6 
- Tunneling 
- proxy de traducation pour les machines sans IPv4 

# TCP et UDP

## UDP

Ses fonctionnalités:

- Adressage d'applications via le numéro de port
- Contrôle d'erreur optionnel
- Transmission non fiable
  - Sans connexion, acquittement et contrôle du débit 

Utilisé pour la transmission multimédia,  multicast et les échanges courts comme DNS. 

l'entête UDP contient 

- le port source
- le port destination
- la longueur du segment 
- la somme de contrôle: calculée sur le pseudo header, l'entête UDP et les données encapsulée. Cela protège contre des bits erronés et des ports erronés. 

la longueur max d'un datagramme est de 65535.

Les numéros de ports sont les adresses de la couche transport et sont sur 16 bits. TCP et UDP peuvent utiliser les mêmes ports. les ports éphémères sont à partir de 1024. 

## TCP

Ses fonctionnalités:

- transmission fiable de bout en bout.
  - numéro de séquence, avec acquittement et retransmission
- Établissement et terminaison de connexions 
- régulation du débit
  - contrôle de flux principe de la fenêtre à taille variable, la taille de la fenêtre correspond à l'espace libre dans le tampon
  - Contrôle de congestion le protocole de la fenêtre glissante permet d'envoyer plusieurs paquets sans attendre un ACK.  

Les octets sont numérotés mais pas les segments. l'émetteur indique le numéro sur le premier octet du segment. le numéro d'acquittement indique le prochain octet attendu. les acquittements sont cumulatifs, c'est dire qu'il confirme tous les données jusqu'à ce point. sans acquittement le segment est retransmis à la fin du temporisateur.   Pour le récepteur, si un segment manque, il envoie trois fois l'acquittement pour segment pour activé une retransmission rapide. 

L'établissement de la connexion en trois temps, si cela ne réussit pas, un signal de reset est envoyé. La libération d'une connexion se fait en 4 temps. 

Le contrôle du flux se fait à l'aide des annonces de fenêtres du récepteur et de la fenêtre de congestion. 

Le démarrage lent permet d'adapter la vitesse pour éviter la congestion. tant qu'il reçoit des ACK il double le nombre de paquet reçu et incrémente MSS (taille minimum d'un paquet). Ensuite quand le débit optimal est approché, il ralentit l'augmentation de paquet envoyé. Le seuil est appelé ssthresh, en dessus on passe en mode évitement de congestion. 

Au début ssthresh croît linéairement et cwnd (fenêtre de congestion) a un accroissement additif. Si une perte est détectée on divise ssthresh par deux et recommence avec un slow start. 

 







