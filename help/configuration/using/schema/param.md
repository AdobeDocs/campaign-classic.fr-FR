---
product: campaign
title: Éléments et attributs de schéma - élément param
description: élément param
feature: Schema Extension
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
TQID: https://experienceleague.adobe.com/fiMkJtGU90FP-G6BJhTnIrgBJ39uIJaakqKD49EhXS0
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: ht
source-wordcount: 177
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
* **inout (string)** : cet attribut définit si le paramètre est en entrée (in) ou en sortie (out) de l’appel SOAP.Si cet attribut n’est pas précisé, le paramètre est par défaut en entrée (« @inout=in »).
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
