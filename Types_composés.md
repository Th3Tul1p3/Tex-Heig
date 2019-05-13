# Les types composés
## Structures: définition et exemples

Une structure regroupe un ou plusieurs éléments appelés membres ou champs qui peuvent avoir des types différents.

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

## Structures, fonctions et pointeurs
## Les Unions
## Le type énumération
## Définition de types synonymes: typedef

