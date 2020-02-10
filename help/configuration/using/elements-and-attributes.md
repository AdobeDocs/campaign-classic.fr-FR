---
title: Eléments et attributs
seo-title: Eléments et attributs
description: Eléments et attributs
seo-description: null
page-status-flag: never-activated
uuid: 72b0128a-a453-4646-93e5-b399914abb76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5e24d94a-f9c1-4642-a881-dfc4b5492f14
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f9b3508fee3b441752648258b1bc9d5d2b919791

---


# Eléments et attributs {#elements-and-attributes}

Durant l&#39;édition d&#39;un schéma, un système de validation basé sur le schéma source (xtk:srcSchema) est accessible. Cependant certaines erreurs peuvent être remontées lors de la mise à jour de la base de données via l&#39;assistant &quot;Mise à jour de la structure de la base...&quot;.

Par défaut dans les schémas Adobe Campaign, tous les attributs de type boolean sont à &quot;false&quot;. Pour les activer, il faut donc spécifier l&#39;attribut dans le schéma et lui passer la valeur &quot;true&quot;.

## `<attribute>` element {#attribute--element}

### Modèle de contenu {#content-model}

attribute:==help

### Attributs {#attributes}

_operation (string), advanced (boolean), applicableIf (string), autoIncrement (boolean), belongsTo (string), dataPolicy (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), edit (string), enum (string), expr (string), feature (string), featureDate (boolean), img (string), inout (string), label (string), length (string), localizable (boolean), name (MNTOKEN), notNull (boolean), pkgStatus (string), ref (string), required (boolean), sql (boolean), sqlDefault (string), sqlname (string), sqltable (string), target (MNTOKEN), template (string), translatedDefault (string), translatedExpr (string), type (MNTOKEN), user (boolean), userEnum (string), visibleIf (string), xml (boolean)

### Parents {#parents}

`<element>`

### Enfants {#children}

`<help>`

### Description {#description}

`<attribute>` permet de définir un champ dans la base de données.

### Usage et contexte d&#39;utilisation {#use-and-context-of-use}

`<attribute>` doit être déclarée dans un `<element>` élément.

La séquence dans laquelle `<attribute>` les éléments sont définis dans une `<srcschema>` n’affecte pas la séquence de création de champ dans la base de données. La séquence de création sera alphabétique.

### Description des attributs {#attribute-description}

* **_operation (string)**: définit le type d&#39;écriture dans la base.

   Cet attribut est principalement utilisé lors d&#39;une extension de schéma usine.

   Les valeurs accessibles sont:

   * &quot;none&quot; : Réconciliation seule. Signifie qu&#39;Adobe Campaign va retrouver l&#39;élément sans le mettre à jour ou générer une erreur s&#39;il n&#39;existe pas.
   * &quot;insertOrUpdate&quot; : Mise à jour avec insertion. Signifie qu&#39;Adobe Campaign va mettre à jour l&#39;élément ou le créer s&#39;il n&#39;existe pas.
   * &quot;insert&quot; : Insertion. Signifie qu&#39;Adobe Campaign va insérer l&#39;élément sans vérifier s&#39;il existe.
   * &quot;update&quot; : Mise à jour. Signifie qu&#39;Adobe Campaign va mettre à jour l&#39;élément ou générer une erreur s&#39;il n&#39;existe pas.
   * &quot;delete&quot; : Suppression. Signifie qu&#39;Adobe Campaign va retrouver et supprimer l&#39;élément.

* **advanced (boolean)**: quand cette option est activée (@advanced=&quot;true&quot;), elle permet de masquer l&#39;élément dans la liste des champs disponibles et accessibles pour la configuration d&#39;une liste dans un formulaire.
* **applicableIf (chaîne)**: cet attribut vous permet de rendre les champs facultatifs. L’ `<attribute>` élément sera pris en compte lors de la mise à jour de la base de données lorsque la contrainte sera respectée. &quot;applicableIf&quot; reçoit une expression XTK.
* **autoIncrement (boolean)**: si cette option est activée, le champ devient un compteur. Cela permet d&#39;incrémenter une valeur (le plus souvent un ID).(usage interne)
* **belongsTo (string)**: prend le nom et le namespace de la table qui partage le champ - renseigne le schéma oà¹ est déclaré l&#39;attribut. (utilisé uniquement dans un `<schema>`).
* **dataPolicy (string)**: permet de préciser des contraintes de validation sur les valeurs permises dans le champ de type SQL ou XML, les valeurs pour cet attribut sont :

   * &quot;none&quot; : pas de valeur
   * &quot;smartCase&quot;: premières lettres en majuscule
   * &quot;lowerCase&quot;: tout en minuscule
   * &quot;upperCase&quot;: tout en majuscule
   * &quot;email&quot;: adresse email
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
* **feature (string)**: définit un champ de caractéristiques. Les champs de caractéristiques sont utilisés pour étendre les données d&#39;une table existante, mais avec un stockage déporté dans une table annexe. Les valeurs acceptées sont :

   * &quot;shared&quot; : le contenu est stocké dans une table partagée par type de données
   * &quot;dedicated&quot; : le contenu est stocké dans une table dédiée
   Les tables SQL de caractéristiques sont construites automatiquement en fonction du type de la caractéristique :

   * dédié : `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`
   Deux types de champs de caractéristiques sont disponibles : les champs simples oà¹ une seule valeur est autorisée sur la caractéristique et les champs à choix multiples oà¹ la caractéristique est associée à un élément de collection qui peut donc contenir plusieurs valeurs.

   Lorsque une caractéristique est définie dans un schéma, ce schéma doit comporter une clef principale basé sur un seul champ (clef composite non autorisée).

* **featureDate (boolean)**: attribut associé au champ de caractéristiques &quot;feature&quot;, si sa valeur est &quot;true&quot;, il permet de connaître la date de la dernière mise à jour de la valeur.
* **img (string)**: permet de définir un chemin pour une image associée à un champ (namespace + nom de l&#39;image)(exemple : img=&quot;cus:mypicture.jpg&quot;). Physiquement l&#39;image doit être importée sur le serveur applicatif.
* **label (string)**: libellé associé au champ, le plus souvent destiné à l&#39;utilisateur dans l&#39;interface. Il permet d&#39;éviter les contraintes de nommage.
* **length (string)**: nombre de caractères maximal autorisés pour une valeur du champ SQL de type &quot;string&quot;. Si l&#39;attribut &quot;@length&quot; n&#39;est pas précisé, Adobe Campaign crée automatiquement un champ de 255 caractères.
* **localizable (boolean)**: s&#39;il est activé, cet attribut indique à l&#39;outil de collecte de récupérer la valeur de l&#39;attribut &quot;@label&quot; pour traduction (usage interne).
* **name (MNTOKEN)**: nom de l&#39;attribut qui correspondra au nom du champ dans la table. La valeur de l&#39;attribut &quot;@name&quot; doit être courte, de préférence en anglais et elle doit respecter les contraintes de nommage liées au XML.

   Lors de l&#39;écriture du schéma en base, des préfixes sont automatiquement rajoutés par Adobe Campaign au nom du champ:

   * &quot;i&quot; : préfixe pour le type &#39;entier&#39;.
   * &quot;d&quot; : préfixe pour le type &#39;double&#39;.
   * &quot;s&quot; : préfixe pour le type chaine de caractère.
   * &quot;ts&quot; : préfixe pour le type &#39;date&#39;.
   Pour définir intégralement le nom du champ dans la table, il faut utiliser l&#39;option &quot;@sqlname&quot; dans la définition d&#39;un attribut.

* **notNull (boolean)**: permet de redéfinir le comportement de Adobe Campaign concernant la gestion des enregistrements NULL en base de données. Par défaut, les champs numériques sont non-nuls et les champs de type chaîne et date peuvent être nuls.
* **pkgStatus (string)**: durant l&#39;export de package, les valeurs seront prises en compte ou non en fonction de la valeur de l&#39;attribut &quot;@pkgStatus&quot; :

   * &quot;always&quot; : toujours présentes
   * &quot;never&quot; : jamais présente
   * &quot;default (ou rien)&quot; : la valeur est exportée sauf si c&#39;est la valeur par défaut ou bien si ce n&#39;est pas un champ interne qui ne serait pas compatible entre plusieurs instances.

* **ref (string)**: cet attribut définit une référence à un `<attribute>` élément partagé par plusieurs schémas (factorisation des définitions). La définition n’est pas copiée dans le schéma actuel.
* **required (boolean)**: si cet attribut est activé (@required=&quot;true&quot;), le champ est mis en avant dans l&#39;interface. Le label du champ est affiché en rouge dans un formulaire.
* **sql (boolean)**: si cet attribut est activé (@sql=&quot;true&quot;), il force le stockage de l&#39;attribut en SQL même lorsque l&#39;élément contenant l&#39;attribut a la propriété xml=&quot;true&quot;.
* **sqlDefault (string)**: cet attribut permet de définir la valeur par défaut qui sera prise en compte pour la mise à jour de la base de données uniquement si l&#39;attribut &quot;@notNull&quot; est activé. Si cet attribut est ajouté après la création de l’attribut, le comportement du schéma ne changera même pas pour les nouveaux enregistrements. Pour modifier le schéma et mettre à jour la valeur des nouveaux enregistrements, vous devez supprimer et créer à nouveau l’attribut.
* **sqlname (string)**: nom du champ lors de la création de la table. Si &quot;@sqlname&quot; n&#39;est pas précisé la valeur de l&#39;attribut &quot;@name&quot; est pris par défaut. Lors de l&#39;écriture du schéma en base, des préfixes sont automatiquement rajoutés en fonction du type du champ.
* **template (chaîne)**: cet attribut définit une référence à un `<attribute>` élément partagé par plusieurs schémas. La définition est automatiquement copiée dans le schéma actuel.
* **translatedDefault (string)**: si un attribut &quot;@default&quot; est présent, l&#39;attribut &quot;@translatedDefault&quot; permet de redéfinir une expression, correspondante de l&#39;expression définie dans &quot;@default&quot;, qui sera collectée par l&#39;outil de traduction (usage interne).
* **translatedExpr (string)**: si un attribut &quot;@expr&quot; est présent, l&#39;attribut &quot;@translatedExpr&quot; permet de redéfinir une expression, correspondante de l&#39;expression définie dans &quot;@expr&quot;, qui sera collectée par l&#39;outil de traduction (usage interne).
* **type (MNTOKEN)**: type du champ.

   Les types de champs sont génériques. C&#39;est en fonction du type de base de donnée installé qu&#39;Adobe Campaign transforme le type défini en valeur propre à la base de données installées lors de la mise à jour de la structure.

   Liste des types disponibles :

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
   Si l&#39;attribut &quot;@type&quot; est laissé vide, Adobe Campaign associe par défaut un type chaîne de caractères (STRING) de longueur 100 au champ.

   Si le champ est de type STRING et que le nom du champ n&#39;est pas précisé par la présence de l&#39;attribut &quot;@sqlname&quot;, alors le nom du champ dans la base de données sera automatiquement précédé du caractère &#39;s&#39;. Ce fonctionnement sera similaire avec les champs de type INTEGER (i), DOUBLE (d) et DATE(ts).

* **userEnum (string)**: reçoit le nom interne d&#39;une énumération &quot;ouverte&quot;. Les valeurs de l&#39;énumération peuvent être définies par l&#39;utilisateur dans l&#39;interface.
* **visibleIf (string)**: définit une condition sous la forme d&#39;une expression XTK pour montrer ou masquer l&#39;attribut.

   >[!CAUTION]
   >
   >L&#39;attribut est masqué mais ses données sont toujours accessibles.

* **xml (boolean)**: si cette option est activée, les valeurs du champ n&#39;ont pas de champ SQL associé. Adobe Campaign crée un champ &quot;mData&quot; de type Text pour stocker les enregistrements. En conséquence, il n&#39;y a pas de filtrage ni de tri sur ces champs.

### Exemples {#examples}

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

Exemple avec un &quot;@applicableIf&quot; : l&#39;attribut &quot;continent&quot; ne sera crée que si le nombre de pays est supérieur au nombre 20.

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

## `<compute-string>` element {#compute-string--element}

### Modèle de contenu {#content-model-1}

compute-string:==EMPTY

### Attributs {#attributes-1}

@expr

### Parents {#parents-1}

`<element>`

### Enfants {#children-1}

Aucun

### Description {#description-1}

The `<compute-string>` element enables you to generate a string based on an XTK expression to display a &quot;built&quot; label in the interface based on several values.

### Usage et contexte d&#39;utilisation {#use-and-context-of-use-1}

When no `<compute-string>` is defined, a `<compute-string>` element is entered by default with the values of the primary key in the schema.

### Description des attributs {#attribute-description-1}

* **expr (string)**: expression XTK et/ou Xpath.

### Exemples {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Résultat de la chaîne calculée sur un destinataire : &quot;Dupont René (rene.dupont@aol.com)&quot; :

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```

## `<condition>` element {#condition--element}

### Modèle de contenu {#content-model-2}

condition:==EMPTY

### Attributs {#attributes-2}

* @boolOperator (string)
* @enabledIf (string)
* @expr (string)

### Parents {#parents-2}

`<sysfilter>`

### Enfants {#children-2}

Aucun

### Description {#description-2}

Cet élément permet de définir une condition de filtrage.

### Usage et contexte d&#39;utilisation {#use-and-context-of-use-2}

One `<sysfiler>`  element can contain several filtering conditions.

### Description des attributs {#attribute-description-2}

* **boolOperator (chaîne)**: si plusieurs `<conditions>` sont définis dans le même `<sysfilter>` élément, cet attribut vous permet de les combiner. Par défaut, le lien logique entre `<condition>` les éléments est &quot;AND&quot;. L’attribut &quot;@boolOperator&quot; permet de combiner des liens de type &quot;OR&quot; et &quot;AND&quot;.
* **enabledIf (string)**: test d&#39;activation de la condition.
* **expr (string)**: une expression XTK.

### Exemples {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```

## `<dbindex>` element {#dbindex--element}

### Modèle de contenu {#content-model-3}

dbindex:==keyfield

### Attributs {#attributes-3}

* @_operation (string)
* @applicableIf (string)
* @label (string)
* @name (MNTOKEN)
* @unique (boolean)

### Parents {#parents-3}

`<element>`

### Enfants {#children-3}

`<keyfield>`

### Description {#description-3}

Cet élément permet de définir un index associé à une table.

### Usage et contexte d&#39;utilisation {#use-and-context-of-use-3}

Il est possible de définir plusieurs index. Un index peut référencer un ou plusieurs champs de la table. Généralement, la déclaration des index suit la définition de l&#39;élément principal du schéma.

L&#39;ordre des `<keyfield>` éléments définis dans un `<dbindex>` est très important. Le premier `<keyfield>` doit être le critère d&#39;indexation sur lequel reposent principalement les requêtes.

Le nom de l&#39;index en base est calculé par concaténation du nom de la table et du nom de l&#39;index. Exemple : Nom de la table : &quot;Sample&quot;, Namespace : &quot;Cus&quot;, nom de l&#39;index : &quot;MyIndex&quot; - nom du champ de l&#39;index lors de la requête de création de l&#39;index en table : &quot;CusSample_myIndex&quot;.

### Description des attributs {#attribute-description-3}

* **_operation (string)**: définit le type d&#39;écriture dans la base.

   Cet attribut est principalement utilisé lors d&#39;une extension de schéma usine.

   Les valeurs accessibles sont:

   * &quot;none&quot; : Réconciliation seule. Signifie qu&#39;Adobe Campaign va retrouver l&#39;élément sans le mettre à jour ou générer une erreur s&#39;il n&#39;existe pas.
   * &quot;insertOrUpdate&quot; : Mise à jour avec insertion. Signifie qu&#39;Adobe Campaign va mettre à jour l&#39;élément ou le créer s&#39;il n&#39;existe pas.
   * &quot;insert&quot; : Insertion. Signifie qu&#39;Adobe Campaign va insérer l&#39;élément sans vérifier s&#39;il existe.
   * &quot;update&quot; : Mise à jour. Signifie qu&#39;Adobe Campaign va mettre à jour l&#39;élément ou générer une erreur s&#39;il n&#39;existe pas.
   * &quot;delete&quot; : Suppression. Signifie qu&#39;Adobe Campaign va retrouver et supprimer l&#39;élément.

* **applicableIf (string)**: condition de prise en compte de l&#39;index - reçoit une XTK expression.
* **label (string)**: libellé de l&#39;index.
* **name (MNTOKEN)**: nom unique de l&#39;index.
* **unique (boolean)**: si cette option est activée (@unique=&quot;true&quot;), alors cet attribut garantie l&#39;unicité de l&#39;index sur l&#39;ensemble des champs qui le composent.

### Exemples {#examples-3}

Création d’un index sur le champ &quot;id&quot;. (l’attribut &quot;@unique&quot; sur l’ `<dbindex>` élément déclenche l’ajout du mot clé SQL &quot;UNIQUE&quot; lorsque l’index est créé dans la base de données (requête)).

```
<element label="Sample" name="Sample">
  <dbindex name="myIndex" label="My index on the ID field" unique="true" applicableIf="HasPackage('nms:social')">
      <keyfield xpath="@id"/>
  </dbindex>
    <attribute name="id" type="long"/>
</element>          
```

```
ALTER TABLE CusSample ADD iSampleId INTEGER;
UPDATE CusSample SET iSampleId = 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET Default 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET NOT NULL; 
CREATE UNIQUE INDEX CusSample_myIndex ON CusSample(iSampleId);
```

Création d&#39;un index composite sur les champs &quot;@mail&quot; et &quot;@phoneNumber&quot;:

```
<element label="NewSchemaUser" name="NewSchemaUser">
  <dbindex name="myIndex" label="My composite index">
         <keyfield xpath="@email"/>
         <keyfield xpath="@phone"/>
  </dbindex>
  
  <attribute name="email" type="string"/>
  <attribute name="phone" type="string"/>
</element>      
```

```
CREATE INDEX DocNewSchemaUser_myIndex ON DocNewSchemaUser(sEmail, sPhone);
```

## `<element>` element {#element--element}

### Modèle de contenu {#content-model-4}

element:==(attribute | compute-string | dbindex | default | element | help | join | key | sysFilter | translatedDefault)

### Attributs {#attributes-4}

_operation (string), advanced (boolean), aggregate (string), applicableIf (string), autopk (boolean), belongsTo (string), convDate (string), dataPolicy (string), dataSource (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), displayAsField (boolean), doesNotSupportDiff (boolean), edit (string), emptyKeyValue (string), enum (string), enumImage (string), expandSchemaTarget (string), expr (string), externalJoin (boolean), feature (string), featureDate (boolean), filterPath (string), folderLink (string), folderModel (string), folderProcess (string), fullLoad (boolean), hierarchical (boolean), hierarchicalPath (string), img (string), inout (string), integrity (string), label (string), labelSingular (string), length (string), localizable (boolean), name (MNTOKEN), noDbIndex (boolean), noKey (boolean), ordered (boolean), overflowtable (boolean), pkSequence (string), pkgStatus (string), ref (string), required (boolean), revAdvanced (boolean), revCardinality (string), revDesc (string), revExternalJoin (boolean), revIntegrity (string), revLabel (string), revLink (string), revTarget (string), revVisibleIf (string), sql (boolean), sqlname (string), sqltable (string), tableSpace (string), tableSpaceIndex (string), target (MNTOKEN), template (string), temporaryTable (boolean), translatedDefault (string), translatedExpr (string), type (MNTOKEN), unbound (boolean), user (boolean), userEnum (string), visibleIf (string), xml (boolean), xmlChildren (boolean)

### Parents {#parents-4}

`<srcschema>`

`<element>`

### Enfants {#children-4}

* `<attribute>`
* `<compute-string>`
* `<dbindex>`
* `<default>`
* `<element>`
* `<help>`
* `<join>`
* `<key>`
* `<sysfilter>`
* `<translateddefault>`

### Description {#description-4}

There are four types of `<element>`  elements in Adobe Campaign:

* Root `<element>`  : defines the name of the SQL table that matches the schema.
* Structure `<element>`  : defines a group of  `<element>`   or   `<attribute>`    elements.
* Lien `<element>` : définit un lien. Ces éléments doivent inclure l’attribut &quot;@type=link&quot;.
* XML `<element>` : définit un champ de type Texte &quot;mData&quot;. Cet élément doit inclure l’attribut &quot;@type=xml&quot;.

### Description des attributs {#attribute-description-4}

* **_operation (string)**: définit le type d&#39;écriture dans la base.

   Cet attribut est principalement utilisé lors d&#39;une extension de schéma usine.

   Les valeurs accessibles sont:

   * &quot;none&quot; : Réconciliation seule. Signifie qu&#39;Adobe Campaign va retrouver l&#39;élément sans le mettre à jour ou générer une erreur s&#39;il n&#39;existe pas.
   * &quot;insertOrUpdate&quot; : Mise à jour avec insertion. Signifie qu&#39;Adobe Campaign va mettre à jour l&#39;élément ou le créer s&#39;il n&#39;existe pas.
   * &quot;insert&quot; : Insertion. Signifie qu&#39;Adobe Campaign va insérer l&#39;élément sans vérifier s&#39;il existe.
   * &quot;update&quot; : Mise à jour. Signifie qu&#39;Adobe Campaign va mettre à jour l&#39;élément ou générer une erreur s&#39;il n&#39;existe pas.
   * &quot;delete&quot; : Suppression. Signifie qu&#39;Adobe Campaign va retrouver et supprimer l&#39;élément.

* **advanced (boolean)**: quand cette option est activée (@advanced=&quot;true&quot;), elle permet de masquer l&#39;élément dans la liste des champs disponibles et accessibles pour la configuration d&#39;une liste dans un formulaire.
* **agrégat (chaîne)**: vous permet de copier la définition d’un schéma `<element>` via un autre schéma. Cet attribut reçoit une déclaration de schéma sous la forme d’un &quot;namespace:name&quot;.
* **applicableIf (string)**: condition d&#39;applicabilité de l&#39;élément. Cet attribut reçoit une expression XTK.
* **autopk (boolean)**: si cette option est activée (autopk=&quot;true&quot;), alors une clé unique est automatiquement définie. Cette option ne peut être utilisée que sur l&#39;élément principal du schéma. Attention, Adobe Campaign donne seulement la garantie que la clef générée est unique. Le fait que les valeurs des clefs soient consécutives et incrémentales n&#39;est pas assuré.
* **dataPolicy (string)**: permet de préciser des contraintes de validation sur les valeurs permises dans le champ SQL, les valeurs pour cet attribut sont :

   * &quot;none&quot; : pas de valeur
   * &quot;smartCase&quot;: premières lettres en majuscule
   * &quot;lowerCase&quot;: tout en minuscule
   * &quot;upperCase&quot;: tout en majuscule
   * &quot;email&quot;: adresse email
   * &quot;phone&quot;: numéro de téléphone
   * &quot;identifier&quot;: nom d&#39;identifiant
   * &quot;resIdentifier&quot;: nom de fichier

* **dbEnum (string)**: reçoit le nom interne d&#39;une énumération &quot;fermée&quot;. Les valeurs de l&#39;énumération doivent être définies dans le `<srcschema>`.
* **defOnDuplicate (boolean)**: si cet attribut est activé, lors de la duplication d&#39;un enregistrement, la valeur par défaut (définie dans &quot;@default&quot;) est réappliquée automatiquement à l&#39;enregistrement.
* **default (string)**: permet de définir le comportement de l&#39;élément (appel à une fonction, valeur par défaut). Cet attribut reçoit une expression XTK.
* **desc (string)**: permet d&#39;insérer une description de l&#39;élément. Cette description s&#39;affiche dans la barre de statut de l&#39;interface.
* **displayAsField (booléen)**: si cet attribut est activé, un type de &quot;lien&quot; `<element>` s’affiche sous forme de champ dans l’arborescence des schémas (onglet &quot;Structure&quot;). De cette façon, il est possible d&#39;afficher un lien en tant que champ local et de modifier son comportement pendant une requête. Lorsque l&#39;élément est trouvé dans le SELECT d&#39;une requête, la valeur de la cible du lien est utilisée. Lorsque l’élément est trouvé dans l’OÙ d’une requête, la clé sous-jacente du lien est utilisée.
* **edit (string)**: cet attribut précise le type d&#39;input qui sera utilisé dans le formulaire associé à l&#39;élément du schéma en cours de définition.
* **enum (string)**: reçoit le nom de l&#39;énumération associé au champ. L&#39;énumération peut être insérée dans le même schéma ou bien dans un schéma distant. L&#39;énumération définie une liste fermée de valeurs.
* **expr (string)**: cet attribut définit un champ calculé dont la définition n&#39;est pas stockée dans la table. Il reçoit un Xpath ou une expression XTK.
* **externalJoin (boolean)**: jointure externe dans un élément de type &quot;link&quot;.
* **feature (string)**: définit un champ de caractéristiques. Les champs de caractéristiques sont utilisés pour étendre les données d&#39;une table existante, mais avec un stockage déporté dans une table annexe. Les valeurs acceptées sont :

   * &quot;shared&quot; : le contenu est stocké dans une table partagée par type de données
   * &quot;dedicated&quot; : le contenu est stocké dans une table dédiée
   Les tables SQL de caractéristiques sont construites automatiquement en fonction du type de la caractéristique :

   * dédié : `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`
   Deux types de champs de caractéristiques sont disponibles : les champs simples où une seule valeur est autorisée sur la caractéristique et les champs à choix multiples où la caractéristique est associée à un élément de collection qui peut donc contenir plusieurs valeurs.

   Lorsque une caractéristique est définie dans un schéma, ce schéma doit comporter une clef principale basé sur un seul champ (clef composite non autorisée).

* **featureDate (boolean)**: attribut associé au champ de caractéristiques &quot;feature&quot;, si sa valeur est &quot;true&quot;, il permet de connaître la date de la dernière mise à jour de la valeur.
* **filterPath (string)**: cet attribut reçoit un Xpath et permet de définir un filtre sur un champ.
* **folderLink (string)**: cet attribut reçoit le nom du lien qui permet de retrouver les dossiers dans lesquels sont stockés les entités.
* **folderModel (string)**: définit le type de dossier permettant le stockage des entités. Cet attribut n&#39;est défini que si &quot;@folderLink&quot; est présent.
* **folderProcess (string)**: définit le lien dans lequel est stocké les instances des modèles des entités. Cet attribut n&#39;est défini que si &quot;@folderLink&quot; est présent.
* **fullLoad (boolean)**: cet attribut force l&#39;affichage de tous les enregistrements d&#39;une table lors de la sélection du champ dans un formulaire.
* **img (string)**: reçoit le chemin d&#39;une image associée a l&#39;élément. La valeur de cet attribut est de la forme &quot;namespace:nom de l&#39;image&quot;. Exemple : img=&quot;cus:monImage.jpg&quot;. Physiquement l&#39;image doit être importée sur le serveur applicatif.
* **integrity (string)**: intégrité référentielle de l&#39;occurrence de la table source envers la table cible.

   Les valeurs accessibles sont:

   * &quot;define&quot; : Adobe Campaign ne supprime pas l&#39;entité si elle est référencée à partir du lien
   * &quot;normal&quot; : la suppression de l&#39;occurrence source initialise les clés du lien sur l&#39;occurrence cible (mode par défaut), ce type d&#39;intégrité initiliase toutes les clés étrangères
   * &quot;own&quot; : la suppression de l&#39;occurrence source entraîne la suppression de l&#39;occurrence cible
   * &quot;owncopy&quot; : similaire à &quot;own&quot; (en cas de suppression) ou duplique les occurrences (en cas de duplication)
   * &quot;neutral&quot; : ne fait rien

* **label (string)**: libellé de l&#39;élément.
* **labelSingular (string)**: libellé au singulier de l&#39;élément ; utilisé dans certaines parties de l&#39;interface.
* **length (string)**: nombre de caractères maximal autorisés pour une valeur du champ SQL de type &quot;STRING&quot;.
* **localizable (boolean)**: s&#39;il est activé, cet attribut indique à l&#39;outil de collecte de récupérer la valeur de l&#39;attribut &quot;@label&quot; pour traduction (usage interne).
* **name (MNTOKEN)**: nom interne de l&#39;élément qui correspondra au nom de la table. La valeur de l&#39;attribut &quot;@name&quot; doit être courte, de préférence en anglais et elle doit respecter les contraintes de nommage liées au XML.

   Lors de l&#39;écriture du schéma en base, des préfixes sont automatiquement rajoutées par Adobe Campaign au nom du champ.

   * &quot;i&quot; : préfixe pour le type &#39;entier&#39;.
   * &quot;d&quot; : préfixe pour le type &#39;double&#39;.
   * &quot;s&quot; : préfixe pour le type chaine de caractère.
   * &quot;ts&quot; : préfixe pour le type &#39;date&#39;.
   Pour définir de manière autonome le nom de la table, il faut utiliser l&#39;attribut &quot;@sqltable&quot; dans la définition de l&#39;élément principal du schéma.

* **noDbIndex (boolean)**: permet de préciser que l&#39;élément ne sera pas indexé.
* **ordered (boolean)**: si l&#39;attribut est activé (ordered=&quot;true&quot;), Adobe Campaign maintient l&#39;ordre de déclaration des éléments dans un élément de collection XML.
* **pkSequence (string)**: reçoit le nom de la séquence à utiliser pour le calcul d&#39;une clef auto-incrémentale. Cet attribut n&#39;est utilisable que si une clef autoincrémentale est définie sur l&#39;élément racine du schéma.
* **pkgStatus (string)**: durant l&#39;export de package, les valeurs seront prises en compte ou non en fonction de la valeur de cet attribut :

   * &quot;always&quot; : l&#39;élément sera toujours présent
   * &quot;never&quot; : l&#39;élément ne sera jamais présent
   * &quot;default (ou rien)&quot; : l&#39;élement est exporté sauf si c&#39;est l&#39;élément par défaut ou bien si ce n&#39;est pas un champ interne qui ne serait pas compatible entre instances

* **ref (string)**: cet attribut définit une référence vers un élément &lt;element> partagé par plusieurs schémas (factorisation des définitions). La définition n&#39;est pas recopiée dans le schéma courant.
* **required (boolean)**: si cet attribut est activé (@required=&quot;true&quot;), le champ est mis en avant dans l&#39;interface. Le label du champ est affiché en rouge dans un formulaire.
* **revAdvanced (boolean)**: s&#39;il est activé, cet attribut précise que le lien inverse est de type &quot;advanced&quot;.
* **revCardinality (chaîne)**: cet attribut définit la cardinalité d’un lien entre deux tables. Il est utilisé dans un type de &quot;lien&quot; `<element>`.

   Les valeurs possibles sont les suivantes :

   * &quot;single&quot; : Lien simple de type 1-1
   * &quot;unbound&quot; : Lien de collection de type 1-N
   Par défaut, si l&#39;attribut n&#39;est pas précisé lors de la création du lien, la cardinalité est de type 1-N.

* **revDesc (string)**: cet attribut reçoit une description associée au lien inverse.
* **revExternalJoin (boolean)**: s&#39;il est activé, cet attribut permet de forcer la jointure externe sur le lien inverse.
* **revIntegrity (string)**: cet attribut définit l&#39;intégrité sur le schéma cible. Les mêmes valeurs que l&#39;attribut &quot;@integrity&quot; sont autorisés. Par défaut, Adobe Campaign donne la valeur &quot;normal&quot; à cet attribut.
* **revLabel (string)**: libellé du lien inverse.
* **revLink (chaîne)**: nom du lien opposé. Si la valeur est &quot;_NONE_&quot;, aucun lien opposé n’est créé dans le schéma de destination.
* **revTarget (string)**: cible du lien inverse.
* **sql (boolean)**: si cet attribut est activé (@sql=&quot;true&quot;), il force le stockage de l&#39;élément en SQL même lorsque l&#39;élément a la propriété xml=&quot;true&quot;.
* **sqlname (string)**: nom du champ lors de la création de la table. Si &quot;@sqlname&quot; n&#39;est pas précisé la valeur de l&#39;attribut &quot;@name&quot; est pris par défaut. Lors de l&#39;écriture du schéma en table des préfixes seront automatiquement rajoutés en fonction du type du champ.
* **sqltable (string)**: pour l&#39;élément principal du schéma, cet attribut surcharge le nom de la table SQL généré par défaut. Si &quot;@sqltable&quot; n&#39;est pas précisé le nom par défaut est de la forme: namespace (avec la première lettre en majuscule) et la valeur du &quot;@name&quot; du SrcSchema.
* **tableSpace (chaîne)**: cet attribut vous permet de spécifier une nouvelle donnée stockant un espace disque logique pour une table (valide à la racine `<element>`).
* **tableSpaceIndex (chaîne)**: cet attribut vous permet de spécifier un nouvel espace disque logique de stockage d&#39;index pour une table (valide à la racine `<element>`).
* **target (MNTOKEN)**: reçoit le nom du schéma cible lors de la création d&#39;un lien entre tables. Cet attribut n&#39;est actif que si l&#39;élément est de type &quot;link&quot;.
* **template (chaîne)**: cet attribut définit une référence à un `<element>` élément partagé par plusieurs schémas. La définition est automatiquement copiée dans le schéma actuel.
* **translatedDefault (string)**: si un attribut &quot;@default&quot; est présent, l&#39;attribut &quot;@translatedDefault&quot; permet de redéfinir une expression, correspondante de l&#39;expression définie dans &quot;@default&quot;, qui sera collectée par l&#39;outil de traduction (usage interne).
* **translatedExpr (string)**: si un attribut &quot;@expr&quot; est présent, l&#39;attribut &quot;@translatedExpr&quot; permet de redéfinir une expression, correspondante de l&#39;expression définie dans &quot;@expr&quot;, qui sera collectée par l&#39;outil de traduction (usage interne).
* **type (MNTOKEN)**: définit le type des données stockées dans l&#39;élément.

   Liste des types disponibles :

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

* **unbound (boolean)**: si l&#39;attribut est activé (unbound=&quot;true&quot;), le lien est déclaré comme élément de collection pour une cardinalité 1-N.
* **userEnum (string)**: reçoit le nom interne d&#39;une énumération &quot;ouverte&quot;. Les valeurs de l&#39;énumération peuvent être définies par l&#39;utilisateur dans l&#39;interface.
* **xml (boolean)**: si cette option est activée, l&#39;ensemble des valeurs définies dans l&#39;élément seront stockées en XML dans un champ &quot;mData&quot; de type TEXT. En conséquence, il n&#39;y a pas de filtrage ni de tri sur ces champs.
* **xmlChildren (booléen)**: force le stockage pour chaque enfant ( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`

## `<enumeration>` element {#enumeration--element}

### Modèle de contenu {#content-model-5}

enumeration:==(help| value)

### Attributs {#attributes-5}

* @basetype (string)
* @default (string)
* @desc (string)
* @label (string)
* @name (string)
* @template (string)

### Parents {#parents-5}

`<srcschema>`

### Enfants {#children-5}

* `<help>`
* `<value>`

### Description {#description-5}

Cet élément permet de définir une énumération de valeurs, une énumération appartient au schéma dans laquelle elle est définie mais elle reste accessible depuis un autre schéma.

### Usage et contexte d&#39;utilisation {#use-and-context-of-use-4}

Une énumération se définit au tout début d&#39;un schéma (avant la définition de l&#39;élément principal).

### Description des attributs {#attribute-description-5}

* **basetype (string)**: type des valeurs stockées dans l&#39;énumération.

   Liste des types disponibles :

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
   * DOMDocument
   * DOMElement
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

* **default (string)**: valeur par défaut. La valeur par défaut peut aussi être une des valeurs définies dans l&#39;énumération.
* **desc (string)**: description de l&#39;énumération.
* **label (string)**: libellé de l&#39;énumération.
* **name (string)**: nom interne de l&#39;énumération.
* **template (chaîne)**: cet attribut définit une référence à un `<enumeration>` élément partagé par plusieurs schémas. La définition est automatiquement copiée dans le schéma actuel.

### Exemples {#examples-4}

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

Définition d&#39;un énumération avec une valeur par défaut:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```

## `<help>` element {#help--element}

### Modèle de contenu {#content-model-6}

help:==EMPTY

### Attributs {#attributes-6}

Aucun

### Parents {#parents-6}

`<srcschema>`  ,  `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

### Enfants {#children-6}

Aucun

### Description {#description-6}

Cet élément vous permet de décrire un `<element>` élément ou `<attribute>` un élément. Il ne peut contenir que du texte et est stocké dans XML dans la base de données.

### Description des attributs {#attribute-description-6}

Cet élément n&#39;a aucun attribut.

### Exemples {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```

## `<join>` element {#join--element}

### Modèle de contenu {#content-model-7}

join:==EMPTY

### Attributs {#attributes-7}

* @dstFilterExpr (string)
* @xpath-dst (string)
* @xpath-src (string)

### Parents {#parents-7}

`<element>`

### Enfants {#children-7}

Aucun

### Description {#description-7}

Cet élément permet de définir les champs créant une jointure entre des tables SQL.

### Usage et contexte d&#39;utilisation {#use-and-context-of-use-5}

Un `<join>` élément ne peut être utilisé que si l’ `<element>` élément parent est de type &quot;link&quot;. Cela signifie que l’attribut &quot;@type=link&quot; doit être déclaré pour l’élément parent.

Il n’est pas nécessaire de spécifier le nom et l’espace de noms de la table distante dans l’ `<join>` élément. Ils doivent être spécifiés dans le parent `<element>`.

Par convention, les liens sont définis à la fin du schéma.

If the `<join>` element isn&#39;t specified when the link type element is defined, the link will automatically be placed on the primary keys of both tables.

### Description des attributs {#attribute-description-7}

* **dstFilterExpr (string)** : cet attribut permet de restreindre le nombre de valeurs éligibles dans la table distante.
* **xpath-dst (string)** : cet attribut reçoit un Xpath (attribut &quot;@name&quot; de la table distante).
* **xpath-src (string)** : cet attribut reçoit un Xpath (attribut &quot;@name&quot; dans le schéma courant).

### Exemples {#examples-6}

Lien entre le champ &#39;email&#39; de la table courante et le champ &quot;@compagny-id&quot; de la table distante:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Lien &#39;filtré&#39; vers la table &quot;cus:Country&quot; basé sur le contenu du champ &quot;@country&quot; qui doit contenir la valeur &#39;FR&#39; :

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```

## `<key>` element {#key--element}

### Modèle de contenu {#content-model-8}

key:==keyfield

### Attributs {#attributes-8}

* @allowEmptyPart (boolean)
* @applicableIf (string)
* @internal (boolean)
* @label (string)
* @name (MNTOKEN)
* @noDbIndex (boolean)

### Parents {#parents-8}

`<element>`

### Enfants {#children-8}

`<keyfield>`

### Description {#description-8}

Cet élément permet de définir une clef permettant d&#39;identifier un enregistrement de la table.

Une table doit posséder au moins une clef.

### Usage et contexte d&#39;utilisation {#use-and-context-of-use-6}

Par convention, les clefs sont déclarées après la déclaration de l&#39;élément principal du schéma et à la suite des déclarations d&#39;index.

Une clé est connue sous le nom de composite si elle comprend plusieurs champs (plusieurs `<keyfield>` enfants, par exemple). N’utilisez pas de clé composite pour définir une clé primaire.

Si l&#39;élément principal du schéma contient l&#39;attribut &quot;@autopk=true&quot; alors la clef primaire est unique. Une seule clef primaire doit être déclarée par schéma.

Les 1000 premiers identifiants sont réservés donc si une plage de valeurs doit être définies pour les clefs, il faut la commencer après la valeur 1000.

### Description des attributs {#attribute-description-8}

* **allowEmptyPart (boolean)**: dans le cas d&#39;une clef composite, si cet attribut est activé, la clef est considérée comme valide si au moins une des clefs composant la clef composite n&#39;est pas vide. Dans ce cas, la notion de valeur vide est &quot;0&quot; (booléen ou pour tous les types de données numériques). Par défaut, toutes les clefs d&#39;une clef composite doivent être remplies.
* **applicableIf (string)**: cet attribut permet de rendre la clef optionnelle. Il définit la condition d&#39;applicabilité de la définition de la clef. Cet attribut reçoit une expression XTK.
* **internal (boolean)**: s&#39;il est activé, cet attribut signifie à Adobe Campaign que la clef est primaire.
* **label (string)**: libellé de la clef.
* **name (MNTOKEN)**: nom interne de la clef.
* **noDbIndex (boolean)**: s&#39;il est activé (noDbIndex=&quot;true&quot;), le champ correspondant à la clef ne sera pas indexé.

### Exemples {#examples-------}

Déclaration d&#39;une clef composite autorisant un des deux champs la composant &quot;@expr&quot; ou &quot;@alias&quot; à être vide:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Declaration of a primary key on the &quot;Name&quot; field of STRING type in an `<srcschema>`  and the matching SQL query:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```

## `<keyfield>` element {#keyfield--element}

### Modèle de contenu {#content-model-9}

keyfield:==EMPTY

### Attributs {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

### Parents {#parents-9}

`<key>`  ,  `<dbindex />`

### Enfants {#children-9}

Aucun

### Description {#description-9}

Cet élément définit les champs à intégrer à un index ou bien à une clef.

### Description des attributs {#attribute-description-9}

* **xlink (MNTOKEN)**: permet de référencer automatiquement les clefs étrangères définies dans la jointure pour une table de relation (lien N-N).
* **xpath (MNTOKEN)**: définition d’un index ou d’une clé sur un `<attribute>` élément. Cet attribut reçoit un Xpath qui définit le chemin d’accès à l’attribut schema qui définit la clé ou l’index.

### Exemples {#examples-}

Sélection du champ &quot;sName&quot; dans un index avec un Xpath sur &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```

## `<method>` element {#method--element}

### Modèle de contenu {#content-model-10}

method:==( help | parameters)

### Attributs {#attributes-10}

* @_operation (string)
* @access (string)
* @const (boolean)
* @hidden (boolean)
* @label (string)
* @library (string)
* @name (MNTOKEN)
* @pkonly (boolean)
* @static (boolean)

### Parents {#parents-10}

`<methods>`  ,  `<interface />`

### Enfants {#children-10}

* `<help>`
* `<parameters>`

### Description {#description-10}

Cet élément permet de définir une méthode SOAP.

### Usage et contexte d&#39;utilisation {#use-and-context-of-use-7}

Les méthodes SOAP permettent des traitements applicatifs.

L&#39;utilisation de l&#39;attribut &quot;@library&quot; est nécessaire pour déclarer une nouvelle méthode (non native): l&#39;espace de nommage et le nom utilisés pour la bibliothèque sont indépendants de l&#39;espace de nommage et du nom du schéma dans lequel se trouve la déclaration.

### Description des attributs {#attribute-description-10}

* **access (string)**: cet attribut définit un contrà´le d&#39;accès sur l&#39;utilisation de la méthode. Si cet attribut est absent, l&#39;identification est obligatoire. Les valeurs disponibles sont &#39;anonymous&#39;, &#39;admin&#39; et &#39;sql&#39;.
* **const (boolean)**: si cet attribut est activé, les paramètres sont compris dans un élément XML qui définit la méthode.
* **label (string)**: libellé de la méthode.
* **library (string)**: méthode qui n&#39;est pas native à l&#39;application . Cet attribut prend la valeur de la bibliothèque de méthodes dans laquelle se trouve la définition de la méthode (nms:mabibliotheque.js).
* **name (MNTOKEN)**: nom unique de la méthode.
* **static (boolean)**: si cet attribut est activé, la méthode est considérée comme autonome, tous les paramètres doivent être indiqués à la méthode lors de son appel.

### Exemples {#examples-7}

Définition de la méthode d&#39;usine &quot;Subscribe&quot; :

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>
```

## `<methods>` element {#methods--element}

### Modèle de contenu {#content-model-11}

methods:==method

### Attributs {#attributes-11}

Aucun

### Parents {#parents-11}

`<srcschema>`

### Enfants {#children-11}

method

### Description {#description-11}

This element lets you define a `<method>`  element. Il est obligatoire pour déclarer une méthode.

### Description des attributs {#attribute-description-11}

Cet élément n&#39;a aucun attribut.

### Exemples {#examples-8}

```
<methods async="true"
...// definition of one or more <method
</methods>
```

## `<param>` element {#param--element}

### Modèle de contenu {#content-model-12}

param:==help

### Attributs {#attributes-12}

* @_operation (string)
* @desc (string)
* @enum (string)
* @inout (string)
* @label (string)
* @localizable (string)
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type (string)

### Parents {#parents-12}

`<parameters>`

### Enfants {#children-12}

`<help>`

### Description {#description-12}

Cet élémént permet de définir un paramètre d&#39;un appel à une méthode SOAP.

### Description des attributs {#attribute-description-12}

* **desc (chaîne)**: description qui concerne l&#39; `<param>` élément.
* **inout (string)**: cet attribut définit si le paramètre est en entrée de l&#39;appel SOAP (in) ou bien en sortie (out). Si cet attribut n&#39;est pas précisé, le paramètre est par défaut en entrée (&quot;@inout=in&quot;).
* **label (chaîne)**: `<param>` libellé
* **localizable (string)**: s&#39;il est activé, cet attribut indique à l&#39;outil de collecte de récupérer la valeur de l&#39;attribut &quot;@label&quot; pour traduction (usage interne).
* **name (MNTOKEN)**: nom interne du `<param>`
* **type (chaîne)**: cet attribut définit le type d’ `<param>` élément

   Liste des types disponibles :

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
   * DOMDocument
   * DOMElement
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

### Exemples {#examples-9}

Définition du paramètre en entrée &quot;serviceName&quot; de type chaîne de caractères:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```

## `<parameters>` element {#parameters--element}

### Modèle de contenu {#content-model-13}

parameters:==param

### Attributs {#attributes-13}

Aucun

### Parents {#parents-13}

`<method>`

### Enfants {#children-13}

`<param>`

### Description {#description-13}

This element defines a group of `<parameter>`  elements.

### Usage et contexte d&#39;utilisation {#use-and-context-of-use-8}

This element is mandatory, even for a single `<param>` child element of the `<method>`  element.

### Description des attributs {#attribute-description-13}

Aucun

### Exemples {#examples-10}

```
<parameters
... //definition of one or more <param
</parameters>
```

## `<srcschema>` element {#srcschema--element}

### Modèle de contenu {#content-model-14}

srcSchema:==(attribute | createdBy | data | element | enumeration | help | interface | methods | modifiedBy)

### Attributs {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), extendedSchema (string), img (string), implements (string), label (string), labelSingular (string), lastModified (datetime), library (boolean), mappingType (string), modifiedBy-id (long), name (string), namespace (string), useRecycleBin (boolean), view (boolean), xtkschema (string)

### Parents {#parents-14}

Aucun

### Enfants {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

### Description {#description-14}

Il `<srcschema>` s’agit de l’élément racine d’un schéma. Il s’agit du point d’entrée pour la définition du schéma.

### Usage et contexte d&#39;utilisation {#use-and-context-of-use-9}

La présentation du schéma est disponible dans [A propos de la référence](../../configuration/using/about-schema-reference.md) du schéma et de la structure [du](../../configuration/using/schema-structure.md)schéma.

### Description des attributs {#attribute-description-14}

* **created (datetime)**: cet attribut renseigne sur la date et l&#39;heure de la création du schéma. Il est de la forme &quot;Date Heure&quot;. Les valeurs affichées sont celles du serveur. L&#39;heure est donnée au format UTC.
* **createdBy-id (long)**: correspond à l&#39;identifiant de l&#39;opérateur qui a crée le schéma.
* **desc (string)**: description du schéma.
* **entitySchema (string)**: schéma de base sur lequel on base la syntaxe et la validation du schéma (par défaut pour Adobe Campaign : xtk:srcSchema). Lors de l&#39;enregistrement du schéma courant, Adobe Campaign validera la grammaire du schéma courant avec le schéma déclaré dans l&#39;attribut @xtkschema.
* **extendedSchema (string)**: reçoit le nom du schéma d&#39;usine sur lequel est basé l&#39;extension du schéma courant. De la forme &quot;namespace:name&quot;.
* **img (string)**: icône associée au schéma (peut se définir dans le wizard de création du schéma).
* **label (string)**: libellé du schéma.
* **labelSingular (string)**: libellé (au singulier) destiné à l&#39;affichage dans l&#39;interface.
* **lastModified (datetime)**: cet attribut renseigne sur la date et l&#39;heure de la dernière modification. Il est de la forme &quot;Date Heure&quot;. Les valeurs affichées sont celles du serveur. L&#39;heure est donnée au format UTC.
* **library (boolean)**: utilisation du schéma comme librairie et non comme entité. Ce schéma peut donc être référencé par d&#39;autres schémas grâce aux attributs &quot;@ref&quot; et &quot;@template&quot;.
* **mappingType (string)**:

   * &quot;sql&quot;: mapping base de données
   * &quot;textFile&quot;: mapping fichier texte
   * &quot;xmlFile&quot;: mapping fichier texte au format XML
   * &quot;binaryFile&quot;: mapping fichier binaire

* **modifiedBy-id (long)**: correspond à l&#39;identifiant de l&#39;opérateur qui a modifié le schéma.
* **name (string)**: nom unique du schéma.
* **namespace (string)**: espace de nommage du schéma (espace par défaut : nms, xtk, nl). Lors de la création d&#39;un nouveau schéma, il est conseillé d&#39;utiliser un namespace spécifique au projet.
* **useRecycleBin (boolean)**: activation de la corbeille dans l&#39;application. Les enregistrements supprimés seront placés en corbeille avant la destruction définitive. Cette fonctionnalité est disponible uniquement pour le module &quot;Diffusions&quot;.
* **view (boolean)**: s&#39;il est activé (@view=&quot;true&quot;), le schéma sera utilisé comme une vue. L&#39;assistant de mise à jour de la structure de la base ne tiendra pas compte du schéma. Cette option permet le plus souvent de référencer des tables externes.
* **xtkschema (string)**: nom du schéma définissant la grammaire des schémas (par défaut xtk:srcSchema).

### Exemples {#examples-11}

`<srcschema>` élément du schéma &quot;nms:delivery&quot; hors zone

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```

## `<sysfilter>` element {#sysfilter--element}

### Modèle de contenu {#content-model-15}

sysFilter:==condition

### Attributs {#attributes-15}

Aucun

### Parents {#parents-15}

`<element>`

### Enfants {#children-15}

`<condition>`

### Description {#description-15}

Cet élément permet de définir un filtre.

### Description des attributs {#attribute-description-15}

Cet élément n&#39;a aucun attribut.

### Exemples {#examples-12}

Définition d&#39;un filtre avec une condition sur l&#39;attribut @name:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```

## `<value>` element {#value--element}

### Modèle de contenu {#content-model-16}

value:==help

### Attributs {#attributes-16}

* @applicableIf (string)
* @desc (string)
* @enabledIf (string)
* @img (string)
* @label (string)
* @name (string)
* @value (string)

### Parents {#parents-16}

`<enumeration>`

### Enfants {#children-16}

`<help>`

### Description {#description-16}

Cet élément permet de définir les valeurs stockées dans une énumération.

### Description des attributs {#attribute-description-16}

* **applicableIf (string)**: cet attribut permet de rendre une valeur d&#39;énumération optionnelle. Il reçoit une expression XTK.
* **desc (string)**: description de la valeur de l&#39;énumération.
* **enabledIf (string)**: condition d&#39;activation de la valeur de l&#39;énumération.
* **img (string)**: image associée à l&#39;énumération sous la forme &quot;namespace:nom_image&quot;. Physiquement l&#39;image doit être importée sur le serveur applicatif.
* **label (string)**: libellé de la valeur de l&#39;énumération.
* **name (string)**: nom interne de la valeur de l&#39;énumération.
* **value (string)**: valeur de la valeur de l&#39;énumération. Le type de la valeur est défini en fonction du type de l&#39;énumération. Si l&#39;énumération est de type chaine de caractère, elle ne peut contenir que des valeurs de type chaine de caractères.

### Exemples {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
