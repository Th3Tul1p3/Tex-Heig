# eLes types composés
## Structures: définition et exemples

cUne structure regroupe un ou plusieurs éléments appelés membres ou champs qui peuvent avoir des types différents.

```c
struct [name]{ // name est optionnel mais si utilisé, initialiser avec une majuscule
    // déclarations des membres 
};
struct Personn{ 
    // le mot clé struct est obligatoire
	struct Date [name]; //On peut utiliser une structure dans une structure. 
};

```

Si on veut utiliser une struct dans plusieurs fichiers, il faut l'initialiser dans le fichier header. Il n'est pas possible d'utiliser extern pour une structure. On peut déclarer des variables portant le même nom que des membres d'une structure. 

On peut faire une déclaration anticipée d'une structure.

```c
struct Date; 	// déclaration anticipée 
struct Date {	// définition de 
    
};
```



## Accès aux membres et initialisation

Il y a trois opérateurs pour accéder le (.), L'opérateur égal et le pointeur avec la flèche. Il n'y a pas d'opérateur de comparaison. On peut aussi copier une structure dans une autre structure. 

```c++
struct Date {
	uint8_t day;
	uint8_t month;
	int year;
};
struct Date
myBirthDay = {1,1,1970}, // à initialiser dans l'ordre si des valeurs sont manquantes, elles sont mises à zéro  
yourBirthDay = {.day = 3,.month = 4,.year = 2000}; // pas obliger de se souvenir de l'ordre. on peut aussi initialiser par fonction dans la liste 

```

Un littéral composé permet de créer un objet sans nom, temporaire. 

```c++
struct Date day = (struct Date) {1,1,2019};
```



## Structures, fonctions et pointeurs

On peut passer les struct par pointeur. Dans ce cas Il faut déréférencer et pointer sur le membre à accéder ou utiliser la flèche.  On peut aussi affecter les variables par pointeur  avec & devant l'expression dans le scanf.  

## Les Unions

L'union regroupe plusieurs membres mais un seul est disponible à la fois car ils sont superposés en mémoire. l'initialisation se fait de la même manière qu'une struct. Pour savoir quel champs a été changé en mémoire en dernier, il est bien d'utiliser un flag.  

## Définition de types synonymes: typedef

```c++
typedef existing_type_name new_type_name;
```

en général on utilise une struct anonyme avec le typedef

# Chaîne de caractères

C'est des tableau de caractères se terminant par le caractère de code 0. 

## Littéraux et variables de type chaîne en C

Un littéral de type chaîne est une série de caractère entouré par des guillemets doubles. On peut concaténer à l'affichage en mettant les séries de caractères à la suite. Les littéraux ne sont pas modifiable. On utilise un tableau a une dimension pour stocker la chaîne de caractère. Ne pas oublier l'espace pour le caractère de fin. Les pointeurs de chaîne ne devrait pas être modifié, les tableaux peuvent l'être. 

## Les chaînes en entrée sortie 

Il y a deux possibilités pour l'affichage, puts, qui retourne une valeur si l'opération a réussie ou un code d'erreur. Ou il y a printf. 

Pour lire des caractères, il suffit d'utiliser scanf avec un spécificateur de conversion. Pour créer ce spécificateur il faut utilise sprintf. les premiers espaces dans le buffer sont ignorés par scanf. Pour vider le tampon d'entrée fflush(stdin)

## Les arguments de la ligne de commande 

argc compte le nombre d'argument mis dans argv, y compris le nom du programme. argv est un tableau de pointeurs  vers des chaîne vers les arguments.