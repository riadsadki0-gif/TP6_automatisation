# TP No 6 -Installation et mise à jour de logiciels Sauvegardes distantes
**Module :** R405 - Automatisation des tâches d'administration
**Auteur :** Riad Sadki
## Introduction
Ce TP a pour objectif de réviser les commandes fondamentales de l'administration système sous UNIX/Linux. À travers une série d'exercices pratiques, nous abordons la gestion des paquets logiciels (installation et dépendances), ainsi que la surveillance des ressources matérielles, notamment l'occupation de l'espace disque. L'ensemble des manipulations est documenté ici pour illustrer la maîtrise des commandes de base du shell Bash et la compréhension de l'arborescence Linux.
## Exercice 1
### 1- Combien de paquets sont-ils installés sur votre système ?
Afin de connaitre le nombre de paquets installés sur mon système j'utilise la commande:
```bash
dpkg -l | wc -l
```
Cette commande permet de lister le nombre de paquets installés et de sortir ce résultat sous forme de nombre de lignes qui correspond donc aux nombres de paquets installés sur le système.

### Résultat
Cette commande affiche 1749, j'ai donc 1749 paquets installés sur mon système.

### 2- Votre systeme est-il à jour ? Si non, mettez-le à jour. Listez les paquets mis à jour dans votre compte rendu.

Pour vérifier si le système Debian est à jour, j’ai d’abord mis à jour la liste des paquets disponibles avec la commande suivante :

```bash
sudo apt update
```
Ensuite, pour installer les mises à jour disponibles, j’ai utilisé la commande suivante :
```bash
sudo apt upgrade
```
### Explication

Cette commande permet d'installer les nouvelles versions des paquets déjà installés sur le système.

### Résultat

Après l'exécution de la commande, les paquets suivants ont été mis à jour :

```bash
Paramétrage de libreoffice-core (1:7.0.4-4+deb11u13) ...
Paramétrage de libridl-java (1:7.0.4-4+deb11u13) ...
Paramétrage de libreoffice-math (1:7.0.4-4+deb11u13) ...
Paramétrage de libreoffice-gtk3 (1:7.0.4-4+deb11u13) ...
Paramétrage de libreoffice-l10n-fr (1:7.0.4-4+deb11u13) ...
Paramétrage de libreoffice-draw (1:7.0.4-4+deb11u13) ...
Paramétrage de yelp (3.38.3-1+deb11u1) ...
Paramétrage de libreoffice-help-common (1:7.0.4-4+deb11u13) ...
Paramétrage de atril (1.24.0-1+deb11u1) ...
Paramétrage de libreoffice-impress (1:7.0.4-4+deb11u13) ...
```bash

### 3. Quel paquet (non installé) fournit le logiciel LibreOffice Writer ?

Pour rechercher quel paquet fournit le logiciel **LibreOffice Writer**, j’ai utilisé la commande suivante :

```bash
apt cache search libreoffice-writer
```
### Résultat obtenu

On obtiens plusieurs fichiers libreoffice. Lorsque je vais dans mon bureau je remarque que libreOffice est déjà installé , cela s 'explique par le fait que la date d'édition du tp est plus ancienne que l'image utilisée actuellement.

### 4. Quels sont les dépendances de ce paquet ?

Pour afficher les informations du paquet **libreoffice-writer**, j’ai utilisé la commande suivante :

```bash
apt-cache show libreoffice-writer
```
### Explication

apt-cache show : permet d’afficher les informations détaillées d’un paquet.

libreoffice-writer : paquet dont on souhaite consulter les informations.

### Résultat obtenu

Les dépendances du paquet apparaissent dans la ligne Depends :
```bash
Depends: libreoffice-base-core (= 1:7.0.4-4+deb11u13), libreoffice-common (>= 1:7.0.0~alpha~), libreoffice-core (= 1:7.0.4-4+deb11u13), ucf (>= 0.8), libabw-0.1-1, libc6 (>= 2.29), libe-book-0.1-1, libepubgen-0.1-1, libetonyek-0.1-1, libgcc-s1 (>= 3.0), libicu67 (>= 67.1-1~), libmwaw-0.3-3, libodfgen-0.1-1, librevenge-0.0-0, libstaroffice-0.0-0, libstdc++6 (>= 9), libuno-cppu3 (>= 4.4.0~alpha), libuno-cppuhelpergcc3-3 (>= 5.3.0~alpha), libuno-sal3 (>= 5.3.0~alpha), libuno-salhelpergcc3-3 (>= 1.4.0), libwpd-0.10-10, libwpg-0.3-3, libwps-0.4-4, libxml2 (>= 2.8), uno-libs-private, zlib1g (>= 1:1.1.4)

```

## Conclusion
Le paquet libreoffice-writer dépend de nombreux autres paquets correspondant aux bibliothèques et composants nécessaires au fonctionnement du logiciel.

### 5- Installer ce logiciel. Quels menus de votre environnement sont-ils modifiés ?

Comme expliqué précédemment les logiciels libre office sont déja présents sur notre machine.

### EXERCICE 2 - Surveillance de l’espace disque

### Question 1 : Quel est l’espace disponible sur le système de fichier qui contient votre répertoire de connexion ?

Commande à exécuter :
```Bash

df -h ~
```
### Résultat obtenu :
```Bash
Sys. de fichiers Taille Utilisé Dispo Uti% Monté sur
/dev/nvme0n1p2     123G    7,1G  110G   7% /
```
### Réponse détaillée :
L'espace disponible sur le système de fichiers contenant mon répertoire de connexion est de 110 Go (indiqué dans la colonne Dispo).

### Analyse du résultat :
Le système de fichiers est monté sur la racine (/), ce qui signifie que mon répertoire personnel (~) partage la partition principale du système.

        Le disque total fait 123 Go.

        Seulement 7% de l'espace est actuellement utilisé.

### 2- Quel espace occupe votre répertoire de connexion ? Et le répertoire /usr ?

### Commande à exécuter
#### Pour le répertoire personnel
 ```Bash
  du -sh ~
```
#### Pour le répertoire /usr
### Explication des options :

    ~ : Est un raccourci vers mon répertoire personnel 

    /usr : Est le répertoire système contenant la majorité des programmes et fichiers d'aide.

    Attention : Le calcul pour /usr peut prendre quelques secondes car il contient énormément de fichiers.

  ### Résultat observé
  #### Répertoire personnel:
   ```Bash
  du -sh ~
215M	/home/riad
 ```
#### répertoire /usr
```Bash
5,9G	/usr
   ```
Le répertoire /usr occupe donc beaucoup plus d'espace que mon répertoire personnel.

### Question 3 : Quel est le plus gros fichier dans /usr/bin ?

Pour trouver le fichier le plus volumineux, nous devons lister les fichiers du répertoire /usr/bin, afficher leur taille, puis les trier par ordre décroissant.

Commande à exécuter :
  ```Bash
du -h /usr/bin/* | sort -rh | head -n 1
  ```
### Explication
du -h /usr/bin/* : Calcule la taille de chaque élément contenu dans le dossier, mais pas du dossier lui-même.

sort -rh : Trie par taille.

head -n 1 : Affiche le premier (le plus gros).

### Résultat obtenu :
  ```Bash
98M    /usr/bin/dockerd
  ```
Le fichier le plus volumineux présent dans le répertoire /usr/bin est dockerd, avec une taille de 98 Mo.


## EXERCICE 3 - Sauvegardes de fichiers sur une machine distante

### Question 1 : Copie simple de /etc/passwd

Action : Copier le fichier en tant qu'utilisateur ordinaire dans le répertoire de connexion (~).

Commandes à exécuter :
```Bash
cp /etc/passwd ~
ls -l /etc/passwd ~/passwd
```
### Résultat obtenu :

-rw-r--r-- 1 root root 2151 11 mars 13:23 /etc/passwd
-rw-r--r-- 1 riad riad 2151 11 mars 14:46 /home/riad/passwd

### Analyse :
Les permissions, le propriétaire et les dates de modification ne sont pas identiques :

Propriétaire et Groupe : L'original appartient à root, alors que la copie appartient à l'utilisateur riad.

Date de modification : L'original date de 13:23, alors que la copie a pris la date et l'heure du moment de l'exécution (14:46).

Permissions : Elles sont restées identiques (-rw-r--r--) dans ce cas précis.

### 2- Copie avec cp -p

Question : Même question en utilisant cp -p.

### Commande exécutée :
```Bash

cp -p /etc/passwd ~/passwd
ls -l /etc/passwd ~/passwd
```
### Analyse du résultat :

Dates de modification : Elles sont maintenant identiques (13:23). L'option -p a réussi à préserver l'horodatage original du fichier.

Propriétaire : Le propriétaire est resté riad pour la copie. C'est normal : un utilisateur ordinaire ne peut pas créer un fichier qui appartient à root.

Permissions : Elles sont identiques (rw-r--r--).

### 3- Copie à l'identique d'un répertoire (et ses sous-répertoires)

Question : Quelles option(s) de cp utiliser ?

Réponse :
Il faut utiliser l'option -a (archive).

#### Explication :
L'option -a est un raccourci qui combine plusieurs options :

    -R : pour copier récursivement les dossiers.

    --preserve=all : pour garder les droits, les dates et, si on est root, les propriétaires.

    -d : pour préserver les liens symboliques.

### 2- Rappels sur les connexions SSH :
1. Demandez à votre voisin de créeer un nouveau compte utilisateur sur sa machine
et de vous fournir les identifiants (nom, mot de passe), ainsi que l’adresse IP de sa machine. Vous utiliserez ce compte pour vous connecter sur sa machine, que l’on dénommera « machine2 » dans la suite de cet exercice.

Voici les differentes infos concernant ma machine voisine:
login:user
 mdp:blop
ip: 192.168.52.10

Connectez-vous sur la machine2 depuis votre machine, en utilisant la commande
ssh. Qu’observez-vous ? Comment être sur que le shell est bien sur la machine
voisine ?

#### Commande utilisé
Je commence par me connecter sur la machine voisine à l'aie de la commande suivante:

```Bash
ssh user@192.168.52.10
```
puis, j'insère le mot de passe donné par mon vosin.

#### Observation
Dès que j'ai validé la connexion, j'ai vu apparaître la ligne ```Bash Last login: Mon Jan 31 13:55:40 2022 from 192.168.53.2```. Ce message est la preuve que je viens de pénétrer sur un système distant qui garde une trace de mes passages.

Ensuite, je remarque que mon invite de commande (le prompt) a radicalement changé : elle affiche désormais ```Bash user@p20210:~$ ```. 
Cela m'indique deux choses fondamentales :

    L'utilisateur : Je n'agis plus sous mon identité locale, mais en tant que user.

    L'hôte : Le nom de la machine sur laquelle je travaille est maintenant p20210

#### Comment être sûr que le shell est bien sur la machine voisine ?

Comme je l'ai vu dans mon prompt précédent (user@p20210), la machine s'appelle p20210. Pour confirmer que ce n'est pas juste un affichage cosmétique, je demande au système son nom officiel.
```Bash
user@p20210:~$ hostname
```
#### Résultat observé
```Bash
p20210
```

### 3. Authentification par clés cryptographiques
#### Génération de la clé avec ssh-keygen

Pour éviter de saisir mon mot de passe à chaque connexion, je crée une identité numérique. J'utilise la commande suivante :
```Bash
ssh-keygen -t dsa
```
Ce que j'ai fait :  J'ai choisi le type DSA (comme demandé).
J'ai appuyé sur Entrée pour l'emplacement par défaut (/home/user/.ssh/id_dsa).
J'ai laissé la passphrase vide (deux fois Entrée) pour que la connexion soit totalement automatique.

Le résultat : 
```Bash
+---[RSA 3072]----+
|B.*o   .=.o      |
|*E . . . B       |
|+o    + + +      |
|  o  o * =       |
|  o.= o S        |
|  .O o   .       |
|  =o..           |
| o.++..          |
|ooo+=o.          |
+----[SHA256]-----+
```

Le système a généré une "empreinte digitale" (fingerprint) et une image aléatoire (randomart) qui confirment la création de mes clés.

2. Distinction entre Clé Publique et Clé Privée

Après la commande, je remarque que deux fichiers ont été créés dans mon dossier .ssh :

id_dsa (Clé privée) : C'est mon secret. Elle reste sur ma machine. Elle ne doit jamais être partagée. C'est elle qui prouve mon identité.

id_dsa.pub (Clé publique) : C'est le fichier d'extension .pub. C'est elle que je vais copier sur la machine voisine. Elle sert de "serrure" que seule ma clé privée peut ouvrir.

#### 3. Analyse des octets de la clé publique

3. Les octets de ma clé publique

Pour répondre à la question, j'affiche le contenu de id_dsa.pub :
```Bash
cat ~/.ssh/id_dsa.pub
 ```
Les 4 premiers octets : Ce sont les 4 premiers caractères qui ouvrent la ligne, soit ssh-.

Les 4 derniers octets : Ce sont les 4 derniers caractères de la ligne complète (incluant le commentaire de fin). D'après l'affichage de mon terminal, cela correspond à la fin du nom de ma machine, soit 0209 (les derniers caractères de riad@p20209).

#### Mise en place :
Pour terminer, j'ai transféré cette clé vers la machine voisine avec ```Bash ssh-copy-id user@192.168.52.10 ```
Désormais, mon identité est reconnue et je peux me connecter à distance sans avoir à saisir de mot de passe.
Je peux ainsi me connecter à la machine distante sans mot de passe.


### question 4
Une fois la commande ssh id vu ci dessous exécuté je peux me connecter pour tester cela je me reconnecte en ssh:
```Bash
ssh user@192.168.52.10
```
Le système ne me demande pas de mot de passe et se connecte automatiquement, cela signifue que la commande a bien marché.

## 3- Copies distantes avec SSH

Je commence par créer un répertoire R405 à l'aide de la commande suivante:
```Bash
mkdir R405
```
puis je réalise une copie de ce dossier en ssh à l'aide de la commande suivante:
```Bash
scp -rp R405 user@192.168.52.10:
```Bash

Une fois cela fait, je me connecte en ssh sur la machine voisine puis,je réalise un ls:
```Bash
ssh user@192.168.52.10
```
```Bash
ls
```
Résultat obtenu
```Bash
user@p20210:~$ ls
Bureau  Documents  GNS3  Public  R405  Téléchargements  trash

```
Le fichier a bien été copié sur la machine distante.

## 4- Copies distantes incrémentales avec rsync

### Objectif :
Mettre en place une synchronisation performante entre le répertoire local et la machine distante en utilisant le protocole rsync. Contrairement à scp, rsync permet de ne transférer que les modifications et de maintenir une copie miroir exacte.
Commande exécutée :
```Bash
rsync -vaze "ssh" --delete R405 user@192.168.52.10:~
```
### Résultat :
Le transfert s'effectue sans demande de mot de passe grâce à la configuration SSH précédente. Le message ```Bash sending incremental file list ```confirme que rsync compare les deux répertoires avant d'envoyer uniquement les données nécessaires. Le répertoire R405 est désormais synchronisé sur la machine 192.168.52.10.

### 1. Créer un répertoire contenant quelques fichiers et sous-répertoires ;

##### Objectif : Préparer un répertoire source structuré avec différents types d'éléments (fichiers et sous-dossiers) pour tester la robustesse de la synchronisation.

#### Commandes exécutées :
```Bash
mkdir -p R405/scripts R405/docs
touch R405/notes.txt R405/scripts/run.sh R405/docs/rapport.pdf
 ```
mkdir -p : Crée le répertoire parent R405 ainsi que les sous-répertoires scripts et docs en une seule fois.

touch : Génère trois fichiers vides répartis dans l'arborescence pour simuler du contenu.  

### Vérification
résultat observe:
```Bash
ls -R R405
R405:
docs  notes.txt  scripts

R405/docs:
rapport.pdf

R405/scripts:
run.sh
```
#### Copier ce répertoire sur machine2 avec la commande rsync précédente. Qu’observez-vous ? Vérifiez que les fichiers sont bien copiés.

Je commence par réalisé la commande vu précédemment:
```Bash
rsync -vaze "ssh" --delete R405 user@192.168.52.10:~
```
Cette commande permet de mettre à jour automatiquement le dossier R405

#### Vérification
Je commence par me connecter en ssh sur la machine distante:
```Bash
ssh user@192.168.52.10
```
Ensuite je vérifie le bon fonctionnnement de la commande:
```Bash
ls -R R405
```
J'obtiens le résultat suivant:
```Bash
ls -R R405
R405:
docs  notes.txt  scripts

R405/docs:
rapport.pdf

R405/scripts:
run.sh
```
Ce résultat confirme le bon fonctionnement de scp , le dossier R405 a bien été mis à jour.

### Modifiez un fichier sur votre machine. Relancez la même commande rsync. Qu’observez-vous

Je commence par modifier le contenu de notes.txt:
```Bash
nano notes.txt
hello user
```
Ensuite je relance la commande rsync vu précedemment afin de mettre à jour le dossier sur la machine voisine:
```Bash
riad@p20209:~$ rsync -vaze "ssh" --delete R405 user@192.168.52.10:~
```
Enfin je me connecte en ssh sur la machine voisine et une fois positionné dans le dossier R405 je visualise le contenu du fichier notes.txt à l'aide de la commande suivante:
```Bash
user@p20210:~/R405$ cat notes.txt 
hello user
```
Le contenu a bien été modifié ce qui signifie que rsync fonctionne.

### 4. Supprimez un fichier (rm) de votre machine. Relancez rsync. Qu’observez-vous ?

Je commence par supprimer le fichier notes.txt sur ma machine (riad):
```Bash
cd R405
rm notes.txt
```
Une fois cela réalisé je met à jour rsync:
```Bash
rsync -vaze "ssh" --delete R405 user@192.168.52.10:~
```
puis je me connecte en ssh sur la machine 2 et je vérifie le contenu du dossier R405:
```Bash
user@p20210:~$ cd R405/
user@p20210:~/R405$ ls
docs  scripts
```
Le fichier notes.txt a bien été supprimé, rsync fonctionne.

## 5- Automatisation de la sauvegarde

### 1. Créez un script shell qui sauvegarde l’un de vos répertoires vers l’autre machine(il suffit de placer la commande précédente dans un script)

Je commence par créé un fichierscript.sh dans le sous répertoire script de r405:
```Bash
user@p20210:~/R405$ cd scripts/
user@p20210:~/R405/scripts$ nano script.sh
```
Ensuite dans ce fichier je met la commande rsync vu précédemment ainsi que le shebang:
```Bash
!/bin/bash
rsync -vaze "ssh" --delete R405 user@192.168.52.10:~
```
### 2. Faire en sorte que ce script soit lancé automatiquement chaque minute (à l’aide
de cron, que vous avez déjà étudié).

Pour réaliser cela j ai modifier le fichier crontab en rajoutant cette ligne à la fin du fichier: 
```Bash
#!/bin/bash
* * * * * /bin/bash /home/riad/R405/scripts/script.sh >> /home/riad/rsync_log.txt 2>&1
```
#### Explication de la syntaxe

 * * * * * /bin/bash /home/riad/R405/scripts/script.sh >> /home/riad/rsync_log.txt 2>&1

  * * * * * : Cette syntaxe programme l'exécution automatique du script toutes les minutes, sans interruption.

    /bin/bash ... : On appelle le script par son chemin absolu pour garantir son lancement correct par le système, peu importe le dossier courant.

    >> ... 2>&1 : Cette redirection fusionne les succès et les erreurs dans un fichier log unique, permettant de garder un historique complet des transferts pour le débogage.

 
### 3. Indiquez comment vous vérifiez que cela fonctionne.

Afin de vérifier que cela fonctionne je regarde le contenu du fichier log vers lequel nous avons mis la redirection:
```Bash
cat /home/riad/rsync_log.txt
```
Les logs nous indique que le script fonctionne.

### 4. D’après-vous, quelles genre d’erreurs peuvent se produire durant l’exécution duscript de sauvegarde ? En général, un script de ce genre n’est pas exécuté chaque minute, mais plutôt chaque nuit : que doit faire l’administrateur système pour s’assurer que les sauvegardes sont correctes

Les erreurs peuvent venir d'une coupure réseau, d'un disque plein ou d'un problème de permissions sur les fichiers. Pour s'assurer que tout est correct, l'administrateur doit vérifier régulièrement les fichiers logs et tester la restauration des données pour confirmer qu'elles ne sont pas corrompues.


## Conclusion
Ce TP m'a permis de maîtriser la synchronisation de données entre deux serveurs grâce à rsync et d'automatiser le processus avec cron. En mettant en place une authentification par clés SSH et une journalisation des logs, j'ai créé un système de sauvegarde autonome, sécurisé et facile à surveiller pour un administrateur.
