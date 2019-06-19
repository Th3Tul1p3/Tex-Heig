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

 







