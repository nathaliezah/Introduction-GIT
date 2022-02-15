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
</style>

<a id='TP4'></a>
# TP 4 : Pull request et résolution de conflits  
[Retour à la page principale](../index.md)


---

## Objectifs du TP 4

L'objectif de ce dernier TP est d'apprendre certaines fonctionnalités de git que vous allez utiliser de manière récurrente : l'option pull request et la résolution des conflits. 

>1. [Créer un compte sur github](#pull-request)
2. [Ajouter une nouvelle clé SSH à votre compte GitHub](#cle)
3. [Pousser un dépôt existant depuis la ligne de commande](#pushremote)
4. [Séquence de travail avec un dépôt distant](#sequence)
5. [Cloner un dépôt distant sur notre machine locale](#clone)
   

[Haut de la page](#TP4)

---

<a id='creation-conflits'></a>
## 1. Créer un conflit  


Allez sur github et créer un repositoire avec le fichier **README.md** suivant :

```shell
**README.md**
# test-conflict

Normalement, dans le développement réel d'une application, des conflits se produiront spontanément. Cependant, pour notre formation, nous allons intentionnellement forcer un conflit dans git.

Dans la plupart des cas, git est capable de mélanger les modifications que différents utilisateurs apportent à différents fichiers, mais si deux utilisateurs apportent des modifications au même fichier localement (surtout si la modification se trouve sur la même ligne), git ne pourra pas savoir quelle modification est la bonne. Produisons un tel conflit :

- Voici une ligne du README.md avec dex (deux) fotes de frape (fautes de frappe) à corriger

- **Athos** corrigera la première faute de frappe (deux) et **Porthos** la seconde (fautes de frappe) 

- Chacun va faire un clone du projet et corriger sa faute de frappe localement, puis essayer de faire un `push` du changement. 

```

Après le push de Athos, le message suivant signale un conflit :

```shell
From github.com:juanluck/test-conflict
   1094a44..dcb1032  main       -> origin/main
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

Si nous essayons de faire un git pull, nous aurons également le message suivant :

```shell
error: Pulling is not possible because you have unmerged files.
hint: Fix them up in the work tree, and then use 'git add/rm <file>'
hint: as appropriate to mark resolution and make a commit.
fatal: Exiting because of an unresolved conflict.
```


---
<a id='cle'></a>
## 2. Résoudre un conflit (avec `git diff`) 

git diff

```shell
diff --cc README.md                                                                                                                                        
index 12d78ec,9c2e1f1..0000000
--- a/README.md
+++ b/README.md
  
++<<<<<<< HEAD
 +- Voici une ligne du README.md avec deux fotes de frape (fautes de frappe) à corriger
++=======
+ - Voici une ligne du README.md avec dex (deux) fautes de frappe à corriger
++>>>>>>> dcb10325482119cf4001d04049e285ea7fe2274a
  
```
Voici, la ligne `<<<<<<< HEAD` nous indique la ligne de notre référentiel local qui diffère du référentiel distant. Ensuite, après `=======` et jusqu'à `>>>>>>` la ligne telle qu'elle se trouve dans le référentiel distant. 

Si nous éditons le fichier README.md avec n'importe quel éditeur de texte, nous verrons que ces lignes apparaissent également marquées avec la même syntaxe. 

- Modifiez le fichier README.md avec votre éditeur de texte préféré et résolvez le conflit afin que le contenu : 

```shell
<<<<<<< HEAD
- Voici une ligne du README.md avec deux fotes de frape (fautes de frappe) à corriger
=======
- Voici une ligne du README.md avec dex (deux) fautes de frappe à corriger
>>>>>>> dcb10325482119cf4001d04049e285ea7fe2274a
```

- soit modifié à la ligne suivante  : 

```shell
- Voici une ligne du README.md avec deux fautes de frappe à corriger
```
- Enregistrez ensuite le fichier et exécutez les commandes appropriées pour mettre à jour le référentiel local et distant :

```shell
$ git status
$ git add README.md
$ git commit -m "Conflit README résolu"
$ git push
```

* **Félicitations !!** Vous venez de résoudre un conflit dans git. Bien que git dispose encore de nombreux outils plus avancés pour gérer le flux de travail, vous disposez déjà de tous les outils pour utiliser git pour le travail d'équipe. 

<div class="note">
	<strong>NOTE : </strong> Lorsque vous aurez un peu plus d'expérience, vous verrez à quel point le clonage d'un dépôt distant est la méthode de travail la plus courante et la plus simple. Dans cet exercice, nous reproduisons ce workflow. 
</div>





[Haut de la page](#TP4)

-----

<a id='pushremote'></a>
## 3. Résoudre un conflit (avec `git mergetool`)  

Jusqu'à présent, nous avons travaillé sur le dépôt git local `tp1`, il est temps de sauvegarder ce dépôt sur github. Pour ce faire, nous allons suivre une description qui montre comment le faire étape par étape. Mais tout d'abord, il est pratique de faire une brève introduction de trois commandes dans git qui nous aideront à gérer notre répertoire distant à partir de notre répertoire local sur la ligne de commande. 

* `git remote` :
: cette commande sert à gérer (ajouter) des dépôts distants ("remotes"). En d'autres termes, nous utiliserons cette commande pour créer un lien entre notre dépôt local `tp1` et celui distant que nous allons créer dans github. 

* `git push` :
: cette commande permet de mettre à jour le dépôt distant (e.g. github) à partir de la dernière version validée (_commit)_ de notre dépôt local. 

* `git pull` :
: cette commande sert à mettre à jour notre dépot local à partir de la dernière version de notre dépôt distant. 

**Êtes-vous prêts ? Allons commencer à travailler avec github !!** La première tâche sera de sauvegarder une copie de notre répertoire local `tp1` sur github. 

* Allez jusqu'au répertoire tp1, de sorte que la commande `pwd` affiche le résultat suivant :

```shell
$:> pwd
/.../courseGIT/tp1 
```

* Sur le site Web de github, allez en haut à droite et cliquez sur **New repository** comme indiqué dans l'image :

![New repository github](./images/clicknewrepo.png)

* Dans le formulaire, tapez **tp1** sous **Repository name** et laissez le reste des champs vides (comme indiqué dans l'image). Vous pouvez choisir que votre dépôt `tp1` soit public ou privé. 

![Create empty repository github](./images/createemptyrepo.png)

* Vous venez de créer un dépôt vide dont le lien `https://github.com/<votre_utilisateur>/tp1.git` sera affiché comme dans l'image ci-dessous. 

![Information empty repository](./images/emptyrepo.png)

* Tapez dans la console la ligne suivante pour vérifier que votre dépôt local `tp1` n'est pas encore lié à un dépôt distant. La réponse de cette commande ne doit rien afficher. 

```shell
$:~/courseGIT/tp1> git remote -v
```

* Maintenant, nous allons lier notre dépôt local `tp1` au répertoire distant `git@github.com:<votre_utilisateur>/tp1.git` pour ce faire, écrivez la commande suivante en remplaçant `<votre_utilisateur>` par votre utilisateur. 

```shell
$:~/courseGIT/tp1> git remote add origin git@github.com:<votre_utilisateur>/tp1.git
```
* Jusqu'à présent, nous n'avons pas examiné le concept de branche dans git, et nous n'entrerons pas dans le détail avant la prochaine séance. Cependant, il faut savoir que toutes les versions que nous sauvegardons avec les différentes _commits_ sont stockées dans une branche. Normalement cette branche s'appellera **master** ou **main**. Pour finir d'établir le lien entre le dépôt local et distant, nous aurons besoin de connaître le nom de cette branche. Pour ce faire, tapez la commande suivante : 

```shell
$:~/courseGIT/tp1> git branch
*master
```
* Il ne reste plus qu'à créer le lien de manière permanente et mettre à jour le dépôt distant. Pour ce faire, écrivons la commande suivante: 

```shell
$:~/courseGIT/tp1> git push -u origin master
```

* Alors que la commande `git push` essaie d'écrire dans le dépôt distant, vous devriez voir des messages similaires à :

```shell
Counting objects: 19, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (14/14), done.
Writing objects: 100% (19/19), 2.11 KiB | 0 bytes/s, done.
Total 19 (delta 0), reused 0 (delta 0)
To https://github.com/juanluck/tp1.git
 * [new branch]      master -> master
Branch master set up to track remote branch master from origin.
```
* **Félicitations !!** les deux dépôts, local et distant, sont maintenant synchronisés. Allez sur le site de votre projet `https://github.com/<votre_utilisateur>/tp1` et voir les résultats. **N'est-ce pas cool ?**

[Haut de la page](#TP2)

-----

<a id='sequence'></a>
## 4. Séquence de travail avec un dépôt distant 

Dans le [tp1](../tp1/index.md), nous avons vu comment établir une séquence de travail simple dans un répertoire local pour enregistrer la trace des différentes versions de notre projet à l'aide de la séquence de commandes suivant : `git status` -> `git add fichier` -> `git commit -m "message"` -> `git status` -> `git add fichier` -> `...`

Une fois que le lien entre notre dépôt local et distant a été établi, nous allons introduire les commandes `git pull` et` git push` dans cette séquence et ainsi pouvoir synchroniser le _commit_ local avec le dépôt distant . En bref, cette séquence se compose des commandes suivantes :



* Tout d'abord, nous allons _puller_ (télécharger et synchroniser) la version la plus récente du dépôt distant vers notre dépôt local :

```shell
$:~/courseGIT/tp1> git pull
```

* **(Optionnel )** Nous pouvons voir les modifications les plus récentes (écrites par nous ou un collègue) si nous tapons :

```shell
$:~/courseGIT/tp1> git log
```

* Une fois que nous avons la version la plus récente, nous pouvons commencer à introduire des modifications dans nos fichiers locaux et effectuer la séquence que nous connaissons déjà pour enregistrer la nouvelle version dans notre référentiel local :

```shell
$:~/courseGIT/tp1> git status
$:~/courseGIT/tp1> git add .
$:~/courseGIT/tp1> git commit -m "Message pour le log"
```

* Finalement, une fois que notre référentiel local a la bonne version, il suffit de le synchroniser (_pusher_) avec le dépôt distant avec la commande : 

```shell
$:~/courseGIT/tp1> git push
```
 
### Exercice
>1. Modifiez le fichier Cryptomonnaie.java avec le code ci-dessous. Pour synchroniser correctement les dépôts, commencez par faire un `git pull` ->` git log`, puis modifiez le fichier pour ensuite continuez avec la sequence `git status` ->` git add Cryptomonnaie.java` -> `git commit -m" Ajout de getters et setters "` - > `git push`. Vérifiez que le référentiel github a été mis à jour. 

```java
public class Cryptomonnaie{
    private String nom;
    private double valeurDeJeton; // Imaginons en euros

    public Cryptomonnaie(String nom, double valeurDeJeton){
        this.nom = nom;
        this.valeurDeJeton = valeurDeJeton;
    }

    public String getNom() {
        return nom;
    }

    public double getValeurDeJeton() {
        return valeurDeJeton;
    }

    @Override
    public String toString() {
        return String.format("%5s",nom) + ":" + String.format("%10.1f",valeurDeJeton);
    }
}
```

[Haut de la page](#TP2)

-----
<a id='clone'></a>
## 5. Cloner un dépôt distant sur notre machine locale 

Dans la [section 3](#pushremote), nous avons appris à initialiser un dépôt localement (avec `git init`) et puis à le synchroniser avec un répertoire distant. Cependant, la plupart du temps, nous allons utiliser un **mécanisme beaucoup plus simple** pour relier les deux dépôts : **le clone**. Pour apprendre ce mécanisme, nous allons créer un nouveau dépôt sur github que nous appellerons `tp2` (**au revoir tp1 !**). 

<div class="note">
	<strong>NOTE : </strong> Lorsque vous aurez un peu plus d'expérience, vous verrez à quel point le clonage d'un dépôt distant est la méthode de travail la plus courante et la plus simple. Dans cet exercice, nous reproduisons ce workflow. 
</div>

* Allons directement sur github pour créer un nouveau répertoire `tp2` en suivant le formulaire ci-dessous :

![Create repository tp2 in github](./images/createRepoTp2.png)


* Vous venez de créer un nouveau dépôt `tp2`. Pour obtenir le lien pour le cloner, cliquez sur <mark style="background-color:green;color:white">Code</mark> comme indiqué dans l'image suivante :

![Clone info tp2 in github](./images/cloneInfoTp2.png)

* Maintenant, il suffit d'aller dans le répertoire courseGIT :

```shell
$:~/courseGIT> ls
tp1
```

* et d'écrire la commande suivante :

```shell
$:~/courseGIT> git clone git@github.com:<votre_utilisateur>/tp2.git
```

* Si nous écrivons maintenant la commande `ls`, nous verrons qu'un nouveau répertoire `tp2` a été créé. Ce répertoire contient un dépôt local qui est déjà lié et synchronisé avec le dépôt distant sur github _(contrairement à la [section 2.](#pushremote), nous n'aurons pas besoin de configurer le lien avec `git remote` ni avec `git push -u origin master`. Si facile !.)_ 

```shell
$:~/courseGIT> ls
tp1 tp2
```
### Exercices
>1. Allez dans le répertoire `tp2` et mettez à jour tous les fichiers avec ceux du répertoire `tp1` (README.md et src/Cryptomonnaie.java) (surtout ne copiez pas le répertoire caché .git).
2.  En utilisant [la séquence](#sequence) que nous avons apprise, synchronisez les dépôts local et distant. 


 

[Haut de la page](#TP2)

-----

**Fin du TP 2**