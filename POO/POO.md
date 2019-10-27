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

- interface: Ensemble de méthodes abstraites qui peuvent implanter des classes afin de garantir un comportement. représenté elle aussi en italique avec une flèche en pointillés. 

- Associations: relation qui existe entre plusieurs objets où chaque objet à un rôle déterminé. représenté par un lien reliant deux classes. caractéristiques:
  - Peuvent être parcourue dans tous les sens
  - Nom: fait avec un verbe conjugué et une flèche pour le sens de lecture du verbe 
  - rôle: pour chacune des classes
  - cardinalités: précisent combien d'objets de chaque classe peuvent être liés à un autre objet.
    - en indiquant le nombre exact ou un étoiles pour plusieurs. 

- Agrégations : est une association spécialisée qu'un tout est composé de parties. dénoté par un losange et un trait plein ainsi qu'une notation de cardinalité

- Composition: agrégation spécialisée décrivant une contenance structurelle. dénoté par un losange plein et d'un trait plein. 
  - si on détruit l'objet, les parties sont aussi détruites.
  - Un objet composant ne peut faire partie que d'un seul objet composite. 

- Classe d'association: classe pour représenté les propriétés d'une association entre deux classes. relié à l'association par un traitillé. Pas nécessairement nommée. elle peut être lié à d'autre classe. chaque association est lié ** à un et un seul ** objet de la classe. 

- Arité des associations: lien binaire entre deux classes différentes. elles peuvent être cycliques. 
  - n-aires
    - Non trivial 
    - une occurrence de l'association lie des objets de chacune des classes 

- Navigabilité : 

  - permet de spécifié dans quelle sens il est possible de traverser l'association lors de l'implémentation
  - Les objets de la classe cible participant à l'l'association doivent pouvoir être atteints directement depuis la source, l'inverse  n'est pas forcement vrai. 

- implémentation des associations: 

  - implémentation n-aires:

  ![1](/media/Partage/HEIG/Tex-Heig/POO/1.png)

  ![2](/media/Partage/HEIG/Tex-Heig/POO/2.png)

  - ne jamais indiquer de références relatifs au langage 
  - selon la navigabilité et les cardinalités, il faut définir : des attributs références et des collections de références 
  - contraintes d'intégrité à ajouter pour ex: forcer une ville à faire partie d'un pays pour être capitale
# Main
Il n'a pas de type de retour, pas de compteur d'argument et il est static. 
On peut passer des arguments par:
- valeur : On encapsule bien car on modifie une copie de l'objet
- référence : On utilise moins de mémoire et on modifie directement l'objet. 
Mais en java, tous les objets sont transmis uniquement par références et les types primitifs par valeur
- Une sous classe est spécifié par le mot clé **extends**. cette dernière hérite des propriétés définies dans la classe parent. **Pas d'héritage multiple** 
- On peut redéfinir une méthode héritée. **avec le même nom et le même nombre et les mêmes types de paramètres et le même type de résultat**  Si la signature est la même, il existe une liaison dynamique entre la méthode originale et la méthode redéfinie. 
- Si ces règles ne sont pas respectés, c'est une surcharge. dont sans liaison dynamique. 
- toString() est héritée par la super classe object. la méthode est invoquée automatiquement dès qu'on doit représenté une instance sous forme d'une chaîne. Mais elle rend seulement l''adresse de l'instance. 
- En java un tables **est un objet**. Un de ses attribut, est sa longueur grâce à length et il ne contient que des éléments de même type. 

