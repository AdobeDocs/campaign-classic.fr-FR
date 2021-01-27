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
source-wordcount: '43'
ht-degree: 100%

---


# élément sysFilter{#sysfilter--element}

## Modèle de contenu {#content-model-15}

sysFilter:==condition

## Attributs {#attributes-15}

Aucun

## Parents {#parents-15}

`<element>`

## Enfants {#children-15}

`<condition>`

## Description {#description-15}

Cet élément permet de définir un filtre.

## Description des attributs {#attribute-description-15}

Cet élément n&#39;a aucun attribut.

## Exemples       {#examples-12}

Définition d&#39;un filtre avec une condition sur l&#39;attribut @name:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
