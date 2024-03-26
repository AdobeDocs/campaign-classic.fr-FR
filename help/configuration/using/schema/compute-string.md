---
product: campaign
title: Éléments et attributs - élément compute-string
description: élément compute-string
feature: Schema Extension
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 100%

---

# élément compute-string {#compute-string--element}

![](../../../assets/v7-only.svg)

## Modèle de contenu {#content-model-1}

compute-string:==EMPTY

## Attributs {#attributes-1}

@expr

## Parents {#parents-1}

`<element>`

## Enfants {#children-1}

Aucun

## Description {#description-1}

L’élément `<compute-string>` sert à générer une chaine basée sur une expression XTK afin d&#39;afficher dans l&#39;interface un libellé « construit » à partir de plusieurs valeurs.

## Usage et contexte d&#39;utilisation {#use-and-context-of-use-1}

Lorsqu’aucun `<compute-string>` n’est défini, un élément `<compute-string>` est renseigné par défaut avec les valeurs de la clé primaire du schéma.

## Description des attributs {#attribute-description-1}

* **expr (string)** : expression XTK et/ou Xpath.

## Exemples       {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Résultat de la chaîne calculée sur un destinataire : &quot;Dupont René (rene.dupont@aol.com)&quot; :

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
