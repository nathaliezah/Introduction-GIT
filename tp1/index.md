<a id='TP1'></a>
# TP 1 : Travailler sur un répertoire local 
[Retour à la page principale](../index.md)

Pour notre premier contact avec git, nous n'aurons besoin que d'un éditeur de texte et d'une installation fonctionnelle de git sur la console. Il ne sera pas nécessaire d'avoir un dépôt distant (comme github) parce que nous ferons tout le travail sur un répertoire locale de la machine. Dans la dernière partie de ce TP, nous commencerons à gérer un petit programme Java, il est donc également pratique d'avoir une machine virtuelle Java installée.
 
 La durée de ce travail pratique sera d'une heure à une heure et demie. 


## Objectifs du TP 1

Le but de ce premier TP est de commencer à se familiariser avec git. Plus précisément, nous allons apprendre: 

>1. [Configuration de GIT](#configuration)
2. [Création d'un dépôt git sur une machine locale](#gitinit)
3. Création d'un fichier texte README.md au format markdown où nous allons sauvegarder notre compte-rendu
   * Gérer les différentes modifications du fichier README.md 
   * Différencier  3 états / 3 zones / 3 actions
4. Gestion de version d'un programme Java 
   * Cycle de vie git (status, add, commit, log, tag)
   * Creation du fichier `.gitignore`

---

<a id='configuration'></a>
## 1. Configuration de GIT 

Git est livré avec un outil appelé `git config` qui vous permet d'obtenir et de définir des variables de configuration qui contrôlent tous les aspects de l'apparence et du fonctionnement de git. 

Pour vérifier les paramètres de configuration actuels de git sur votre machine, ouvrez un terminal et tapez : 

```shell
$:> git config --list
```
ce qui devrait afficher des informations similaires à ce qui suit :

```shell
user.name=...
user.email=...
color.status=auto
color.branch=auto
color.interactive=auto
color.diff=auto
push.default=matching
merge.tool=...
```

### 1.1. Votre identité

La première chose à faire lorsque vous installez git est de définir votre nom d'utilisateur et votre adresse e-mail. Ceci est important car chaque commit Git utilise ces informations, et elles sont immuablement intégrées dans les commits que vous commencez à créer: 

```shell
$:> git config --global user.name "John Doe"
$:> git config --global user.email johndoe@example.com
```
Vous ne devez le faire qu'une seule fois si vous passez l'option `--global`, car alors git utilisera toujours ces informations pour tout ce que vous faites sur ce système.

### 1.2. Votre editeur

Maintenant que votre identité est configurée, vous pouvez configurer l'éditeur de texte par défaut qui sera utilisé lorsque git a besoin de vous pour taper un message :

```shell
$:> git config --global core.editor XXXX
```
où **XXXX** correspond au nom de votre éditeur de texte préféré, par exemple, vim, emacs, gedit, ... 

<!--### 1.3. Votre nom de branch par défaut

Par défaut, git créera une branche appelée `master` lorsque vous créez un nouveau dépôt avec `git init` (nous allons voir les branches et la création d'un dépôt plus tard). À partir de la version 2.28 de git, vous pouvez définir un nom différent pour la branche initiale.

Pour définir `main` comme nom de branche par défaut, procédez comme suit : 

```shell
$:> git config --global init.defaultBranch main
```
-->

### Exercices
> 1. Suivez les étapes précédentes et configurez votre nom, votre adresse e-mail et votre éditeur de texte dans git. 
2. Tapez la commande `git config --list` et assurez-vous que toutes les informations fournis sont correctes.
3. Afin de vérifier que votre nom est correct, tapez  `git config user.name`
4. Faire pareil pour votre email, tapez  `git config user.email`

[Haut de la page](#TP1)

--------

<a id='gitinit'></a>
## 2. Création d'un dépôt git sur une machine locale

Une fois git correctement configuré, nous allons procéder sans plus tarder à créer notre premier répertoire dont nous allons gérer les changements à l'aide de git. La première chose que nous allons décider est la structure de répertoires que nous allons utiliser pour ce cours. 

Accédez à votre répertoire de travail (quel qu'il soit) et créez un répertoire `courseGIT` puis le répertoire `tp1`, de sorte que la structure du répertoire soit la suivante: 

```shell
$:> tree courseGIT
courseGIT/
└── tp1
```
Allez jusqu'au répertoire tp1, de sorte que la commande `pwd` affiche le résultat suivant :

```shell
$:> pwd
/.../courseGIT/tp1 
```

Tapez la commande `ls -a` et voir que le résultat est le suivant :

```shell
$:> ls -a
. ..
```

<mark> Prêt à créer votre premier dépôt git ? </mark> **Tapez :**
```shell
$:> git init
```
Vous devriez obtenir une réponse de type :

```shell
Initialized empty Git repository in /.../courseGIT/tp1/.git/
```
Ce message indique que votre répertoire `tp1` sera désormais géré par git. En particulier, le répertoire `.git` (qui est caché) contiendra la base de données avec toutes les modifications que nous apportons au répertoire `tp1`. <mark> Attention : </mark> nous n'accéderons jamais directement au répertoire `.git` mais via des commandes git. Pour vérifier que le répertoire existe : 

```shell
$:> ls -a
.  ..  .git
```

### Exercices
> 1. Suivez les étapes précédentes et assurez-vous que le répertoire `.git` a été bien crée.

**Félicitations, vous venez de créer votre premier dépôt git !!**

[Haut de la page](#TP1)

--------

### 3. Création d'un fichier texte README.md 

Nous allons créer maintenant un fichier texte README.md (au format markdown) dans le repertoire `tp1` où nous allons sauvegarder notre compte-rendu. Utilisez votre éditeur de texte préféré pour cela.


```shell
$:> git status
On branch master

Initial commit

nothing to commit (create/copy files and use "git add" to track)
```








