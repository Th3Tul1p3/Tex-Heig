# Exceptions

## Gérer les erreurs et lever une exception

Il y a trois types d'erreurs, pré-condition, post-condition et d'invariant de classe. L'erreur pré-condition reçoit une paramètre non valide. L'erreur post-condition ne peut pas retourner le résultat pour des raisons techniques. L'erreur d'invariant de classe apparaît quand les données membres d'une classe sont changés et qu'ils ne respectent plus la validités.

Les messages d'erreur sont utilisé en pratique pour les langages qui n'ont pas d'exceptions. Dans ce cas il faut gérer directement le'erreur. Ce qui implique de mélanger exécution et gestion d'erreur. 

En c++, on peut interrompre le flux d'exécution normale lorsqu'une erreur apparaît pour passer aux instructions de traitement d'erreur. Avec le mot clé "throw" suivi d'une variable permet de signaler l'erreur. 

try permet de délimiter le bloc de code qui peut générer une exception. Catch permet de gérer les différentes erreur qui peuvent survenir dans le bloc try. 

Toutes les exceptions héritent de std::exception soit directement ou indirectement. L'héritage indirect se fait par std::logic_error qui indique que le programmeur appel mal une fonction et std::runtime_error qui indique plutôt une erreur indépendante du programmeur. 

En général, une exception est capturée par référence. 

```c++
catch (std::out_of_range& e)
catch (const std::out_of_range& e)
```

```c++
try{
    throw out_of_range("hello");
}catch (exception& e){
    cout << e.what(); // affiche hello
}
```

Dans le cas où elle est passée par copie, elle converti e en chaîne par défaut et la chaîne de valeur "hello" est perdue. 

```c++
try{
    throw out_of_range("hello");
}catch (exception e){
    cout << e.what(); // std::exception
}
```

La classe exception déclare la méthode what() comme virtual, elle possède seulement un constructeur par défaut et elle ne possède pas de donnée membre. La conséquence est que l'on ne peut pas créer une exception à partir d'une chaîne de caractère. 

## lever une exception: la hiérarchie des exceptions

On utilise que des types créées explicitement pour servir d'exception. Soit une créer par nous même soit un type de la librairie standard C++.  Une classe peut hériter d'une autre classe. Elle possède les mêmes données membres et fonctions membres mais elle peut aussi en rajouter d'autres. La classe la plus générale pour les exceptions est "exception". Et il y a des des classes dérivées de cette dernière. Leur contenu est pauvre mais ce qui nous importe est leur type. 

Dans exception, il y a parmi les plus utilisées:
- bad_exception
- bad_alloc
- logic_error : mauvaise appelle de fonction de la part du programmeur, elle a besoin d'une chaîne de caractère en paramètre. 
  - out_of_range
  - length_error
  - invalid_argument
- runtime_error erreur indépendante du programmeur
  - range_error
  - overflow_error
  - underflow_error
- bad_typeid
toutes les exceptions sont héritièrent de la classe exception. Cette dernière ne possède qu'un constructeur par défaut.
Pour aider au débogage, il est possible d'utiliser des macros ANSI pour faciliter la résolution d'erreur. le bloc catch reçoit l'exception par copie mais nous devons utiliser la syntaxe par référence pour garder la châine de caractère mise par le programmeur. 
## Garantir l'état du programme après une exception
L'introduction d'exceptions crée un nombre considérable de flux alternatifs. 
- Garantie no-throw : ne lève pas d'exception. exemple les destructeurs, constructeurs par déplacement et swap.
- Garantie forte : si exception, le programme est laissé dans l'état d'avant l'appel de la fonction
- Garantie de base: si exception, la fonction laisse les invariants du programme valide et ne laisse pas de ressources fuiter.
- Pas de garantie: fonction inutilisable
Un invariant est par exemple dans le cas d'une pile, que la taille corresponde bien aux nombre d'éléments contenu. 
throw appel le destructeur de toutes les variables locales avant de sortir d'une fonction pour remonter dansla pile d'exécution. indiquer throw(A,B), signifie le type d'exception qu'une fonction peut lever. 
noexcept indique qu'une fonction ne lève pas d'exceptions. Il y a possibilité de mettre une condition dans le noexcept. Il peut aussi être utilisé comme un opérateur qui prend une expression en paramètre. Comme pour des classes ou des fonctions.  
## Terminer un programme 
Le programme peut être terminer à tout moment par le programmeur 
- exit, sort proprement du programme, avec appel aux destructeurs ou statiquement dans l'ordre inverse d'initialisation. atexit permet d'appeler des fonctions que nous avons définit
- quick_exit, sort rapidement mais sans libérer les ressources dont le programme avait la charge. at_quick_exit permet d'appeler des fonction que nous avons définit. 
- \_Exit,  sort du programme sans rien faire.
les fonctions a exécuter lors de la fin du programme ne prenne pas de paramètres, ne retourn rien. elles sont appelées dans l'ordre inverse de leur enregistrement. 
On peut aussi sortir anormalement du programme en appelant la fonction abort(). La fonction terminate() est appelée dans le cas où une exception n'est pas capturée. La fonction unexpected() est appelée si les spécification dynamique ne sont pas respectée. 
unexpeted() appelle terminate() qui appelle abort(). on peut modifier ce comportement avec set_terminate().
# Introduction au C
## Feedback quizz

Il y a d'abord prétraitement, puis une compilation et l'édition des liens. 

si on double une macro dans un printf cela ne va pas compiler. Si on utilise une constante et qu'on la déclare après cela fonctionne. le '#' dans un printf affiche le nom de la variable passer dans la macro y compris si on fait ++n. 
## L'usage du préprocesseur

### création d'un exécutable

Dans un premier temps le préprocesseur pré traite le code. Ensuite ce dernier est compilé. On effectue l'assemblage des fichiers objets et dans un dernier on fait l'édition des liens. Pour afficher le pré traitement du préprocesseur avec l'option gcc -E. les commandes préprocesseur débutent toutes avec un # et elles doivent tenir sur une ligne. 

### Les macros

Lors de la définition de la macro, le préprocesseur remplace le nom de la macro par son contenu. si on veut faire une macro sur plusieurs lignes, il faut utiliser l’échappement ' \ ' à la fin de la ligne. 

```c
// permet de définir une macro avec paramètres
#define min(a,b) ((a)<(b)?(a):(b))
```

le caractère # dans une macro permet de dire que le paramètre doit apparaître sous forme de chaîne.  le double ## permet faire des choses similaires à la généricité. 

```c
#define GENERIC_MIN(type)\
// permet de générer une macro qui retourne le min en précisant son type dans l'appelle de la fonction 
type type##_min(type x, type y)\
{return x < y ? x : y; }
```

Pour garantir la bonne exécution d'une macro on peut utiliser les blocs d'instructions. Une macro déclarée ne peut pas supprimée. Certaines macros standard permettent de faire des actions prédéfinient 

## #if #endif #define

Si la condition n'est pas remplie, le code n'est pas compilé. Les conditions doivent pouvoir être évaluable à la compilation. On peut aussi inverser la condition avec #!define. 

## #elif #else

Ces opérateurs permettent de gérer la portabilité du code pour différent OS. Pour bloquer la compilation avec #error. La commande #pragma permet de donner des instructions au compilateur. 

## Les types de base en C  et leurs qualifieurs

## Les types de base 

Le type bool peut être utilise avec la librairie <stdbool.h>. La librairie <stdint.h> permet d'avoir des entiers occupant un nombre précis de bits. 

le qualifieur volatile veut dire que la donnée peut changer pendant l'exécution. Par exemple pour des pointeurs. 

Une variable marquée const ne permet pas de construire des expressions courantes et elle n'a pas besoin d'être initialisée. 

## Les opérateur en C: logiques, bit à bit

Les opérateurs binaires sont associatifs à gauche tandis que les unaires le sont à droite. 

points de séquence?????????????????????

Les opérateurs de décalage binaires ont une priorité plus faible que les opérateurs arithmétiques. 

## Les entrées et sorties en C avec <stdio.h>

getchar() lit un caractère et le retourne comme caractère convertit en int. putchar(int c) fait la même chose mais en écrivant. 

## printf() et scanf()

Les codes de formatage sont composés d'un % au début, gabarit d'affichage ou nombre de chiffre minimal à afficher (optionnel), un point, précision après la virgule (optionnel) et du code de conversion (lettre). Le gabarit d'affichage et la précision peuvent être remplacés par des *. Cela veut dire qu'ils sont donné en argument du printf. L'introduction d'un # entre le % et le gabarit, veut dire qu'on affiche le préfixe du nombre. 

```c
printf() // écrit dans stdout 
fprintf() // écrit dans un fichier
sprintf() // écrit dans la chaîne de caractère
```

scanf() prend comme premier argument le format, ensuite l'adresse de la variable de stockage et elle retourne le nombre de données saisies. 

```c
// %* la valeur est ignorée
// %Nc lit N caractère
// %[LISTOFCHARS] lit seulement les caractères dans la liste 
// %[^LISTOFCHARS] lit seulement les caractères qui ne sont pas dans la liste 
// %n retourne le nombre de caractères lu
```

# Pointeurs
## Organisation mémoire
(void*) convertit l'adresse d'un entier en une adresse générique pour l'affichage par printf .  on ne peut pas enchaîner une déclaration de pointeur tel que:

```c
int* p, q; // ne fonctionne pas pour la variable q
```

## Définitions
Pour la définition d'un type pointeur il faut toujours indiquer vers quel type ce dernier pointe. Il est de bonne pratique d'initialiser un pointeur à NULL. void\* désigne un pointeur générique. 
Déréférencer un pointeur pointant sur un endroit NULL ou non initialisé produit une erreur de segmentation.

## Pointeurs et fonctions
Comme le passage par référence n'existe pas en C, on passe les adresses des variables pour pouvoir les modifier. Il est aussi utile de passer le pointeur sour format constant pour éviter une copie de la variable mais il est nécessaire  si la variable est constante. 

## Pointeurs et tableau
Il est possible de faire trois différents calculs sur des pointeurs:
- ajouter un entier sur un pointeur
- soustraire un entier sur un pointeur 
- soustraire un pointeur d'un autre, par exemple sur un tableau pour avoir leur écart.
Si on fait une incrémentation sur un pointeur, elle sera plus prioritaire. 
```c
*p++	// retourne la valeur pointée avant incrémentation et incrémente le pointeur
(*p)++	// retourne la valeur pointée et modifie la valeur pointée
*++p	// incrémente le pointeur et retourne la valeur
++*p	// incrémente la valeur pointée
```
On peut tester des pointeurs comme des variables. Si différent de NULL, ils sont vrai
```c
int A[] = {1,2,3,4,5};
int* ptr = &A[0];
// depuis C99 on remplacer les lignes du dessus par celle du dessous 
int* ptr = (int []){1,2,3,4,5};
```
Lors de l'initalisation d'un pointeur sur un tableau à plusieurs dimensions, il faut faire attention qu'il soit du bon type. Il faut le déclarer en fonction de la dernière dimension. 
Lors de l'appel de fonction, ily a deux manières de considérer les dimensions des tableaux. soit sous la forme d'un tableau avec un seul indice ou en créant un tableau de pointeurs sur les lignes d'un tableau à 2 dimensions. 

## Pointeurs vers des fonctions
```c
int (*adrf) (int); // pointeur sur une fonction qui prend un int en paramètre
void (*file_cmd[])(void) = {new_cmd, ....}; // tableau de pointeur sur des fonctions 
```
## Allocation dynamique
Ces fonctions se trouvent dans le tas. La perte du pointeur entraîne une fuite de mémoire. Pour libérer la mémoire appeler la fonction free(). 
alloca() permet d'allouer de la mémoire le temps du bloc de code.
```c
- malloc: réserve un bloc de mémoire et n'initialise pas 
// la taille doit correspondre à la taille en octet
void* malloc (size_t size); // retourne l'adresse dans la mémoire 
- calloc: réserve un bloc de mémoire et initialise le tout à 0
// nmemb nombre d'élément, size la taille en octet
void* calloc(size_t nmemb, size_t size); // retourne l'adresse en mémoire, ou NULL si pas possible
- realloc: redimensionne un bloc mémoire précédemment affecté 
// ptr l'adresse de l'adresse mémoire, size est la nouvelle taille. si le pointeur retourné est NULL, la taille n'a pas pu être changé
// si size est nulle, la mémoir est libérée.
void* realloc(void* ptr, size_t size);
```
## Manipulation mémoire
Toutes les fonctions suivantes ont besoin de <string.h>
```c
// copie un certain nombre d'octet 
- void* memcpy(destination, source, nbr d'octet)
// copie un certain nombre d'octet 
- void* memmove(destination, source, nbr d'octet)
// rempli le n premiers octets de la mémoire 
- void* memset(source, valeur à mettre, nbr octets)
// compare les n premier octets
- void* memcmp(pointeur 1, pointeur 2, nombre d'octets)
// cherche la première occurence d'un octet 
// retourne le pointeur sur l'octet trouvé
- void* memchr(source, valeur à chercher, nombre octet)
// recherche depuis la fin
- void* memrchr(source, valeur à chercher, nombre octet)
```
le mot clé restrict permet d'indiquer que seul ce pointeur est utilisé à la case mémoire. 