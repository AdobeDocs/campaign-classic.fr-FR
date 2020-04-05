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

En complément des variantes du graphique disponibles, présentées dans la section [Types de graphiques et leurs variantes](../../reporting/using/creating-a-chart.md#chart-types-and-variants), vous pouvez adapter l&#39;affichage et ajouter des éléments dans la ou les pages du rapport.

Vous pouvez utiliser les conteneurs : ils permettent de regrouper plusieurs éléments d&#39;une page et d&#39;en paramétrer la mise en page en colonnes et/ou en cellules. Leur utilisation est présentée dans [cette section](../../web/using/defining-web-forms-layout.md#creating-containers).

Vous pouvez paramétrer la mise en page du rapport au niveau de la page (à la racine de l&#39;arborescence) et la surcharger pour chaque conteneur. Les pages sont organisées en colonnes. Les conteneurs sont également organisés en colonne. Seuls les éléments statiques et les graphiques sont organisés en cellule.

## Définir les options de chaque page {#defining-the-options-for-each-page}

Vous pouvez utiliser les options de chaque page du rapport.

L&#39;onglet **[!UICONTROL Général]**, vous permet de modifier le titre de la page, de choisir la position des légendes et de paramétrer la navigation entre les différentes pages du rapport.

![](assets/s_ncs_advuser_report_wizard_022.png)

Le champ **[!UICONTROL Titre]** permet de personnaliser le libellé qui apparaît en tête de la page du rapport. Le titre de la fenêtre est quant à lui paramétrable depuis la fenêtre **[!UICONTROL Propriétés]** du rapport. Voir à ce sujet la section [Ajouter un en-tête et un pied de page](#adding-a-header-and-a-footer).

Les options des **[!UICONTROL Paramètres d&#39;affichage]** permettent de choisir la position de la légende des contrôles dans la page d&#39;un rapport et de définir le nombre de colonnes de la page. Pour plus d&#39;informations sur la mise en page, reportez-vous à la section **Mettre en page les éléments** de [cette section](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page).

Sélectionnez les différentes options de la section **[!UICONTROL Navigation]** pour autoriser ou non le passage entre les différentes pages du rapport. Lorsque l&#39;option **[!UICONTROL Ne pas autoriser le retour à la page précédente]** ou **[!UICONTROL Ne pas autoriser le passage à la page suivante]** est sélectionnée, les boutons **[!UICONTROL Suivant]** ou **[!UICONTROL Précédent]** ne sont plus disponibles dans la page du rapport.

## Ajouter un en-tête et un pied de page {#adding-a-header-and-a-footer}

La fenêtre des propriétés du rapport permet également de définir des éléments de mise en page, tels que : le titre de la fenêtre, le contenu HTML de la zone d&#39;en-tête et celui du pied de page.

Pour accéder à la fenêtre les propriétés, cliquez sur le bouton **[!UICONTROL Propriétés]** du rapport.

![](assets/reporting_properties.png)

L&#39;onglet **[!UICONTROL Page]** permet de personnaliser l&#39;affichage.

![](assets/s_ncs_advuser_report_properties_04.png)

Le contenu paramétré dans cet onglet sera visible sur toutes les pages du rapport.

Le sous-onglet **[!UICONTROL Textes]** permet de définir des contenus variables : ils seront pris en compte dans le cycle de traduction lorsque le rapport est destiné à être proposé dans plusieurs langues.

Vous pouvez ainsi créer une liste de fragments de textes et les associer à des identifiants :

![](assets/s_ncs_advuser_report_properties_04a.png)

Puis insérer ces identifiants dans les contenus HTML du rapport :

![](assets/s_ncs_advuser_report_properties_04b.png)

Ils seront remplacés automatiquement à l&#39;affichage du rapport par le contenu correspondant.

Ce mode de fonctionnement permet, comme pour les textes HTML, de centraliser les textes utilisés dans le rapport et d&#39;en gérer les traductions. En effet, les textes créés dans cet onglet sont collectés automatiquement dans l&#39;outil de traduction intégré d&#39;Adobe Campaign.
