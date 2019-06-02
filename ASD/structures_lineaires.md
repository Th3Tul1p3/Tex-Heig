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

# structures linéaires

insérer à la fin devient le pire cas quand la taille == la capacité. suppression à la fin pourrait être de complexité constante si on utilise pas shrink to fit. 

# Tableau
## Tableau à taille fixe 
Un tableau de taille fixe est constitué d'un pointeur sur le premier élément et de sa taille. Les éléments sont accéder par l'indice physique. L'indice pour accéder à chaque élément est valide de 0 à N compris. On peut accéder à son emplacement mémoire via la formule: adresse <-- tableau + i *taille(type). 

La notion de capacité fixe permet de pouvoir insérer et supprimer en fin en changeant la variable taille. Si ces actions ne sont pas possible, il faut alerter l'utilisateur. Même chose s'il on veut insérer et supprimer en position quelconque. 

Le buffer circulaire permet de se libérer des contraintes de commencer à l'indice 0. Ce dernier possède un indice physique pour l'emplacement mémoire et un indice logique pour les indices utilisateur. 

## Tableau de taille variable et de capacité fixe

Cela permet d'allouer dynamiquement de la mémoire si la capacité n'est plus suffisante. S'il n'y a plus de capacité suffisante, il faut allouer un espace mémoire plus grand, déplacer les éléments contenu de l'ancien espace data puis détruire l'ancienne espace de data. 

Complexité de l'insertion en fin: si assez de mémoire O(1) dans le pire des cas, il est de O(N). le cas moyen se situe dans l'intervalle 2 et 3 on dit  alors que la complexité et constante en temps amorti. Une bonne méthode pour gérer une capacité plus gande que la taille est d'attendre que taille sois 4 fois plus petite que capacité. 

![comp_capa_var](/media/Partage/HEIG/Tex-Heig/ASD/comp_capa_var.png)

# Listes

## simplement chaînées

Les éléments ne sont pas forcément consécutif. Mis en oeuvre avec une structure générique. pour le parcours il est préférable de faire de manière itérative. L'encapsulation permet de ne pas avoir de problème lors de la manipulation des éléments. Le mieux serait d'avoir des itérateurs ainsi que des opérateurs pour accéder et passer au suivant (approche de la STL). 

## doublement chaînées

L'utilisation d'un attribut vide pour stocker l'adresse du premier et l'adresse du dernier. Pour une liste vide, les deux pointeurs pointe sur lui même. la méthode dernier retourne l'adresse de apad. 

## tri

On ne peut pas appliquer les algorithmes de tri vu précédemment car il n'y pas d'accès indexé. Les tris par sélection, par insertion et à bulles peuvent être adapté pour les listes. le tri se fait en réordonnant les éléments. Il ne faut pas changer la valeur de l'élément. Splice after permet de déplacer des maillons pour le tri par insertion. La fonction splice nous permet de mettre en œuvre le tri fusion. Cette dernière a une complexité temporelle et spatiale constante. 

# Deque

Les données sont stockées dans plusieurs petits tableaux de capacité fixe. Ils sont appelés chunk. Les adresse de ces chunk sont stocké dans un buffer circulaire, appelé map, qui est a capacité variable. Pour accéder aux éléments, il faut pratiquer un double déréférencement. La map et le chunk possède chacun un méthode pour le calcul de l'indic physique. 

![comp_deque](/media/Partage/HEIG/Tex-Heig/ASD/comp_deque.png)

# Tas 

Le tas est un tableau de taille variable que l'on représente comme un arbre bianaire. Chaque élément a un parent sauf la racine, aucun élément n'a plus de deux enfants. La complexité pour trouver l'élément le plus grand est constante car c'est le premier. L'insertion et la suppression se font avec une complexité logarithmique.  

push_heap : L'insertion se fait en fin de tableau. Ensuite il faut faire remonter l'élément jusqu'à que la condition de tas soit respectée. 

pop_heap : La suppression s'effectue en général sur l'élément le plus grand. Pour ce faire on échange la racine et le plus petit élément et ensuite on supprime le dernier. Pour rétablir la condition de tas, on fait redescendre l'élément par le plus grand de ses enfants jusqu'a respecté la condition de tas.  

make_Heap sert à faire le tas, il fait descendre les parents, s'ils sont plus petits, vers le plus grand enfant. La complexité est de O(N*log(N)) car chaque insertion est logarithmique. 

sort_heap: il faut créer le tas avec make heap. Ensuite on prend à chaque fois la racine et on la met en dernière position et on fait remonter le plus grand des enfants. ce tri est instable et s'effectue en place. 

les conditions de tas sont :

- tout élément est plus grand (ou égal) que ses enfants
- réciproquement, tout élément est plus petit (ou égal) que son parent

![indice_tas](/media/Partage/HEIG/Tex-Heig/ASD/indice_tas.png)

# Type de donnée abstrait
Ces types restreignent la manière d'insérer, d'accéder et de supprimer les éléments. 
## Pile 
Principe LIFO. opérations de base push, pop et top. 
Les évaluations d'expressions arithmétiques se fait lorsqu'on rencontre des ')'. Pour stocker les opérandes et les opérateurs, on utilise deux piles et on évalue dès qu'une ')' est là. la notation polonaise inverse permet d'éviter davoir deux piles.  
## Queue
Principe FIFO, opérations de bases push, pop, front et back
## priority_queue

Même chose que queue mais avec notion de priorité. Si on rentre une paire d'élément dans la file, on ressort en regardant d'abord le premier mais si ils sont égales on regarde le deuxième. 

emplace sort les éléments dans l'ordre inverse de pop. 
# Structures linéaire en C++
- Sequence container : Array, Vector, Deque, List, Forward_list. 
- Container adaptors: Stack, Queue, priority_queue. 
- Les fonctions de tas sont aux nombre de 6. push_heap, pop_heap, make_heap, sort_heap, is_heap et is_heap_until. 
![comp_STL](/media/Partage/HEIG/Tex-Heig/ASD/comp_STL.png)

# Allocation dynamique 

```c++
T* ident = new T; // ident est un pointeur sur la variable de type T
int* i = new int(42); // ou {42}
delete ident;

T* ident = new T[N]; // ident est un pointeur sur le tableau de type T
// on doit initialiser chaque élément 
delete[] ident;
// Il est autoriser un tableau de taille nulle

```

Il faut appeler delete dans le flot d'exécution pour éviter une fuite de mémoire.  Il est de bonne pratique de mettre le pointeur supprimé à nullptr. L'opérateur new appelle le constructeur spécifié, malloc et calloc allouent juste de la mémoire sans appeler le constructeur. Même différence entre delete et free. 

```c++
T* Ptr = (T*) ::operator new(N*sizeof(T)); // ne construit rien mais alloue la mémoire
::operator delete(Ptr);// ne détruit pas mais libère la mémoire 
```

Les destructeurs ne lèvent pas d'exceptions. Les constructeurs lèvent soient des std::bad_alloc  ou des exceptions du constructeurs. 

Trois sources de fuite de mémoire:

- écraser la valeur du pointeur 
- perdre le pointeur
- le programme ne s'exécute pas de manière attendue et fait perdre le pointeur
Si une exception est levée elle doit appelé les destructeurs. Le constructeur de copie par défaut va copier tout les attributs d'une classe. Cela pose problème lors de leurs destructions car ils ont les même pointeurs. 
Pour pouvoir trier une classe, il faut mettre en oeuvre les opérateurs > et <. 
Un emplace_back appelle juste le constructeur avec élément, le push_back appelle le constructeur vide puis l'opérateur de copie, et le destructeur. Si on affecte vecteur avec un type complexe, il va construire un élément, affecter ce élément puis le détruire. 
La complexité de std::swap est de O(N). si on fait une méthode qui une fonction qui swap simplement les éléments, on passe à O(1). 
Une rvalue reference est une rvalue dont l'existence est temporaire, une expression en cours d'évaluation, une valeur en retour de fonction. Le move est noexecpt contrairement à l'opérateur d'affectation. 
# Arbres 
Le but est d'insérer et de supprimer en O(log(N)) et qui permet de chercher en O(log(N)). 
## arbres quelconques
- degré de noeud : nombre de fils 
- Racine : seul noeud sans père 
- étiquette: information associée à un noeud
- feuille : noeud sans fils
- chemin : suite de noeuds reliant la racine à un noeud
- niveau: nombre de noeuds sur le chemin du noeud
- noeud interne : noeud avec fils
- hauteur longueur du chemin le plus long 
- degré de l'arbre: degrés max de ses noeuds
- sous-arbre : sous ensemble de noeuds ayant une structure d'arbre 
- arbre plein: degré(N) = degré(arbre), en tout nœud interne N
- arbre complet : arbre plein, rempli depuis la gauche. 
- arbre dégénéré: degré de chaque noeud interne vaut 1
Le parcours en profondeur est un algorithme récursif qui permet de parcourir de haut en bas et de gauche à droite. 
Le parcour en largeur est un algorithme nécessitant une queue où on fait chaque niveau de gauche à droite. 
## Arbres binaires
C'est un arbre de degré 2. 
Un parcour préordonné est un parcours en profondeur. Un parcours symétrique consiste à prendre l'enfant gauche, la racine et l'enfant droit. Le parcours postordonné prend l'enfant gauche, droit et la racine. Puis parcours en largeur. 
Les expressions arithmétiques sont équivalentes à des arbres dont les feuilles sont des valeurs et les noeuds internes des opérations. 
On peut rechercher, insérer, supprimer, un élément dans un ABR. Le rang d'une clé est toujours de 1 pour une feuille. 
![comp_ABR](/media/Partage/HEIG/Tex-Heig/ASD/comp_ABR.png)
L'équilibrage permet d'éviter de grande complexité pour avoir une hauteur en O(log(N)). On considère qu'un arbre est équilibré si la différence entre la hauteur de l'enfant gauche et droit est plus grand ou égal à 1. 

# Set
Les sets stockent des éléments dans un ordre spécifique et ne peuvent être modifiés dans la structure. utilisé pour les ABR. Pour l'insertion, seul les éléments sont insérés O(log(n)). cherche en O(log(n)), efface en O(log(n)), begin O(1).
# Map 
Structure formé par une combianaison de clé et de valeur. Les clés sont utilisé pour triés la map. operator [] en O(log(n)), 1