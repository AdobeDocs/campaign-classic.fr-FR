---
product: campaign
title: Éléments et attributs de schéma - élément help
description: élément help
feature: Schema Extension
exl-id: 8207868c-25ff-4ca9-afdd-41b324c7ac0d
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# élément help {#help--element}


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
