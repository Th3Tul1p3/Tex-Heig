```c++
void f(int a, int b){
if (a <b){
    cout << a << b << " ";
    f(a+1, b);
    f(a, b-2);
}
// pour affichage avant 04 14 24 34 12 02 12 04 
// pour affichage au milieu 34 24 14 12 04 12 02 
// pour affichage après 34 24 12 14 12 02 04 
```

# Tri 

les caractéristiques d'un algorithme de tri est caractériser par une complexité en temps de calcul, en mémoire et maintient( façon d'insérer des éléments).  Il faut toujours utiliser swap pour échanger deux valeurs car cette fonction échange au niveau des pointeurs et ne fait pas de copie. 

la notion de stabilité indique que si deux éléments sont égaux, ils restent dans le même ordre. 

## Tri à bulle 

On prend deux élément du tableau, on les compare et si elles ne sont pas dans l'ordre, on les échange. Lors du premier passage, le plus élément du tableau est au bout. Lors de chaque passage on travaille avec n-1 élément du tableau. Elle est stable. La complexité est de O(n²) .

## Tri par sélection

On recherche l'élément le plus petit du tableau est on le place au début du tableau. Contrairement au tri à bulle on trie depuis le début. La complexité est de O(n²) . Ce tri n'est pas stable. 

## Tri par insertion



## Tri de Shell



## Tri par fusion



## Tri rapide



## Tri optimal



## Tri en C et C++

# structures linéaires

insérer à la fin devient le pire cas quand la taille == la capacité. suppression à la fin pourrait être de complexité constante si on utilise pas shrink to fit. 





