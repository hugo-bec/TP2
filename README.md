# ![](ressources/logo.jpeg) Bases de la programmation orientée objet 

### IUT Montpellier-Sète – Département Informatique

* **Cours:** [M2103](http://cache.media.enseignementsup-recherche.gouv.fr/file/25/09/7/PPN_INFORMATIQUE_256097.pdf) - support [ici](https://github.com/IUTInfoMontp-M2103/Ressources)
* **Enseignants:** [Marin Bougeret](mailto:marin.bougeret@umontpellier.fr), [Sébastien Gagné](mailto:sebastien.gagne@umontpellier.fr), [Jérôme Palaysi](mailto:jerome.palaysi@umontpellier.fr), [Victor Poupet](mailto:victor.poupet@umontpellier.fr), [Petru Valicov](mailto:petru.valicov@umontpellier.fr), [Bruno Yun](mailto:bruno.yun@umontpellier.fr) 
* Le [forum Piazza](https://piazza.com/class/jpv7gf0lltk4kc) de ce cours pour poser vos questions
* [Email](mailto:petru.valicov@umontpellier.fr) pour une question d'ordre privée concernant le cours.

## TP 2 : Prise en main de l'IDE et travail en mode TDD
Pendant les TP nous vous conseillons d'utiliser un environnement de développement intégré (IDE en anglais).
Les avantages sont multiples : le refactoring du code, l'auto-complétion, la suggestion des méthodes/attributs/classes,
la documentation intégrée, le debuggage, une bonne intégration de Git et GitHub, des tests unitaires etc.
Dans ce cours nous utiliserons l'IDE **[IntelliJ IDEA](https://www.jetbrains.com/idea/)** de chez **[JetBrains](https://www.jetbrains.com)**,
installé sur les machines du département. Il devrait vous faciliter la vie au quotidien dans la réalisation de vos TP.
Bien évidement, rien ne vous empêche d'en utiliser un autre ([Eclipse](https://www.eclipse.org/), [NetBeans](https://netbeans.org/) etc.).

D'abord, et comme pour tous les tps de POO qui vont suivre, vous allez forker ce dépôt pour pouvoir commencer à travailler localement :

https://classroom.github.com/a/sOEtP2b1

Contrairement au TP1, ne clonez pas tout de suite vous même ce fork, l'IDE s'en chargera tout seul (cf ci-dessous).

### Découverte et prise en main de l'IDE


IntelliJ IDEA possède deux versions, la première dite *'communautaire'* est totalement open source et peut être utilisée 
gratuitement par n'importe qui et la seconde dite *'ultimate'* qui est plus riche en fonctionnalité et qui n'est pas 
gratuite pour les individus lambda. Par chance, comme dans le cas de GitHub, en tant qu'étudiant, vous avez la 
possibilité de pouvoir bénéficier d'une licence pour tous les produits JetBrains. Pour bénéficier de cette remise, il 
vous suffit de remplir [ce formulaire](https://www.jetbrains.com/shop/eform/students).

Quelques minutes après, vous recevrez un email de confirmation suivi d'un second email d'activation ou vous devrez accepter 
les conditions d'utilisation et choisir un nom d'utilisateur et un mot de passe. Conservez précieusement ces 
informations dans un coin identifié de votre cerveau car c'est grâce à elle que vous pourrez importer votre licence 
chez vous et dans les salles de TP.

**Lancement de l'IDE**

Ouvrir 'IntelliJ IDEA' (dans la section 'Programmation'/'Application').
Après le chargement, vous devriez tomber sur une première fenêtre vous proposant d'importer vos paramètres. Vous pouvez laisser sur 'Do not import settings' et valider :

![](src/main/resources/complete_installation.png)

À partir de là vous allez tomber sur la partie de personnalisation de votre installation pour qu'elle corresponde à vos besoins. Sur l'aspect esthétique, choisissez ce qui vous convient le mieux. En ce qui concerne les différents plugins à intégrer, à priori, les options installées par défaut sont suffisantes, donc vous choisirez l'installation par défaut.

À la fin, vous allez saisir vos données de connexion pour terminer le paramétrage de votre IDE.

**Import du projet dans l'IDE**

Pour pouvoir maintenant travailler sur votre TP, il vous faut cloner votre dépôt Git :

![](src/main/resources/ImportProjet.png)

Le repository sera celui correspondant à votre TP sur GitHub :

![](src/main/resources/CloneGitHub.png)

Lorsque vous ouvrez votre projet Java, la fenêtre d'affichage de votre IDE devrait rassembler à quelque chose comme ceci :

![](src/main/resources/FenetreIDE.png)

Prenez quelques minutes pour observer l'interface utilisateur. Les éléments principaux :
* à gauche : l'arborescence de votre projet Java
* centre-droite : la fenêtre d'édition ou vous allez taper vos programme
* en bas : le terminal où seront affichés les messages concernant l'exécution de vos programmes


### Workflow

Maintenant que vous savez utiliser Git en ligne de commande, que vous avez forké, importé et ouvert le TP dans votre IDE, 
vous êtes en capacité de travailler sur vos exercices. Pour cette séance nous vous proposons de suivre un workflow particulier pour résoudre vos exercices progressivement et en consolidant 
progressivement un filet de sécurité qui vérifiera que votre code continue à bien faire ce qu'il doit. Il s'agit d'un premier apperçu de ce qu'on appelle le Développement Piloté par les Tests ([Test-Driven Development](https://fr.wikipedia.org/wiki/Test_driven_development) ou TDD pour faire court). 

Le TDD est une méthode de développement de logiciels qui consiste
à travailler sur des cycles de développement très courts. La conception apparaît au fur et à mesure du développement en commençant à écrire les tests avant le code applicatif. Ceci favorise une meilleure compréhension du problème. Pour le développeur, les tests vont constituer une spécification technique exécutable et vérifiable à tout 
moment. Ainsi en rajoutant des tests, le développeur converge progressivement à la fois vers une spécification plus fine 
et un code fonctionnel associé.

Ci-dessous le déroulement d’un cycle :
1. Écrire un premier test automatique qui est censé définir une nouvelle fonctionnalité. Le test
doit s’écrire avant la fonctionnalité voulue, il est donc censé échouer initialement (normal, car vous n'avez encore rien programmé).
2. Écrire le code __minimal__ suffisant pour passer le test (principe _BabySteps_).
3. Vérifier que le test passe.
4. __Réfactoriser__ (simplifier, améliorer, optimiser etc.) tous le code tout en gardant la fonctionnalité. Durant cette étape les tests écrits préalablement sont exécutés en permanence pour certifier la validité des changements.


Ce workflow se décrit par le triptyque "RED, GREEN, REFACTOR" dans le schéma suivant :

![](src/main/resources/test-driven-development.png)

Le workflow que vous allez devoir suivre va reprendre la même structure, mis à part qu'au début, les tests vous seront donnés pour vous faire découvrir cette méthode sans trop de douleur.

#### Et au fait les tests, c'est quoi ?

Un **test unitaire** est une méthode écrite par le programmeur afin de vérifier qu'une fonctionnalité _précise_ et _élémentaire_ fonctionne correctement.
Le terme _unitaire_ insiste sur le côté "élémentaire" de la fonctionnalité (unité) à tester.

L'outil le plus répandu pour gérer les tests unitaires en Java est le framework [JUnit](https://junit.org/junit5/).
Les tests sont écrits dans une classe Java comme vous avez l'habitude.
La différence entre le fonctions "normales" et les fonctions de test est l'annotation `@Test`.
Celle-ci doit préceder chaque test unitaire. Exemple :
```java
import static org.junit.jupiter.api.Assertions.assertEquals;
import org.junit.jupiter.api.Test;

class MaPetiteClasseDeTests {
    
    @Test
    void monJoliPremierTest() {
        assertEquals(3, 1 + 2); // On vérifie que 1 + 2 vaut bien 3
    }
}
```

Pour exécuter les tests, la façon la plus simple est d'utiliser votre IDE : ouvrir la classe contenant le test et utiliser le bouton 'Play' exécuter les tests contenues dans cette classe.
Le résultat de l’exécution s'affiche en bas de la fenêtre de l'IDE :
 * les tests ayant **réussi** sont affiché en **vert**
 * les test ayant **échoué** sont en **rouge**

Votre IDE vous affiche également la cause de l'échec en vous indiquant le résultat attendu de la fonctionnalitée testée
et le résultat effectif.

#### Organisation du projet Java - convention Maven
Pour bien séparer le code de ses tests, nous allons utiliser la convention [Maven](https://fr.wikipedia.org/wiki/Apache_Maven)
dans l'ensemble des TPs de POO.
Ainsi le code est organisé de la façon suivante :

![](src/main/resources/ArborescenceMaven.png)
* l'intégralité des sources du projet se trouve dans le répertoire `src/`
* le code source et fichiers source principaux se trouvent dans `src/main`
* tous les fichiers de tests sont dans dans `src/test`

![](src/main/resources/ArborescenceMavenDetail.png)
* le code source (ou code applicatif) se trouve dans `src/main/java`
* le code source de test se trouve dans `src/test`



Maven est un system de _build_ et administration de projets Java. Pour faire une analogie vous pouvez le comparer
à l'outil bien connu [make](https://fr.wikipedia.org/wiki/Make) avec lequel vous serez bercés tout au long de vos études.
Utiliser Maven permet de gérer facilement toutes les dépendances du projet (comme les librairies de tests unitaire par exemple).
Il est également utile pour créer le fichier `.jar` du projet : une archive contenant l'ensemble de classes Java et de ressources
 d'un projet informatique (comme `.AppImage` sous Linux ou `.exe` sous Windows).   

Comme indiqué précédemment, dans ce TP les tests unitaires vous seront données dans le repertoire de test correspondant.
Vous allez les activer un par un en commentant l'annotation `@Disabled`.

__La règle principale à retenir__ : avant de faire un commit tous les tests qui ne sont pas annotés avec `@Disabled` __doivent
passer__ (pas de messages en rouge dans la console de l'IDE).


### Exercice 1 : Fizz Buzz !

Le kata Fizz Buzz est un des katas les plus connus pour l'apprentissage du TDD.
Une série 'FizzBuzz' de taille `n` est une suite d'entiers positifs où lorsqu'un multiple de 3 est rencontré on imprime "Fizz" et lorsqu'un multiple de 5 est renctontré, on imprime "Buzz". Voici la série FizzBuzz de taille 20 :

1 ; 2 ; Fizz ; 4 ; Buzz ; Fizz ; 7 ; 8 ; Fizz ; Buzz ; 11 ; Fizz ; 13 ; 14 ; FizzBuzz ; 16 ; 17 ; Fizz ; 19 ; Buzz

Implémentez la classe `FizzBuzz` qui vous est donnée dans le paquetage `fr.umontpellier.iut.exercice1`. Cette classe contient deux fonctions qu'il faudra compléter :
  - `getValue(int i)` qui retournera une chaîne de caractères correspondant au nombre `i`dans la série FizzBuzz
  - `computeList(int n)` qui retournera toute la série 'FizzBuzz' jusqu'à la valeur passée en paramètre 

La classe contenant les tests est situéé dans le répertoire correspondant au paquetage `fr.umontpellier.iut.exercice1` dans l'arborescence `src/test` de votre projet.
Vous activerez les tests les un après les autres et soumettrez (avec un commit) votre solution après __chaque itération__ du cycle principal du workflow.

La classe principale (contenant le `main`) est la classe `App`, et se trouve dans le paquetage `fr.umontpellier.iut.exercice1`. Implémentez là (supprimez la ligne qui lève une exception) pour simuler le bon fonctionnement de votre programme.

Même si l'exercice paraît facile, prêtez une attention particulière à l'étape de réfactorisation. Vous vous servirez de votre IDE pour renommer les méthodes ou variables, pour l'autocomplétion etc.



### Exercice 2 : Facteurs Premiers

D'après le Théorème fondamental de l'arithmétique, tout entier strictement positif peut être écrit comme un produit de nombres premiers.
Dans cet exercice il vous est demandé d'implémenter la méthode qui, pour un entier strictement positif donné, renvoie la liste de ces facteurs premiers en ordre croissant.
Par exemple pour l'entier 5, la liste retournée devrait être [5], alors que pour l'entier 12, la liste retournée devrait être [2,2,3].

La méthode que vous devez implémenter est `computeFactors(int)`. Elle est située dans la classe `PrimeFactors` (paquetage `fr.umontpellier.iut.exercice2`) qui renvoie la liste de facteurs premiers pour l'entier passé en paramètre.

Comme pour l'exercice précédent, vous activerez les tests les un après les autres.  N'oubliez pas de __refactoriser__ (i.e. simplifier/nettoyer/factoriser) le code à chaque étape. Vous soumettrez avec Git votre solution après chaque itération du cycle principal du workflow.

À la fin de l'exercice, pour vous convaincre de la validité de votre code, vous ajouterez un test supplémentaire pour un nouveau nombre que vous aurez choisi aléatoirement. Est-ce que votre programme passe ce nouveau test ?



### Exercice 3 : Calculette romaine

Vous êtes chargé de réaliser une calculette simplifiée qui effectue des additions et des soustractions des nombres écrits en numérotation romaine. Dans cette numérotation on utilise des caractères parmi sept lettres de l'alphabet latin : `I`, `X`, `L`, `C`, `D` et `M`. La signification en numérotation décimale classique est donnée ci-dessous :


| I | V | X  | L  |  C  |  D  |  M   |
|---|---|----|----|-----|-----|------|
| 1 | 5 | 10 | 50 | 100 | 500 | 1000 |


Un nombre romain se lit de gauche à droite en faisant des additions et des soustractions des valeurs des chiffres. Par exemple le nombre romain `MLXIII` correspond à 1063 dans la numérotation décimale car il se décompose comme `M`+`L`+`X`+`I`+`I`+`I` = 1000+50+10+1+1+1. Alors que le nombre `XXXIV` vaut 34 car il se décompose comme `X`+`X`+`X`+`IV`=10+10+10+4. Une meilleure façon de voir ce dernier exemple c'est d'utiliser la soustraction `X`+`X`+`X`-`I`+`V`=10+10+10-1+5.

Les nombres romains sont majoritairement représentés selon les principes suivants :
- Un même symbole n'est pas employé quatre fois de suite (sauf `M`) ;
- Tout symbole qui suit un symbole de valeur supérieure ou égale s’ajoute à celui-ci (exemple : 6 s'écrit `VI`) ;
- Tout symbole qui précède un symbole de valeur supérieure se soustrait à ce dernier :

  * `I` doit être retranché à `V` ou à `X` quand `I` est devant `V` ou `X` (ex. : 4 s'écrit `IV`),

  * `X` doit être retranché à `L` ou à `C` quand `X` est devant `L` ou `C` (ex. : 40 s'écrit `XL`),

  * `C` doit être retranché à `D` ou à `M` quand `C` est devant `D` ou `M` (ex. : 900 s'écrit `CM`),

  * Par contre, ôter `I` de `L` ou de `C` n'est pas pratiqué (49 s'écrit `XLIX` et non `IL` ; 99 s'écrit `XCIX` et pas `IC`) ;

- Les symboles sont groupés par ordre décroissant, sauf pour les valeurs à retrancher selon la règle précédente (ex. : 1030 s'écrit `MXXX` et non `XXXM` qui est une des façons de représenter 970).
- `CM`, `CD`, `XC`, `XL`, `IX`, `IV` sont valides
- `XM`, `IM`, `XD`, `ID`, `IC`, `IL` sont non-valides



D'autres variantes de règles concernant la soustraction existent, vous pouvez choisir celles qui vous paraissent les plus pertinentes. Pour plus d'informations sur la numérotation romaine :

https://fr.wikipedia.org/wiki/Numération_romaine

Faites très attention pour cet exercice de bien respecter le principe du TDD en ajoutant vraiment tout le temps la quantité minimale de code nécessaire à la validation des tests. Si vous suivez cette règle, il se résout très facilement alors qu'en l'abordant de manière générale, il comporte de nombreux pièges pouvant vous faire perdre un temps précieux.

Dans cet exercice, vous allez manipuler la classe [`String`](https://docs.oracle.com/javase/8/docs/api/?java/lang/String.html). Cette classe possède de nombreuses méthodes utilitaires pour manipuler facilement les chaines de caractères.

**Convertisseur de nombres romains**

Écrivez la classe Java `RomanToNumeral` donnée. Cette classe aura une méthode  `getNumeral()` qui prend un nombre romain en paramètre et retourne sa valeur en numérotation décimale (un type `int`). 

N'oubliez pas de faire des "commits" au fur et à mesure !

**Convertisseur de nombres décimaux** 

Écrivez la classe `NumeralToRoman` qui contiendra une méthode `getRoman()`, qui prend un nombre entier en paramètre et retourne sa valeur en numérotation romaine (de type `String` donc).

Est-ce que vos tests sont suffisants ? Que se passe-t-il lors de la conversion `romain` -> `décimal` -> `romain` ?

**Additionneur romain**

En utilisant les deux classes écrites précédemment, créez une classe `RomanAdditionner` qui contiendra une méthode `compute()`. Cette méthode prendra en paramètre une chaîne de caractères représentant une expression arithmétique romaine telle que :

 - les opérandes sont écrits en numérotation romaine
 - les opérations possibles sont `+` et `-`

Voici un exemple d'expression arithmétique : `MMMXL` + `XII` - `CIX`.

Le résultat correspondant devrait être : `MMCMXLIII`.

### Et ce n'est pas fini !

Vous trouverez d'autres katas qui vous permettront de mieux apprendre la programmation en mode TDD :

http://codingdojo.org/kata/


### Si l'IDE n'est pas votre tasse de thé...

Naturellement vous pouvez faire le tout en ligne de commande.
Supposons que vous êtes sur Linux (la démarche étant quasiment identique sur Windows ou MacOS) et que la racine de votre projet est le répertoire `~/POO/TP2`.
Positionnez-vous dans ce répertoire :
```
~/RepertoireCourant$ cd ~/POO/TP2
~/POO/TP2$ ls
~/POO/TP2$ pom.xml  README.md  src  target  tp2.iml
```

Pour compiler le code source de l'exercice 1 à partir de la racine de votre projet :

```
~/POO/TP2$  javac -d target/ src/main/java/fr/umontpellier/iut/exercice1/*.java
```

L'option `-d target` permet d'indiquer que la destination des fichiers compilés est le répertoire `target/`
Alternativement, avec l'option `-sourcepath`, il est possible d'indiquer le chemin où le compilateur va chercher
l'ensemble du code source à compiler :
```
~/POO/TP2$  javac -sourcepath src/ -d target src/main/java/fr/umontpellier/iut/exercice1/*.java
```

Pour exécuter le programme compilé :
```
~/POO/TP2$  cd target/
~/POO/TP2/target$  java fr.umontpellier.iut.exercice1.App
```
