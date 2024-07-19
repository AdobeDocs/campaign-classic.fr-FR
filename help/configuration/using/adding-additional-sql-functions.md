---
product: campaign
title: Ajout dʼautres fonctions SQL
description: Découvrez comment définir une autre fonction SQL.
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 100%

---

# Définition dʼautres fonctions SQL{#adding-additional-sql-functions}

Adobe Campaign permet à l&#39;utilisateur de définir **ses propres fonctions**, qui peuvent accéder aux fonctions SQL offertes par la base de données, et qui ne seraient pas déjà disponibles dans la console. Ce mécanisme est utile par exemple dans le cas de fonctions d&#39;agrégats (moyenne, maximum, somme) qui ne peuvent être calculées que sur le serveur ou bien quand la base de données offre un moyen plus facile d&#39;implémenter certaines fonctions, plutôt que d&#39;écrire l&#39;expression &quot;à la main&quot; dans la console (par ex. gestion de dates).

Ce mécanisme peut aussi servir dans le cas où l&#39;on souhaiterait utiliser une fonction SQL récente, ou rare, d&#39;un moteur de base de données, et qui ne serait pas encore offerte par la console Adobe Campaign.

Une fois ces fonctions ajoutées, elles apparaissent dans l&#39;éditeur d&#39;expressions, au même titre que les fonctions prédéfinies.

>[!IMPORTANT]
>
>Les appels de fonctions SQL dans la console ne sont plus naturellement transmis au serveur. Le mécanisme décrit ici devient donc **le seul moyen d&#39;appeler** sur le serveur des fonctions SQL non prévues initialement.

## Installation {#installation}

La ou les fonctions à ajouter se présentent sous la forme d&#39;un **fichier &quot;package&quot; au format XML**, dont la structure est décrite au paragraphe suivant.

Pour l&#39;installer, depuis la console, sélectionner les options de menu **Tools/Advanced/Import package**, puis le bouton **[!UICONTROL Installer depuis un fichier]**, et suivre les instructions de l’assistant d’import.

>[!IMPORTANT]
>
>Attention, même si la liste des fonctions importées apparaît tout de suite dans l&#39;éditeur de fonctions, elles ne seront pas utilisables tant que le serveur Adobe Campaign n&#39;aura pas été redémarré.

## Structure générale du package à importer {#general-structure-of-package-to-import}

La ou les fonctions à ajouter se présentent sous la forme d&#39;un **fichier &quot;package&quot;** au format XML dont voici un exemple :

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

* Les champs **nom**, **espace de noms**, et **description du package** (&quot;name&quot;, &quot;namespace&quot; et &quot;label&quot;) sont essentiellement indicatifs. Ils permettent de voir le package récapitulé dans la liste des packages installés (Explorateur/Administration/Gestion des packages/Packages installés).
* Les champs **buildVersion** et **buildNumber** sont obligatoires. Ils doivent correspondre à la version du serveur auquel la console est connectée. Cette information est disponible dans la boîte de dialogue &quot;Aide/À propos&quot;.
* Les blocs suivants, **entities** et **funclist**, sont obligatoires. Dans funcList, les champs « name » et « namespace » sont obligatoires, mais leur nom est laissé au choix de l’utilisateur, et il désignent la liste de fonctions de manière unique.

  Cela signifie que si l’on importe plus tard une autre liste de fonctions avec le même couple namespace/name (ici « cus::maListe »), les fonctions précédemment importées seront effacées. Inversement, si l’on change ce couple namespace/name, la nouvelle série de fonctions importées s’ajoutera à la précédente. 

* L&#39;élément **group** permet de définir visuellement dans quel groupe de fonctions la ou les fonctions importées apparaîtront dans l&#39;éditeur de fonction. L&#39;attribut @name peut, soit être un nom déjà existant (auquel cas les fonctions s&#39;ajouteront au groupe considéré), soit un nouveau nom, qui apparaîtra sous forme d&#39;un nouveau groupe.
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
>Attention à bien remplir l&#39;attribut @label : c&#39;est le nom qui sera affiché dans la liste des fonctions disponibles. Si vous ne mettez rien, le groupe n&#39;aura pas de nom, par contre si vous mettez un autre nom que le nom existant, c&#39;est le tout le groupe qui changera de nom.

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
* **@display** est informatif.

  >[!NOTE]
  >
  >Dans les attributs @help et @display, la chaîne &quot;$1&quot; représente le nom qui a été donné au premier paramètre de la fonction (ici, &quot;Âge&quot;). $2, $3... représenteraient les paramètres suivants. Dans l&#39;attribut @body décrit ci-après, $1 désigne la valeur de l&#39;argument passé à la fonction lors de l&#39;appel.

  >[!NOTE]
  >
  >La description doit être une chaîne de caractères valide au sens XML : noter l&#39;utilisation de &#39;&lt;&#39; et &#39;>&#39; au lieu de &lt; et >.

* **@type** est le type de retour de la fonction, il peut prendre les valeurs habituelles (long, string, byte, datetime...). S&#39;il est omis, le serveur détermine le type au mieux d&#39;après les types intervenant dans l&#39;expression implémentant la fonction.
* **@minArgs** et **maxArgs** désignent le nombre de paramètres (minimum et maximum) de la fonction. Par exemple, dans le cas d&#39;une fonction à 2 paramètres, minArgs et maxArgs vaudront 2 et 2. Dans le cas de 3 paramètres, plus 1 optionnel, ils vaudront 3 et 4 respectivement.
* Enfin, l&#39;élément **providerPart** fournit l&#39;implémentation de la fonction.

   * L&#39;attribut **@provider** est obligatoire, il indique pour quels systèmes de bases de données l&#39;implémentation est fournie. Comme le montre l&#39;exemple, on peut fournir des implémentations différentes selon la base de données, quand les syntaxes des expressions ou fonctions sous-jacentes diffèrent.
   * Et l&#39;attribut **@body** contient l&#39;implémentation de la fonction. Noter que cette implémentation doit être une expression, au sens du langage de la base de données (pas de bloc de code). Selon les bases, les expressions peuvent être des sous-requêtes (&quot;(select column from table where...)&quot;) ne retournant qu&#39;une seule valeur. C&#39;est par exemple le cas sous Oracle (la requête doit être parenthésée).

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

## Exemples      {#examples}

D’autres exemples de fonctions sont disponibles dans le package prédéfini « xtkdatakitfuncList.xml ».
