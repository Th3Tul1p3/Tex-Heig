# Codes Malveillants

## description et classification 

Les codes malveillants rapportent de l'argent en transférant de l'argent depuis des cartes de crédit, en faisant de l'extorsion en chiffrant les données de la victime, en exploitant la messagerie, en utilisant le machine comme bot, en affichant des publicité sur l'écran de la victime et en l'espionnant. 

Les dégâts qui en découlent sont la perte de données, la perte de ressources et de temps, le manque à gagner ou la perte de crédibilité. 

### Un virus

Un virus est un code malveillant qui se propage à l'aide d'un autre programme ou fichier. Il ne peut pas se propager sans cet hôte

#### Fichiers Exécutable 

Infection de fichier exécutable par le virus qui continue à exister même si l'hôte est inactif. 

#### secteur d'amorçage

Les virus qui s'installent sur le secteur d'amorçage peuvent s'introduire dans la mémoire avant que l'OS ne démarre. Il est aussi possible que le secteur d'amorçage d'une clé USB soit infecté. Normalement avant de démarrer l'OS fait une vérification du secteur d'amorçage.

#### Macros

Les macros des fichiers texte peuvent être utilisé pour créer des virus. 

### Vers 

Un vers peut se propager par ses propre moyen en faisant usage des réseaux informatiques. Ils passent d'un ordinateur à un autre en exploitant des failles logiciels ou envoyant des copies d'eux mêmes à d'autre machine via mail.

### Chevaux de Troie 

Les chevaux de Troie sont des programmes à l'apparence utile ou ludique alors qu'il contient des fonctionnalités malveillantes. Elles sont exécutées lors du démarrage du programme. la fonction malveillante de ces derniers est souvent une backdoor, un rootkit ou un spyware. 

### Backdoors 

Programme qui permet de prendre le contrôle de la machine à distance. Elles permettent de copier des fichiers, de lancer des programmes à distance. 

### Spywares et adwares

Le spyware sont des logiciels espions qui recueille des informations sur la machine infectée et qui les transmet à un serveur central et cela dans le but de lui adresser des pub ciblée. les adwares sont les logiciels qui affichent cette publicité. 

### rootkits

Ensemble d'outils pour cacher la présence d'un logiciel malveillant sur une machine. à la base ce sont des commandes UNIX. l'objectif d'un rootkit est de cacher la présence d'une backdoor ou d'un spyware. 

### Rançongiciels et cryptovirus

Le ransonware est un logiciel qui essaie de forcer sa victime à verser une rançon en l'empêchant de lancer sa session. Les versions plus avancées cryptent les données de l'utilisateur.

### polymorphisme

le polymorphisme permet aux virus de changer leurs caractéristiques à chaque infection. le but étant de changer l'apparence du code sans changer sa sémantique. 

## Protections

### Antivirus

Ils utilisent la liste de tous les codes malveillant connus et cherchent leurs signatures. Dans un deuxième temps ils peuvent l'analyser statiquement pour voir si le programme fait des opérations douteuses. Et dans un troisième temps, ils peuvent simuler un démarrage pour analyser le comportement.  

