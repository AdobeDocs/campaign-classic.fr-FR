---
solution: Campaign Classic
product: campaign
title: Eléments et attributs
description: Eléments et attributs
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
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
