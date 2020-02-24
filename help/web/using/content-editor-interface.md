---
title: Interface de l'éditeur de contenu
seo-title: Interface de l'éditeur de contenu
description: Interface de l'éditeur de contenu
seo-description: null
page-status-flag: never-activated
uuid: b108ea74-ae2c-4e47-bee8-12070927ba89
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
dc-title: </strong> and
discoiquuid: 20c64d31-c2ed-4bc9-9f0e-46f2e0c08c88
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Interface de l&#39;éditeur de contenu{#content-editor-interface}

## Fenêtre d&#39;édition {#editing-window}

La fenêtre d&#39;édition du DCE est organisée en trois sections distinctes. Elles permettent de visualiser le contenu, le modifier et contrôler son état.

![](assets/dce_decoupe_window_nb.png)

1. The **top** section is a display area for messages to the user. These messages indicate the status of the Web application status or the delivery being created as well as warnings and error messages related to the content. Pour plus d’informations, reportez-vous aux états [du contenu](#html-content-statuses)HTML.
1. The section to the **left** of the window is the area for editing content. From this area, the user can directly interact with the content using the pop-up toolbar: insert a link into an image, change the font, delete a field, etc. For more on this refer to [Editing forms](../../web/using/editing-content.md#editing-forms).
1. The section to the **right** of the window is the control panel area. This area groups the different options for the editor, particularly those related to configuring the page heading and general options for a block: add a border, link a database field with an input zone, access Web page properties, etc. Pour plus d’informations, reportez-vous aux sections Options [](#global-options) globales et [Modification du contenu](../../web/using/editing-content.md) .

## Options globales {#global-options}

La section supérieure droite de l&#39;éditeur permet d&#39;accéder à des options globales qui permettent d&#39;agir sur le contenu en cours de création.

![](assets/dce_global_options.png)

Elle contient quatre icônes :

![](assets/dce_icons_sidebar.png)

* The **Display/Hide blocks** icon lets you display blue frames around the content blocks (corresponding to the `<div>` HTML tag).

* L&#39;icône **Choisir un autre contenu** permet à l&#39;utilisateur de charger un nouveau contenu à partir d&#39;un modèle (existant ou modèle livré d&#39;usine).

   ![](assets/dce_popup_templatechoice.png)

   >[!CAUTION]
   >
   >Le contenu sélectionné remplace le contenu actuel.

* L’icône **Enregistrer comme modèle** permet d’enregistrer le contenu actuel en tant que modèle. Vous devez saisir le libellé et le nom interne du modèle. Les modèles sont stockés dans le nœud : **[!UICONTROL Ressources > Modèles > Modèles de contenu]**.

   ![](assets/dce_popup_savetemplate.png)

   Une fois enregistré, le modèle est disponible et peut être sélectionné lors de la création d&#39;un nouveau contenu.

   ![](assets/dce_create_fromtemplate.png)

* L&#39;icône **Propriétés de la page** permet de saisir les informations contenues dans l&#39;entête de la page HTML.

   ![](assets/dce_popup_headerhtml.png)

   >[!NOTE]
   >
   >This information corresponds to the **`<title>`** and **`<meta>`** HTML tags on the page.
   >
   >Les mots-clés doivent être séparés par des virgules.

## Options des blocs {#block-options}

La section droite de l&#39;éditeur regroupe les principales options qui permettent d&#39;agir sur le contenu. Pour afficher ces options, vous devez sélectionner un bloc : la nature de ces options dépend du bloc sélectionné.

![](assets/dce_right_section.png)

Vous pouvez ainsi :

* Déterminez l&#39;affichage d&#39;un ou de plusieurs blocs, reportez-vous à la section [Définition d&#39;une condition](../../web/using/editing-content.md#defining-a-visibility-condition)de visibilité,
* Définissez les bordures et les cadres, reportez-vous à la section [Ajout d&#39;une bordure et d&#39;un arrière-plan](../../web/using/editing-content.md#adding-a-border-and-background),
* Définissez des attributs d’image (taille, légende), reportez-vous à la section [Modification des propriétés](../../web/using/editing-content.md#editing-image-properties)d’image,
* Liez la base de données à un élément de formulaire (zone d’entrée, case à cocher), reportez-vous à la section [Modification des propriétés de données d’un formulaire](../../web/using/editing-content.md#changing-the-data-properties-for-a-form),
* Rendre une partie d’un formulaire obligatoire, voir [Modification des propriétés de données d’un formulaire](../../web/using/editing-content.md#changing-the-data-properties-for-a-form),
* Définissez une action pour un bouton, voir [Ajout d’une action à un bouton](../../web/using/editing-content.md#adding-an-action-to-a-button).

## Barre d&#39;outils de contenu {#content-toolbar}

La barre d&#39;outils est un **élément contextuel** de l&#39;interface du DCE qui présente des fonctionnalités différentes selon le bloc sélectionné.

>[!CAUTION]
>
>Certaines fonctionnalités de la barre d&#39;outils permettent de mettre en forme le contenu HTML. Cependant, si la page contient une feuille de style CSS, les **instructions** provenant de la feuille de style peuvent s&#39;avérer **prioritaires** par rapport aux instructions spécifiées avec la barre d&#39;outils.

