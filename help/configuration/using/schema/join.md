---
product: campaign
title: Éléments et attributs de schéma - élément join
description: élément join
feature: Schema Extension
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 100%

---

# élément join {#join--element}


## Modèle de contenu {#content-model-7}

join:==EMPTY

## Attributs {#attributes-7}

* @dstFilterExpr (string)
* @xpath-dst (string)
* @xpath-src (string)

## Parents {#parents-7}

`<element>`

## Enfants {#children-7}

Aucun

## Description {#description-7}

Cet élément permet de définir les champs créant une jointure entre des tables SQL.

## Usage et contexte d&#39;utilisation {#use-and-context-of-use-5}

Un  élément `<join>` ne peut être utilisé que si l’élément `<element>` parent est de type &quot;link&quot;. Cela signifie que l’attribut « @type=link » doit être déclaré pour l’élément parent.

Il n’est pas nécessaire de spécifier le nom et l’espace de noms de la table distante dans l’élément `<join>`. Ils doivent être spécifiés dans le `<element>` parent.

Par convention, les liens sont définis à la fin du schéma.

Si l’élément `<join>` n&#39;est pas précisé lors de la définition d&#39;un élément de type &quot;link&quot;, alors le lien sera automatiquement posé sur les clefs primaires des deux tables.

## Description des attributs {#attribute-description-7}

* **dstFilterExpr (string)** : cet attribut permet de restreindre le nombre de valeurs éligibles dans la table distante.
* **xpath-dst (string)** : cet attribut reçoit un Xpath (attribut « @name » de la table distante).
* **xpath-src (string)** : cet attribut reçoit un Xpath (attribut « @name » dans le schéma courant).

## Exemples       {#examples-6}

Lien entre le champ &#39;email&#39; de la table courante et le champ &quot;@compagny-id&quot; de la table distante:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Lien &#39;filtré&#39; vers la table &quot;cus:Country&quot; basé sur le contenu du champ &quot;@country&quot; qui doit contenir la valeur &#39;FR&#39; :

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
