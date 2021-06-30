---
product: campaign
title: Eléments et attributs
description: Eléments et attributs
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: ht
source-wordcount: '101'
ht-degree: 100%

---

# élément keyfield{#keyfield--element}

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

Cet élément définit les champs à intégrer à un index ou bien à une clef.

## Description des attributs {#attribute-description-9}

* **xlink (MNTOKEN)**: permet de référencer automatiquement les clefs étrangères définies dans la jointure pour une table de relation (lien N-N).
* **xpath (MNTOKEN)** : définition d’un index ou d’une clé sur un élément `<attribute>`. Cet attribut reçoit un Xpath qui définit le chemin d’accès à l’attribut du schéma qui définit la clé ou l’index.

## Exemples       {#examples-}

Sélection du champ &quot;sName&quot; dans un index avec un Xpath sur &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
