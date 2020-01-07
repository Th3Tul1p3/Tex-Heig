# BDR

Le but est de concevoir et modéliser correctement une base de données relationnelle et d'exploiter/gérer les données d'une base de données relationnelle. Puis d'interfacer avec le JAVA

Pour concevoir, on commence par un modèle entités-associations puis avec un modèle relationnel. Pour finir on fait un fichier SQL. 

# Concept de base 

On utilise les bases de données pour la recherche sur le web, data mining et pour des recherches sur google, amazon. La base de données (**BD**) est un ensemble structuré et organisé de données. Un système de gestion de bases de données (**SGBD**) est un ensemble de logiciels qui permet le stockage de grande quantités de données persistantes et qui facilite l'accès multi-utilisateurs. 

## Pourquoi utiliser un SGBD 

1. Gérer et manipuler de grandes quantités de données
2. Pour garantir la persistance des données de manière sûr et efficace
3. Accès multi-utilisateurs. état fiable à tout moment. 
4. Pour sa sécurité même en cas de panne
5. facilite l'accès à l'information grâce au langage de haut niveau
6. Pour sa performance 
7. pour sa fiabilité (accès en tout temps)

Les middleware est un logiciel qui rajoute un niveau d'abstraction supplémentaire. Ils se trouvent entre la couche logicielle et les programmes d'application et le SGBD. Les requêtes interactives permettent de créer/supprimer/modifier des données et envoie directement la requête au SGBD. Le programme d'application accèdent à la BD en envoyant des requêtes au SGBD. 

## Indépendance données-programmes 

le catalogue stocke la structure des données et la description de chaque base de données (structure, les types et les contraintes). ces dernières sont des métadonnées. Le but est que si on ajoute ou supprime un champ à une données, les programmes d'accès à la base de données ne sera pas influencés. Grâce à l'abstraction des données, les SGBD offrent à l'utilisateur une représentation des données sans les détails relatifs au mode de stockage ou à leurs implémentation. Cette représentation est fournie sous forme de modèle de données. 

Un modèle de données décrit la structure, les opérations et les contraintes sur les données. 

un enregistrement dans la table est appelé un tuple. 

## Différentes catégories de modèles de données 

- conceptuels (haut niveau) : concepts proches de la façon dont la plupart des utilisateur perçoivent les données. 

- physique (bas niveau): détail le stockage informatique des données. 

- logiques(moyen niveau): entre deux. 

- relationnel: exemple SGBDR

La description de BD pour sa conception est appelé un schéma de base de données. Il contient sa structure, le type et les contraintes. 

Un diagramme schématique est une illustration du schéma de BD qui affiche plusieurs aspects du schéma. Les données  stockées à un instant *t* sont appelées instance ou état de la base de données. 

l'état courant est sont état actuel. Le SGBD s'assure que l'état soit valide à tout moment. Le schéma peut être appelé intention et l'état peut être appelé extension. 

- Architecture trischématique est constitué de trois niveaux:
  - le schéma interne structure de stockage physique
  - le schéma logique définit la structure et les contraintes
  - le schéma externe définit les vues utilisateur

Le SGBD doit transformer toutes les requêtes de schéma externe en requête schéma logique puis en requête de schéma interne. ce processus est appelé correspondance. 

# Indépendance des données 

- indépendance physique des données la capacité à modifier le schéma interne sans modifier le schéma logique.

- indépendance logique des données la capacité à modifier le schéma logique sans que cela affecte le transformer schéma externe

les schémas supérieurs ne doivent pas être impactées par des changement à la couche inférieur. 
Les vues permettent de voir différemment l'information sans taper une requête très longue. Elles donnes un nom à la requête. 

# Transaction

C'est un processus en cours d'exécution qui implique un ou plusieurs accès à la BD. Si e.o. COMMIT sinon ROLLBACK et ça garde l'état d'avant la transaction. 

Propriété ACID:

- Atomicité: Soit toutes les opérations sont effectuées soit aucune. 
- Cohérence: le contenu à la fin de la transaction est cohérente. si incohérent -> annulation des modifications et échec de transaction
- Isolation: si deux transactions sont effectuées en même temps, les modifications ne sont par d'autre transaction. 
- Durabilité: Une fois validé, l'état de la BD est permanent. 

# langage SQL

Le langage est découpé en 4 sous langage. 

- DDL comprend les instruction de manipulation des métadonnées. (entête de table et les contraintes)
- DML sert à manipuler des données dans les tables. 
- DCL sert à attribuer ou à révoquer des droits sur certaines opérations 
- TCL sert à comfirmer ou d'annuler des transactions.

# chapitre 2

## Modèle Entité-Association
- se compose de la conception d'application -> programme et interface qui accèdent à la BD
- et de la conception de la base de donnée 
  - modélisation conceptuelle
  - modèle logique
  - modélisation physique 
l'objectif du modèle EA permet la formalisation d'un problème indépendant de l'implémentation. C'est donc un modèle conceptuel de données. Cela permet aussi de structurer les données. Il faut éviter la redondance. 

Avantages :
- très peu de concept 
- convention graphique simple
- modélisation graphique et efficace
- supporter par diver outils logiciels

# Entité et type d'entité

Le modèle se base sur les principes suivant:

- entité, attribut clé, association, cardinalité, rôle.

Un attribut peut être :

- monovalué: il ne peut prendre qu'une seule valeur
- multivalué:peut prendre plus d'une valeur
- composite  qui peut être décomposé en plusieurs type simple
- obligatoire ou non
- dérivé: calculé à la volée 
- Si on ne connaît pas sa valeur, elle est renseignée à NULL



- EntitéTout objet identifiable et pertinent pour l'application
- Type d'entité
    - identificateur 
    - une liste de ses attributs
    - indication des attributs 
- Instance: instance de son type d'entité
- Extension 
- attribut caractéristique d'un type d'entité Il est désigné par un identificateur et prend ses valeurs dans un domaine énumérable
    - un attribut monovalué veut dire qu'il ne peut prendre qu'une seule valeur 
    - un attribut multivalué veut dire qu'il peut prendre plusieurs valeurs
    - obligatoire doit renseigné pour chaque occurence sinon facultatif
    - si non décomposable = simple 
    - si décomposable = composite
    - stocké dans la base de donnée
    - dérivé : calculé soit à partir d'autre attributs ou attributs d'entité associations
    - l'identifiant ou clé doit être unique, ne doit pas pouvoir être modifié, doit avoir une taille de stockage minime 
- clé naturelle : appartient naturellement à l'entité comme l'année de naissancei ou le numéro AVS
    - avantage : existe déjà dans l'entité
    - désavantage : liée à la logique métier. si elle change tout change. par exemple N°AVS qui pourrait changer 
- clé artificielle : attribut non lié à l'individu naturellement comme un numéro d
    - avantage : pas lié à la logique métier 
    - désavantage : ne véhicule pas d'information. 
- Association : relation entre ensemble 
    - degré d'une association nombre de TE impliqué dans une association 
        - binaire 2 TE
        - ternaire 3 TE
        - n-aire n TE
    - Cardinalité est une paire (cardinalité minimale, cardinalité maximale) pour dire le nombre de fois que l'entité peut intervenir dans l'association.
    - notation MERISE les cardinalités sont INVERVé
    - association un-un
    - association un à plusieurs 
    - association plusieurs à plusieurs
- Dans le cas d'une association n:m certains attributs ne peuvent pas être affectés qu'à l'association elle-même. 
- type d'entité faible : ne peut exister qu'en étroite association avec des types d'entités forts (composition en UML)
- Une association réflexive est une associtation entre un type d'identité et elle-même. 
Les contraintes d'intégrité qui ne peuvent pas être exprimée à l'aide de concepts de base du modèle EA sont à mettre en commentaires.
- Les cardinalités minimales sont aussi appelées contraintes de participation

Le problème des associations n-aires, et que dans une clé composé de plusieurs éléments, si un seul élément change, on peut faire rentrer des tuples que l'on ne voudrait pas. On résoudre ce problème en introduisant une clé artificielle composé d'un seul attributs. 

- Le modèle entité association est non déterministe dans le sens où il n'y a pas de règle absolue pour déterminer ce qui est un type d'entité, un attribut ou une association. Dans le cas d'une séance de cinéma avec une plage horaire, il est bien d'avoir un type d'entité horaire mais cela alourdit le schéma et cela n'est pas rattaché à une séance.  
# Héritage 

Une association de type "est un(e)" est une association de type 1:1. On peut dire que c'est un lien d'héritage. Un lien d'héritage est appelé jointure. 
- un héritage est dit total si toute instance de la super classe est une instance de l'une des sous-classes. 
- Un héritage est dit disjoint si toute instance de la super-classe ne peut appartenir simultanément qu'au maximum à une seule sous-classe. 

- dans sa forme simple, **INSERT** permet d'ajouter un seul tuple. Il faut ajouter un nom de relation ainsi que les valeurs du tuple. Et ces dernières doivent respecter un ordre précis.
  - Mais une autre forme permet d'omettre les champs marqué comme **NOT NULL** 
- **DELETE** supprime un tuple. 
- **WHERE** sertà selectionner les tuples à supprimer. sans cette clause tous les tuples de la relation sont supprimés. mais cela laisse la relation. 
- **DROP** supprime la relation 

```sql
DELETE FROM table
WHERE champs = valeurs;

DELETE FROM table
WHERE Dno IN 
(SELECT Dnumber
FROM department 
WHERE champs = valeurs);
```

- **UPDATE** sert à modifier la valeur d'un ou plusieurs attributs de un ou plusieurs tuples 
- **WHERE** sert à sélectionner les tuples à modifier. sans cette clause tous les tuples de la relation sont modifiés. 
- **SET** spécifie les attributs à modifier ainsi que leurs nouvelles valeurs

l'intégrité révérencielle est le fait d'empêcher l'insertion d'une clé primaire qui n'existe pas. 

# Chapitre 3 : modèle relationnel

Se base sur une notion mathématique de relation. Et se fait uniquement à partir du modèle EA. 

## Le produit cartésien 

Peut être représenté :

- en extension
- tabulaire
- cartésien
- arborescent
- sagittale

## Relation 

Une relation est l'ensemble des attributs. Une arité de relation est le nombre d'attributs. La valeur NULL est utilisée pour représenté les valeurs inconnues ou manquantes. 

## SQL

Il est utilisé par tous les SGBDR. 

```sql
// création de schéma 
CREATE SCHEMA compagny;
CREATE DATABASE compagny;

// spécifie le schéma à utiliser
USE compagny;

CREATE TABLE department(
	// attribut
	DATE INT VARCHAR TIME DECIMAL BOOLEAN // sont des types de données
);

```

### Contraintes 

on peut faire des contraintes de plusieurs manières:

- de domaine: s'exprime au travers tu type de donnée de l'attribut
- de clé : désigné par **PRIMARY KEY** 

```sql
CREATE TABLE department(
	Ssn char(9),
	PRIMARY KEY (Ssn)
	CONSTRAINT PK_employee PRIMARY KEY (Ssn) // pour une contrainte de clé
);
```



- d'intégrité des entités : aucune  valeur de clé primaire ne peut être NULL
- des valeurs non NULL:  En spécifiant NOT NULL
- valeurs uniques : en spécifiant UNIQUE
- intégrité révérencielle

```sql
CREATE TABLE department(
	Dno INT(11) NOT NULL DEFAULT1,
	FOREIGN KEY (Dno) REFERENCES Department(Dnumber)
);
```

- d'intégrité sémantique: ne peuvent être exprimées via le modèle relationnelle

### changement d'état de base 

- insertion : INSERT permet d'ajouter un seul tuple à la relation et être écrites dans l'ordre spécifiés dans la table. Ou de spécifier l'ordre de ceux-ci. 
- suppression : DELETE where sert à sélectionner un tuple à supprimer sinon tous les tuples sont supprimés.
- modification : UPDATE 
  - WHERE sert à sélectionner un tuple à modifier sinon tous les tuples sont modifiés.
  - SET permet de changer un attributs et de lui attribuer une nouvelle valeur.

Modifications automatique sur des clés étrangères ON DELETE/UPDATE CASCADE

# Chapitre 4: Règle de transformation

## types entités normaux

On fait simplement une relation avec la clé primaire et les attributs. 

## types entités faibles

On fait d'abord une relation de l'entité forte avec ses différents attributs. Puis ensuite une deuxième relation avec une  avec la clé de l'entité forte, la clé de l'entité faible ainsi que les attributs de l'entité faible. Finalement on fait une référence de contrainte sur la clé étrangère. 

## binaire 1:1

Trois différents cas :

- obligatoire de chaque côté, donc cardinalité de 1 

  Faire une relation avec une des entité en incluant la clé primaire de l'autre. Puis faire une relation de cette dernière. Faire une référence sur la clé étrangère en la spécifiant NOT NULL et UNIQUE

- mixte avec une cardinalité 0..1 et 1

  Faire une relation avec l'entité ayant une cardinalité de 1 en incluant la clé primaire de l'autre. Puis faire une relation de cette dernière. Faire une référence sur la clé étrangère en la spécifiant NOT NULL et UNIQUE

- complètement facultatif avec 0..1 pour tous

  Faire une relation avec une des entité en incluant la clé primaire de l'autre. Puis faire une relation cette dernière. Faire une référence sur la clé étrangère en la spécifiant  NULLABLE et UNIQUE

Faire attention aux types d'entités spéciaux sans identifiant explicite. 

## binaire 1:N

- association sans attribut avec cardinalité de 1 ou 0..1

Une référence de l'entité avec cardinalité de 1 et la clé primaire de l'autre. Une référence sur l'autre entité. Une référence sur la clé étrangère avec NOT NULL si cardinalité de 1 ou NULLABLE si cardinalité de 0..1.

- association avec attribut et cardinalité de 1

Une référence de l'entité avec cardinalité de 1 et la clé primaire de l'autre et les arguments de l'association. Une référence sur l'autre entité. Une référence sur la clé étrangère avec NOT NULL.

- association avec attribut et cardinalité de 0..1

Une référence pour chaque entité. Une référence avec la clé primaire de chaque entité ainsi que les attributs de l'association. les références des clés étrangères **en Spécifiant la clé de l'entité de cardinalité de 1 comme NOT NULL**

## binaire M:N avec attributs d'association

Chaque entité devient une relation,  ainsi qu'une relation contenant les deux clés primaires des entités et des attributs de l'association. Ne pas oublier les références sur les clés étrangères. 

## attributs multivalués

Faire une relation avec les attributs simples. Puis une autre avec la clé et l’attribut multivalué en référençant la clé primaire  avec la relation précédente. 

## associations n-aires

Transformer les associations n-aires en binaires. Puis faire une relation pour chaque entité avec "l'entité noeu" .  Puis faire une relation avec les clés primaires de toutes les entités ainsi que des attributs de l'association. en faisant référence aux clés étrangères. 

## type héritage

Il existe plusieurs types d'héritage:

- complet, disjoint

- complet overlapping

- incomplet disjoint

- incomplet overlapping

  Faire une relation pour l'entité parent. Puis faire une relation pour chaque entité héritant en incluant la clé primaire du parent avec une référence. 

Pour les autres types c'est plus complexe. 

## associations réflexives 

- Type N:M

  Faire une relation de l'entité elle-même Puis du lien qui l'uni à elle-même avec les références. 

# Opérateur 

chaque opérateur algébrique ressort une nouvelle relation. 

## Selection

équivalent SQL WHERE. selectionne par lignes 

## Projection 

selection par colonne. en supprimant les doublons de cette dernière. équivalent SQL SELECT DISTINCT ( pour avoir un équivalent ensembliste)

## Produit Cartésien

Associe toutes les lignes d'une table à toutes celles d'une autre table. Mais multiplie aveuglement sans regarder la pertinence. 

## Union

l'équivalent SQL UNION est déjà ensembliste.

## La différence 



## La jointure 

