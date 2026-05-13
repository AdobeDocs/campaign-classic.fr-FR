---
product: campaign
title: Gestion des clés dans les schémas de données
description: Comprendre la gestion des clés dans les schémas de données
feature: Configuration, Instance Settings
role: Developer
exl-id: faf63c8f-9d10-43c1-a990-91361594af9f
TQID: https://experienceleague.adobe.com/dErbfzRabMls-5x1S3eRZO94Kqcz9LRh3PaUhVD5zAU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 627
ht-degree: 78%

---

# Gestion des clés dans les schémas {#management-of-keys}

Chaque table associée à un schéma de données doit posséder au moins une clé pour identifier un enregistrement dans une table.

Une clé est déclarée à partir de l’élément principal du schéma de données.

```sql
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Une clé est dite primaire lorsqu’elle est renseignée en premier dans le schéma ou si elle contient l’attribut `internal` avec la valeur « true ».

Les règles suivantes s’appliquent aux clés :

* Une clé peut référencer un ou plusieurs champs de la table.
* Un index unique est implicitement déclaré pour chaque définition de clé. Il est possible d’empêcher la création de l’index sur la clé en définissant l’attribut `noDbIndex` sur « true ».

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

La clé primaire de la plupart des tables Adobe Campaign est un entier long 32 bits auto-généré par le moteur de base de données. Le calcul de la valeur de la clé repose sur une séquence (par défaut, la fonction SQL **XtkNewId**) générant un nombre unique dans toute la base de données. Le contenu de la clé est automatiquement renseigné à l’insertion de l’enregistrement.

L&#39;avantage d&#39;une clé incrémentale est de fournir une clé technique non modifiable pour les jointures entre les tables. En outre, cette clé n&#39;occupe pas beaucoup de mémoire car elle utilise un entier à deux octets.

Vous pouvez spécifier dans le schéma source le nom de la séquence à utiliser avec l’attribut **pkSequence**. Si cet attribut n’est pas indiqué dans le schéma source, la séquence **XtkNewId** par défaut est utilisée. L’application utilise des séquences dédiées pour les schémas **nms:broadLog** et **nms:trackingLog** (**NmsBroadLogId** et **NmsTrackingLogId**, respectivement), car il s’agit des tables qui contiennent le plus d’enregistrements.

Depuis ACC 18.10, **XtkNewId** n’est plus la valeur par défaut de la séquence dans les schémas d’usine. Vous pouvez désormais créer un schéma ou étendre le schéma existant avec une séquence dédiée.

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
>Un enregistrement avec une clé primaire à 0 est automatiquement inséré à la création de la table. Cet enregistrement est utilisé pour éviter les jointures externes, qui ne sont pas efficaces sur les tables de volumes. Par défaut, toutes les clés étrangères sont initialisées avec la valeur 0 afin qu&#39;un résultat puisse toujours être retourné sur la jointure lorsque la donnée n&#39;est pas renseignée.


## En savoir plus

Pour en savoir plus, consultez les liens suivants :

* [Prise en main des schémas](about-schema-reference.md)
* [Structure d&#39;un schéma](schema-structure.md)
* [Mapping de la base de données](database-mapping.md)
* [Gestion des liens](database-links.md)
* [Modèle de données Campaign](about-data-model.md)
