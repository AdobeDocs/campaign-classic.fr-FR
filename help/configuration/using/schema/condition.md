---
product: campaign
title: Éléments et attributs de schéma - élément condition
description: élément condition
feature: Schema Extension
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
TQID: 'https://experienceleague.adobe.com/Jx8bLCt1UEqAZDm0cSuexx25js-e5xTsvkeSMzVCUHw'
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
source-wordcount: '95'
ht-degree: 100%
---
# élément condition {#condition--element}


## Modèle de contenu {#content-model-2}

condition:==EMPTY

## Attributs {#attributes-2}

* @boolOperator (string)
* @enabledIf (string)
* @expr (string)

## Parents {#parents-2}

`<sysfilter>`

## Enfants {#children-2}

Aucun

## Description {#description-2}

Cet élément permet de définir une condition de filtrage.

## Usage et contexte d&#39;utilisation {#use-and-context-of-use-2}

Plusieurs conditions de filtrage peuvent être définies dans un même élément `<sysfiler>`.

## Description des attributs {#attribute-description-2}

* **boolOperator (string)** : si plusieurs `<conditions>` sont définis dans le même élément `<sysfilter>`, cet attribut vous permet de les combiner. Par défaut, le lien logique entre les éléments `<condition>` est « AND ». L’attribut « @boolOperator » permet de combiner des liens de type « OR » et « AND ».
* **enabledIf (string)**: test d&#39;activation de la condition.
* **expr (string)**: une expression XTK.

## Exemples {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
