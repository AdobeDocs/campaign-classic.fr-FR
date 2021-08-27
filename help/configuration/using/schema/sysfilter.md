---
product: campaign
title: Eléments et attributs
description: Eléments et attributs
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '43'
ht-degree: 100%

---

# élément sysFilter {#sysfilter--element}

![](../../../assets/v7-only.svg)

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
