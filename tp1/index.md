# TP 1 : Travailler sur un répertoire local  {#TP1}
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

## 1. Configuration de GIT {#configuration}

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

>**Exercices : **
> 1. Suivez les étapes précédentes et configurez votre nom, votre adresse e-mail et votre éditeur de texte dans git. 
> 2.Tapez la commande `git config --list` et assurez-vous que toutes les informations fournis sont correctes.
> 3. Afin de vérifier que votre nom est correct, tapez  `git config user.name`
> 4. Faire pareil pour votre email, tapez  `git config user.email`

## 2. Création d'un dépôt git sur une machine locale {#gitinit}

Une fois git correctement configuré, nous allons procéder sans plus tarder à créer notre premier répertoire dont nous allons gérer les changements à l'aide de git. 












