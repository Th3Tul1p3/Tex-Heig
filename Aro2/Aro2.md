# Pipeline 
Decode

- Execute

- Memory Access

- Write back
  Pour que cela soit possible il faut égaliser la longueur de chaque étape du pipeline pour éviter que certain étage attende sur d'autre. 
  
- temps de cycle : temps de traitement de chaque étage 

- latence : temps d'attente du premier résultat

  ![aro](D:\HEIG\Tex-Heig\Aro2\aro.png)

  ![calcul_perf](D:\HEIG\Tex-Heig\Aro2\calcul_perf.png)

- débit : nombre d'instruction par seconde traité par le pipeline

- Les deux derniers éléments sont généralement utilisé pour mesurer la performance d'un processeur. 
  

Chaque registre est généralement isolé par un registre. 

## Aléa 
- Aléa structurel :conflits d'accès aux ressources
- Aléa de donnée: modifications de l'ordre d'accès aux ressources
  - RAW : lecture d'un registre où on récemment écrit
  - WAR : écriture d'un registre qu'une autre instruction utilise comme source
  - WAW : écriture dans un registre où on a récemment écrit 
- Aléa de contrôle :décision de branchement 
## Résolution des aléas
### Données
- Méthode simple : hardware: arrêter le pipeline, insérer des nops
- Forwardinf ou bypassing. : Utiliser les résultat de l'alu sans attendre l'étape write back
  - les opérandes sont stockés dans des registres
    Ces méthodes ne fonctionnent pas pour des pipelines à plus de 5 étages ou quand le temps de traitement varie selon l'instruction. Dès lors, on résout les aléas avec :
- Un ordonancement dynamique : On modifie l'ordre d'exécution pour éviter les aléas. 
- Scoreboarding :Les instruction sont lues dans l'ordre du programme mais exécutées selon une liste d'attente pour la disponibilité des opérandes. Bonne technique pour les RAW.
- Méthode Tomasulo : Utilisation de registres temporaires, particuliérement bonne pour la résolution WAR et WAW
### Contrôle 
- Arrêt de N instructions jusqu'à qu'on connaisse l'adresse de saut , changement de l'ordre des d'exécution des instructions , exécution des tests de branchement dans le decode 
- Une prédiction dynamique : Permet d'anticiper les branchements en utilisant les probabilités. L'adresse la plus probable est stockée dans la table. En cas de saut c'est cette adresse qui est chargée. La prédiction peut se faire sur un bit ou deux bits. 

# Hiérarchie des mémoires 

Dans l'ordre de grandeur et de temps d'accès: registres -> Cache ->mémoire principale -> disque 

## DMA 

Procéder permettant de transférer des données directement depuis un périphérique sans passer par le processeur. Pendant le transfert, le processeur exécute des instructions de la mémoire cache. 

## Mémoire cache 

antémémoire très rapide permet d'accélérer le temps d'accès à l'information pour le processeur. Elle a la même fréquence que le CPU jusqu'à 128Ko. il n'y a pas de contrôle sur son contenu. 