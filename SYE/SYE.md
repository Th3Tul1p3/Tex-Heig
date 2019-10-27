# SYE

# Caractéristique d'un OS

Un OS est une couche entre l'utilisateur et la machine. Il donne une API qui est un environnement de programmation standardisé qui s'adapte à toutes les machines. linux est le noyau. Les OS sont très optimisé. 

- **couche application**
- **couche OS (Noyau)**
- **couche matériel **

- perspective utilisateur: environnement d'exécution et gestion de la protection

- perspective système : gestion de la ressource physique, logique et de la protection

monolithique: qui a tous les sous-système est inclus dans le noyau. 
- performance accrue 
- simplicité d'accès sur le structures du noyau
- Mais probème liés à la sécurité d'exécution

micro-noyau: noyau plus petits qui offre des garantie forte

  - approche client-serveur 
  - Sécurité accrue au niveau des applications 
  - Extensibilité aisée 
  - limiter en performance

- monotâche: Un seul programme utilisateur chargé à **l'adresse fixe**
- multitâche: 
  - plusieurs applications en RAM
  - commutation entre applications
  - nécessite de gérer la mémoire : **sous système de la gestionnaire mémoire **
  - Nécessite **Scheduler / ordonnanceur**
- temps partagé:
- système multiprocesseur 

# SO3

Système d'exploitation développé par le REDS pour les processeur ARM CORTEX-An 32-bits. Il est écrit en C avec gcc Gnu et assembleur ARM. 

- ipc: Inter-Process Communication 
- arch : donne des caratéristiques sur la machine
- kernel: Code noyau principal (process, thread, scheduler)
- mm: gestionnaire mémoire
# Usr
- libc :fonctions de librairie standards C
- src: tous les programmes utilisateur
- deploy.sh:déploiement des exec dans une carte SD virtuelle
- les exec sont au format .elf

L'espace d'adressage est constitué du système d'exploitation et l'application utilisateur. Cet espace est linéaire et il est adressable par octet. 

# Architecture matérielle 

le processeur dispose d'un jeu d'instructions dont certaines sont particulières et des régions mémoire peuvent être également protégées (code de l'OS et accès I/O). Il y a deux modes :

- utilisateur 

- privilégié ou noyau

Le sous système mémoire est le programme le plus compliqué. IRQ controller est un registre qui stocke pour le CPU les demandes d'interruptions. Les interruptions matérielle sont asynchrone et celles logicielle sont synchrone. 

- Matérielle : IRQ 
- logicielle : instruction réservées ou exception

Déroulement d'une interruption:
1. un périphérique envoie une interrruption
2. le contrôleur d'interruptions émet l'interruption pour le CPU
3. Arrêt de la tâche e cours et passage en mode noyau
4. activation de la routine d'interruption par L'ISR
5. à la fin de la routine, restauration de la tâche suspendu et passage en mode utilisateur 
L'accès aux espaces d'adressage est sous contrôle d'une unité matérielle : MMU. Il traduit une adresse virtuelle en adresse physique. 

# Appel système 

syscall est une fonction C permettant l'utilisation des services offerts par l'OS pour l'allocation mémoire, l'accès fichiers...

# modes

- noyau : accès plus étendu à la mémoire et un plus grand set d'instruction. 

Basculement en mode noyau: interruption matériel asynchrone et interruption logiciel. Pour revenir en mode user, on va modifier le registre le registre d'état. 

ABI : application binary interface
POSIX: signatures des différentes fonctions pour utiliser les services noyau.

- le stub est le morceau de code assembleur qu'on écrit pour l'appel système. 

# unité de compilation 
- l'ensemble de tous les fichiers d'entête qui est générer après le passage du pré-processeur. 
- le fichier .o est la partie binaire mais sans les dépendances 
- ensuite on peut faire deux types de linkage, statique où on inclut toutes les librairies dans l'image binaire. linkage dynamique où on admet qu'il n'y a pas toutes les librairies mais qu'elles seront disponible à l'exécution. 
le compilateur traduit le code en lagage machine, et l'optimise. 

bss : block start symbol. section qui dit la taille des variables globales pour que à l'exécution, le runtimeC puisse les initialiser
# adresses
- adresses relatives: adresse dans le .o
- adresses absolues: adresse dans la mémoire 
- addresse symbolique: par exemple l'adresse d'une fonction dans une autre librairie 