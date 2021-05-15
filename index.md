# Introduction à la gestion de version à l'aide de git {#introduction_main}

<mark style="background-color:yellow;text-align:center">
	<b>
	Prenez 10 minutes à lire ce introduction
	</b>
</mark>

[Git](https://git-scm.com/) est un outil de **gestion de version distribué open source** initialement conçu par [Linus Torvalds](https://fr.wikipedia.org/wiki/Linus_Torvalds) pour la maintenance du noyau Linux. Bien que nous ne devons pas oublier qu'il existe d'autres systèmes de gestion de version (par exemple, subversion ou mercurial), git est aujourd'hui l'outil de gestion de version le plus utilisé. Ce cours ne prétend pas entrer dans les fondements théoriques de git ou dans des notions avancées: il s'agit essentiellement d'une introduction pratique dans laquelle dans 10 minutes nous serons en mesure de créer notre premier dépôt git. 

Le lecteur intéressé peut se référer à des manuels plus complets sur git, comme le livre [Pro Git book](http://git-scm.com/book) par Scott Chacon ([CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/)) ou [ce cours en ligne](https://pigne.org/teaching/general/lecture/Gestion-de-version-travail-en-equipe) ([CC BY-NC-SA 4.0](http://creativecommons.org/licenses/by-nc-sa/4.0/)) dont ce cours est en partie inspiré. 


## Exigences d'installation
Pour ce cours pratique, <mark style="background-color:gray;color:white"> <b> nous allons travailler exclusivement en utilisant la ligne de commande</b></mark>. De nos jours, il existe de nombreux environnements visuels pour travailler avec git, ainsi que des environnements intégrés dans différents IDE. Oubliez-les. Une fois que vous aurez appris à utiliser git sur la ligne de commande, vous n'aurez aucun problème à utiliser un environnement graphique. A l'inverse, ce n'est pas si facile.

Plus précisément, nous aurons besoin de : 

>1. Un éditeur de texte.
2. Une installation git (déjà installé sur les machines de l'IUT):
   * Vous pouvez télécharger git [ici pour différentes plates-formes](https://git-scm.com/downloads)
   * Installation de git sur ubuntu : `sudo apt-get update; sudo apt-get install git `
   * [Installation de git sur windows 10](https://www.develves.net/blogs/asd/articles/using-git-with-powershell-on-windows-10/#installing-git)
3. Une machine virtuelle Java[^1]
4. Pour le [TP 2](./tp2/index.md) et [TP 3](./tp3/index.md) une compte sur [github](https://github.com/)

[^1]: La machine virtuelle Java n'est pas nécessaire pour git mais pour les exercices proposés.

## Travaux pratiques 

Ce cours d'[introduction à la gestion des versions à l'aide de GIT](#introduction_main)  est divisé en trois séances pratiques :

>* [TP 1 : Travailler sur un répertoire local ](./tp1/index.md)
>* [TP 2 : Travailler en autonomie sur un depôt github distant ](./tp2/index.md) 
>* [TP 3 : Travailler en équipe sur un depôt github distant ](./tp3/index.md)


## Liens d'aide pour le cours 

### [Feuille de triche git](https://education.github.com/git-cheat-sheet-education.pdf)

### [Feuille de triche markdown](https://www.markdownguide.org/cheat-sheet)



Markdown est une syntaxe légère et facile à utiliser pour créer du texte formaté à l'aide d'un éditeur de texte. Il est couramment utilisé dans git, entre autres, pour créer des documents tels que des fichiers README ou pour déployer facilement des documents tels que [ce site web](#introduction_main) qui est écrit en utilisant markdown et [github pages](https://pages.github.com/). Vous pouvez trouver ci-dessous les principales conventions pour la syntaxe.

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List


**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```
Pour plus de détails consultez [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

