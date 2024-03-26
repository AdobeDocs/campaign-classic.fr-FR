---
product: campaign
title: Gestion des clés dans les schémas de données
description: Présentation de la gestion des clés dans les schémas de données
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
exl-id: faf63c8f-9d10-43c1-a990-91361594af9f
source-git-commit: 46dcd80d5adc31a66b47c6d75e7914b0a686326b
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 72%

---

# Gestion des clés dans les schémas {#management-of-keys}

Chaque table associée à un schéma de données doit posséder au moins une clé pour identifier un enregistrement dans une table.

Une clé est déclarée à partir de l&#39;élément principal du schéma de données.

```sql
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Une clé est dite &quot;clé primaire&quot; lorsqu’elle est renseignée en premier dans le schéma, ou si elle contient la variable `internal` est défini sur &quot;true&quot;.

Les règles suivantes s’appliquent aux clés :

* Une clé peut référencer un ou plusieurs champs du tableau.
* Un index unique est implicitement déclaré pour chaque définition de clé. Vous pouvez empêcher la création d’un index sur la clé en définissant la variable `noDbIndex` sur &quot;true&quot;.

>[!NOTE]
>
>* Par convention, les clés sont les éléments déclarés à partir de l’élément principal du schéma après la définition des index.
>
>* Les clés sont crées lorsque, lors du mapping de la table (mapping standard ou FDA), Adobe Campaign trouve des index uniques.

**Exemple**:

* Ajout d’une clé à l’adresse e-mail et la ville :

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </key>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

  Le schéma généré :

  ```sql
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
  
     <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
     <element label="Location" name="location">      
       <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
     </element>  
    </element>
  </schema>
  ```

* Ajout d&#39;une clé primaire ou interne sur le champ de nom &quot;id&quot; :

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="id" internal="true">
        <keyfield xpath="@id"/> 
      </key>
  
      <key name="email" noDbIndex="true">
        <keyfield xpath="@email"/> 
      </key>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

  Le schéma généré :

  ```sql
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
      <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
    </element>
  </schema>
  ```

## Clé auto-incrémentale {#auto-incremental-key}

La clé primaire de la plupart des tables Adobe Campaign est un entier long 32 bits généré automatiquement par le moteur de base de données. Le calcul de la valeur de la clé dépend d’une séquence (par défaut, la variable **XtkNewId** fonction SQL) générant un nombre unique dans la base de données entière. Le contenu de la clé est automatiquement renseigné à l&#39;insertion de l&#39;enregistrement.

L’avantage d’une clé incrémentale est d’obtenir une clé technique non modifiable utilisée pour les jointures entre les tables. De plus, cette clé n’est pas consommatrice car elle utilise un entier sur deux octets.

Vous pouvez spécifier dans le schéma source le nom de la séquence à utiliser avec l’attribut **pkSequence**. Si cet attribut n’est pas indiqué dans le schéma source, la séquence **XtkNewId** par défaut est utilisée. L’application utilise des séquences dédiées pour les schémas **nms:broadLog** et **nms:trackingLog** (**NmsBroadLogId** et **NmsTrackingLogId** respectivement), car il s’agit des tables qui contiennent le plus d’enregistrements.

À compter d’ACC 18.10, **XtkNewId** n’est plus la valeur par défaut de la séquence dans les schémas d’usine. Vous pouvez désormais créer ou étendre un schéma avec une séquence dédiée.

>[!IMPORTANT]
>
>Lors de la création ou de l’extension d’un schéma, vous devez conserver la valeur de la séquence de la clé primaire (@pkSequence) pour l’ensemble du schéma.

Une séquence référencée dans un schéma Adobe Campaign (**NmsTrackingLogId** par exemple) doit être associée à une fonction SQL qui renvoie le nombre d’identifiants dans les paramètres, séparés par des virgules. Cette fonction doit être appelée **GetNew** XXX **Ids**, où **XXX** correspond au nom de la séquence (**GetNewNmsTrackingLogIds**, par exemple). Affichez les fichiers **postgres-nms.sql**, **mssql-nms.sql** ou **oracle-nms.sql** fournis avec l’application dans le répertoire **datakit/nms/eng/sql/** pour récupérer l’exemple de création de séquence « NmsTrackingLogId » pour chaque moteur de base de données.

Pour déclarer une clé unique, il faut renseigner l’attribut **autopk** (avec la valeur &quot;true&quot;) sur l’élément principal du schéma de données.

**Exemple**:

Déclaration d&#39;une clé incrémentale dans le schéma source :

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

Le schéma généré :

```sql
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

>[!IMPORTANT]
>
>Un enregistrement avec une clé primaire à 0 est automatiquement inséré à la création de la table. Cet enregistrement est utilisé pour éviter les jointures externes, non efficaces sur les tables à volumes. Par défaut, toutes les clés étrangères sont initialisées avec la valeur 0, ce qui permet de toujours retourner un résultat sur la jointure lorsque la donnée n’est pas renseignée.


## En savoir plus

Pour en savoir plus, consultez les liens suivants :

* [Prise en main des schémas](about-schema-reference.md)
* [Structure d&#39;un schéma](schema-structure.md)
* [Mapping de la base de données](database-mapping.md)
* [Gestion des liens](database-links.md)
* [Modèle de données Campaign](about-data-model.md)
