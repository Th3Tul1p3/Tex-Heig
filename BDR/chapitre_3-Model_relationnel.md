# définition

c'est un modèle logique de données. Il est élaboré une fois le modèle EA établit. Il est régit par des règles de transformation pour passer de EA à MR. 

# Algèbre relationnel 

On peut représenter un produit cartésien :
- en extension: 
- cartésienne
- arborescente
- sagittale

On appelle une **relation n-aire** entre éléments de ces ensembles. L'arité d'une relation est le nombre d'attribut. 

## propriété 

- il n'y a pas d'ordre dans les tuples, Idem pour l'ordre des attributs. (toujours vraie)
- On ne peut pas avoir deux fois le même tuple. (seulement s'il y a une clé primaire)
- Il n'y a jamais de case vide dans la table. (dépend de la situation)

On utilise la valeure **NULL** pour représenter une valeur inconnue ou manquante. Une clé d'une relation tel qu'il n'existe pas deux tuples ayant la même valeur. 

Une base de données est un ensemble fini de relations 

Un schéma relationnel est l'ensemble des schémas des relations de cette base. 

## SQL

C'est un langage déclaratif et non un langage de programmation. Il se subdivise en 4 sous-langages spécifique regroupant des domaines d'application. 

On crée un schéma avec :

```sql
CREATE SCHEMA NOM; ou CREATE DATABASE NOM;
```

On crée une table avec un nom et l'ensemble de ses attributs.  En spécifiant dans quel schéma on ajoute la table. 

```sql
USE company;
CREATE TABLE department (
Dname VARCHAR(15),
Dnumber INT(11) <--- affichage de 11 chiffre mais pas de limite sur le stockage 
);
```

## Types de données 

### Numériques

INT, TINYINT, SMALLINT, MEDIUMINT, BIGINT

DECIMAL(i, j) : i est le nombre de chiffres décimaux et j est le nombre de chiffres
après la virgule.

### Chaînes de caractères 

CHAR(n) de longueur fixe de n caractères
VARCHAR(n) de longueur variable où n est le nombre maximal de caractères

### Booléens
BOOL ou BOOLEAN
Valeurs : TRUE ou FALSE
### Chaînes de bits 
BIT(n) de longueur fixe
BIT VARYING(n) de longueur variable où n est le nombre maximal de bits
### Temporel 
DATE : sous la forme AAAA-MM-JJ
TIME : sous la forme HH:MM:SS
TIME(n) : sous la forme HH:MM:SS.xxx (xxx sur n positions)
### Estampilles 
TIMESTAMP ou DATETIME : incluent les types DATE et TIME plus un minimum
de 6 positions pour les fractions de secondes
## Contraintes d'intégrité 

Les conditions que doivent vérifier les tuples d'une relation. 

- Domaine --> se vérifie par le type de données spécifié pour l'attribut. On pouvait aussi créer un domaine et l'utilisé pour plusieurs attributs mais ce n'est plus supporté par MySql. On utiliser la clause ChECK pour préciser une contrainte de domaine mais pas non plus accepté. 

- Clé: Une relation peut avoir plusieurs clés (clé candidates) et la clé candidate retenue est appelée clé primaire. Cette dernière est souligné dans un schéma relationnel. 

```sql

```



- intégrité des entités

- valeurs non NULL

- valeurs uniques

- intégrité 

- sémantique 
