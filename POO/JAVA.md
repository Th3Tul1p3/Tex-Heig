# JAVA

- Fiabilité, sécurité
- indépendant vis à vis du processeur
- interaction avec l'extérieur
- récupération d'erreurs
- multi-plateforme: compiler en java byte code exécuter dans une machine virtuel.
Les types primitifs ne sont pas des objets. 
## compilation et exécution
On part d'un \*.java, on effectue la commande javac pour compiler. On obtient un fichier .class. on exécute le .class avec la commande java. 
## Types primitifs
- Entiers signés : byte(8 bits), short(16 bits), int(32 bits), long(64 bits)
- Réels float (32 bits), double(64 bits)
- Booléen: boolean 
- Caractère char (16 bits)
**Par défaut un nombre est un int.** ** Par défaut un littéral flottant est un double** 
## type objet primitif
- Chaque type à son équivalent en classe en ajoutant une majuscule. (sauf Integer, Character). Une fois créer la classe ne peut plus être modifié. On peut convertir un type primitif en sa contrepartie objet.
Déclaration comme en C. 
## Références
En java, tous les objets sont manipulés au moyen de références typées. Si on fait une égalité entre deux classe on aura une **référence**. ce qui n'est pas le cas avec des types primitifs. 
## Chaînes de caractères
il suffit de faire string s = "salut";
String s = "a", p = s; 
s += "!";// retourne une nouvelle chaîne de caractère car on ne peut pas la modifier 
# classes
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

# Paquetages

est une bibliothèque de classes :

se déclare **package nomPackage;**  Si aucun package n'est déclaré dans un fichier, les classes correspondantes appartiennent au package par défaut. Les fichiers .class doivent être placés dans le même répertoire. 

Pour utiliser une classe d'un paquetage, on peut utiliser la notation **import nomPackage.nomClasse;**   ou  **import nomPackage.*;** pour importer toutes les classes du package. 

# Visibilité

- private visible dans la classe uniquement (à utiliser)
- (aucun) visibilité niveau package 
- protected visibilité package et pour les sous-classes 
- public visible partout 

Un constructeur peut être déclarer private. 

# polymorphisme

- Universel 
  - paramétrique généricité 
  - inclusion Opération applicable sur des types liés par une relation d'héritage
- Ad hoc 
  - surcharge même identificateur pour des opérations différentes
  - conversion automatique de type

![Capture d’écran_2019-10-14_09-53-27](/media/Partage/HEIG/Tex-Heig/POO/img/Capture d’écran_2019-10-14_09-53-27.png)

