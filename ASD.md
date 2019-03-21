# complexité exo prog

la tour de Hanoï a une complexité qui a une complexité de =(2^n). Pour le triangle récursif, la complexité est de O(a^2 - b^2). Pour le PGDC, la complexité est de O(log_x(a)) avec phi comme x. Pour les fractales, la complexité est de O(4^n + i*2^n) car le 4^n calcul un carré et le i * 2^n le triangle. Et pour les conversions de base, la complexité est de O(log_B(n)). 



## accélération du parcours exact de l'arbre 

l'élagage alpha beta est le fait d'abandonner des branches classées non optimal. Dans le meilleur cas, il permet de doubler la profondeur d'exploration et  dans le pire des cas cela n'apporte rien. L'ordre correspond à la branche par laquelle on commence. 

La table de transposition est de regarder les branches qui ont la même situation. 

Il faut fait attention lors d'appel récursif car la pile d'appel a une limite. L'algorithme de Fibonacci ne doit surtout pas être écrite de manière récursive. Quand un appel est tout à la fin de la fonction, l'optimisation du compilateur fait que la fonction a la même exécution qu'une fonction itérative. 

Avec les tris, on a deux sortes de complexité.  spatiale ou temporel. spatiale pour l'utilisation mémoire. temporel pour la durée. 



### Tri de shell

On divise le tableau en sous tableaux d'abord très grand puis de plus en plus petit jusqu'à des tableaux d'un élément. la complexité dépend de la séquence choisi pour h (taille du tableau). La performance est assez proche du tri par fusion. 

### Tri fusion

