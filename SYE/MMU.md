# MMU

Le chargeur d'une image doit trouver un emplacement disponible en mémoire:

- Il détermine l'adresse de base et calcul les adresse relatives en adresse absolues. 

Les adresses relatives le sont par rapport aux sections. 

## First-Fit 

- recherche de la première zone libre satisfaisante avec l'aide d'un pointeur sur la première adresse disponible 
- implémentation simple et performance élevée mais il produit beaucoup de fragmentation. 

## Best-Fit 

implémenté avec des listes chaînées .

- Recherche de la zone la mieux adaptée
- Nécessite de parcourir toute la mémoire donc plus lent 
- mais génère peu de résidu

## Quick-fit

- résidus minimaux, fusion des zones adjacentes et sélection rapides. 
- Une liste chaînée de la taille des trous avec pour chaque trou les adresses de tous les trous de cette taille 
- Il est difficile de maintenir une liste de taille raisonnable. 

## Adressage virtuel 

Réimplantation dynamique d'adresse: traduction d'adresse virtuel en adresse physique. Cela est fait par la MMU(unité matérielle). Avantage:

- Isolation garantie entre processus
- gestion facilitée de l'adressage
- Permet l'utilisation d'une mémoire physique étendue 

La MMU va lire le page table qui est propre à chaque processus. La taille idéale de ce tableau est 16GB. Les opérations de chargement mémoires sont très coûteuses en temps. 

Une page mémoire est un ensemble d'octets contigus de 4Ko. Une page virtuelle est mappé sur une page physique et elles sont numérotées. 

L'allocation d'un octet entraîne automatiquement l'allocation d'une page mémoire. 

Grâce à la TLB de la MMU dans 98% des cas on aura un coût minimum pour un accès mémoire. La mémoire cache la plus proche du CPU à des adresses virtuelles tandis que L2 et L3 ont des adresses physique. 

La pagination multi-niveau consiste à avoir plusieurs sous page pour réduire la taille des 

## Faute de page

Une entrée dans table de page contient :  

- un bit de référence dit si quelqu'un à fait un accès à la page récemment. 
- bit de validité car les données ne sont pas générées à la volée 
- bit de droit d’accès, détermine les opérations qui sont permise 
- bit de modification détermine si on a fait une opération d'écriture sur les données 
- bit de cache pas important 

TLB: translation lookaround buffer, est une anté mémoire qui stocke les pages accédée récemment.  

