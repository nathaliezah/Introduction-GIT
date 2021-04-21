# TP 1 : Travailler sur un répertoire local  {#TP1}
<p style="text-align: left;">
	<a href="../index.md">Retour à la page principale</a>
</p>
Pour notre premier contact avec git, nous n'aurons besoin que d'un éditeur de texte et d'une installation fonctionnelle de git sur la console. Dans la dernière partie de ce TP, nous commencerons à gérer un petit programme Java, il est donc également pratique d'avoir une machine virtuelle Java installée.
 
 La durée de ce travail pratique sera d'une heure à une heure et demie. 


## Objectifs du TP 1

Le but de ce premier TP est de commencer à se familiariser avec git. Plus précisément, nous allons apprendre: 

>1. [Configuration de GIT](#configuration)
2. [Création d'un dépôt git sur une machine locale](#gitinit)
3. Création d'un fichier texte README.md au format markdown où nous allons sauvegarder notre compte-rendu
   3.1. Gérer les différentes modifications du fichier README.md 
   3.2. Différencier  3 états / 3 zones / 3 actions
4. Gestion de version d'un programme Java 
   4.1. Cycle de vie git (status, add, commit, log, tag)
   4.2. Creation du fichier `.gitignore`

---

## 1. Configuration de GIT {#configuration}

Git est livré avec un outil appelé `git config` qui vous permet d'obtenir et de définir des variables de configuration qui contrôlent tous les aspects de l'apparence et du fonctionnement de git. 

<mark style="background-color:lightblue;color:black">Pour vérifier les paramètres de configuration actuels de git sur votre machine, ouvrez un terminal et tapez : </mark> 

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

### Votre identit
Afin de configurer correctement votre git, commençons par définir votre identité 

>```
>$ ping -c 4 host
>```


## 2. Création d'un dépôt git sur une machine locale {#gitinit}

