# Compléments de programmation - TD 1

## Remarques préliminaires
* Pour l'ensemble des TDs, vous créerez un compte individuel sur [github](https://github.com/) si vous n'en possédez pas déjà un.
Vous nommerez ce compte de la façon suivante: `uvsq<MonNuméroÉtudiant>`.
Par exemple, pour un étudiant de numéro *21601234*, le compte sera `uvsq21601234`.
* Les commandes `git` sont à taper en ligne de commande dans un *shell*.
* Vous pouvez utiliser l'IDE de votre choix.
Sur le cartable numérique, [Eclipse](www.eclipse.org), [IntelliJ IDEA](http://www.jetbrains.com/idea/) et [Visual Studio Code](https://code.visualstudio.com/) sont installés.
* Vous répondrez aux questions directement dans ce fichier en complétant les emplacements correspondants.
Ajoutez ensuite ce fichier au dépôt `git`.

## Partie I (à faire durant le TD) : découverte de `git`
Dans cet exercice, vous créerez une classe `Fraction` représentant un nombre rationnel et une classe `Main` qui testera les méthodes de la classe `Fraction` **avec des assertions** (cf. [Utilisation d'assertions](https://koor.fr/Java/Tutorial/java_assert.wp)).
À chaque étape, consultez le statut des fichiers du projet (`git status`) ainsi que l'historique (`git log`).

1. Sur la forge, créez le dépôt (_repository_) `SimpleFraction`;
En terme de *commits*, quelle différence constatez-vous entre cocher une (ou plusieurs) des cases *Initialize this repository with* et n'en cocher aucune ?
    > On peut cocher des cases pour ajouter un fichier README, un .gitignore ou un fichier LICENSE dans notre repository. Dans le cas où l'on ne coche rien, le repo créé est vide.

    *Pour la suite, ne cochez aucune de ces cases*.
1. Localement, configurez `git` avec votre nom (`user.name`) et votre email (`user.email`) (cf. [Personnalisation de Git](https://git-scm.com/book/fr/v2/Personnalisation-de-Git-Configuration-de-Git));
    ```bash
    $ git config --global user.name "uvsq21916945"
    $ git config --global user.email anne.duveau@ens.uvsq.fr
    ```
1. Initialisez le dépôt `git` local pour le projet (cf. [Démarrer un dépôt Git](https://git-scm.com/book/fr/v2/Les-bases-de-Git-D%C3%A9marrer-un-d%C3%A9p%C3%B4t-Git));
    ```bash
    # avec SSH: (la fonction avec http ne fonctionne pas?)
    # on clone le README initial 
    git clone @adress_readme
    # on clone ensuite le repo créé dans mon git
    git clone git@github.com:uvsq21916945/SimpleFraction_1.git
    # je peux faire un ls -rtla dans le fichier cloné pour voir si on a bien un ".git"
    # on peut alors déplacer le fichier que l'on veut modifier du 1er clonage dans le 2e où l'on va le modifier
    ```
1. Dans votre IDE, créez la classe `Fraction` (vide pour le moment) et la classe `Main` (avec un simple affichage) dans le projet (cf. [Méthode `main`](https://docs.oracle.com/javase/specs/jls/se19/html/jls-12.html#jls-12.1.4));
Vérifiez que le projet compile et s'exécute dans l'IDE;
Validez les changements (cf. [Enregistrer des modifications dans le dépôt](https://git-scm.com/book/fr/v2/Les-bases-de-Git-Enregistrer-des-modifications-dans-le-d%C3%A9p%C3%B4t));
    ```bash
    # pour vérifier que le projet compile et exécuter
    javac Fraction.java Main.java
    java Main

    # validation des chgts
    git status
    git add *.java
    git commit -m "ajout de fichiers.java"
    git push
    ```
1. Ajoutez la méthode `toString` à la classe `Fraction` (cf. [`Object.toString`](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/lang/Object.html#toString())) qui retournera la chaîne `"Je suis une fraction."` et modifiez la classe `Main` en conséquence;
Validez les changements;
    ```Java
    public String toString()
    {
        return ("Je suis une Fraction");
    }

    // dans la classe Main

    String s = x.toString();
    System.out.println(s);
    ```
1. Publiez vos modifications sur le dépôt distant (cf. [Travailler avec des dépôts distants](https://git-scm.com/book/fr/v2/Les-bases-de-Git-Travailler-avec-des-d%C3%A9p%C3%B4ts-distants));
Vous utiliserez le protocole `https` pour cela;
Vérifiez avec le navigateur;
    ```bash
    git add 
    git commit -m "commentaires"
    git push
    ```
1. Sur la forge, ajoutez un fichier de documentation `README.md`.
Quelle syntaxe est utilisée pour ce fichier ?
    > Ce fichier utilise la synthaxe Markdown.
1. Récupérez localement les modifications effectuées sur la forge.
    ```bash
    git pull
    ```
1. Ajoutez les répertoires et fichiers issus de la compilation aux fichiers ignorés par `git` (cf. [`.gitignore` pour Java](https://github.com/github/gitignore/blob/main/Java.gitignore));
    ```bash
    # Compiled class file
    *.class

    # Log file
    *.log

    # BlueJ files
    *.ctxt

    # Mobile Tools for Java (J2ME)
    .mtj.tmp/

    # Package Files #
    *.jar
    *.war
    *.nar
    *.ear
    *.zip
    *.tar.gz
    *.rar

    # virtual machine crash logs, see http://www.java.com/en/download/help/error_hotspot.xml
    hs_err_pid*
    replay_pid*
    ```
1. Retirez les fichiers de configuration de l'IDE du projet;
    ```bash
    # Il n'y a pas de fichiers de configuration de l'IDE pour l'éditeur VSC...
    ```
    Ajoutez-les aux fichiers ignorés par `git`.
    ```bash
    # je ne peux pas ici..
    ```
1. Configurez l'accès par clé publique/clé privée à la forge (cf. [Connecting to GitHub with SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)).
    >  Procédure de la configuration de la clé à la forge:
    - Avant de générer une clé, on vérifie s'il n'en existe pas déjà une dans notre machine locale.
    - Dans le cas où il n'en existe aucune, générer la clé sur le terminal.
    - ajouter la clé SSH sur le github dans les paramètres
    SSH ( = Secure Shell)

## Partie II (à faire durant le TD) : compléter la classe `Fraction`
Dans cet partie, vous compléterez les classes `Fraction` et `Main`.
Un exemple d'interface pour une telle classe est donné par la classe [`Fraction`](http://commons.apache.org/proper/commons-math/javadocs/api-3.6.1/org/apache/commons/math3/fraction/Fraction.html) de la bibliothèque [Apache Commons Math](http://commons.apache.org/math/).

Vous respecterez les consignes ci-dessous :
* chaque méthode de `Fraction` sera testée dans `Main` **avec des assertions** (cf. [Utilisation d'assertions](https://koor.fr/Java/Tutorial/java_assert.wp));
* à la fin de chaque question, consultez le statut des fichiers du projet (`git status`) ainsi que l'historique (`git log`) puis validez les changements.

1. Ajoutez les attributs représentants le numérateur et le dénominateur (nombres entiers).
    ```Java
    private int numerateur;
    private int denominateur;
    ```
1. Ajoutez les constructeurs (cf. [Constructor Declarations](https://docs.oracle.com/javase/specs/jls/se19/html/jls-8.html#jls-8.8)) suivants :
    * initialisation avec un numérateur et un dénominateur,
    * initialisation avec juste le numérateur (dénominateur égal à _1_),
    * initialisation sans argument (numérateur égal _0_ et dénominateur égal à _1_),
    ```Java
    assert "3/4".equals(x.toString()): assertion fausse;
    ```
1. Ajoutez les fractions constantes ZERO (0, 1) et UN (1, 1) (cf. [Constants in Java](https://www.baeldung.com/java-constants-good-practices)),
    ```Java
    public static final Fraction ONE = new Fraction(1);
    public static final Fraction ZERO = new Fraction();
    ```
1. Ajoutez une méthode de consultation du numérateur et du dénominateur (par convention, en Java, une méthode retournant la valeur de l'attribut `anAttribute` est nommée `getAnAttribute`),
    ```Java
    public int getNumerateur()
    {
        return numerateur;
    }

    public int getDenominateur()
    {
        return denominateur;
    }
    ```
1. Ajoutez une méthode de consultation de la valeur sous la forme d'un nombre en virgule flottante (méthode `doubleValue()`) (cf. [`java.lang.Number`](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/lang/Number.html)),
   ```Java
    public double doubleValue()
    {
        return (double)this.numerateur/(double)this.denominateur;
    }
    ```
1. Ajoutez une méthode permettant l'addition de deux fractions (la méthode `add` prend en paramètre *une* fraction et *retourne* la somme de la fraction courante et du paramètre),
   ```Java
    Fraction z = new Fraction();
    z = x.add(y);
    assert z.toString().equals("1/1"): "la somme n'a pas fonctionné";
    ```
1. Ajoutez le test d'égalité entre fractions (deux fractions sont égales si elles représentent la même fraction réduite) (cf. [`java.lang.Object.equals`](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/lang/Object.html#equals(java.lang.Object))),
   ```Java
    assert f1.reduction(f1).toString().equals(f2.reduction(f2).toString()): "les 2 fractions ne sont pas égales";
    ```
1. Ajoutez la comparaison de fractions selon l'ordre naturel (cf. [`java.lang.Comparable`](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/lang/Comparable.html)).
   ```Java
    assert f1.compareTo(f2) == 0 : "les 2 fractions ne sont pas égales";
    ```
1. Faites hériter votre classe `Fraction` de la classe [`java.lang.Number`](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/lang/Number.html) et complétez les méthodes
   ```Java
    // Vérifiez avec le code ci-dessous
    Number aNumber = java.math.BigDecimal.ONE;
    Number anotherNumber = new Fraction(1, 2);
    assert java.lang.Math.abs(aNumber.doubleValue() + anotherNumber.doubleValue() - 1.5) < 1E-8;
    ```

## Partie III (à faire à la maison) : révisions et perfectionnement *shell* et *IDE*
### Maîtriser le *shell* de commandes
L'objectif de cet exercice est de vous faire réviser/découvrir les commandes de base du *shell* de votre machine.
Vous pouvez répondre en utilisant le shell de votre choix (*bash*, *Powershell*, …).
Pour répondre à ces questions, vous devez effectuer les recherches documentaires adéquates (livre, web, …).

1. Quel OS et quel shell de commande utilisez-vous ?
    > J'utilise Linux, et j'utilise le bash.
1. Quelle commande permet d'obtenir de l'aide ?
Donnez un exemple.
    ```bash
    $ help nom 
    # permet d'en savoir plus sur la fonction nom
    
    $ man mv
    # permet de comprendre comment fonctionne la commande mv 
    ```
1. Donnez la ou les commandes shell permettant de
    1. afficher les fichiers d'un répertoire triés par taille (taille affichée lisiblement)
        ```bash
        $ ls -lS /path/to/folder
        # -S va trier les fichiers par taille
        # sort by size
        ```
    1. compter le nombre de ligne d'un fichier
        ```bash
        $ wc -l < text.txt
        # le paramètre -c de la commande grep renvoie le nombre de lignes.
        ```
    1. afficher les lignes du fichier `Main.java` contenant la chaîne `uneVariable`
        ```bash
        $ grep "uneVariable" -Rn mon_repertoire/
        # -n c'est pour le numéro de la ligne
        # -R: lis tous les fichiers dans chaque directory, de manière récursive.
        ```
    1. afficher récursivement les fichiers `.java` contenant la chaîne `uneVariable`
        ```bash
        $ find /chemin/toto -type f -name *.java ...?
        ```
    1. trouver les fichiers (pas les répertoires) nommés `README.md` dans une arborescence de répertoires
        ```bash
        $ find /chemin/toto -type f -name "README.md"
        ```
    1. afficher les différences entre deux fichiers textes
        ```bash
        diff text1 text2
        # compare les fichiers text1 et text2 ligne par ligne

        cmp text1 text2
        # compare les fichiers caractère par caractère
        ```
1. Expliquez en une ou deux phrases le rôle de ces commandes et dans quel contexte elles peuvent être utiles pour un développeur.
    * `ssh`
        > Commande (protocole réseau) qui permet des connexions distantes sécurisées entre deux systèmes
        Permet par exemple de gérer les machines, copier ou déplacer des fichiers entre les systèmes.
        On peut par exemple se connecter à un serveur distant grâce à ça.
    * `screen`/`tmux`
        > permet d'ouvrir plusieurs terminaux dans une même console et de passer de l'un à l'autre et de les récupérer plus tard.
    * `curl`/[HTTPie](https://httpie.org/)
        > Curl (ou Client URL) est conçue pour fonctionner comme un moyen de vérifier la connectivité aux URL Pour transférer des données d'un serveur ou sur un serveur.
    * [jq](https://stedolan.github.io/jq/)
        > jq est comme la commande "sed", "awk", et "grep" et peut-être utilisé pour fragmenter, filtrer, transformer les données

### Découverte de votre *IDE*
Dans cet exercice, vous expliquerez en quelques phrases comment vous réalisez les actions ci-dessous dans votre IDE.
Vous pouvez choisir l'IDE/éditeur de texte de votre choix.
Pour réaliser cette exercice, vous devez bien évidemment vous reporter à la documentations de l'IDE ([IntelliJ IDEA](https://www.jetbrains.com/help/idea/discover-intellij-idea.html#developer-tools), [Visual Studio Code](https://code.visualstudio.com/docs), [Eclipse](https://help.eclipse.org/2020-09/index.jsp), …).

1. Quels IDE ou éditeurs de texte utilisez-vous pour le développement Java ?
    > Pour le développement de Java, j'utilise Visual Studio Code.

    Pour la suite, ne considérez que l'un de vos choix.
1. Comment vérifier/définir que l'encodage utilisé est *UTF-8* ?
    > Aller dans > Paramètres > Éditeur de texte > Files: Encoding > Sélectionner UTF-8 (si pas déjà le cas)
1. Comment choisir le JDK à utiliser dans un projet ?
    > Il en existe plusieurs que l'on peut installer. Aller dans le déroulé à gauche et aller sur "Java Projects", cliquer droit et >configure classpath
1. Comment préciser la version Java des sources dans un projet ?
    > Aller dans Java Projects dans le déroulé à gauche et cliquer droit sur le projet souhaité et changer dans JDK Runtime et ensuite on peut modifier.
1. Comment ajouter une bibliothèque externe dans un projet ?
    > Aussi dans configure ClassPath puis dans referenced libraries. On pourra importer des librairies externes dans le projet.
1. Comment reformater un fichier source Java ?
    > **Je ne comprends pas la question**
1. Comment trouver la déclaration d'une variable ou méthode ?
    > Cliquer droit sur la méthode par exemple et sur "atteindre la définition". Pareil si c'est une variable. On atterira sur l'endroit de la déclaration de la variable ou méthode.
1. Comment insérer un bloc de code prédéfini (*snippet*) ?
    > Aller dans > Affichage > Palette de commandes
    . Il est possible aussi d'installer des snippets avec des extensions.
1. Comment renommer une classe dans l'ensemble du projet ?
    > A gauche sélectionner la classe en question, puis cliquer droit et "Renommer". Changer le nom le changera dans tout le projet

1. Comment exécuter le programme en lui passant un paramètre en ligne de commande ?
    > Par exemple, si on ajoute le paramètre pour activer les assertions, on peut écrire en ligne de commandes:
    ```bash
    $ java -ea Main
    ```
1. Comment déboguer le programme en visualisant le contenu d'une ou plusieurs variables ?
    > Il faut démarrer l'exécution en appuyant sur "Debug" et en mettant les breakpoints au bon endroit.
    On verra s'afficher en temps réel la valeur des variables à gauche.
1. Quels paramètres ou fonctionnalités vous semblent particulièrement importants/utiles pour le développement Java ?
    > Savoir utiliser le debugger, savoir gérer les librairies, etc..
