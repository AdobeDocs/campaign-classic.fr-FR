---
product: campaign
title: Éléments et attributs - élément srcschema
description: Éléments et attributs
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
TQID: https://experienceleague.adobe.com/nUdM-iVzh7yI2Z3ZnFh5JK8FDZpmHAR1crzEb9S5xYg
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2: id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 459
ht-degree: 57%

---

# élément srcSchema {#srcschema--element}


## Modèle de contenu {#content-model-14}

srcSchema:==(attribute | createdBy | data | element | enumeration | help | interface | methods | modifiedBy)

## Attributs {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), extendedSchema (string), img (string), implements (string), label (string), labelSingular (string), lastModified (datetime), library (boolean), mappingType (string), modifiedBy-id (long), name (string), namespace (string), useRecycleBin (boolean), view (boolean), xtkschema (string)

## Parents {#parents-14}

Aucun

## Enfants {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

## Description {#description-14}

Le `<srcschema>` est l’élément racine d’un schéma. Il s’agit du point d’entrée pour la définition du schéma.

## Usage et contexte d&#39;utilisation {#use-and-context-of-use-9}

La présentation du schéma est disponible dans [À propos de la référence du schéma](../../../configuration/using/about-schema-reference.md) et [Structure du schéma](../../../configuration/using/schema-structure.md).

## Description des attributs {#attribute-description-14}

* **created (datetime)** : cet attribut fournit des informations sur la date et l&#39;heure de création du schéma. Elle comporte un formulaire « Date et heure ». Les valeurs affichées proviennent du serveur. L’heure s’affiche au format UTC.
* **createdBy-id (long)**: correspond à l&#39;identifiant de l&#39;opérateur qui a crée le schéma.
* **desc (string)**: description du schéma.
* **entitySchema (string)** : schéma de base sur lequel on base la syntaxe et la validation du schéma (par défaut pour Adobe Campaign : xtk:srcSchema). Lors de l&#39;enregistrement du schéma courant, Adobe Campaign validera la grammaire du schéma courant avec le schéma déclaré dans l&#39;attribut @xtkschema.
* **extendedSchema (string)**: reçoit le nom du schéma d&#39;usine sur lequel est basé l&#39;extension du schéma courant. Le formulaire est « espace de noms :name. »
* **img (string)** : icône associée au schéma (peut se définir dans l’assistant de création du schéma).
* **label (string)**: libellé du schéma.
* **labelSingular (string)**: libellé (au singulier) destiné à l&#39;affichage dans l&#39;interface.
* **lastModified (datetime)** : cet attribut fournit des informations sur la date et l’heure de la dernière modification. Elle comporte un formulaire « Date et heure ». Les valeurs affichées proviennent du serveur. L’heure s’affiche au format UTC.
* **library (boolean)** : utilisation du schéma en tant que bibliothèque et non en tant qu&#39;entité. Ce schéma peut donc être référencé par d&#39;autres schémas grâce aux attributs « @ref » et « @template ».
* **mappingType (string)**:

   * &quot;sql&quot;: mapping base de données
   * &quot;textFile&quot;: mapping fichier texte
   * &quot;xmlFile&quot;: mapping fichier texte au format XML
   * &quot;binaryFile&quot;: mapping fichier binaire

* **modifiedBy-id (long)**: correspond à l&#39;identifiant de l&#39;opérateur qui a modifié le schéma.
* **name (string)**: nom unique du schéma.
* **namespace (string)**: espace de noms du schéma (espace par défaut : nms, xtk, nl). Lors de la création d’un schéma pour un projet, nous vous recommandons d’utiliser un espace de noms dédié.
* **useRecycleBin (booléen)** : active la fonctionnalité de corbeille dans l&#39;application. Les enregistrements supprimés seront placés dans la corbeille avant la suppression finale. Cette fonction n’est disponible qu’en mode « Diffusion ».
* **view (boolean)**: s&#39;il est activé (@view=&quot;true&quot;), le schéma sera utilisé comme une vue. L’assistant de mise à jour de la structure de la base ne tiendra pas compte du schéma. Cette option permet le plus souvent de référencer des tables externes.
* **xtkschema (string)** : nom du schéma qui définit la grammaire du schéma (xtk:srcSchema par défaut).

## Exemples {#examples-11}

`<srcschema>` du schéma d&#39;usine « nms:delivery »

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
