---
product: campaign
title: Éléments et attributs de schéma - élément param
description: élément param
feature: Schema Extension
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
TQID: 'https://experienceleague.adobe.com/fiMkJtGU90FP-G6BJhTnIrgBJ39uIJaakqKD49EhXS0'
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
source-wordcount: '177'
ht-degree: 100%
---
# élément param {#param--element}


## Modèle de contenu {#content-model-12}

param:==help

## Attributs {#attributes-12}

* @_operation (string)
* @desc (string)
* @enum (string)
* @inout (string)
* @label (string)
* @localizable (string)
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type (string)

## Parents {#parents-12}

`<parameters>`

## Enfants {#children-12}

`<help>`

## Description {#description-12}

Cet élément permet de définir un paramètre d&#39;un appel à une méthode SOAP.

## Description des attributs {#attribute-description-12}

* **desc (string)** : description qui concerne l’élément `<param>`.
* **inout (string)** : cet attribut définit si le paramètre est en entrée (in) ou en sortie (out) de l’appel SOAP. Si cet attribut n’est pas précisé, le paramètre est par défaut en entrée (« @inout=in »).
* **label (string)** : libellé `<param>`
* **localizable (string)**: s&#39;il est activé, cet attribut indique à l&#39;outil de collecte de récupérer la valeur de l&#39;attribut &quot;@label&quot; pour traduction (usage interne).
* **name (MNTOKEN)**: nom interne du `<param>`
* **type (string)** : cet attribut définit le type d’élément `<param>`

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

## Exemples {#examples-9}

Définition du paramètre en entrée &quot;serviceName&quot; de type chaîne de caractères:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
