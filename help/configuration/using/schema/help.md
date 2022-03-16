---
product: campaign
title: 'Éléments et attributs de schéma - élément d’aide '
description: élément help
exl-id: 8207868c-25ff-4ca9-afdd-41b324c7ac0d
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 87%

---

# élément help {#help--element}

![](../../../assets/v7-only.svg)

## Modèle de contenu {#content-model-6}

help:==EMPTY

## Attributs {#attributes-6}

Aucun

## Parents {#parents-6}

`<srcschema>`  ,  `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

## Enfants {#children-6}

Aucun

## Description {#description-6}

Cet élément vous permet de décrire un élément `<element>` ou `<attribute>`. Il ne peut contenir que du texte et est stocké en XML dans la base de données.

## Description des attributs {#attribute-description-6}

Cet élément n&#39;a aucun attribut.

## Exemples       {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```
