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

On utilise que des types créées explicitement pour servir d'exception. Une classe peut hériter d'une autre classe. Elle possède les mêmes données membres et fonctions membres mais elle peut aussi en rajouter d'autres. La classe la plus générale pour les exceptions est "exception". Et il y a des des classes dérivées de cette dernière. Leur contenu est pauvre mais ce qui nous importe est leur type. 