# Ordonnancement

Le fait que l'OS gère le temps CPU pour chaque processus. Un système 

## Points de préemption

Via la fonction *schedule()*, Seulement pour les processus en état ready. L'instant qui définit quand on change, est appelé point de préemption. Le quantum temps est le temps alloué au processus actif. Le passage à l'état ready est appelé préemption. 4

## Critères et mesures

**Burst est un processus qui effectue une alternance de cycle CPU** 4

### Taux d'utilisation CPU

Bien mais seulement pour les processus de type batch mais difficile avec beaucoup d'entrée sorties.

### Capacité de traitement 

La mesure est compliquée et dur interpréter du fait que chaque processus ne prends toujours le même temps pour s'exécuter. 

### Délai d'attente

consite à mesurer le temps que passe un processus dans l'état ready. 

## Politique d'ordonnancement

### FCFS

Pas de préemption, premier arrivé, premier servi 

### SJF

### RR

### priorité

