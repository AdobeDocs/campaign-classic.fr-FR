---
solution: Campaign Classic
product: campaign
title: Eléments et attributs
description: Eléments et attributs
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 100%

---


# `<keyfield>` element {#keyfield--element}

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

## Exemples      {#examples-}

Sélection du champ &quot;sName&quot; dans un index avec un Xpath sur &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
