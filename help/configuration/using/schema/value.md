---
product: campaign
title: Éléments et attributs - élément value
description: Éléments et attributs
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
TQID: 'https://experienceleague.adobe.com/rGaA--VHVGxCBHX5SgZUQQ9AwMgOTYWqMYGpYWU4-WY'
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
source-wordcount: '147'
ht-degree: 100%
---
# élément value {#value--element}


## Modèle de contenu {#content-model-16}

value:==help

## Attributs {#attributes-16}

* @applicableIf (string)
* @desc (string)
* @enabledIf (string)
* @img (string)
* @label (string)
* @name (string)
* @value (string)

## Parents {#parents-16}

`<enumeration>`

## Enfants {#children-16}

`<help>`

## Description {#description-16}

Cet élément permet de définir les valeurs stockées dans une énumération.

## Description des attributs {#attribute-description-16}

* **applicableIf (string)** : cet attribut permet de rendre une valeur d’énumération facultative. Il reçoit une expression XTK.
* **desc (string)**: description de la valeur de l&#39;énumération.
* **enabledIf (string)**: condition d&#39;activation de la valeur de l&#39;énumération.
* **img (string)** : image associée à l’énumération dans le formulaire « namespace:image_name ». Physiquement l&#39;image doit être importée sur le serveur applicatif.
* **label (string)**: libellé de la valeur de l&#39;énumération.
* **name (string)**: nom interne de la valeur de l&#39;énumération.
* **label (string)** : valeur de la valeur de l’énumération. Le type de la valeur est défini en fonction du type de l’énumération. Si l’énumération est de type chaîne de caractères, elle ne peut contenir que des valeurs de type chaîne de caractères.

## Exemples {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
