---
product: campaign
title: Eléments et attributs de schéma - élément element
description: élément element
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '2014'
ht-degree: 100%

---

# élément element {#element--element}

![](../../../assets/v7-only.svg)

## Modèle de contenu {#content-model-4}

element:==(attribute | compute-string | dbindex | default | element | help | join | key | sysFilter | translatedDefault)

## Attributs {#attributes-4}

_operation (string), advanced (boolean), aggregate (string), applicableIf (string), autopk (boolean), belongsTo (string), convDate (string), dataPolicy (string), dataSource (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), displayAsField (boolean), doesNotSupportDiff (boolean), edit (string), emptyKeyValue (string), enum (string), enumImage (string), expandSchemaTarget (string), expr (string), externalJoin (boolean), feature (string), featureDate (boolean), filterPath (string), folderLink (string), folderModel (string), folderProcess (string), fullLoad (boolean), hierarchical (boolean), hierarchicalPath (string), img (string), inout (string), integrity (string), label (string), labelSingular (string), length (string), localizable (boolean), name (MNTOKEN), noDbIndex (boolean), noKey (boolean), ordered (boolean), overflowtable (boolean), pkSequence (string), pkgStatus (string), ref (string), required (boolean), revAdvanced (boolean), revCardinality (string), revDesc (string), revExternalJoin (boolean), revIntegrity (string), revLabel (string), revLink (string), revTarget (string), revVisibleIf (string), sql (boolean), sqlname (string), sqltable (string), tableSpace (string), tableSpaceIndex (string), target (MNTOKEN), template (string), temporaryTable (boolean), translatedDefault (string), translatedExpr (string), type (MNTOKEN), unbound (boolean), user (boolean), userEnum (string), visibleIf (string), xml (boolean), xmlChildren (boolean)

## Parents {#parents-4}

`<srcschema>`

`<element>`

## Enfants {#children-4}

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

## Description {#description-4}

Il existe quatre types d&#39;élément `<element>` dans Adobe Campaign.

* Racine `<element>` : définit le nom SQL de la table qui correspond au schéma.
* Structure`<element>` : définit un groupe d’éléments `<element>` ou `<attribute>`.
* Lien `<element>` : définit un lien. Ces éléments doivent inclure l’attribut « @type=link ».
* XML `<element>` : définit un champ de type Texte « mData ». Cet élément doit inclure l’attribut « @type=xml ».

## Description des attributs {#attribute-description-4}

* **_operation (string)**: définit le type d&#39;écriture dans la base.

  Cet attribut est principalement utilisé lors d&#39;une extension de schéma usine.

  Les valeurs accessibles sont:

   * &quot;none&quot; : Réconciliation seule. Signifie qu&#39;Adobe Campaign va retrouver l&#39;élément sans le mettre à jour ou générer une erreur s&#39;il n&#39;existe pas.
   * &quot;insertOrUpdate&quot; : Mise à jour avec insertion. Signifie qu&#39;Adobe Campaign va mettre à jour l&#39;élément ou le créer s&#39;il n&#39;existe pas.
   * &quot;insert&quot; : Insertion. Signifie qu&#39;Adobe Campaign va insérer l&#39;élément sans vérifier s&#39;il existe.
   * &quot;update&quot; : Mise à jour. Signifie qu&#39;Adobe Campaign va mettre à jour l&#39;élément ou générer une erreur s&#39;il n&#39;existe pas.
   * &quot;delete&quot; : Suppression. Signifie qu&#39;Adobe Campaign va retrouver et supprimer l&#39;élément.

* **advanced (boolean)**: quand cette option est activée (@advanced=&quot;true&quot;), elle permet de masquer l&#39;élément dans la liste des champs disponibles et accessibles pour la configuration d&#39;une liste dans un formulaire.
* **aggregate (string)** : vous permet de copier la définition d’un `<element>` via un autre schéma. Cet attribut reçoit une déclaration de schéma sous la forme d’un « namespace:name ».
* **applicableIf (string)**: condition d&#39;applicabilité de l&#39;élément. Cet attribut reçoit une expression XTK.
* **autopk (boolean)**: si cette option est activée (autopk=&quot;true&quot;), alors une clé unique est automatiquement définie. Cette option ne peut être utilisée que sur l&#39;élément principal du schéma. Attention, Adobe Campaign donne seulement la garantie que la clef générée est unique. Le fait que les valeurs des clefs soient consécutives et incrémentales n&#39;est pas assuré.
* **dataPolicy (string)**: permet de préciser des contraintes de validation sur les valeurs permises dans le champ SQL, les valeurs pour cet attribut sont :

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
* **default (string)**: permet de définir le comportement de l&#39;élément (appel à une fonction, valeur par défaut). Cet attribut reçoit une expression XTK.
* **desc (string)**: permet d&#39;insérer une description de l&#39;élément. Cette description s&#39;affiche dans la barre de statut de l&#39;interface.
* **displayAsField (boolean)** : si cet attribut est activé, un `<element>` de type « link » s’affiche sous forme de champ dans l’arborescence des schémas (onglet « Structure »). De cette façon, il est possible d&#39;afficher un lien en tant que champ local et de modifier son comportement pendant une requête. Lorsque l&#39;élément est trouvé dans le SELECT d&#39;une requête, la valeur de la cible du lien est utilisée. Lorsque l’élément est trouvé dans le WHERE d’une requête, la clé sous-jacente du lien est utilisée.
* **edit (string)**: cet attribut précise le type d&#39;input qui sera utilisé dans le formulaire associé à l&#39;élément du schéma en cours de définition.
* **enum (string)**: reçoit le nom de l&#39;énumération associé au champ. L&#39;énumération peut être insérée dans le même schéma ou bien dans un schéma distant. L&#39;énumération définie une liste fermée de valeurs.
* **expr (string)**: cet attribut définit un champ calculé dont la définition n&#39;est pas stockée dans la table. Il reçoit un Xpath ou une expression XTK.
* **externalJoin (boolean)**: jointure externe dans un élément de type &quot;link&quot;.
* **feature (string)**: définit un champ de caractéristiques. Les champs de caractéristiques sont utilisés pour étendre les données d&#39;une table existante, mais avec un stockage déporté dans une table annexe. Les valeurs acceptées sont :

   * &quot;shared&quot; : le contenu est stocké dans une table partagée par type de données
   * &quot;dedicated&quot; : le contenu est stocké dans une table dédiée

  Les tables SQL de caractéristiques sont construites automatiquement en fonction du type de la caractéristique :

   * dédié : `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  Deux types de champs de caractéristiques sont disponibles : les champs simples où une seule valeur est autorisée sur la caractéristique et les champs à choix multiples où la caractéristique est associée à un élément de collection qui peut donc contenir plusieurs valeurs.

  Lorsque une caractéristique est définie dans un schéma, ce schéma doit comporter une clef principale basé sur un seul champ (clef composite non autorisée).

* **featureDate (boolean)**: attribut associé au champ de caractéristiques &quot;feature&quot;, si sa valeur est &quot;true&quot;, il permet de connaître la date de la dernière mise à jour de la valeur.
* **filterPath (string)**: cet attribut reçoit un Xpath et permet de définir un filtre sur un champ.
* **folderLink (string)**: cet attribut reçoit le nom du lien qui permet de retrouver les dossiers dans lesquels sont stockés les entités.
* **folderModel (string)**: définit le type de dossier permettant le stockage des entités. Cet attribut n&#39;est défini que si &quot;@folderLink&quot; est présent.
* **folderProcess (string)**: définit le lien dans lequel est stocké les instances des modèles des entités. Cet attribut n&#39;est défini que si &quot;@folderLink&quot; est présent.
* **fullLoad (boolean)**: cet attribut force l&#39;affichage de tous les enregistrements d&#39;une table lors de la sélection du champ dans un formulaire.
* **img (string)**: reçoit le chemin d&#39;une image associée a l&#39;élément. La valeur de cet attribut est de la forme &quot;namespace:nom de l&#39;image&quot;. Exemple : img=&quot;cus:monImage.jpg&quot;. Physiquement l&#39;image doit être importée sur le serveur applicatif.
* **integrity (string)**: intégrité référentielle de l&#39;occurrence de la table source envers la table cible.

  Les valeurs accessibles sont:

   * &quot;define&quot; : Adobe Campaign ne supprime pas l&#39;entité si elle est référencée à partir du lien
   * &quot;normal&quot; : la suppression de l&#39;occurrence source initialise les clés du lien sur l&#39;occurrence cible (mode par défaut), ce type d&#39;intégrité initiliase toutes les clés étrangères
   * &quot;own&quot; : la suppression de l&#39;occurrence source entraîne la suppression de l&#39;occurrence cible
   * &quot;owncopy&quot; : similaire à &quot;own&quot; (en cas de suppression) ou duplique les occurrences (en cas de duplication)
   * &quot;neutral&quot; : ne fait rien

* **label (string)**: libellé de l&#39;élément.
* **labelSingular (string)**: libellé au singulier de l&#39;élément ; utilisé dans certaines parties de l&#39;interface.
* **length (string)**: nombre de caractères maximal autorisés pour une valeur du champ SQL de type &quot;STRING&quot;.
* **localizable (boolean)**: s&#39;il est activé, cet attribut indique à l&#39;outil de collecte de récupérer la valeur de l&#39;attribut &quot;@label&quot; pour traduction (usage interne).
* **name (MNTOKEN)**: nom interne de l&#39;élément qui correspondra au nom de la table. La valeur de l&#39;attribut &quot;@name&quot; doit être courte, de préférence en anglais et elle doit respecter les contraintes de nommage liées au XML.

  Lors de l&#39;écriture du schéma en base, des préfixes sont automatiquement rajoutées par Adobe Campaign au nom du champ.

   * &quot;i&quot; : préfixe pour le type &#39;entier&#39;.
   * &quot;d&quot; : préfixe pour le type &#39;double&#39;.
   * &quot;s&quot; : préfixe pour le type chaine de caractère.
   * &quot;ts&quot; : préfixe pour le type &#39;date&#39;.

  Pour définir de manière autonome le nom de la table, il faut utiliser l&#39;attribut &quot;@sqltable&quot; dans la définition de l&#39;élément principal du schéma.

* **noDbIndex (boolean)**: permet de préciser que l&#39;élément ne sera pas indexé.
* **ordered (boolean)**: si l&#39;attribut est activé (ordered=&quot;true&quot;), Adobe Campaign maintient l&#39;ordre de déclaration des éléments dans un élément de collection XML.
* **pkSequence (string)**: reçoit le nom de la séquence à utiliser pour le calcul d&#39;une clef auto-incrémentale. Cet attribut n&#39;est utilisable que si une clef autoincrémentale est définie sur l&#39;élément racine du schéma.
* **pkgStatus (string)**: durant l&#39;export de package, les valeurs seront prises en compte ou non en fonction de la valeur de cet attribut :

   * &quot;always&quot; : l&#39;élément sera toujours présent
   * &quot;never&quot; : l&#39;élément ne sera jamais présent
   * &quot;default (ou rien)&quot; : l&#39;élement est exporté sauf si c&#39;est l&#39;élément par défaut ou bien si ce n&#39;est pas un champ interne qui ne serait pas compatible entre instances

* **ref (string)** : cet attribut définit une référence vers un élément &lt;element> partagé par plusieurs schémas (factorisation des définitions). La définition n&#39;est pas recopiée dans le schéma courant.
* **required (boolean)**: si cet attribut est activé (@required=&quot;true&quot;), le champ est mis en avant dans l&#39;interface. Le label du champ est affiché en rouge dans un formulaire.
* **revAdvanced (boolean)**: s&#39;il est activé, cet attribut précise que le lien inverse est de type &quot;advanced&quot;.
* **revCardinality (string)** : cet attribut définit la cardinalité d&#39;un lien entre deux tables. Il est utilisé dans un `<element>` de type &quot;link&quot;.

  Les valeurs possibles sont les suivantes :

   * &quot;single&quot; : Lien simple de type 1-1
   * &quot;unbound&quot; : Lien de collection de type 1-N

  Par défaut, si l&#39;attribut n&#39;est pas précisé lors de la création du lien, la cardinalité est de type 1-N.

* **revDesc (string)**: cet attribut reçoit une description associée au lien inverse.
* **revExternalJoin (boolean)**: s&#39;il est activé, cet attribut permet de forcer la jointure externe sur le lien inverse.
* **revIntegrity (string)**: cet attribut définit l&#39;intégrité sur le schéma cible. Les mêmes valeurs que l&#39;attribut &quot;@integrity&quot; sont autorisés. Par défaut, Adobe Campaign donne la valeur &quot;normal&quot; à cet attribut.
* **revLabel (string)**: libellé du lien inverse.
* **revLink (string)** : nom du lien inverse. Si la valeur est &quot;_NONE_&quot;, aucun lien inverse ne sera créé dans le schéma destination.
* **revTarget (string)**: cible du lien inverse.
* **sql (boolean)**: si cet attribut est activé (@sql=&quot;true&quot;), il force le stockage de l&#39;élément en SQL même lorsque l&#39;élément a la propriété xml=&quot;true&quot;.
* **sqlname (string)**: nom du champ lors de la création de la table. Si &quot;@sqlname&quot; n&#39;est pas précisé la valeur de l&#39;attribut &quot;@name&quot; est pris par défaut. Lors de l&#39;écriture du schéma en table des préfixes seront automatiquement rajoutés en fonction du type du champ.
* **sqltable (string)**: pour l&#39;élément principal du schéma, cet attribut surcharge le nom de la table SQL généré par défaut. Si &quot;@sqltable&quot; n&#39;est pas précisé le nom par défaut est de la forme: espace de noms (avec la première lettre en majuscule) et la valeur du &quot;@name&quot; du SrcSchema.
* **tableSpace (string)** : cet attribut permet de spécifier un nouveau tablespace de stockage de données pour une table (valable sur l’élément `<element>` racine).
* **tableSpaceIndex (string)** : cet attribut permet de spécifier un nouveau tablespace de stockage des index pour une table (valable sur l&#39;élément `<element>` racine).
* **target (MNTOKEN)**: reçoit le nom du schéma cible lors de la création d&#39;un lien entre tables. Cet attribut n&#39;est actif que si l&#39;élément est de type &quot;link&quot;.
* **template (string)** : cet attribut définit une référence à un élément `<element>` partagé par plusieurs schémas. La définition est automatiquement copiée dans le schéma actuel.
* **translatedDefault (string)**: si un attribut &quot;@default&quot; est présent, l&#39;attribut &quot;@translatedDefault&quot; permet de redéfinir une expression, correspondante de l&#39;expression définie dans &quot;@default&quot;, qui sera collectée par l&#39;outil de traduction (usage interne).
* **translatedExpr (string)**: si un attribut &quot;@expr&quot; est présent, l&#39;attribut &quot;@translatedExpr&quot; permet de redéfinir une expression, correspondante de l&#39;expression définie dans &quot;@expr&quot;, qui sera collectée par l&#39;outil de traduction (usage interne).
* **type (MNTOKEN)**: définit le type des données stockées dans l&#39;élément.

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

* **unbound (boolean)**: si l&#39;attribut est activé (unbound=&quot;true&quot;), le lien est déclaré comme élément de collection pour une cardinalité 1-N.
* **userEnum (string)**: reçoit le nom interne d&#39;une énumération &quot;ouverte&quot;. Les valeurs de l&#39;énumération peuvent être définies par l&#39;utilisateur dans l&#39;interface.
* **xml (boolean)**: si cette option est activée, l&#39;ensemble des valeurs définies dans l&#39;élément seront stockées en XML dans un champ &quot;mData&quot; de type TEXT. En conséquence, il n&#39;y a pas de filtrage ni de tri sur ces champs.
* **xmlChildren (booléen)** : force le stockage pour chaque enfant ( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
