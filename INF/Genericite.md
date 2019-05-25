# classe révision test

L'opérateur d'affectation composé est obligatoirement une fonction membre. 

```c++
// initialisation 
obj(1.0);
obj2 = 2.0;
obj3{3.0};
obj4 = {4.0};
// constructeur à plus de deux arguments seulement les deux derniers. 
```



## Membre static

Un membre d'une class peut être déclaré static, il est unique pour la classe et il est commun à tous les objets de cette classe. On y accède via l'opérateur de portée (::) ou comme membre d'un objet avec la notation pointée. Les membres static sont initialisés dans le .h 

Les fonctions membres static n'ont pas accès aux membres non static. Si elle est public on y accès avec l'opérateur de portée.

## membre constant

Les membres constant peuvent varier d'un objet à un autre. l'initialisation se fait lors de la construction de l'objet. 

# Fonction génériques

la déclaration est la définition d'une fonction sont précédées du mot template.

```` c++
template <typename T> void echanger (T& v1);

template <typename T> void echanger (T& v1){ //...
}
````

On peut aussi utiliser "class" à la place de "typename" mais c'est uniquement pour être retro compatible. Une définition de fonction ne crée pas de code si elle n'est pas instanciée. 

```` c++
template void echanger<int> (int&);	// explicitement
echanger<int>(a,b);					// ou impliciement 
````

Il peut y avoir plusieurs paramètres génériques. Pour les fonctions, il n'est pas nécessaire de préciser les types souhaités. ils peuvent être déduits mais cela n'est pas le cas pour les classes. Pour la déduction des arguments c'est toujours le type exact qui est demandé.  A noter que le "<>" est optionnel s'il y a déduction de type. On peut aussi assigner une valeur par défaut aux paramètres génériques. La déduction d'arguments prime sur la valeur par défaut. 

## spécialisation 

Il est possible de spécialiser une fonction pour un type spécifique. C'est une surcharge de fonction. On peut le faire en changeant de type ou on traitant les références constantes ou non différemment.  

## compilation séparée 

Mettre la définition dans un fichier .h ensuite. Il n'y a pas besoin de déclarer la fonction, la définir suffit. La définition va dans le .cpp. Pour faciliter la compilation, il faut utiliser faire comme cela:

```` c++
extern template void echanger<int> (int&);
extern template void echanger<char> (char&);
````

On peut aussi définir des paramètres génériques qui ne sont pas des types tel que des constantes. Pour ce genre de cas, il faut que la valeur puisse être définie à la compilation. 

# Classes génériques 

## Déclaration

```` c++
templatee <typename T>
class Cvector
{
  T x, y;
  // et blabla
};
````

Une classe doit absolument être instanciée comme pour la classe vector. Pour une classe il n'y a jamais de déduction d'argument. Pour éviter l'instanciation implicite utiliser appellation extern. 

## Compilation séparée

## Méthode générique

## spécialisation

# alias générique

## Définition de constantes génériques 

```c++
template<typename T>
using rIter = vector<T>::reverse_iterator;
using rIter = typename vector<T>::reverse_iterator;

// seulement c++14
template <typename T>
const T pi = T(3.1415)
```

## Fonction boost 

boost est un namespace. si on veut l'utiliser il faut le télécharger et ne pas oublier de mettre Boost::...

# Contrats et concepts dans la STL

La STL et La C++Standard library ne sont pas la même chose. Tous les header dont on fait un Include dans notre code sont dans la C++Standard library. 

