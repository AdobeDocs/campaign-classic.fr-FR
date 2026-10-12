---
product: campaign
title: Mapping de la base de données
description: Mapping de la base de données
feature: Configuration, Instance Settings
role: Developer
exl-id: 728b509f-2755-48df-8b12-449b7044e317
TQID: 'https://experienceleague.adobe.com/d3oQ8zJVsjVdj9PZ30rQ8hEuern1l3ZlMAWrbymhnvs'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 73%
---
# Mapping de la base de données{#database-mapping}

Cette page décrit comment déclarer des index sur les champs d’un schéma.

Dans le cadre de la transition de Campaign v7 vers v8, le jeu de documentation de Campaign Classic a été rationalisé et réorganisé. Les fonctionnalités communes sont désormais disponibles exclusivement dans le jeu de documentation de Campaign v8. Pour en savoir plus sur le mapping SQL des schémas, consultez la documentation de [Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/developer/schemas-forms/database-mapping){target=_blank}.

[![Image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/developer/schemas-forms/database-mapping){target=_blank}

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
* [Gestion des liens](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/developer/schemas-forms/database-links){target="_blank"} (documentation de Campaign v8)
