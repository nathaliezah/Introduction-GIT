<style>
.note {
  min-height: 17px;
  margin: 4px 0 2px;
    margin-bottom: 2px;
  font-size: 12px;
  color: #000000;
  font-size: 14px !important;
  padding: 16px !important;
  margin-bottom: 24px !important;
  border-color: #000000; !important;
  background-color: rgba(84,174,255,0.4); !important;
  border-radius: 4px !important;
  border: 1px solid #000000; !important;
}

img[alt=drawing] { width: 200px; }
</style>

<a id='TP5'></a>
# TP 5 : Comment créer un site Web sur GitHub pages
[Retour à la page principale](../index.md)


---

## Objectifs du TP 5

En plus de toutes les fonctionnalités vues précédemment, avec les **pages GitHub**, GitHub vous permet d'héberger une page Web à partir d'un référentiel. Dans ce TP, nous allons apprendre à :

>1. [Créer un site Web pour un référentiel](#creation-web)
2. [Ajouter du contenu à l'aide de Markdown et HTML](#markdown)
3. [Créer un site Web pour la SAE 2.03](#sae)

   

[Haut de la page](#TP5)

---

<a id='creation-web'></a>
## 1. Créer un site Web pour un référentiel existant 

[Haut de la page](#TP5)

---
<a id='markdown'></a>
## 2. Ajouter du contenu à l'aide de Markdown et HTML 

Vous venez de créer une page web dépourvue de contenu. Dans cette section, nous vous invitons à vous familiariser avec les outils de [markdown](https://www.markdownguide.org) et [html](https://www.w3schools.com/tags/default.asp) pour savoir comment ajouter un tel contenu. Soyez libre, cet exercice n'est pas évalué, il s'agit simplement de jouer et de vous familiariser avec l'environnement.

### Flux de travail

Les [pages Github](https://pages.github.com/) vous permettent de traiter les mises à jour de sites Web comme s'il s'agissait simplement d'un autre référentiel. Après avoir créé le site Web (voir section précédente), vous devez cloner le référentiel localement (```git clone ...```). Vous l'avez probablement déjà cloné sur votre machine locale.

Ce qui est intéressant avec les pages github, c'est que le contenu web est traité dans une branche appelée ```gh-pages```. Cela nous permet de différencier le contenu web (qui sera traité dans la branche ```gh-pages```) de la partie du code du répositoire (qui sera normalement dans la branche principale ```main```).

Pour vous assurer que nous modifions le contenu Web, accédez à votre référentiel local et tapez :

```shell
$ git branch
* gh-pages
  main
```
Si l'étoile est sur la branche ```main```, vous devez faire un ```checkout``` sur la branche ```gh-pages``` avec la commande :

```shell
$ git checkout gh-pages
```

Désormais, toutes les modifications que vous apporterez au fichier ```index.md``` (ou autres), modifieront le contenu web. Pour le mettre à jour sur le site Web, nous le traitons comme un autre référentiel. C'est-à-dire qu'il faut valider les changements, faire un ```commit``` et enfin un ```push```.

### Exemples 

Rien n'empêche tout type de contenu dans cet exercice. Ci-dessous, nous vous montrons quelques exemples. Certains d'entre eux sont insérés grâce au markdown et d'autres grâce au html. Essayez de les reproduire mais n'en restez pas là. Explorez des differents possibilités.

- **Accès à une page web interne**

[Cliquez sur ce lien](./exemple/exemple.md)

- **Accès à une page web externe**

[Cliquez sur ce lien](https://en.wikipedia.org/wiki/Linus_Torvalds)

- **Insertion image interne (stocké dans ./images)**

![drawing](./images/linus.jpeg "Comment avons-nous modifié la taille de l'image ?")

- **Insertion image externe (Passez la souris sur l'image)**

![Image Linus](https://upload.wikimedia.org/wikipedia/commons/e/e8/Lc3_2018_%28263682303%29_%28cropped%29.jpeg "Lorsque vous passez votre souris sur l'image de Linus, ce titre apparaît. Comment se fait ceci?")

- **Insertion de contenu avec css**

<div class="note">

</div>

- **Intégration vidéo youtube**

 <iframe width="420" height="315"
src="https://www.youtube.com/embed/tgbNymZ7vqY">
</iframe> 

[Haut de la page](#TP5)

-----

<a id='sae'></a>
## 3. Créer un site Web pour la SAE 2.03  

La [SAE 2.03](https://di.iut.univ-lehavre.fr/pedago/info1/SAE_2_03/index.xml) porte sur l'installation de services réseaux. En particulier, dans ce SAE, nous apprendrons comment installer ces services avec docker : une plate-forme qui utilisent la virtualisation au niveau du système d'exploitation pour fournir des logiciels dans des packages appelés conteneurs. Pour le moment, nous n'avons pas besoin d'entrer dans les détails. Nous verrons comment docker fonctionne plus tard.

Ce qu'il faut savoir c'est qu'on va faire **le compte-rendu de ce SAE en utilisant les pages github**. Cette section est destinée à créer un site Web que nous devrons compléter au fur et à mesure de notre progression dans la SAE.

<div class="note">
	<h3> Préliminaires </h3>

	<p>
	Avant de commencer à créer le site Web, vous trouverez ci-dessous certains éléments à prendre en compte pour la <b>SAE 2.03 </b>:
	</p>

	<ul>
		<li> <h3>Évaluation de la SAE</h3></li>
		<ul>
			<li> Le SAE consistera en un travail d'équipe et un travail individuel, chacun d'eux valant 50% de la note finale.</li>
			<li><b>Travail en équipe :</b></li>
			<ul>
					<li>La plupart du temps à la SAE vous allez travailler en équipe. Jetez un œil à l'<b>organisation des équipes</b> ci-dessous et commencez à vous organiser. Pour la création du site Web, vous devez avoir l'équipe déjà formée.</li>
					<li>Le travail consistera à réaliser un projet avec différents types d'exercices en docker. Les résultats seront livrés sur github (lors de la SAE on vous expliquera comment faire). </li>
					<li> Le compte-rendu du projet se fera par le site web que nous allons commencer à créer dans cette rubrique.</li>
			</ul>
			<li><b>Travail individuel :</b></li>
			<ul>
					<li>Le travail individuel vous sera proposé le 30 mai et vous aurez l'après-midi pour le compléter.</li>
			</ul>

		</ul>
	</ul>

	<ul>
		<li> <h3>Organisation des équipes</h3></li>
		<ul>
			<li> C'est à vous de vous organiser en équipes.</li>
			<li> Pour la SAE vous allez vous organiser en équipes de minimum 2 personnes et maximum 3.</li>
			<li>Le non respect du nombre de membres de l'équipe entraîne une pénalité dans le grade.</li>
			<li> Commencez à vous organiser dès maintenant. Pour la réalisation du site web sur github, l'équipe doit être organisée.</li>
		</ul>
	</ul>

</div>

[Haut de la page](#TP5)

-----

**Fin du TP 5**
