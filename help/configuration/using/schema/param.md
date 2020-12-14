---
solution: Campaign Classic
product: campaign
title: Eléments et attributs
description: Eléments et attributs
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 98%

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

Cet élémént permet de définir un paramètre d&#39;un appel à une méthode SOAP.

## Description des attributs {#attribute-description-12}

* **desc (string)** : description qui concerne l’élément `<param>`.
* **inout (string)**: cet attribut définit si le paramètre est en entrée de l&#39;appel SOAP (in) ou bien en sortie (out). Si cet attribut n&#39;est pas précisé, le paramètre est par défaut en entrée (&quot;@inout=in&quot;).
* **label (string)** : libellé `<param>`
* **localizable (string)**: s&#39;il est activé, cet attribut indique à l&#39;outil de collecte de récupérer la valeur de l&#39;attribut &quot;@label&quot; pour traduction (usage interne).
* **name (MNTOKEN)**: nom interne du `<param>`
* **type (string)** : cet attribut définit le type d’élément `<param>`

   Liste des types disponibles :

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
