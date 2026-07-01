---
product: campaign
title: Éléments et attributs de schéma - élément method
description: élément method
feature: Schema Extension
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
TQID: https://experienceleague.adobe.com/GaT6bmWzojcbk8-XjCoqrMv2-02aoxv1cIXM0E0Y0UU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: ht
source-wordcount: 207
ht-degree: 100%

---

# élément method {#method--element}


## Modèle de contenu {#content-model-10}

method:==( help | parameters)

## Attributs {#attributes-10}

* @_operation (string)
* @access (string)
* @const (boolean)
* @hidden (boolean)
* @label (string)
* @library (string)
* @name (MNTOKEN)
* @pkonly (boolean)
* @static (boolean)

## Parents {#parents-10}

`<methods>`  ,  `<interface />`

## Enfants {#children-10}

* `<help>`
* `<parameters>`

## Description {#description-10}

Cet élément permet de définir une méthode SOAP.

## Usage et contexte d&#39;utilisation {#use-and-context-of-use-7}

Les méthodes SOAP permettent des traitements applicatifs.

L&#39;utilisation de l&#39;attribut &quot;@library&quot; est nécessaire pour déclarer une nouvelle méthode (non native): l&#39;espace de noms et le nom utilisés pour la bibliothèque sont indépendants de l&#39;espace de noms et du nom du schéma dans lequel se trouve la déclaration.

## Description des attributs {#attribute-description-10}

* **access (string)** : cet attribut définit le contrôle d’accès pour utiliser la méthode.Si cet attribut est manquant, l’identification est obligatoire.Les valeurs disponibles sont les suivantes : « anonyme », « admin » et « sql ».
* **const (boolean)**: si cet attribut est activé, les paramètres sont compris dans un élément XML qui définit la méthode.
* **label (string)**: libellé de la méthode.
* **library (string)**: méthode qui n&#39;est pas native à l&#39;application . Cet attribut prend la valeur de la bibliothèque de méthodes où se trouve la définition de la méthode (nms:mylibrary.js).
* **name (MNTOKEN)**: nom unique de la méthode.
* **static (boolean)**: si cet attribut est activé, la méthode est considérée comme autonome, tous les paramètres doivent être indiqués à la méthode lors de son appel.

## Exemples {#examples-7}

Définition de la méthode d&#39;usine &quot;Subscribe&quot; :

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>
```
