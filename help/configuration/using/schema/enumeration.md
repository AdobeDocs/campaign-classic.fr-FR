---
product: campaign
title: Éléments et attributs de schéma - élément enumeration
description: élément enumeration
feature: Schema Extension
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 100%

---

# élément enumeration {#enumeration--element}

![](../../../assets/v7-only.svg)

## Modèle de contenu {#content-model-5}

enumeration:==(help| value)

## Attributs {#attributes-5}

* @basetype (string)
* @default (string)
* @desc (string)
* @label (string)
* @name (string)
* @template (string)

## Parents {#parents-5}

`<srcschema>`

## Enfants {#children-5}

* `<help>`
* `<value>`

## Description {#description-5}

Cet élément permet de définir une énumération de valeurs. Une énumération appartient au schéma dans laquelle elle est définie mais elle reste accessible depuis un autre schéma.

## Usage et contexte d&#39;utilisation {#use-and-context-of-use-4}

Une énumération se définit au tout début d&#39;un schéma (avant la définition de l&#39;élément principal).

## Description des attributs {#attribute-description-5}

* **basetype (string)**: type des valeurs stockées dans l&#39;énumération.

  Liste des types disponibles :

   * ANY
   * bin
   * blob
   * boolean
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * DOMDocument
   * DOMElement
   * double
   * enum
   * float
   * html
   * int64
   * link
   * long
   * memo
   * MNTOKEN
   * percent
   * primarykey
   * short
   * string
   * time
   * timespan
   * uuid

* **default (string)**: valeur par défaut. La valeur par défaut peut aussi être une des valeurs définies dans l&#39;énumération.
* **desc (string)**: description de l&#39;énumération.
* **label (string)**: libellé de l&#39;énumération.
* **name (string)**: nom interne de l&#39;énumération.
* **template (string)** : cet attribut définit une référence à un élément `<enumeration>` partagé par plusieurs schémas. La définition est automatiquement copiée dans le schéma actuel.

## Exemples  {#examples-4}

Exemple d&#39;énumération dont les valeurs sont stockées en base:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

Définition d&#39;un énumération avec une valeur par défaut:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```
