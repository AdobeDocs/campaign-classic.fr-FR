---
product: campaign
title: Modification de formulaires
description: Modification de formulaires
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: f4b9ac3300094a527b5ec1b932d204f0e8e5ee86
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 100%

---


# Modification de formulaires{#editing-forms}

![](../../assets/common.svg)

## Vue d’ensemble

Les marketeurs et les opérateurs utilisent des formulaires de saisie pour créer, modifier et prévisualiser des enregistrements. Les formulaires affichent une représentation visuelle des informations.

Vous pouvez créer et modifier des formulaires de saisie :

* Vous pouvez modifier les formulaires de saisie d’usine fournis par défaut. Les formulaires de saisie d’usine sont basés sur les schémas de données d’usine.
* Vous pouvez créer des formulaires de saisie personnalisés, en fonction des schémas de données que vous définissez.

Les formulaires sont des entités de type `xtk:form`. Vous pouvez afficher la structure du formulaire de saisie dans le schéma `xtk:form`. Pour afficher ce schéma, sélectionnez **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Schémas de données]** à partir du menu. En savoir plus sur la [structure des formulaires](form-structure.md).

Pour accéder aux formulaires de saisie, sélectionnez **[!UICONTROL Administration] > [!UICONTROL Configuration] > [!UICONTROL Formulaires de saisie]** à partir du menu :

![](assets/d_ncs_integration_form_arbo.png)

Pour concevoir des formulaires, modifiez le contenu XML dans l’éditeur XML :

![](assets/d_ncs_integration_form_edit.png)

[En savoir plus](form-structure.md#formatting).

Pour prévisualiser un formulaire, cliquez sur l’onglet **[!UICONTROL Aperçu]** :

![](assets/d_ncs_integration_form_preview.png)

## Types de formulaires

Vous pouvez créer différents types de formulaires de saisie. Le type de formulaire détermine la manière dont les utilisateurs naviguent dans ce dernier :

* Écran console

   Il s’agit du type de formulaire par défaut. Le formulaire comprend une seule page.

   ![](assets/console_screen_form.png)

* Gestion de contenu

   Utilisez ce type de formulaire pour la gestion de contenu. Consultez ce [cas d’utilisation](../../delivery/using/use-case--creating-content-management.md).

   ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Assistant

   Ce formulaire comprend plusieurs écrans flottants organisés en séquences spécifiques. Les utilisateurs peuvent naviguer d’un écran à l’autre. [En savoir plus](form-structure.md#wizards).

* Iconbox

   Ce formulaire comprend plusieurs pages. Pour parcourir le formulaire, les utilisateurs doivent sélectionner les icônes à sa gauche.

   ![](assets/iconbox_form_preview.png)

* Notebook

   Ce formulaire comprend plusieurs pages. Pour parcourir le formulaire, les utilisateurs doivent sélectionner les onglets dans la partie supérieure.

   ![](assets/notebook_form_preview.png)

* Séparation verticale

   Ce formulaire affiche une arborescence de navigation.

* Séparation horizontale

   Ce formulaire affiche une liste d’éléments.

## Conteneurs

Dans les formulaires, vous pouvez utiliser des conteneurs à diverses fins :

* Organisation du contenu dans les formulaires
* Définition de l’accès aux champs de saisie
* Imbrication de formulaires dans d’autres formulaires

[En savoir plus](form-structure.md#containers).

### Organisation du contenu

Utilisez des conteneurs pour organiser le contenu dans les formulaires :

* Vous pouvez regrouper des champs en sections.
* Vous pouvez ajouter des pages à des formulaires de plusieurs pages.

Pour insérer un conteneur, utilisez l’élément `<container>`. [En savoir plus](form-structure.md#containers).

#### Regroupement de champs

Utilisez des conteneurs pour regrouper les champs de saisie en sections organisées.

Pour insérer une section dans un formulaire, utilisez l’élément suivant : `<container type="frame">`. Vous pouvez éventuellement ajouter un titre de section. Pour ce faire, utilisez l’attribut `label`.

Syntaxe : `<container type="frame" label="`*titre_section*`"> […] </container>`

Dans cet exemple, un conteneur définit la section **Création**, qui comprend les champs de saisie **[!UICONTROL Créé par]** et **[!UICONTROL Nom]** :

```xml
<form _cs="Coupons (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Coupons"
      name="coupon" namespace="nms" type="default" xtkschema="xtk:form">
  <input xpath="@code"/>
  <input xpath="@type"/>
  <container label="Creation" type="frame">
    <input xpath="createdBy"/>
    <input xpath="createdBy/@name"/>
  </container>
</form>
```

![](assets/console_screen_form.png)

#### Ajout de pages à des formulaires de plusieurs pages

Pour les formulaires à plusieurs pages, utilisez un conteneur pour créer une page de formulaire.

Cet exemple montre les conteneurs pour les pages **Général** et **Détails** d’un formulaire :

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

### Définition de l’accès aux champs

Utilisez des conteneurs pour définir ce qui est visible et l’accès aux champs. Vous pouvez activer ou désactiver des groupes de champs.

### Imbrication de formulaires

Utilisez des conteneurs pour imbriquer des formulaires dans d’autres formulaires. [En savoir plus](#add-pages-to-multipage-forms).

## Références aux images

Pour rechercher des images, sélectionnez **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]** à partir du menu.

Pour associer une image à un élément du formulaire, par exemple une icône, vous pouvez ajouter une référence à une image. Par exemple, utilisez l’attribut `img` dans l’élément `<container>`.

Syntaxe : `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

Cet exemple montre les références aux images `book.png` et `detail.png` de l’espace de noms `ncm` :

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

Ces images constituent les icônes sur lesquelles les utilisateurs cliquent pour parcourir un formulaire à plusieurs pages :

![](assets/nested_forms_preview.png)
