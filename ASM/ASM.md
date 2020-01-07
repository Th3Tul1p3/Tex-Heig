# ASM 

## Architecture hôte/cible

Cross-development est le fait de développer des applications pour une autre plateforme sur un ordinateur. 

## Toolchain

- compilateur : compile un code vers un fichier objet. 
- éditeur de liens : lie tous les codes objets 
- assembleur : compile un programme écrit en assembleur
- debugger
- librairies 

## Makefile 

- $@ fait référence à la cible 
- $^ fait référence à la liste des dépendances
- $< fait la première dépendance 

Descente récursive, exécution récursive et sélection opportuniste d'une règle.  

## Cisc

- instructions de taille variable entre 1 et 17 
- 

## Risc

- instruction de taille fixe 
- possède plusieurs contrôleur 
- pas de segmentation mémoire 
- r10 à r15 pris par d'autre tâches 

## Langage d'assemblage 

### macro instruction

permet de définir de nouvelles instructions basées sur des instructions de base. Elles sont sensible à la case.

### pseudo instruction

sont liés au type d'assembleur et elles sont traduites par le compilateur en instructions de base

### directives 

Sont liés au type de compilateur. Elle commence par un ".". 

- .include pour inclure un fichier 
- .equiv <constante>, <expression> pour définir des constantes. 
- .space pour réserver de la mémoire de N octets
- déclaration de sections
- .global et .extern signal qu'on exporte ou importe le label au delà du fichier **elles sont résolues par le fichier**
- .align <val> permet d'aligner les valeurs de multiple val octets

### Label 

Étiquette spécifiant un emplacement dans le code. Il doit commencer par une lettre. Si dans une macro, le label est numérique et on doit spécifier avec le suffixe b et ou f lequel est appelé. 





