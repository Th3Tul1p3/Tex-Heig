# POO 

un objet est une structure informatique qui a un état et un comportement . 

- un objet est une instance d'une classe.  il a un état (valeur des attributs) , un comportement (ensemble des opérations applicables) et une identité 

- classes: permettent de définir des objets 

  - décrit des entités qui ont les mêmes propriétés la structure statique (attributs ou champs ) et un comportement dynamique (méthode). 

- héritage est une extension d'une classe dans une nouvelle sous-classe. Spécialisation d'une autre classe en ajoutant des nouvelles propriétés. une sous classe peut accéder aux propriétés non privées dont elle hérite. 

- polymorphisme voir un objet sous une différente forme. On peut redéfinir des méthodes. Une instance d'une classe est membre de toutes les super-classes de sa classe. 

  Il est donc possible de manipuler un objet d'un autre point de vue .  La liaison dynamique permet d'invoquer automatiquement la méthode la plus spécialisée d'un objet. Mais la méthode invoquée doit être déclarée dans la super classe. 

- encapsulation protection de données. Les avantages : la modularité par l'implémentation d'une classe indépendante d'une autre classe. et Masquage de l'information  en modifiant les propriétés privées d'une classe sans affecter les autres classes. Cela permet de ne pas donner accès à une méthode en dehors de la classe (méthode privée). 

  - publique : visible en dehors de la classe. 
  - private: non visible en dehors de la classe. 
  - protected: visible uniquement dans les sous classes. 

- L'héritage multiple est le fait d'hériter de plus d'une super classe. 

La POO permet un gain en productivité et en sécurité de programmation. Une écriture réutilisable avec les classe et extensible avec l'héritage et la liaison dynamique. et l'encapsulation. 
# UML 
La modélisation est un processus d'abstraction permettant de représeneter un problème. Modéliser sert à choisir les objets sans considérer l'implémentation. Cela sert aussi de documentation. 
L'UML permet de spécifier et de visualiser les composants d'une application. 
- diagramme de classes : coeur du langage et description des classe. C'est une modélisation statique. 
  - Nom
  - attributs et leurs visibilité (+ publique, - privée, # protégée, ~ paquetage)
  - méthodes et leurs visibilité 
  - les propriétés de classe qui sont soulignées. 
- l'héritage dénoté par une flêche en trait plein. 
- Classe abstaite : Non instanstiable directement. elles sont représentées en italique 
- méthode abstraite: seulement sa signature est définie. elle est aussi représentée en italique. 
