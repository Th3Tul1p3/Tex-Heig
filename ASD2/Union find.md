# Union find 

## recalcul des composantes connexes

Si on ajoute une arrête à un Graphe, si les deux sommets font partie de la même composantes connexes, rien ne change sinon les CC sont réunies. 

On utilise les API suivantes: 

- find pour savoir la CC d'un sommet
- connected savoir si deux sommets sont de la même CC
- union unir deux CC

Faire pointer chaque sommet sur un autre sommet de la CC et identifier chaque sommet par un sommet représentatif qui pointe sur lui-même. 



a) quick find

b) quick union

c) WQUPC(wighted path compressions)

complexité en log*(n) augmente très lentement 
