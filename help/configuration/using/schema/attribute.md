---
product: campaign
title: Éléments et attributs - élément attribute
description: Éléments et attributs
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: e4d34f56-b065-4dce-8974-11dc2767873a
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '1555'
ht-degree: 100%

---

# élément attribute {#attribute--element}

![](../../../assets/v7-only.svg)

## Modèle de contenu {#content-model}

attribute:==help

## Attributs {#attributes}

_operation (string), advanced (boolean), applicableIf (string), autoIncrement (boolean), belongsTo (string), dataPolicy (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), edit (string), enum (string), expr (string), feature (string), featureDate (boolean), img (string), inout (string), label (string), length (string), localizable (boolean), name (MNTOKEN), notNull (boolean), pkgStatus (string), ref (string), required (boolean), sql (boolean), sqlDefault (string), sqlname (string), sqltable (string), target (MNTOKEN), template (string), translatedDefault (string), translatedExpr (string), type (MNTOKEN), user (boolean), userEnum (string), visibleIf (string), xml (boolean)

## Parents {#parents}

`<element>`

## Enfants {#children}

`<help>`

## Description {#description}

Les éléments `<attribute>` vous permettent de définir un champ dans la base de données.

## Usage et contexte d&#39;utilisation {#use-and-context-of-use}

Les éléments `<attribute>` doivent être déclarés dans un élément `<element>`.

La séquence dans laquelle les éléments `<attribute>` sont définis dans un `<srcschema>` n’affecte pas la séquence de création de champ dans la base de données. La séquence de création sera alphabétique.

## Description des attributs {#attribute-description}

* **_operation (string)**: définit le type d&#39;écriture dans la base.

   Cet attribut est principalement utilisé lors d&#39;une extension de schéma usine.

   Les valeurs accessibles sont:

   * &quot;none&quot; : Réconciliation seule. Signifie qu&#39;Adobe Campaign va retrouver l&#39;élément sans le mettre à jour ou générer une erreur s&#39;il n&#39;existe pas.
   * &quot;insertOrUpdate&quot; : Mise à jour avec insertion. Signifie qu&#39;Adobe Campaign va mettre à jour l&#39;élément ou le créer s&#39;il n&#39;existe pas.
   * &quot;insert&quot; : Insertion. Signifie qu&#39;Adobe Campaign va insérer l&#39;élément sans vérifier s&#39;il existe.
   * &quot;update&quot; : Mise à jour. Signifie qu&#39;Adobe Campaign va mettre à jour l&#39;élément ou générer une erreur s&#39;il n&#39;existe pas.
   * &quot;delete&quot; : Suppression. Signifie qu&#39;Adobe Campaign va retrouver et supprimer l&#39;élément.

* **advanced (boolean)**: quand cette option est activée (@advanced=&quot;true&quot;), elle permet de masquer l&#39;élément dans la liste des champs disponibles et accessibles pour la configuration d&#39;une liste dans un formulaire.
* **applicableIf (string)** : cet attribut vous permet de rendre les champs facultatifs. L’élément `<attribute>` sera pris en compte lors de la mise à jour de la base de données lorsque la contrainte sera respectée. &quot;applicableIf&quot; reçoit une expression XTK.
* **autoIncrement (boolean)**: si cette option est activée, le champ devient un compteur. Cela permet d&#39;incrémenter une valeur (le plus souvent un ID).(usage interne)
* **belongsTo (string)**: prend le nom et l’espace de noms de la table qui partage le champ - renseigne le schéma où est déclaré l&#39;attribut. (utilisé uniquement dans un `<schema>`).
* **dataPolicy (string)**: permet de préciser des contraintes de validation sur les valeurs permises dans le champ de type SQL ou XML, les valeurs pour cet attribut sont :

   * &quot;none&quot; : pas de valeur
   * &quot;smartCase&quot;: premières lettres en majuscule
   * &quot;lowerCase&quot;: tout en minuscule
   * &quot;upperCase&quot;: tout en majuscule
   * &quot;email&quot; : adresse email
   * &quot;phone&quot;: numéro de téléphone
   * &quot;identifier&quot;: nom d&#39;identifiant
   * &quot;resIdentifier&quot;: nom de fichier

* **dbEnum (string)**: reçoit le nom interne d&#39;une énumération &quot;fermée&quot;. Les valeurs de l&#39;énumération doivent être définies dans le `<srcschema>`.
* **defOnDuplicate (boolean)**: si cet attribut est activé, lors de la duplication d&#39;un enregistrement, la valeur par défaut (définie dans &quot;@default&quot;) est réappliquée automatiquement à l&#39;enregistrement.
* **default (string)**: permet de définir la valeur du champ par défaut (appel à une fonction, valeur par défaut). Cet attribut reçoit une expression XTK.
* **desc (string)**: permet d&#39;insérer une description de l&#39;attribut. Cette description s&#39;affiche dans la barre de statut de l&#39;interface.
* **edit (string)**: cet attribut précise le type d&#39;input qui sera utilisé dans le formulaire associé au schéma.
* **enum (string)**: reçoit le nom de l&#39;énumération associé au champ. L&#39;énumération peut être insérée dans le même schéma ou bien dans un schéma distant. L&#39;énumération définie une liste fermée de valeurs.
* **expr (string)**: définit une expression de précalcul du champ. Cet attribut reçoit un Xpath ou une expression XTK.
* **feature (string)**: définit un champ de caractéristiques. Les champs de caractéristiques sont utilisés pour étendre les données d&#39;une table existante, mais avec un stockage déporté dans une table annexe. Les valeurs acceptées sont :

   * &quot;shared&quot; : le contenu est stocké dans une table partagée par type de données
   * &quot;dedicated&quot; : le contenu est stocké dans une table dédiée

   Les tables SQL de caractéristiques sont construites automatiquement en fonction du type de la caractéristique :

   * dédié : `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   Deux types de champs de caractéristiques sont disponibles : les champs simples oà¹ une seule valeur est autorisée sur la caractéristique et les champs à choix multiples oà¹ la caractéristique est associée à un élément de collection qui peut donc contenir plusieurs valeurs.

   Lorsque une caractéristique est définie dans un schéma, ce schéma doit comporter une clef principale basé sur un seul champ (clef composite non autorisée).

* **featureDate (boolean)**: attribut associé au champ de caractéristiques &quot;feature&quot;, si sa valeur est &quot;true&quot;, il permet de connaître la date de la dernière mise à jour de la valeur.
* **img (string)**: permet de définir un chemin pour une image associée à un champ (namespace + nom de l&#39;image)(exemple : img=&quot;cus:mypicture.jpg&quot;). Physiquement l&#39;image doit être importée sur le serveur applicatif.
* **label (string)**: libellé associé au champ, le plus souvent destiné à l&#39;utilisateur dans l&#39;interface. Il permet d&#39;éviter les contraintes de nommage.
* **length (string)**: nombre de caractères maximal autorisés pour une valeur du champ SQL de type &quot;string&quot;. Si l&#39;attribut &quot;@length&quot; n&#39;est pas précisé, Adobe Campaign crée automatiquement un champ de 255 caractères.
* **localizable (boolean)**: s&#39;il est activé, cet attribut indique à l&#39;outil de collecte de récupérer la valeur de l&#39;attribut &quot;@label&quot; pour traduction (usage interne).
* **name (MNTOKEN)**: nom de l&#39;attribut qui correspondra au nom du champ dans la table. La valeur de l&#39;attribut &quot;@name&quot; doit être courte, de préférence en anglais et elle doit respecter les contraintes de nommage liées au XML.

   Lors de l&#39;écriture du schéma en base, des préfixes sont automatiquement rajoutés par Adobe Campaign au nom du champ:

   * &quot;i&quot; : préfixe pour le type &#39;entier&#39;.
   * &quot;d&quot; : préfixe pour le type &#39;double&#39;.
   * &quot;s&quot; : préfixe pour le type chaine de caractère.
   * &quot;ts&quot; : préfixe pour le type &#39;date&#39;.

   Pour définir intégralement le nom du champ dans la table, il faut utiliser l&#39;option &quot;@sqlname&quot; dans la définition d&#39;un attribut.

* **notNull (boolean)**: permet de redéfinir le comportement de Adobe Campaign concernant la gestion des enregistrements NULL en base de données. Par défaut, les champs numériques sont non-nuls et les champs de type chaîne et date peuvent être nuls.
* **pkgStatus (string)**: durant l&#39;export de package, les valeurs seront prises en compte ou non en fonction de la valeur de l&#39;attribut &quot;@pkgStatus&quot; :

   * &quot;always&quot; : toujours présentes
   * &quot;never&quot; : jamais présente
   * &quot;default (ou rien)&quot; : la valeur est exportée sauf si c&#39;est la valeur par défaut ou bien si ce n&#39;est pas un champ interne qui ne serait pas compatible entre plusieurs instances.

* **ref (string)** : cet attribut définit une référence à un élément `<attribute>` partagé par plusieurs schémas (factorisation des définitions). La définition n’est pas copiée dans le schéma actuel.
* **required (boolean)**: si cet attribut est activé (@required=&quot;true&quot;), le champ est mis en avant dans l&#39;interface. Le label du champ est affiché en rouge dans un formulaire.
* **sql (boolean)**: si cet attribut est activé (@sql=&quot;true&quot;), il force le stockage de l&#39;attribut en SQL même lorsque l&#39;élément contenant l&#39;attribut a la propriété xml=&quot;true&quot;.
* **sqlDefault (string)**: cet attribut permet de définir la valeur par défaut qui sera prise en compte pour la mise à jour de la base de données uniquement si l&#39;attribut &quot;@notNull&quot; est activé. Si cet attribut est ajouté après la création de l’attribut, le comportement du schéma ne change pas, même pour les nouveaux enregistrements. Pour modifier le schéma et mettre à jour la valeur des nouveaux enregistrements, vous devez supprimer et créer à nouveau l’attribut.
* **sqlname (string)**: nom du champ lors de la création de la table. Si &quot;@sqlname&quot; n&#39;est pas précisé la valeur de l&#39;attribut &quot;@name&quot; est pris par défaut. Lors de l&#39;écriture du schéma en base, des préfixes sont automatiquement rajoutés en fonction du type du champ.
* **template (string)** : cet attribut définit une référence à un élément `<attribute>` partagé par plusieurs schémas. La définition est automatiquement copiée dans le schéma actuel.
* **translatedDefault (string)**: si un attribut &quot;@default&quot; est présent, l&#39;attribut &quot;@translatedDefault&quot; permet de redéfinir une expression, correspondante de l&#39;expression définie dans &quot;@default&quot;, qui sera collectée par l&#39;outil de traduction (usage interne).
* **translatedExpr (chaîne)** : si un attribut « @expr » est présent, l’attribut « @translatedExpr » permet de redéfinir une expression, correspondant à l’expression définie dans « @expr », qui sera collectée par l’outil de traduction (usage interne).
* **type (MNTOKEN)**: type du champ.

   Les types de champs sont génériques. C&#39;est en fonction du type de base de donnée installé qu&#39;Adobe Campaign transforme le type défini en valeur propre à la base de données installées lors de la mise à jour de la structure.

   Liste des types disponibles :

   * ANY
   * bin
   * blob
   * boolean
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * double
   * enum
   * float
   * html
   * int64
   * link
   * long
   * memo
   * MNTOKEN
   * percent
   * primarykey
   * short
   * string
   * time
   * timespan
   * uuid

   Si l&#39;attribut &quot;@type&quot; est laissé vide, Adobe Campaign associe par défaut un type chaîne de caractères (STRING) de longueur 100 au champ.

   Si le champ est de type STRING et que le nom du champ n&#39;est pas précisé par la présence de l&#39;attribut &quot;@sqlname&quot;, alors le nom du champ dans la base de données sera automatiquement précédé du caractère &#39;s&#39;. Ce fonctionnement sera similaire avec les champs de type INTEGER (i), DOUBLE (d) et DATE(ts).

* **userEnum (string)**: reçoit le nom interne d&#39;une énumération &quot;ouverte&quot;. Les valeurs de l&#39;énumération peuvent être définies par l&#39;utilisateur dans l&#39;interface.
* **visibleIf (string)**: définit une condition sous la forme d&#39;une expression XTK pour montrer ou masquer l&#39;attribut.

   >[!IMPORTANT]
   >
   >L&#39;attribut est masqué mais ses données sont toujours accessibles.

* **xml (boolean)**: si cette option est activée, les valeurs du champ n&#39;ont pas de champ SQL associé. Adobe Campaign crée un champ &quot;mData&quot; de type Text pour stocker les enregistrements. En conséquence, il n&#39;y a pas de filtrage ni de tri sur ces champs.

### Exemples   {#examples}

Exemple d&#39;énumération dont les valeurs sont stockées en base:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>     
```

Déclaration d&#39;un champ XML avec &quot;@datapolicy&quot;:

```
<attribute dataPolicy="phone" desc="Mobile number" label="Mobile"
     length="32" name="mobilePhone" sqlname="sMobilePhone" type="string"/>
```

Exemple avec un &quot;@applicableIf&quot; : l&#39;attribut &quot;continent&quot; ne sera crée que si le nombre de pays est supérieur au nombre 20.

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

Exemple avec &quot;@feature&quot; de type &quot;shared&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

Exemple avec &quot;@feature&quot; de type &quot;dedicated&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
