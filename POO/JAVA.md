# JAVA

- Fiabilité, sécurité
- indépendant vis à vis du processeur
- interaction avec l'extérieur
- récupération d'erreurs
- multi-plateforme: compiler en java byte code exécuter dans une machine virtuel.
Les types primitifs ne sont pas des objets. 
- Robuste, et presque tout objet
## compilation et exécution
On part d'un \*.java, on effectue la commande javac pour compiler. On obtient un fichier .class. on exécute le .class avec la commande java. 
## Types primitifs
- Entiers signés : byte(8 bits), short(16 bits), int(32 bits), long(64 bits)
- Réels float (32 bits), double(64 bits)
- Booléen: boolean 
- Caractère char (16 bits)
**Par défaut un nombre est un int.** **Par défaut un littéral flottant est un double** 
## Classes enveloppes primitif
- Chaque type à son équivalent en classe en ajoutant une majuscule. (sauf Integer, Character). Une fois créer la classe ne peut plus être modifié. On peut convertir un type primitif en sa contrepartie objet (autoboxing/unboxing). Déclaration comme en C. 
**l'opérateur == compare l'identité des objets et non leurs valeurs**
## Références
La création d'un nouvel objet est stocké sous forme de référence typées444
## Chaînes de caractères
il suffit de faire string s = "salut";
- **s += "!";// retourne une nouvelle chaîne de caractère car on ne peut pas la modifier**
- **La surcharge utilisateur d'opérateur n'est pas possible**

# Classes
Toutes les classes héritent implicitement de la classe object. Toutes les classes commencent par une majuscule. Une seule classe par fichier. 
## Attributs
C'est des variables membres. Ils commencent toujours par des minuscules
## Méthodes 
C'est une fonction membre de la classe. 
```java
NomDeClasse{
    int age; // attribut
    valeurDeRetour nomDeLaMéthode(){
    }
}
```

## Mode de transmission des paramètres 

Les paramètres peuvent être transmis par valeur ou par référence. 

- Pour les types primitifs et les String c'est par valeur 
- pour les autres objets, par référence

## Héritage 

On spécifie une sous classe avec **extends**. Et les classes héritent d'une seul et unique classe. 

On peut redéfinir une méthode d'une classe parent en redéfinissant la méthode. **même nom, nombre et types de paramètres, même type de résultat**. Mais on peut aussi appeler la méthode de la classe parent avec **super.methode()** 

La liaison dynamique est le fait que la décision de quelle méthode sera exécutée, se fait à l'exécution du programme.  

## Tableaux

Un tableau est un objet de taille fixe avec des éléments de taille fixe avec des éléments du même type, objet ou primitif. Pour des objets, la création d'un tableau ne crée pas ses éléments, il faut donc les créent. On peut définir un tableau à la volée.  

## Ellipse

Cela permet d'accepter un nombre variable de paramètres. (Type ... args) et doit être la dernière de la liste de paramètre. aussi valable pour le main. 

## Exceptions

Ce sont des objets. traité comme en C. 

# Paquetages

est une bibliothèque de classes :

se déclare **package nomPackage;**  Si aucun package n'est déclaré dans un fichier, les classes correspondantes appartiennent au package par défaut. Les fichiers .class doivent être placés dans le même répertoire. 

Pour utiliser une classe d'un paquetage, on peut utiliser la notation **import nomPackage.nomClasse;**   ou  **import nomPackage.*;** pour importer toutes les classes du package. 

# Visibilité

### attributs

- private visible dans la classe uniquement (à utiliser)
- (aucun) visibilité niveau package 
- protected visibilité package et pour les sous-classes 
- public visible partout 

Un constructeur peut être déclarer private:

- si un autre constructeur l'appel
- s'il faut interdire la création d'instance

### Classes

- (aucun) visibilité niveau package, classe non exposée
- public visible partout
- private/ protected classe interne
  - private seulement pour la classe et la classe englobant
  - protected: package et sous-classes

Dans une sous classe on peut augmenter la visibilité mais pas la restreindre.

# polymorphisme

Une classe parent peut être instanciée comme une classe enfant mais pas l'inverse. Mais on ne peut pas utiliser les méthodes de la sous classe dans ce cas. tout comme deux sous classes ayant la même classe parent ne peuvent pas être instanciée l'une dans l'autre. 

- Universel 
  - paramétrique généricité 
  - inclusion Opération applicable sur des types liés par une relation d'héritage
- Ad hoc 
  - surcharge même identificateur pour des opérations différentes
  - conversion automatique de type

![Capture d’écran_2019-10-14_09-53-27](/media/Partage/HEIG/Tex-Heig/POO/img/Capture d’écran_2019-10-14_09-53-27.png)

```java	
personn p = new sportman();
p.getclass() // retourne sportman
p.class		// retourne person
p.getclass().getclass() // retourne class
```

La différence entre isinstance et instanceof est que le premier compile de toute façon. le deuxième vérifie si la comparaison est possible. 

Dans ref instanceof C avec ref une référence à un objet et C un nom de classe, d'interface ou de tableau. 

- C est une classe, détermine si c'est une instance ou une référence
- C est une inferface, détermine si la classe est implémentée dans une instance ref d'une classe
- C est un tableau, détermine si c'est le même type 

C et ref doivent être compatible à la compilation. 

La classe Class permet de représenter la classe où est instancié l'objet manipulé. chaque classe a un unique objet Class. 

## Collections 

Permet de gérer des collections de tailles variables. Sur la classe *Arrays* des méthodes statiques sont disponible pour trier et comparer les tableaux. 

L'interface Collection (*listes, ensembles*) permet:

- d'insérer des éléments
- supprimer un élément
- connaître la taille de la collection ou si l'objet existe
- obtenir un itérateur sur la collection

**Les collections stockent seulement des objets**. 

### Types de collections 

- ArraysList 
  - tableaux extensibles, peu performants en insertion et en suppression, accès à l'élément indexé. 
- LinkedList
  - listes doublement chaînées, accès lents

Il faut toujours utiliser des collections génériques pour éviter la perte d'information. 

## Itérateurs 

Permet de parcourir une collection donnée. Lorsqu'il est crée, il se réfère au début de la collection. Il définit les méthodes suivantes:

- hasNext() 
- next()
- remove()

## Généricité

Permet de faire des collections d'un type donné et de ses sous-types. Cela permet aussi d'éviter le transtypage et d'interdire des objets d'un autre genre. 

Si le type n'est pas préciser, c'est une collection de type *raw* et équivaut un collection de type *Object* 

## Mot clé: final 

Signifie qu'on a pas le droit de changer **la référence sur un objet**. Ces derniers sont des constantes connues à la compilation. L'initialisation peut être tardive ou explicite.

```java
	final int a = 4; // explicite
	final int a; // pas de valeur par défaut, il faut donc les initialiser dans le constructeur 

// paramètres final
void m(final Personn p, final  int i){
    // il est interdit de modidifier les paramètres. 
}

// méthode final
// Empêche la redéfinition d'une méthode dans les sous-classes.
// les méthodes private sont implicitement final
public final void m(){
    // On ne pourra pas utiliser la même signature 
}
// pour une classe empêcher la possibilité de faire des sous-classes
```

Lorsqu'on déclare une méthode final, on empêche la spécialisation de la méthode parent. Si elle est private On peut utiliser la même signature. 

Pour les classes, la mention final permet d'empêcher la spécialisation d'une classe. 

## Propriété statiques 

Si la classe est définie avec 's' à la fin comme Objects, cela veut dire que cette classe contient des méthodes static. 

### Attributs statiques

Il n'existe qu'un seul exemplaire pour **toute la classe qui est globale à la classe.** Ils sont accessible par une notation pointée (s'ils ne sont pas private). Ils ont valeurs par défaut. 

*Pour un attribut statique et final, Il faut obligatoirement fournir sa valeur à sa déclaration.*

### Méthode statique 

Indépendantes de tout objet de la classe qui manipule des attributs statiques. **Cette dernière ne peut pas manipuler des attributs non statiques**. Dans une méthode static, pas de paramètre this et de liaison dynamique

### importation statique

```java
import static java.lang.Math.*;
// permet d'éviter de préfixer PI
double r = cos(PI * 2.15)
```

## Blocs statiques

### dynamique

Délimiter par **{ }** Exécuter à chaque création d'objet, constructeur anonyme. 

### static

Exécuter une seule fois dès que la classe est référencée qui ne peuvent pas utiliser des propriétés non statiques de la classe. 

# Classes abstraites 

Elle sert de canevas de base pour d'autre classe. Elle ne peut pas être instanciées directement. Si elle définit des méthodes abstraites, la classe doit l'être aussi. l'inverse n'est pas obligatoire. 

## Une méthode abstraite

C'est une méthode dont on donne que la signature. Elles ne peuvent pas être privée ou statique. 

## Covariance / contravariance 

Certain langages permettent la modification de la signature de la méthode redéfinie.  

### Polymorphisme 

On peut voir un objet d'un type plus spécialisé que celui défini par la signature de la méthode. 

### Covariance (sous-type)

Spécialisation du type de retour dans une méthode redéfinie. **Mais possible seulement pour le type de retour** car les erreurs seraient détectées à l'exécution et non pour le type des arguments. 

### Contravariance (sur-type)

**N'est pas possible en java**. le fait de rendre plus générique, via une classe parent, un type d'argument. 

## Surcharge 

pas de liaison dynamique en cas de surcharge. 

- Même nom
- Nombre différent et type de paramètre 
- type de retour quelconque

Les méthodes static peuvent être surchargées. Un type de retour **final** n'est pas pris en compte pour une surcharge. 

# Interfaces

Une interface est un contrat qui doit être respecté par les classes qui l'implémentent 

Une interface est une classe abstraite sans aucune propriété. Elles permettent une forme d'héritage multiple. On peut définir des constantes qui seront accessibles à toutes les classes qui l'implémentent. Elles sont accessible par notation pointée. 

**Toutes les méthodes d'une interface sont obligatoirement abstraites et publiques. et tous ses attributs sont forcément static final** 

## Variable de type interface

On peut définir des variables de type interface. Pour stocker une référence sur un objet d'une classe implémentant cette interface. 

```java
public interface I{/*..*/}
```

## Méthodes par défaut 

Permet de définir une implémentation par défaut d'une méthode. De cette manière on peut soit avoir l'implémentation par défaut ou la redéfinir. 

```java
// Si on a deux implémentation de la même méthode dans deux interfaces différentes il faut redéfinir la méthode dans la classe. 
interface.super.methode();
```

## Types énumérés sûrs 



## Généricité 

Le type de paramètre et le type de retour peuvent être paramétrée. Il n'est pas possible de faire du polymorphisme du des types génériques. Pour lire un type inconnu on peut utiliser la notation <?> , **On peut seulement lire ces objets**. On peut aussi borné le type inconnu à toutes les sous-classe d'une certaine classe. 

Pour les méthodes génériques, lors de l'utilisation d'un type générique il faut l'initialiser dans la définition de la fonction.

```java
public <X> linkedList<X> exemple (X a){
    
}
```

 ## Hashcode 

Rend une valeur unique pour chacun des objets. Cette fonction est liée à la fonction equals(). **Si on redéfini equals on doit redéfinir hashcode**. 

Lorsqu'on modifie un objet, il faut retirer ce dernier de la table  de hachage **avant** de le changer car sinon on peut plus le retrouver. 

## Exceptions et Erreurs

### Exceptions 

Erreurs potentiellement récupérables. On peut les attraper avec try{}catch(){}. si on ajoute un finally après ce bloc, il est **toujours exécuté**. 

Si une méthode lance des exceptions custom, on doit le dire lors de la définition de la méthode. Si on extends Runtimeexception, on sera pas obligé de l'attraper. 

### Erreurs

Erreurs système irrécupérable.

## Try-with-ressources

Cette rressource sera fermée automatiquement à la fin du try même si une exception a eu lieu. Cette ressource doit implémenter l'interface AutoCloseable. Elle sert à fermer proprement la ressource. 

## Suppression d'objet

Privilégier le système try-with-ressources en ayant implémenter l'interface autocloseabale . Les Cleaner peut être utilisé comme filet de sécurité mais sans garantie. 

## References

Un objet avec une référence forte n'est pas éligible à la destruction par le remasse miettes. Un objet Reference permet de référencer un objet tout en autorisant le ramasse miettes à le nettoyer. 

les trois références ne possèdent pas l'objet, c'est à dire qu'il faut reference.get() pour obtenir accès à l'objet. 

### Douce

Tente de conserver l'objet en mémoire mais peut le perdre si on a besoin de mémoire. 

### Faible

même chose que Douce mais avec une priorité moindre.

### Fantôme 

Sert à savoir qu'un objet à exister. un get() de cette référence retourne toujours NULL. 

# Classe interne

Une classe interne n'est pas un attribut. Pour créer une instance de la classe interne, il faut créer une instance de la classe englobante. Le garbage collector ne peut pas  détruire la classe englobante tant qu'on utilise la classe interne. La classe englobant a toujours accès à toutes les propriétés de la classe interne. 

Les classes internes n'ont pas le droit d'avoir d'élément static car on est obligé d'avoir au moins une instance de cette classe. Si elle est protected, Les sous-classe de la classe englobante et les éléments du package y ont accès. 

# Interface interne 

Peut aussi être définie à l'intérieur d'une classe ou d'une interface. Et elle peut être déclarée privée. 

# Classes locales 

C'est une classe interne. Elle est définie dans un bloc de code. Elles ne peuvent accéder aux variables ou aux paramètres que s'ils sont **final**. 

# Classes anonyme 

classe sans nom. **Ne pas oublier le ';' à la fin de la déclaration de la classe.** Elles ne peuvent être ni statique, ni abstraite. Elles n'ont pas de constructeur mais on peut définir des blocs d'initialisation **non-static**. 