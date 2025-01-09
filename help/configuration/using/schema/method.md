---
product: campaign
title: Éléments et attributs de schéma - élément method
description: élément method
feature: Schema Extension
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: ht
source-wordcount: '207'
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

* **access (string)**: cet attribut définit un contrà´le d&#39;accès sur l&#39;utilisation de la méthode. Si cet attribut est absent, l&#39;identification est obligatoire. Les valeurs disponibles sont &#39;anonymous&#39;, &#39;admin&#39; et &#39;sql&#39;.
* **const (boolean)**: si cet attribut est activé, les paramètres sont compris dans un élément XML qui définit la méthode.
* **label (string)**: libellé de la méthode.
* **library (string)**: méthode qui n&#39;est pas native à l&#39;application . Cet attribut prend la valeur de la bibliothèque de méthodes dans laquelle se trouve la définition de la méthode (nms:mabibliotheque.js).
* **name (MNTOKEN)**: nom unique de la méthode.
* **static (boolean)**: si cet attribut est activé, la méthode est considérée comme autonome, tous les paramètres doivent être indiqués à la méthode lors de son appel.

## Exemples       {#examples-7}

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
