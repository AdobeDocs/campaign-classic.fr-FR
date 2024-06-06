---
product: campaign
title: Mapping de la base de données
description: Mapping de la base de données
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: ht
source-wordcount: '525'
ht-degree: 100%

---

# Mapping de la base de données{#database-mapping}

Le mapping SQL de l’exemple de schéma décrit [dans cette page](schema-structure.md) génère le document XML suivant :

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient email address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

L’élément racine du schéma est passé de **`<srcschema>`** à **`<schema>`**.

Cet autre type de document est généré automatiquement à partir du schéma source et est simplement appelé schéma.

Les noms SQL sont déduits automatiquement en fonction du nom et du type de l&#39;élément.

Les règles de nommage des noms SQL sont les suivantes :

* **table** : concaténation de l&#39;espace de noms et du nom du schéma

  Dans notre exemple le nom de la table est renseigné à partir de l&#39;élément principal du schéma dans l&#39;attribut **sqltable** :

  ```sql
  <element name="recipient" sqltable="CusRecipient">
  ```

* **champ** : nom de l&#39;élément précédé d&#39;un préfixe défini en fonction de son type :&#39;i&#39; pour entier, &#39;d&#39; pour doublon, &#39;s&#39; pour chaîne, &#39;ts&#39; pour les dates, etc.

  Le nom du champ est renseigné à partir de l&#39;attribut **sqlname** pour chaque **`<attribute>`** et **`<element>`** typé :

  ```sql
  <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
  ```

>[!NOTE]
>
>Les noms SQL peuvent être surchargés à partir du schéma source, il faut renseigner les attributs &quot;sqltable&quot; ou &quot;sqlname&quot; sur l&#39;élément concerné.

Le script SQL de création de la table généré à partir du schéma étendu est le suivant :

```sql
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

Les contraintes des champs SQL sont les suivantes :

* pas de valeurs nulles sur les champs numériques et de dates
* les champs numériques sont initialisés à 0

## Champs XML {#xml-fields}

Par défaut, tout élément de type **`<attribute>`** et **`<element>`** est mappé sur un champ SQL de la table du schéma de données. Vous pouvez toutefois référencer ce champ au format XML plutôt que SQL, ce qui signifie que les données sont stockées dans un champ mémo (&quot;mData&quot;) de la table contenant les valeurs de tous les champs XML. Le stockage de ces données est un document XML qui respecte la structure du schéma.

Pour renseigner un champ en XML, il faut ajouter l&#39;attribut **xml** avec la valeur &quot;true&quot; sur l&#39;élément concerné.

**Exemple** : voici deux exemples d&#39;utilisation des champs de type XML.

* Champ commentaire multi-lignes :

  ```sql
  <element name="comment" xml="true" type="memo" label="Comment"/>
  ```

* Description de données au format HTML :

  ```sql
  <element name="description" xml="true" type="html" label="Description"/>
  ```

  Le type &quot;html&quot; permet de stocker le contenu HTML dans une balise CDATA et d&#39;afficher un contrôle spécifique d&#39;édition HTML dans l&#39;interface cliente Adobe Campaign.

Utilisez les champs XML pour ajouter de nouveaux champs sans modifier la structure physique de la base de données. Un autre avantage est d&#39;utiliser moins de ressources (taille allouée des champs SQL, limite du nombre de champs par table, etc.). Notez toutefois que vous ne pouvez pas indexer ou filtrer un champ XML.

## Champs indexés {#indexed-fields}

Les index permettent d’optimiser les performances des requêtes SQL utilisées dans l’application.

Un index est déclaré à partir de l’élément principal du schéma de données.

```sql
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Les index suivent les règles suivantes :

* Un index peut référencer un ou plusieurs champs de la table.
* Un index peut être unique (afin d’éviter les doublons) dans tous les champs si l’attribut **unique** contient la valeur « true ».
* Le nom SQL de l’index est déterminé à partir du nom SQL de la table et du nom de l’index.

>[!NOTE]
>
>* Par convention, les index sont les éléments déclarés en premier à partir de l’élément principal du schéma.
>
>* Les index sont crées automatiquement lors d’un mapping de table (mapping standard ou FDA).

**Exemple**:

* Ajout d’un index à l’adresse e-mail et la ville :

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </dbindex>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

* Ajout d’un index unique au champ du nom « id » :

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="id" unique="true">
        <keyfield xpath="@id"/> 
      </dbindex>
  
      <dbindex name="email">
        <keyfield xpath="@email"/> 
      </dbindex>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

## En savoir plus

Pour en savoir plus, consultez les liens suivants :

* [Prise en main des schémas](about-schema-reference.md)
* [Structure d&#39;un schéma](schema-structure.md)
* [Gestion des clés](database-keys.md)
* [Gestion des liens](database-links.md)
* [Modèle de données Campaign](about-data-model.md)