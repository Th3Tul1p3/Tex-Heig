### Qualité d'un logiciel 

fiabilité, robustesse, extensibilité, réutilisabilité, compatibilité et efficacité. 

std::find a une complexité de O(n) et std:: lower_bound O(log(n)+1).

### Complexité 

algorithme dichotomique O(log(n)).

```c++
for(N fois ){}// O(N)
for(N fois){
    for(M fois){} // O(N*M)
}
for(i < N){
    for(j < i ){} // O(n²)
}
// Pour une boucle dont l'incrément est de *2 O(log(n)) idem pour les divisions 
```

Dans le cas d'un enchaînement alternatif, il faut calculer le meilleur, le cas moyen et le pire cas. Une recherche séquentielle a dans le pire cas O(n).

```c++
// O(n)
int p2 = 1;
for(int i = 0; i < n; ++i) {
	if(i == p2) {
        for(int j = 0; j < i; ++j) {
        	++k;
        }
        p2 *= 2;
    }
}
// O(n²)
for(size_t i = 1; i < v.size(); ++i) {
    size_t j = i;
    while( j > 0 and v[j-1] > v[j] )
    {
        swap(v[j-1], v[j]);
        --j;
    }
}
```

f = O(g)  f croît au plus vite que g 
f = o(g) f croît strictement plus lentement que g.
f = Ω(g) f croît au moins aussi vite que g .
f Θ(g) f et g ont le même ordre de grandeur.

si une fonction est la somme de plusieurs termes, on garde que celui qui croît le plus vite. Si une fonction est le produit de plusieurs termes, on peut ignorer le facteur constant. 

### Récursivité

Une fonction factorielle  a une complexité de O(N) , de O(log(n)) si on divise n dans l'appel de la fonction. L'algorithme de Fibonacci est de O(log(n)) avec comme base ( 1 ± √5 ) / 2. le nombre de déplacement pour les tours de hanoï est de 2^n -1 et sa complexité est exponentielle O(2^n). 

### Complexité exo prog

La tour de Hanoï a une complexité qui a une complexité de =(2^n). Le triangle récursif, la complexité est de O(a^2 - b^2). Le PGDC, la complexité est de O(log_x(a)) avec phi comme x. Les fractales, la complexité est de O(4^n + i*2^n) car le 4^n calcul un carré et le i * 2^n le triangle. Et pour les conversions de base, la complexité est de O(log_B(n)). 

### Accélération du parcours exact de l'arbre 

L'élagage alpha beta est le fait d'abandonner des branches classées non optimal. Dans le meilleur cas, il permet de doubler la profondeur d'exploration et  dans le pire des cas cela n'apporte rien. L'ordre correspond à la branche par laquelle on commence. La table de transposition est de regarder les branches qui ont la même situation. 

Il faut fait attention lors d'appel récursif car la pile d'appel a une limite. L'algorithme de Fibonacci ne doit surtout pas être écrite de manière récursive. Quand un appel est tout à la fin de la fonction, l'optimisation du compilateur fait que la fonction a la même exécution qu'une fonction itérative. 

### Tri à bulles 

Il compare deux élément successif d'un tableau. S'ils sont en désordre ils sont échangé. au niveau mémoire juste besoin d'une variable tampon. 

### Tri par sélection 

Recherche de l'élément le plus petit et l'échange avec le début du tableau. 

### Tri par insertion 

On prend le premier élément non trié et tant qu'il est plus petit que le précédent, on le permute avec celui-ci. 

### Tri de shell

On divise le tableau en sous tableaux d'abord très grand puis de plus en plus petit jusqu'à des tableaux d'un élément. la complexité dépend de la séquence choisi pour h (taille du tableau). La performance est assez proche du tri par fusion. les petits sous-tableaux sont triés par insertion h(x)=3h(x-1)+1. 

### Tri fusion

On divise en sous-tableaux, on compare à chaque fois les premiers. Pour les petits tableaux, on fait un tri pas insertion. 

### Tri rapide

Pour optimiser le tri rapide, on fait un appel récursif seulement sur la partition la plus petite. le pire cas est en théorie impossible si on choisit bien le pivot. le quick select  et nth_element à la même complexité que le tri rapide. 

le C++ sort a besoin de l'opérateur < pour fonctionner, il garanti une complexité de O(n log(n)) mais pas la stabilité contrairement à stable sort. 

- #### tri stable : tri à bulles, tri par insertion, tri par fusion. 


- #### tri par échange : tri à bulle, tri par sélection, tri rapide. 


- #### tri qui ne dépendent pas de la taille des données :tri à bulle, tri par sélection, tri par fusion. le tri par insertion dépend de l'état de l'entrée. 


