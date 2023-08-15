---
product: campaign
title: Éléments et attributs - élément value
description: Éléments et attributs
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 100%

---

# élément value {#value--element}

![](../../../assets/v7-only.svg)

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

* **applicableIf (string)**: cet attribut permet de rendre une valeur d&#39;énumération optionnelle. Il reçoit une expression XTK.
* **desc (string)**: description de la valeur de l&#39;énumération.
* **enabledIf (string)**: condition d&#39;activation de la valeur de l&#39;énumération.
* **img (string)**: image associée à l&#39;énumération sous la forme &quot;namespace:nom_image&quot;. Physiquement l&#39;image doit être importée sur le serveur applicatif.
* **label (string)**: libellé de la valeur de l&#39;énumération.
* **name (string)**: nom interne de la valeur de l&#39;énumération.
* **value (string)**: valeur de la valeur de l&#39;énumération. Le type de la valeur est défini en fonction du type de l&#39;énumération. Si l&#39;énumération est de type chaine de caractère, elle ne peut contenir que des valeurs de type chaine de caractères.

## Exemples       {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
