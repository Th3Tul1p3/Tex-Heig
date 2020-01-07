# Résumé Crypto

- le chiffre de césar est un décalage de 3 positions 
- le chiffre de vigenère est basé sur le même principe que le chiffre de césar mais avec un décalage en fonction d'une clé 
- Vernam clé aléatoire aussi longue que le message. sûr inconditionnellement. 
- Machine Enigma : trois rotors avec une taille de clé de 52bits
- cryptographie : technique mathématiques et physiques 
- cryptanalyse: consiste à mesurer ou à casser la sécurité. 
- cryptologie : englobe cryptographie et cryptanalyse

# adversaires
- passif : d'espionner un lien de communication mais pas d'en modifier le contenu. c'est le concept de confidentialité qui est touché. 
- actif: peut espionner, modifier une information. dans ce cas l'authenticité et l'intégrité sont touché. 

- black-box : appelé oracles on a que le strict minimum d'information sur elles 
- grey-box: on a des informations sur leur implantation. 
- white-box : on sait tout de l'environnement. lire écrire dans les mémoire des clefs cryptographiques ou perturber l'implantation de l'algorithme. 
- principe de kerkhoffs: il faut qu'il exige pas le secret, et qu'il puisse sans inconvénient tomber dans les mains ennemies 

# Groupe Additif 

Ensemble G muni d'une opération qui vérifie les propriétés suivantes:

- le résultat de l'opération a,b appartient également à l'ensemble **loi interne**
- Associativité, le déplacement de parenthèse ne change rien 
- l'opération possède un élément neutre 
- il existe un élément symétrique ou inverse
- commutatif ou abélien. on peut intervertir les opérandes 

Un ensemble muni de l'addition modulo m est un groupe abélien 

# Inverse modulaire

Un entier a est inversible modulo m si ax congru à 1 modulo m avec x appartenant à l'ensemble. donc si leur pgcd est égal à 1. 

On peut simplifier une équation de ac congru bc mod m uniquement si c et m sont premiers entre eux. C'est multiplication par l'inverse modulaire. 

![](/media/Partage/HEIG/Tex-Heig/CRY/img/Capture d’écran_2019-10-28_23-10-04.png)

## Indicatrice d'Euler

indique le nombre d'élément premier avec n. 

- si n premier, phi(n) = n-1
- $phi(p^{k}) et k > 1, donc (n-1)*p^{k-1}$
- si phi(m*n) et que pgcd(m,n) = 1. on peut multiplier leurs deux indicatrices respectifs. 

![](/media/Partage/HEIG/Tex-Heig/CRY/img/Capture d’écran_2019-10-28_23-16-44.png)

# Groupe Multiplicatif

Un groupe multiplicatif contient tous les éléments entre 1 et m qui sont premiers avec m. Ce groupe est muni de la multiplication modulo m. C'est un groupe abélien. 

![](/media/Partage/HEIG/Tex-Heig/CRY/img/Capture d’écran_2019-10-28_23-31-24.png)

L'ordre d'un groupe est le nombre d'élément de celui-ci. L'ordre d'un élément est le plus petit exposant tel que $a^i = 1$. Si  ce dernier à la puissance jusqu'à n (n nombre d'élément) donne chaque fois un nombre différent, cet élément sera un générateur. 

l'ordre d'un élément du groupe divive l'ordre du groupe. 

![](/media/Partage/HEIG/Tex-Heig/CRY/img/Capture d’écran_2019-10-28_23-36-19.png)

# Anneaux et corps

## Anneau

Un anneau est un ensemble muni de deux opérations. qui vérifie:

- groupe abélien muni de l'addition
- la multiplication est un loi de composition interne 
- la multiplication est distributive par rapport à l'addition
- la multiplication a un élément neutre 
- si la multiplication est commutative, l'anneau est commutatif. 

![](/media/Partage/HEIG/Tex-Heig/CRY/img/Capture d’écran_2019-10-28_23-41-09.png)

## Corps

Un corps est **un anneau** dans lequel l'ensemble des éléments non nuls forme un groupe. Si un corps est fini, il contient $p^m éléments$ avec p premier. Pour chaque puissance de p, il existe un nombre unique de corps fini. 

**p est appelé la caractéristique du corps** 

# Polynômes sur un corps 

L'anneau est formé des polynômes en x possédant des coefficients dans le corps. Tous les polynômes appartenant à cet anneau sont irréductible. 

Une polynôme de degré 2 et 3 est irréductible seulement s'il ne possède pas de racine. c'est à dire de tester tous les polynôme d'un degré <= au degré du polynôme. 

# Corps de Galois

On utilise comme coefficient tout les éléments modulo p. Pour le construire, on choisit des polynôme de degré $m-1, p^m$ irréductible. 