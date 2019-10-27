# Minimum spanning Trees MST

Sur un graphe dont les arrêtes ont des poids positifs. Un arbre couvrant est un sous-graphe qui est **Connexe, acyclique et qui inclus tous les sommets**. Trouver un arbre couvrant tous les sommets d'un poids minimum. 

propriétés équivalentes pour Caractérisé un arbre:

- connexe et sans cycle 
- sans cycle et avec n-1 arrêtes
- connexe et admet n-1 arrêtes 
- sans cycle, en ajoutant une arrête on crée un et un seul cycle élémentaire
- connexe, en supprimant une arrête quelconque, il n'est plus connexe. 
- il existe une chaîne et une seule entre 2 sommets. 

## Algorithme glouton

Un algorithme qui suit le principe de faire, étape par étape, un choix optimum local. 

La coupe d'un graphe est une partition en deux sous ensemble disjoints et exhaustifs. C'est aussi un ensemble des arêtes ayant un sommet dans chacune des deux partitions. 

L'arrête de poids minimum fait partie du MST.

pour chaque sommet on "colorie" l'arrête de poids minimum qui n'est pas déjà colorié jusqu'à que V-1 soient rouges. 

## Algorithme de Kruskal

Fait croître jusqu'à couverture totale. On considère les arrêtes par liste de poids croissant. si l'arrête ne fait pas de cycle, on l'ajoute. On teste si l'arrête ajoutée crée un cycle avec des union-find avec une complexité de O(log*V). Le calcul du MST se fait en tamps proportionnel de E * log(E) mais si les arrêtes sont déjà ordonné, cela ne prend que E * log(V) qui est linéaire en E. 

## Algorithme de Prim

### Version paresseuse

### Version stricte

