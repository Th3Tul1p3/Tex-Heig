# Table de hachage 

## Les base du hachage 

Stockage des éléments dans un tableau linéaire. Une fonction de hachage est une application qui fait correspondre à chaque clé k, un index h(k), appelé **l'adresse de hachage**. Idéalement des clés différentes, qui produisent des  adresses différentes. 

## La fonction de hachage 

- Cas idéal:
  - facile à calculer
  - minimise les collisions
  - distribue les adresses uniformément dans la table de hachage
  - utilise toute l'information fournie par la clé. Un changement produit une autre adresse. 

### Un adressage par extraction 

extrait des bits de la clé pour obtenir la valeur de hachage. **Mais une bonne fonction de hachage doit utiliser tous les bits de la clé.**

### Adressage par division h(k) = k modulo M

- possède une bonne répartition mais multiplie les collisions
- à combine avec d'autre méthode 
- Pour minimiser les collisions, on doit choisir **M premier et éloigner des puissances de 2**

### Adressage par multiplication

h(k) = ⎣m∙(k∙A modulo 1) ⎦avec A étant une constante réelle

Le choix de la constante A dépend du type de la clé.  A = (√5 – 1)/2

### Adressage par Multiplication, Addition et Division

h(k) = (ak + b) modulo M, avec a > 0 et b > 0 

La constante a ne doit pas être un multiple de M. 

### Adressage par compression 

On découpe en morceau de n bits et on réduit les morceaux avec une opération. 

### Adressage par compression polynomiale

■ on calcule le polynôme :
P(z)=a0 +a1 z+a2 z2 + a3 z3+...+an-1zn-1

On calcul sur des longueurs de 8, 16, 32 ou 64 bits. Bonne méthode pour les String. 

## En C++

Pour les entiers on cast en size_t. Pour les réels et les strings on a une mise en œuvre spécifiques. Pour les types utilisateurs, il faut une cohérence pour l'opérateur d'égalité et l'opérateur de différence. 

## Résolution des collisions

N = Nombre de paires clé-valeur
M = Nombre d’éléments dans la table de hachage

### Le chaînage 

utiliser un tableau de M listes chaînes

- Mappe un entier entre i et M - 1 avec la clé
- met l'élément au début de la liste d'index
- on recherche seulement la liste d'index i



### L'adressage ouvert 

On stocke N paires clé-valeur dans une table de taille M > N. On utilise des emplacements vides dans la table pour la résolution de collisions.  Stocker dans le tableau à l’index i si vide; dans le cas contraire essayer i+1, i+2, etc.

- Le sondage linéaire consiste à rechercher à l'index i, et si occupé on essaie i+1, i+2. 

## Mise en œuvre des tables de hachage 

## Les fonctions de hachage cryptographiques

## Conclusion

