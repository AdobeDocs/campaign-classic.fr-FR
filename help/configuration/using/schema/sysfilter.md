---
product: campaign
title: Éléments et attributs - élément sysFilter
description: Éléments et attributs
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# élément sysFilter {#sysfilter--element}


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

Définition d&#39;un filtre avec une condition sur l&#39;attribut @name :

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
