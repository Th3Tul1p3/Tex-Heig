# IPC

Étant donné que les processus ne peuvent pas interférer entre eux car ils n'ont pas le même espace mémoire. Pour cela , les inter-process communication sont implémentés au niveau noyau pour leurs permettre de s'échanger des données. Ils sont coûteux en terme de temps CPU de ressource mémoire. 

### descripteurs de fichiers

Lors de l'ouverture d'un fichier, la fonction *open()* retourne un file descriptor. 

- identifiant unique vers une ressource de type fichier 
- un tableau de descripteur de fichier par process
- référence vers une table des fichiers ouverts dans l'espace noyau

Chaque processus dispose d'une table des fichiers ouverts avec leurs référence, elle est stockée dans le PCB. Elle stocke des références vers la table des fichiers ouvert dans l'espace noyau. 

La fonction *dup2(file_descriptor, new_file_descriptor)* permet de manipuler ces références. 

La gestion des files descriptor est pris en charge par la VFS dans linux. 

## Tubes

## Anonymes

Communication entre un processus parent et enfant. Ils sont unidirectionnelle, de taille limitée et de type FIFO. La lecture est destructive. Il est considéré comme un fichier spécial. On les créent à l'aide de la fonction *pipe(tableau de deux file descriptor)*, le premier sera pour la lecture et le deuxième pour l'écriture. Chaque côté du tube est accessible par les deux, de ce fait il faut fermer un des côtés. 

## Nommés 

Ils sont créée avec la fonction *mkfifo()* et doivent être détruit explicitement *unlink()*. Ils existent virtuellement dans le système de fichier et ils sont persistants.  

## Signaux

Ce sont des événements asynchrones qui peuvent être envoyés par le noyau ou un processus. Il provoque l'exécution d'un traitant dans l'espace utilisateur. Le processus traite le signal immédiatement. Un seul exemplaire de signal peut être en attente. On peut masquer ou ignorer le signal. 

Pour associer un signal et un traitant on utilise la fonction *sigaction()*, pour envoyer le signal *kill()*. 

## Fichiers Mappés

Un fichier mappés peut être partagé par plusieurs processus. La fonction *mmap()* charge le fichier dans l'espace d'adressage du processus. 

## Sockets

C'est une extrémité d'une communication. Pour y faire référence on utilisera un descripteur de socket. La connexion entre deux processus sur la même machine utilise la connexion de type loopback.

![](/media/Partage/HEIG/Tex-Heig/SYE/img/Capture d’écran_2019-11-14_15-53-37.png)

L'adresse IP et le port sont définies dans la structure de type sockaddr. La fonction *bind()* permet de se connecter avec ces éléments. Puis le serveur effectue une demande au noyau pour initialiser une file d'attente. La fonction *listen()* sert à remplir cette dernière. la fonction *accept()* traite les requêtes en attentes. La fermeture s'effectue de manière asynchrone , c'est à dire que la fermeture, côté client ou serveur, ne s'effectue pas de manière simultanée. 

### Serveur itératif et concurrent

- plusieurs communications en parallèle 
- pas de délais d'attente de traitement
- implémenté par des threads et des processus

le serveur crée un thread par connexion. 

### serveur TCP 

- communication fiable 
- établissement fiable de connexion
- contrôle de flux
- full-duplex

## Segments de mémoire de partagée

Les processus peuvent se partager des segments de mémoire mais il n'y pas de structure organisationnelle au niveau du contenu. 



