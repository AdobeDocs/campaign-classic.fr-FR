---
product: campaign
title: Eléments et attributs
description: Eléments et attributs
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: ht
source-wordcount: '93'
ht-degree: 100%

---

# élément condition{#condition--element}

## Modèle de contenu {#content-model-2}

condition:==EMPTY

## Attributs {#attributes-2}

* @boolOperator (string)
* @enabledIf (string)
* @expr (string)

## Parents {#parents-2}

`<sysfilter>`

## Enfants {#children-2}

Aucun

## Description {#description-2}

Cet élément permet de définir une condition de filtrage.

## Usage et contexte d&#39;utilisation {#use-and-context-of-use-2}

Plusieurs conditions de filtrage peuvent être définies dans un même élément `<sysfiler>`.

## Description des attributs {#attribute-description-2}

* **boolOperator (string)** : si plusieurs `<conditions>` sont définis dans le même élément `<sysfilter>`, cet attribut vous permet de les combiner. Par défaut, le lien logique entre les éléments `<condition>` est « AND ». L’attribut « @boolOperator » permet de combiner des liens de type « OR » et « AND ».
* **enabledIf (string)**: test d&#39;activation de la condition.
* **expr (string)**: une expression XTK.

## Exemples       {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
