<a id='TP3'></a>
# TP 3 : Travailler en équipe sur un depôt github distant 
[Retour à la page principale](../index.md)

Il est temps de commencer à utiliser git pour le travail d'équipe. En fait, git a été initialement conçu dans ce but et c'est là qu'il peut nous montrer sa puissance. 

Avant de continuer, nous allons nous organiser en binômes. Si vous êtes un nombre impair, un équipe peut être composé de trois personnes malgré le TP est conçu pour deux roles. 

**Êtes-vous déjà constitué en équipe ?** Lancez une pièce et décidez qui assumera le rôle de <mark style="background-color:red;font-weight:bold; color:white">Athos</mark> et qui assumera le rôle de <mark style="background-color:green;font-weight:bold; color:white">Porthos</mark> pour ce travail pratique. Si vous êtes trois, deux personnes seront regroupées dans le rôle d'<mark style="background-color:red;font-weight:bold; color:white">Athos</mark>.

 
---

## Objectifs du TP 3

Le but de ce troisième TP  est de commencer à travailler en équipe sur github et développer un marché pour le projet de crypto-monnaie que nous avions déjà lancé. Dans ce TP, nous allons apprendre à : 

>1. [Inviter des collaborateurs dans un dépôt personnel](#collaborateurs)
2. [Développement d'un projet java en équipe](#projet)
3. [Gérer des nouvelles fonctionnalités à l'aide des branches](#branch)

   

[Haut de la page](#TP3)

---

<a id='collaborateurs'></a>
## 1. Inviter des collaborateurs dans un dépôt personnel

<mark style="background-color:red;font-weight:bold; color:white">Athos</mark> :

: * Pour commencer, <mark style="background-color:red;font-weight:bold; color:white">Athos</mark> va créer un nouveau dépôt dans son compte github appelé `tp3` (<mark style="background-color:green;font-weight:bold; color:white">Porthos</mark> fera bien de regarder et de commenter avec <mark style="background-color:red;font-weight:bold; color:white">Athos</mark> comment cela est fait). Nous allons remplir le formulaire de la même manière que nous l'avons fait avec le dépôt `tp2`.

: * Une fois le dépôt créé, cliquez sur **Settings** :

![Settings](./images/settings.png)

: * ensuite sur **Manage access** et puis sur **Invite a collaborator** :
tp3/tp3/tp3/
![Manage access](./images/inviteCollaborator.png)

: * demandez à <mark style="background-color:green;font-weight:bold; color:white">Porthos</mark> son nom d'utilisateur sur github et invitez-le dans votre dépôt :

![Manage access](./images/invitePorthos.png)

<mark style="background-color:green;font-weight:bold; color:white">Porthos</mark> :

: * <mark style="background-color:green;font-weight:bold; color:white">Porthos</mark>  doit aller dans sa boîte email pour recevoir l'invitation d'<mark style="background-color:red;font-weight:bold; color:white">Athos</mark> à collaborer dans le dépôt `tp3` et l'accepter.

<mark style="background-color:red;font-weight:bold; color:white">Athos</mark>  et <mark style="background-color:green;font-weight:bold; color:white">Porthos</mark> :

: * Chacun de vous peut faire un clone du projet en se plaçant dans le répertoire `courseGIT` :

```shell
$:~/courseGIT> git clone https://github.com/<utilisateur_de_athos>/tp3.git
```

: * Si vous l'avez bien fait, votre répertoire `courseGIT` devrait contenir trois répertoires comme indiqué ci-dessous :

```shell
$:~/courseGIT> ls
tp1 tp2 tp3
```

### Exercices
>1. <mark style="background-color:green;font-weight:bold; color:white">Porthos</mark> : allez dans le répertoire `tp3` et mettez à jour tous les fichiers avec ceux du répertoire `tp2` (README.md et src/Cryptomonnaie.java) (surtout ne copiez pas le répertoire caché .git). Synchronisez les dépôts local et distant.
2.  <mark style="background-color:red;font-weight:bold; color:white">Athos</mark> : après que <mark style="background-color:green;font-weight:bold; color:white">Porthos</mark> vous en informe, faissez un `git pull` depuis votre répertoire local `tp3` pour synchroniser les changements.
3. Les deux : vérifiez que tous les dépôts sont bien synchronisés (ce qui est sur github correspond bien à ce que vous avez dans votre répertoire local).

[Haut de la page](#TP3)

-----

<a id='projet'></a>
## 2. Développement d'un projet java en équipe

Git a été principalement conçu pour gérer le travail en équipe. Revenons au projet Crypto-monnaie pour lequel nous allons créer un marché avec différents portefeuilles. Avant de commencer, décrivons certains concepts :

**Portefeuille :**
: Un portefeuille cryptographique est un portefeuille virtuel dans lequel un utilisateur peut stocker un certain nombre de jetons d'une crypto-monnaie. Cet utilisateur peut posséder plusieurs portefeuilles, mais chaque portefeuille ne peut contenir qu'un seul type de crypto-monnaie. Un portefeuille permet des achats de jetons ainsi qu'un transfert de jetons entre portefeuilles si le type de crypto-monnaie est le même. 

**Marché :**
: Le marché est un registre avec une série de portefeuilles cryptographiques. En principe, le marché nous permet de poser certaines questions telles que quel est le capital total d'un utilisateur avec plusieurs portefeuilles ou quel est le capital total en circulation d'une crypto-monnaie spécifique.

<mark style="background-color:red;font-weight:bold; color:white">Athos</mark>  et <mark style="background-color:green;font-weight:bold; color:white">Porthos</mark> :

: * Avant de continuer, assurez-vous que votre dépôt `tp3` est parfaitement synchronisé.

<mark style="background-color:red;font-weight:bold; color:white">Athos</mark> :

: * Copiez les fichiers suivants dans le répertoire `tp3/src`, validez-les dans le dépôt local et distant :
   * [CryptoMarche.java](./src/CryptoMarche.java)
   * [Portefeuille.java](./src/Portefeuille.java)
   * [TestCryptoMarche.java](./src/TestCryptoMarche.java) 
   
<mark style="background-color:green;font-weight:bold; color:white">Porthos</mark> :
: * Assurez-vous d'obtenir la dernière version du dépôt distant. 

<mark style="background-color:red;font-weight:bold; color:white">Athos</mark>  et <mark style="background-color:green;font-weight:bold; color:white">Porthos</mark> :

: * Votre mission sera de compléter la fonctionnalité qui manque pour compléter notre application de marché de crypto-monnaie. <mark style="background-color:green;font-weight:bold; color:white">Porthos</mark> se concentrera sur l'implementation de la classe **Portefeuille.java** et <mark style="background-color:red;font-weight:bold; color:white">Athos</mark> sur l'implementation de la classe **CryptoMarche.java**. **L'objectif est de faire passer les tests décrits dans le fichier TestCryptoMarche.java (il n'est pas permis de modifier ce fichier).**
* Avant de continuer, compilez tout le code et assurez-vous qu'il n'y a pas d'erreurs de compilation. 
* Exécutez en ligne de commande `java TestCryptoMarche`. La réponse devrait être la suivante :

```shell
Test Portefeuille transfertDevise        ... FAIL
Test Portefeuille achatDevise            ... FAIL
Test CryptoMarche capitalEnEuros         ... FAIL
Test CryptoMarche capitalMonneaie        ... FAIL
```

<mark style="background-color:red;font-weight:bold; color:white">Athos</mark> :

: * Votre tâche consiste à terminer l'implémentation des deux fonctions suivantes de la classe **CryptoMarche.java**. Suivez la spécification dans le javadoc pour les compléter. Une fois terminé, synchronisez vos modifications avec le dépôt local et distant. 

```java
    /**
     * Cette fonction recherche sur le marché tous les portefeuilles 
     * du propriétaire et calcule son capital en euros. 
     * @param proprietare
     * @return capital en euros du propriétare.
     */
    public double capitalEnEuros(String proprietaire){
        /**
			FONCTION À IMPLEMENTER
        **/
        return 0;
    }

    /**
     * Cette fonction recherche sur le marché tous les portefeuilles 
     * d'un type de devise et calcule le volume total de capital de 
     * cette devise sur le marché 
     * @param monnaie
     * @return capital total en circulation de la cryptomonnaie (en euros).
     */
    public double capitalMonneaie(Cryptomonnaie monnaie){
        /**
			FONCTION À IMPLEMENTER
        **/
        return 0;
    }
```


 <mark style="background-color:green;font-weight:bold; color:white">Porthos</mark> :

 : * Votre tâche consiste à terminer l'implémentation des deux fonctions suivantes de la classe **Portefeuille.java**. Suivez la spécification dans le javadoc pour les compléter. Une fois terminé, synchronisez vos modifications avec le dépôt local et distant. 
 
```java
  /**
   * Cette fonction vous permet de transférer des devises du portefeuille actuel 
   * vers le portefeuille de destination pour le montant indiqué. Le type de devise 
   * (nom du Jeton) doit être le même entre les deux portefeuilles et le montant 
   * du portefeuille actuel doit être supérieur ou égal à celui indiqué.
   * @param destination 
   * @param montantJetons
   * @return true si la transaction a été effectuée, false sinon.  
   */
  public boolean transfertDevise (Portefeuille destination, double montantJetons){
      /**
           FONCTION À IMPLEMENTER
	  **/
      return false;
  }

  /**
   * Cette fonction vous permet d'acheter des jetons de la 
   * crypto-devise en fonction de leur valeur en euros. 
   * Le résultat est l'augmentation des jetons de la crypto-monnaie.
   * @param montantEuros Valeur d'achat en euros 
   * @return true si le montant en euros est supérieur ou égal à 0 
   */
  public boolean achatDevise (double montantEuros){
	/**
           FONCTION À IMPLEMENTER
	**/
    return false;
  }
```

### Exercice
>1. Réalisez les étapes précédentes. Une fois les dépôts synchronisés, <mark style="background-color:red;font-weight:bold; color:white">Athos</mark> et <mark style="background-color:green;font-weight:bold; color:white">Porthos</mark> doivent compiler et lancer le test `java TestCryptoMarche`. Le résultat doit être le suivant :

```shell
Test Portefeuille transfertDevise        ... OK
Test Portefeuille achatDevise            ... OK
Test CryptoMarche capitalEnEuros         ... OK
Test CryptoMarche capitalMonneaie        ... OK
``` 

[Haut de la page](#TP3)

-----


<a id='branch'></a>
## 3. Gérer des nouvelles fonctionnalités à l'aide des branches

[Haut de la page](#TP3)

-----

**Fin du TP 3**