---
solution: Campaign Classic
product: campaign
title: Eléments et attributs
description: Eléments et attributs
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 95%

---


# élément d&#39;aide {#help--element}

## Modèle de contenu {#content-model-6}

help:==EMPTY

## Attributs {#attributes-6}

Aucun

## Parents {#parents-6}

`<srcschema>`  ,  `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

## Enfants {#children-6}

Aucun

## Description {#description-6}

Cet élément vous permet de décrire un élément `<element>`  ou `<attribute>`. Il ne peut contenir que du texte et est stocké en XML dans la base de données.

## Description des attributs {#attribute-description-6}

Cet élément n&#39;a aucun attribut.

## Exemples      {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```
