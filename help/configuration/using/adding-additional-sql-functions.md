---
product: campaign
title: Ajout dʼautres fonctions SQL
description: Découvrez comment définir une autre fonction SQL.
feature: Configuration, Instance Settings
role: Developer
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
TQID: https://experienceleague.adobe.com/HRym19p3YGAa3PEPgFBfU3ka39l5348CkdQaWcHZOJk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: ht
source-wordcount: 1040
ht-degree: 100%

---

# Définition dʼautres fonctions SQL{#adding-additional-sql-functions}

Adobe Campaign permet à l’utilisateur ou à l’utilisatrice de définir **ses propres fonctions** qui peuvent accéder aux fonctions SQL offertes par la base de données et qui ne seraient pas déjà disponibles dans la console.Cela est utile dans le cas de fonctions d’agrégats par exemple (moyenne, maximum, somme) qui ne peuvent être calculées que sur le serveur ou bien lorsque la base de données offre un moyen plus facile d’implémenter certaines fonctions, plutôt que d’écrire l’expression « manuellement » dans la console (par ex. gestion de dates).

Ce mécanisme peut aussi servir dans le cas où l&#39;on souhaiterait utiliser une fonction SQL récente, ou rare, d&#39;un moteur de base de données, et qui ne serait pas encore offerte par la console Adobe Campaign.

Une fois ces fonctions ajoutées, elles apparaissent dans l&#39;éditeur d&#39;expressions, au même titre que les fonctions prédéfinies.

>[!IMPORTANT]
>
>Les appels de fonctions SQL dans la console ne sont plus naturellement transmis au serveur. Le mécanisme décrit ici devient donc **le seul moyen d&#39;appeler** sur le serveur des fonctions SQL non prévues initialement.

## Installation {#installation}

La ou les fonctions à ajouter se présentent sous la forme d’un **fichier « package » au format XML**, dont la structure est décrite au paragraphe suivant.

Pour l’installer depuis la console, sélectionnez les options de menu **Outils/Avancé/Import de package**, puis le bouton **[!UICONTROL Installer depuis un fichier]**, et suivez les instructions de l’assistant d’import.

>[!IMPORTANT]
>
>Attention, même si la liste des fonctions importées apparaît tout de suite dans l’éditeur de fonctions, elles ne seront pas utilisables tant que le serveur Adobe Campaign n’aura pas été redémarré.

## Structure générale du package à importer {#general-structure-of-package-to-import}

La ou les fonctions à ajouter se présentent sous la forme d’un **fichier « package »** au format XML.Voici un exemple :

```
<?xml version="1.0" encoding='ISO-8859-1' ?>
<!-- ===========================================================================
  Additional SQL functions for Adobe Campaign
  ========================================================================== -->
<package
  namespace   = "nms"
  name        = "package-additional-funclist"
  label       = "Additional functions"
  buildVersion= "7.1"
  buildNumber = "10000">

  <entities schema="xtk:funcList">
    <funcList name="myList" namespace="cus">
      <group name="date" label="Personalized date">
        <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
                  minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
          <providerPart provider="MSSQL,Sybase,PostgreSQL" body="extract(year from age($1))-18"/>
        </function>
      </group>
    </funcList>
  </entities>
</package>
```

* Les champs **name**, **namespace** et **label** sont essentiellement indicatifs.Ils vous permettent de voir un résumé du package dans la liste des packages installés (Explorateur/Administration/Gestion des packages/Packages installés).
* Les champs **buildVersion** et **buildNumber** sont obligatoires.Ils doivent correspondre au numéro du serveur auquel la console est connectée.Ces informations se trouvent dans la zone « Aide/À propos ».
* Les blocs suivants, **entities** et **funclist**, sont obligatoires.Dans funcList, les champs « name » et « namespace » sont obligatoires, mais leur nom est laissé au choix de l’utilisateur ou de l’utilisatrice, et ils désignent la liste de fonctions de manière unique.

  Cela signifie que si une autre liste de fonctions avec la même paire espace de noms/nom (ici « cus::myList ») est importée ultérieurement, les fonctions précédemment importées seront supprimées.Inversement, si vous modifiez cette paire espace de noms/nom, la nouvelle série de fonctions importées s’ajoutera à la précédente.

* L’élément **group** permet de spécifier le groupe de fonctions dans lequel la ou les fonctions importées apparaîtront dans l’éditeur de fonction.L’attribut @name peut être soit un nom déjà existant (auquel cas les fonctions seront ajoutées au groupe désigné), soit un nouveau nom (qui apparaîtra sous forme d’un nouveau groupe).
* Pour mémoire, les valeurs possibles pour l’attribut @name dans l’élément `<group>` sont :

  ```
    name="aggregate"      ( label="Aggregates"         )
    name="string"             ( label="String"           )
    name="date"               ( label="Date"             )
    name="numeric"          ( label="Numeric"        )
    name="geomarketing" ( label="Geomarketing"     )
    name="other"              ( label="Others"           )
    name="window"          ( label="Windowing functions" )
  ```

>[!IMPORTANT]
>
>Veillez à renseigner l’attribut @label : il s’agit du nom qui sera affiché dans la liste des fonctions disponibles.Si vous ne saisissez rien, le groupe n’aura pas de nom.Par contre, si vous saisissez un autre nom que le nom existant, c’est tout le groupe qui changera de nom.

Si vous souhaitez ajouter des fonctions dans plusieurs groupes différents, il est possible de faire se suivre plusieurs éléments `<group>` dans la même liste.

Enfin, un élément `<group>` peut contenir la définition d’une ou de plusieurs fonctions, c’est-à-dire l’objectif du fichier de package. L’élément `<function>` est présenté dans le paragraphe ci-après.

## Descripteur de fonction &lt;function>&lt;/function> {#function-descriptor--function-}

Le cas présenté ici est le cas général, où l&#39;on souhaite fournir **l&#39;implémentation de la fonction**.

Ci-dessous l&#39;exemple d&#39;une fonction de &quot;pseudo-maturité&quot;, qui, à partir d&#39;un âge, indique depuis combien d&#39;années la personne est majeure.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

Le champ **@name** fait référence au nom de la fonction et « args » correspond à la liste des paramètres qui s’affichera dans la description. Dans ce cas, la fonction apparaît sous la forme « relativeMaturity ( `<age>` ) » dans la fenêtre de sélection de fonction.

* **@help** est le champ qui est affiché en bas de la fenêtre d&#39;édition d&#39;expressions.
* **@display** est un message informatif.

  >[!NOTE]
  >
  >Dans les attributs @help et @display, la chaîne « $1 » représente le nom qui a été donné au premier paramètre de la fonction (ici, « Âge »).$2, $3… représenteraient les paramètres suivants.Dans l’attribut @body détaillé ci-dessous, $1 désigne la valeur d’argument transmise à la fonction pendant l’appel.

  >[!NOTE]
  >
  >La description doit être une chaîne de caractères valide au sens XML : noter l&#39;utilisation de &#39;&lt;&#39; et &#39;>&#39; au lieu de &lt; et >.

* **@type** est le type de retour de la fonction et est une valeur standard (long, string, byte, datetime…).S’il est omis, le serveur détermine le meilleur type d’après les types disponibles dans l’expression implémentant la fonction.
* **@minArgs** et **maxArgs** désignent le nombre de paramètres (minimum et maximum) pour un paramètre.Par exemple, dans le cas d’une fonction à 2 paramètres, minArgs et maxArgs vaudront 2 et 2.Dans le cas de 3 paramètres, plus 1 facultatif, ils vaudront 3 et 4 respectivement.
* Enfin, l&#39;élément **providerPart** fournit l&#39;implémentation de la fonction.

   * L’attribut **@provider** est obligatoire, il indique pour quels systèmes de bases de données l’implémentation est fournie.Comme le montre l’exemple, il est possible de fournir des implémentations différentes selon la base de données lorsque les syntaxes des expressions ou fonctions sous-jacentes diffèrent.
   * L’attribut **@body** contient l’implémentation de la fonction.Remarque : cette implémentation doit être une expression, en langage de base de données (et non un bloc de code).En fonction des bases de données, les expressions peuvent être des sous-requêtes (« (sélectionner une colonne dans la table où…) »)ne renvoyant qu’une seule valeur.C’est le cas, par exemple, dans Oracle (la requête doit être écrite entre parenthèses).

  >[!NOTE]
  >
  >Si seules une ou deux bases de données sont susceptibles d&#39;être interrogées par la fonction que l&#39;on définit, on peut bien sûr ne fournir que les définitions correspondant à ces bases.

## Le descripteur de fonction &#39;pass-through&#39; {#pass-through--function-descriptor}

Un descripteur de fonction spéciale est le bloc **« pass-through »** avec un système de base de données « provider » non spécifié. Dans ce cas, l’implémentation « body » ne peut contenir qu’un seul appel de fonction avec une syntaxe qui ne dépend pas de la base de données utilisée. Pendant ce temps, le bloc « ProviderPart » est unique.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

Dans ce cas, l&#39;ajout d&#39;une fonction sert uniquement à rendre visible pour le client une fonction de la base de données qui n&#39;aurait pas été rendue disponible par défaut.

## Exemples {#examples}

D’autres exemples de fonctions sont disponibles dans le package prédéfini « xtkdatakitfuncList.xml ».
