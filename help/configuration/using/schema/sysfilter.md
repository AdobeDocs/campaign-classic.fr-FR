---
product: campaign
title: Éléments et attributs - élément sysFilter
description: Éléments et attributs
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
TQID: 'https://experienceleague.adobe.com/hjsD-JSGBPnwyj1IsLDo-tUy-63apy0-6kT9vngaaQk'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '45'
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

## Exemples {#examples-12}

Définition d&#39;un filtre avec une condition sur l&#39;attribut @name :

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
