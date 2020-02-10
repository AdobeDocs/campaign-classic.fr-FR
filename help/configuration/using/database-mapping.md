---
title: Mapping de la base de données
seo-title: Mapping de la base de données
description: Mapping de la base de données
seo-description: null
page-status-flag: never-activated
uuid: a51df3eb-cae6-4e8d-8386-d62defc1b610
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: bc06c00d-f421-452e-bde0-b4ecc12c72c8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# Mapping de la base de données{#database-mapping}

Le mapping SQL de notre schéma d&#39;exemple donne le document XML suivant :

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient e-mail address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

## Description {#description}

The root element of the schema is no longer **`<srcschema>`**, but **`<schema>`**.

Nous sommes sur un autre type de document qui est généré automatiquement à partir du schéma source, on parle alors simplement de schéma. C&#39;est ce schéma qui sera utilisé par l&#39;application Adobe Campaign.

Les noms SQL sont déduits automatiquement en fonction du nom et du type de l&#39;élément.

Les règles de nommage des noms SQL sont les suivantes :

* table : concaténation de l&#39;espace de nommage et du nom du schéma

   Dans notre exemple le nom de la table est renseigné à partir de l&#39;élément principal du schéma dans l&#39;attribut **sqltable** :

   ```
   <element name="recipient" sqltable="CusRecipient">
   ```

* champ : nom de l&#39;élément précédé d&#39;un préfixe défini en fonction de son type (&#39;i&#39; pour entier, &#39;d&#39; pour double, &#39;s&#39; pour chaîne, &#39;ts&#39; pour les dates, etc.)

   The field name is entered via the **sqlname** attribute for each typed **`<attribute>`** and **`<element>`**:

   ```
   <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
   ```

>[!NOTE]
>
>Les noms SQL peuvent être surchargés à partir du schéma source, il faut renseigner
les attributs &quot;sqltable&quot; ou &quot;sqlname&quot; sur l&#39;élément concerné.

Le script SQL de création de la table généré à partir du schéma étendu est le suivant :

```
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

Les contraintes des champs SQL sont les suivantes :

* pas de valeurs nulles sur les types numériques et dates,
* les champs numériques sont initialisés à 0.

## Champs XML {#xml-fields}

Par défaut, tout élément saisi **`<attribute>`** et **`<element>`** élément est mappé sur un champ SQL de la table du schéma de données. Vous pouvez toutefois référencer ce champ au format XML au lieu de SQL, ce qui signifie que les données sont stockées dans un champ mémo (&quot;mData&quot;) de la table contenant les valeurs de tous les champs XML. Le stockage de ces données est un document XML qui observe la structure du schéma.

Pour renseigner un champ en XML, il faut ajouter l&#39;attribut **xml** avec la valeur &quot;true&quot; sur l&#39;élément concerné.

**Exemple** : voici deux exemples d&#39;utilisation des champs de type XML.

* Champ commentaire multi-lignes :

   ```
   <element name="comment" xml="true" type="memo" label="Comment"/>
   ```

* Description de données au format HTML :

   ```
   <element name="description" xml="true" type="html" label="Description"/>
   ```

   Le type &quot;html&quot; permet de stocker le contenu HTML dans une balise CDATA et d&#39;afficher un contrôle spécifique d&#39;édition HTML dans l&#39;interface cliente Adobe Campaign.

L&#39;utilisation de champs XML permet d&#39;ajouter des champs sans avoir à modifier la structure physique de la base. Un autre avantage est d&#39;utiliser moins de ressources (taille alouée des champs SQL, limite sur le nombre de champs par table, etc.).

L&#39;inconvénient principal est l&#39;impossibilité d&#39;indexer ou de filtrer un champ XML.

## Champs indexés {#indexed-fields}

Les index permettent d&#39;optimiser les performances des requêtes SQL utilisées dans l&#39;application.

Un index est déclaré à partir de l&#39;élément principal du schéma de données.

```
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Les index suivent les règles suivantes :

* Un index peut référencer un ou plusieurs champs de la table.
* Un index peut être unique (afin d&#39;éviter les doublons) sur l&#39;ensemble des champs qui le compose si l&#39;attribut **unique** est renseigné avec la valeur &quot;true&quot;.
* Le nom SQL de l&#39;index est déduit à partir du nom SQL de la table et du nom de l&#39;index.

>[!NOTE]
>
>Par convention, les index sont les éléments déclarés en premier à partir de l&#39;élément principal du schéma.

>[!NOTE]
>
>Les index sont crées automatiquement lors d&#39;un mapping de table (mapping standard ou FDA).

**Exemple**:

* Ajout d&#39;un index sur l&#39;email et la ville :

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <dbindex name="email">
         <keyfield xpath="@email"/> 
         <keyfield xpath="location/@city"/> 
       </dbindex>
   
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
       <element name="location" label="Location">
         <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
       </element>
     </element>
   </srcSchema>
   ```

* Ajout d&#39;un index unique sur le champ du nom &quot;id&quot; :

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <dbindex name="id" unique="true">
         <keyfield xpath="@id"/> 
       </dbindex>
   
       <dbindex name="email">
         <keyfield xpath="@email"/> 
       </dbindex>
   
       <attribute name="id" type="long" label="Identifier"/>
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
     </element>
   </srcSchema>
   ```

## Gestion des clés {#management-of-keys}

Une table doit posséder au moins une clé permettant d&#39;identifier un enregistrement de la table.

Une clé est déclarée à partir de l&#39;élément principal du schéma de données.

```
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Les clés suivent les règles suivantes :

* Une clé peut référencer un ou plusieurs champs de la table.
* Une clé est dite primaire (ou prioritaire) lorsqu&#39;elle est renseignée en premier dans le schéma ou si elle contient l&#39;attribut **internal** avec la valeur &quot;true&quot;.
* Un index unique est implicitement déclaré pour chaque définition de clé. Il est possible d&#39;empêcher la création de l&#39;index sur la clé en ajoutant l&#39;attribut **noDbIndex** avec la valeur &quot;true&quot;.

>[!NOTE]
>
>Par convention, les clés sont les éléments déclarés à partir de l&#39;élément principal du schéma après la définition des index.

>[!NOTE]
>
>Les clés sont crées lorsque, lors du mapping de la table (mapping standard ou FDA), Adobe Campaign trouve des index uniques.

**Exemple**:

* Ajout d&#39;une clé sur l&#39;email et la ville :

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <key name="email">
         <keyfield xpath="@email"/> 
         <keyfield xpath="location/@city"/> 
       </key>
   
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
       <element name="location" label="Location">
         <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
       </element>
     </element>
   </srcSchema>
   ```

   Le schéma généré :

   ```
   <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
     <element name="recipient" sqltable="CusRecipient">    
      <dbindex name="email" unique="true">      
        <keyfield xpath="@email"/>      
        <keyfield xpath="location/@city"/>    
      </dbindex>    
   
      <key name="email">      
       <keyfield xpath="@email"/>      
       <keyfield xpath="location/@city"/>    
      </key>    
   
      <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
      <element label="Location" name="location">      
        <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
      </element>  
     </element>
   </schema>
   ```

* Ajout d&#39;une clé primaire ou interne sur le champ de nom &quot;id&quot; :

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <key name="id" internal="true">
         <keyfield xpath="@id"/> 
       </key>
   
       <key name="email" noDbIndex="true">
         <keyfield xpath="@email"/> 
       </key>
   
       <attribute name="id" type="long" label="Identifier"/>
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
     </element>
   </srcSchema>
   ```

   Le schéma généré :

   ```
   <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
     <element name="recipient" sqltable="CusRecipient">    
       <key name="email">      
         <keyfield xpath="@email"/>    
       </key>    
   
       <dbindex name="id" unique="true">      
         <keyfield xpath="@id"/>    
       </dbindex>    
   
       <key internal="true" name="id">      
        <keyfield xpath="@id"/>    
       </key>    
   
       <attribute label="Identifier" name="id" sqlname="iRecipientId" type="long"/>    
       <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
     </element>
   </schema>
   ```

### Clé auto-incrémentale {#auto-incremental-key}

La clé primaire de la plupart des tables Adobe Campaign est un entier long 32 bits auto-généré par le moteur de base de données. Le calcul de la valeur de la clé repose sur une séquence (par défaut la fonction SQL **XtkNewId**) générant un nombre unique dans toute la base. Le contenu de la clé est automatiquement renseigné à l&#39;insertion de l&#39;enregistrement.

L&#39;avantage d&#39;une clé incrémentale est d&#39;obtenir une clé technique non modifiable utilisée pour les jointures entre les tables. De plus, cette clé n&#39;est pas consommatrice car elle utilise un entier sur deux octets.

Vous pouvez spécifier dans le schéma source le nom de la séquence à utiliser avec l’attribut **pkSequence** . Si cet attribut n’est pas donné dans le schéma source, la séquence **par défaut XtkNewId** est utilisée. L’application utilise des séquences dédiées pour les schémas **nms:broadLog** et **nms:trackingLog** (**NmsLargeLogId** et **NmsTrackingLogId respectivement), car il s’agit des tables qui contiennent le plus d’enregistrements.**

À compter d’ACC 18.10, **XtkNewId** n’est plus la valeur par défaut de la séquence dans les schémas d’usine. Vous pouvez désormais créer ou étendre un schéma avec une séquence dédiée.

>[!CAUTION]
>
>Lors de la création ou de l’extension d’un schéma, vous devez conserver la valeur de la séquence de la clé primaire (@pkSequence) pour l’ensemble du schéma.

>[!NOTE]
>
>Une séquence référencée dans un schéma Adobe Campaign (**NmsTrackingLogId** , par exemple) doit être associée à une fonction SQL qui renvoie le nombre d’ID dans les paramètres, séparés par des virgules. Cette fonction doit être appelée ******GetNewXXXIds**, où **XXX** est le nom de la séquence (**GetNewNmsTrackingLogIds** , par exemple). Affichez les fichiers **postgres-nms.sql**, **mssql-nms.sql** ou **oracle-nms.sql** fournis avec l’application dans le répertoire **datakit/nms/eng/sql/ pour récupérer l’exemple de création de séquence &#39;NmsTrackingLogId&#39; pour chaque moteur de base de données.**

Pour déclarer une clé unique, il faut renseigner l&#39;attribut **autopk** (avec la valeur &quot;true&quot;) sur l&#39;élément principal du schéma de données.

**Exemple**:

Déclaration d&#39;une clé incrémentale dans le schéma source :

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

Le schéma généré :

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" autopk="true" pkSequence="XtkNewId" sqltable="CusRecipient"> 
    <dbindex name="id" unique="true">
      <keyfield xpath="@id"/>
    </dbindex>

    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key>

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iRecipientId" type="long"/>
  </element>
</schema>
```

En plus de la définition de la clé et de son index, un champ numérique de nom &quot;id&quot; a été ajouté dans le schéma étendu afin de contenir la clé primaire auto générée.

>[!CAUTION]
>
>Un enregistrement avec une clé primaire à 0 est automatiquement inséré à la création de la table. Cet enregistrement est utilisé pour éviter les jointures externes, non efficaces sur les tables à volumes. Par défaut, toutes les clés étrangères sont initialisées avec la valeur 0, ce qui permet de toujours retourner un résultat sur la jointure lorsque la donnée n&#39;est pas renseignée.

## Liens : relation entre les tables {#links--relation-between-tables}

Un lien décrit l&#39;association d&#39;une table vers une autre table.

Les différents types d&#39;associations (dites &quot;cardinalités&quot;) sont les suivants :

* cardinalité 1-1 : à une occurrence de la table source peut correspondre au plus une occurrence de la table cible,
* cardinalité 1-N : à une occurrence de la table source peuvent correspondre plusieurs occurrences de la table cible, mais à une occurrence de la table cible peut correspondre au plus une occurrence de la table source,
* cardinalité N-N : à une occurrence de la table source peuvent correspondre plusieurs occurrences de la table cible et vice versa.

Dans l&#39;interface, vous pouvez distinguer facilement les différents types de relations grâce à leurs icônes.

Pour les relations de jointure avec une table/base de données de campagne :

* ![](assets/join_with_campaign11.png) : Cardinalité 1-1. Par exemple, entre un destinataire et une commande en cours. Un destinataire ne peut être associé qu’à une seule occurrence du tableau de commande actuel à la fois.
* ![](assets/externaljoin11.png) : Cardinalité 1-1, jointure externe. Par exemple, entre un destinataire et son pays. Un destinataire ne peut être associé qu’à une seule occurrence du pays de la table. Le contenu du tableau de pays ne sera pas enregistré.
* ![](assets/join_with_campaign1n.png) : Cardinalité 1-N. Par exemple, entre un destinataire et le tableau des abonnements. Un destinataire peut être associé à plusieurs occurrences du tableau des abonnements.

Pour les relations de jointure à l’aide de l’accès aux bases de données fédérées :

* ![](assets/join_fda_11.png) : Cardinalité 1-1
* ![](assets/join_fda_1m.png) : Cardinalité 1-N

For more information on FDA tables, refer to [Accessing an external database](../../platform/using/accessing-an-external-database.md).

Un lien doit être déclaré dans le schéma possédant la clé étrangère de la table liée à partir de l&#39;élément principal :

```
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

Les liens suivent les règles suivantes :

* The definition of a link is entered on a **link**-type **`<element>`** with the following attributes:

   * **name** : nom du lien à partir de la table source,
   * **target** : nom du schéma cible,
   * **label** : libellé du lien,
   * **revLink** (optionnel) : nom du lien reverse à partir du schéma cible (déduit automatiquement par défaut),
   * **integrity** (optionnel) : intégrité référentielle de l&#39;occurrence de la table source envers l&#39;occurrence de la table cible. Les valeurs possibles sont les suivantes :

      * **define**: la suppression de l&#39;occurrence source est possible si elle n&#39;est plus référencée par une occurrence cible,
      * **normal** : la suppression de l&#39;occurrence source initialise les clés du lien sur l&#39;occurrence cible (mode par défaut), ce type d&#39;intégrité initiliase toutes les clés étrangères,
      * **own** : la suppression de l&#39;occurrence source entraîne la suppression de l&#39;occurrence cible,
      * **owncopy** : idem **own** (en cas de suppression) ou duplique les occurrences (en cas de duplication),
      * **neutral** : ne fait rien.
   * **revIntegrity** (optionnel) : intégrité sur le schéma cible (optionnel, &quot;normal&quot; par défaut),
   * **revCardinality** (optionnel) : avec la valeur &quot;single&quot; renseigne la cardinalité de type 1-1 (par défaut 1-N).
   * **externalJoin** (optionnel) : force la jointure externe
   * **revExternalJoin** (optionnel) : force la jointure externe sur le lien reverse


* Un lien fait référence à un ou plusieurs champs du tableau source vers le tableau de destination. Il n’est pas nécessaire de renseigner les champs constituant l’ `<join>` élément join, car ils sont automatiquement déduits par défaut à l’aide de la clé interne du schéma cible.
* Un index sur la clé étrangère du lien est automatiquement ajouté dans le schéma étendu.
* Un lien est composé de deux demi-liens, le premier est déclaré à partir du schéma source et le second est créé automatiquement dans le schéma étendu du schéma cible.
* La jointure d&#39;un lien peut être externe (&quot;external join&quot;) en ajoutant l&#39;attribut **externalJoin** avec la valeur &quot;true&quot; (supporté sous PostgreSQL).

>[!NOTE]
>
>Par convention, les liens sont les éléments déclarés en fin de schéma.

### Exemple 1 {#example-1}

Relation 1-N vers la table de schéma &quot;cus:company&quot; :

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

Le schéma généré :

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>
    ...
    <element label="Company" name="company" revLink="recipient" target="cus:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Company' link (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

La définition du lien est complétée avec les champs composant la jointure, c&#39;est-à -dire la clé primaire avec son XPath (&quot;@id&quot;) dans le schéma destination et la clé étrangère avec son XPath (&quot;@company-id&quot;) dans le schéma.

La clé étrangère est ajoutée automatiquement dans un élément reprenant les même caractéristiques que le champ associé dans la table destination avec comme convention de nommage le nom du schéma cible suivi du nom du champ associé (&quot;company-id&quot; dans notre exemple).

Le schéma étendu de la cible (&quot;cus:company&quot;) :

```
<schema mappingType="sql" name="company" namespace="cus" xtkschema="xtk:schema">  
  <element name="company" sqltable="CusCompany" autopk="true"> 
    <dbindex name="id" unique="true">     
      <keyfield xpath="@id"/>    
    </dbindex>   
    <key internal="true" name="id">      
      <keyfield xpath="@id"/>    
    </key>
    ...
    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iCompanyId" type="long"/>
    ...
    <element belongsTo="cus:recipient" integrity="define" label="Contact" name="recipient" revLink="company" target="nms:recipient" type="link" unbound="true">      
      <join xpath-dst="@company-id" xpath-src="@id"/>    
    </element>
  </element>
</schema>
```

Un lien réverse vers la table &quot;cus:recipient&quot; a été ajouté avec les paramètres suivant :

* **name** : déduit automatiquement avec le nom du schéma source (peut être forcé avec l&#39;attribut &quot;revLink&quot; dans la définition du lien sur le schéma source)
* **revLink** : nom du lien réverse
* **target** : clé du schéma lié (schéma &quot;cus:recipient&quot;)
* **unbound** : le lien est déclaré comme élément de collection pour une cardinalité 1-N (par défaut)
* **integrity** : par défaut &quot;define&quot; (peut être forcée avec l&#39;attribut &quot;revIntegrity&quot; dans la définition du lien sur le schéma source)

### Example 2 {#example-2}

Dans cet exemple, nous déclarons un lien vers la table de schéma &quot;nms:address&quot;. La jointure est externe et est renseignée explicitement avec l&#39;email du destinataire et le champ &quot;@address&quot; de la table liée (&quot;nms:address&quot;).

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"> 
    ...
    <element integrity="neutral" label="Info about email" name="emailInfo" revIntegrity="neutral" revLink="recipient" target="nms:address" type="link" externalJoin="true">      
      <join xpath-dst="@address" xpath-src="@email"/>
    </element>
  </element>
</srcSchema>
```

### Example 3 {#example-3}

Relation 1-1 vers la table de schéma &quot;cus:extension&quot; :

```
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

### Example 4 {#example-4}

Lien sur un dossier (schéma &quot;xtk:folder&quot;) :

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

La valeur par défaut retourne l&#39;identifiant du premier dossier éligible de type du paramètre renseigné dans la fonction &quot;DefaultFolder(&#39;nmsFolder&#39;)&quot;.

### Example 5 {#example-5}

Dans cet exemple, on souhaite créer une clé sur un lien (&quot;company&quot; vers le schéma &quot;cus:company&quot;) avec l&#39;attribut **xlink** et un champ de la table (&quot;email&quot;) :

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <key name="companyEmail"> 
      <keyfield xpath="@email"/>
      <keyfield xlink="company"/>
    </key>
    
    <attribute name="email" type="string" length="80" label="Email" desc="Recipient email"/>
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

Le schéma généré :

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>

    <dbindex name="companyEmail" unique="true">
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </dbindex>    

    <key name="companyEmail">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </key>

    <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

La définition de la clé de nom &quot;companyEmail&quot; a été entendue avec la clé étrangère du lien &quot;company&quot;, cette clé engendre un index unique sur les deux champs.
