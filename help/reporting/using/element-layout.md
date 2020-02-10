---
title: Mettre en page les éléments
seo-title: Mettre en page les éléments
description: Mettre en page les éléments
seo-description: null
page-status-flag: never-activated
uuid: 60dc80d9-f81b-48ce-9341-f975daaf5ebc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 8fdda764-3e42-4972-a9c9-63567588931e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Mettre en page les éléments{#element-layout}

In addition to the various charts detailed here: [Chart types and variants](../../reporting/using/creating-a-chart.md#chart-types-and-variants), you can adapt the display and add elements to the report page(s).

Vous pouvez utiliser les conteneurs : ils permettent de regrouper plusieurs éléments d&#39;une page et d&#39;en paramétrer la mise en page en colonnes et/ou en cellules. Leur utilisation est présentée dans [cette section](../../web/using/defining-web-forms-layout.md#creating-containers).

Vous pouvez paramétrer la mise en page du rapport au niveau de la page (à la racine de l&#39;arborescence) et la surcharger pour chaque conteneur. Les pages sont organisées en colonnes. Les conteneurs sont également organisés en colonne. Seuls les éléments statiques et les graphiques sont organisés en cellule.

## Définir les options de chaque page {#defining-the-options-for-each-page}

Vous pouvez utiliser les options de chaque page du rapport.

The **[!UICONTROL General]** tab lets you change the title of the page, as well as configure legend positions and browsing between the report pages.

![](assets/s_ncs_advuser_report_wizard_022.png)

Le **[!UICONTROL Title]** champ permet de personnaliser le libellé dans l’en-tête de la page du rapport. Le titre de la fenêtre peut être configuré via la **[!UICONTROL Properties]** fenêtre du rapport. Pour plus d’informations, voir [Ajout d’un en-tête et d’un pied de page](#adding-a-header-and-a-footer).

Les **[!UICONTROL Display settings]** options vous permettent de sélectionner la position de la légende de contrôle dans une page de rapport et de définir le nombre de colonnes sur la page. Pour plus d’informations sur la mise en page, reportez-vous à la section Mise en page **de l’** élément de [cette section](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page).

Sélectionnez les différentes options de la **[!UICONTROL Browse]** section pour autoriser la navigation d&#39;une page de rapport à une autre. Si l’option **[!UICONTROL Disable next page]** ou **[!UICONTROL Disable previous page]** est sélectionnée, les boutons **[!UICONTROL Next]** et **[!UICONTROL Previous]** disparaissent de la page du rapport.

## Ajouter un en-tête et un pied de page {#adding-a-header-and-a-footer}

La fenêtre des propriétés du rapport permet également de définir des éléments de mise en page, tels que : le titre de la fenêtre, le contenu HTML de la zone d&#39;en-tête et celui du pied de page.

To access the properties window, click the **[!UICONTROL Properties]** button of the report.

![](assets/reporting_properties.png)

L&#39;onglet **[!UICONTROL Page]** permet de personnaliser l&#39;affichage.

![](assets/s_ncs_advuser_report_properties_04.png)

Le contenu paramétré dans cet onglet sera visible sur toutes les pages du rapport.

The **[!UICONTROL Texts]** sub-tab enables you to define variable content: it will be taken into account during the translation cycle if the report is designed for use in several languages.

Vous pouvez ainsi créer une liste de fragments de textes et les associer à des identifiants :

![](assets/s_ncs_advuser_report_properties_04a.png)

Puis insérer ces identifiants dans les contenus HTML du rapport :

![](assets/s_ncs_advuser_report_properties_04b.png)

Ils seront remplacés automatiquement à l&#39;affichage du rapport par le contenu correspondant.

Ce mode de fonctionnement permet, comme pour les textes HTML, de centraliser les textes utilisés dans le rapport et d&#39;en gérer les traductions. En effet, les textes créés dans cet onglet sont collectés automatiquement dans l&#39;outil de traduction intégré d&#39;Adobe Campaign.
