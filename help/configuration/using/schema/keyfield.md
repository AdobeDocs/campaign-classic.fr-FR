---
product: campaign
title: Éléments et attributs de schéma - élément keyfield
description: élément keyfield
feature: Schema Extension
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
TQID: https://experienceleague.adobe.com/tVWLlgg97dREZZHvUW81FhDVhS-uNvUHlbhH0YBrAdY
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 104
ht-degree: 100%

---

# élément keyfield {#keyfield--element}


## Modèle de contenu {#content-model-9}

keyfield:==EMPTY

## Attributs {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Parents {#parents-9}

`<key>`  ,  `<dbindex />`

## Enfants {#children-9}

Aucun

## Description {#description-9}

Cet élément définit les champs à intégrer à un index ou bien à une clé.

## Description des attributs {#attribute-description-9}

* **xlink (MNTOKEN)** : permet de référencer automatiquement les clefs étrangères définies dans la jointure pour une table de relation (lien N-N).
* **xpath (MNTOKEN)** : définition d’un index ou d’une clé sur un élément `<attribute>`. Cet attribut reçoit un Xpath qui définit le chemin d’accès à l’attribut du schéma qui définit la clé ou l’index.

## Exemples {#examples-}

Sélection du champ « sName » dans un index avec un Xpath sur « @name » :

```
<keyfield xpath="@name"/>
```
