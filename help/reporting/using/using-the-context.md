---
title: Utiliser le contexte
seo-title: Utiliser le contexte
description: Utiliser le contexte
seo-description: null
page-status-flag: never-activated
uuid: ac8c7068-d640-4934-b7f5-bc91b98eab4c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 72fe6df0-0271-48f9-bd6d-bb1ff25fbdf3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Utiliser le contexte{#using-the-context}

When you want to represent data in the form of **[!UICONTROL tables]** or **[!UICONTROL charts]**, it can be taken from two sources: a new query (refer to [Defining a direct filter on data](#defining-a-direct-filter-on-data)) or the report context (refer to [Using context data](#using-context-data)).

## Définir un filtre direct sur les données {#defining-a-direct-filter-on-data}

### Filtrer les données {#filtering-data}

Il n&#39;est pas obligatoire d&#39;utiliser une activité de type **[!UICONTROL Requête]** lors de la construction d&#39;un rapport. En effet, les données peuvent être filtrées directement au niveau des tableaux et des graphiques qui composent ce rapport.

Ainsi, vous pouvez sélectionner les données à afficher dans le rapport directement depuis l&#39;activité **[!UICONTROL Page]** du rapport.

Pour cela, cliquez sur le lien **[!UICONTROL Filtrer les données...]** disponible dans l&#39;onglet **[!UICONTROL Données]** : ce lien permet d&#39;accéder à l&#39;éditeur d&#39;expressions pour définir une requête sur les données à analyser.

![](assets/reporting_filter_data_from_page.png)

### Exemple : utilisation d&#39;un filtre dans un graphique {#example--use-a-filter-in-a-chart}

Dans l&#39;exemple suivant, le graphique ne doit afficher que les profils de destinataires vivant en France et qui ont effectué des achats pendant l&#39;année.

Pour définir ce filtre, positionnez une page dans le diagramme et éditez-la. Cliquez sur le lien **[!UICONTROL Filtrer les données]** et créez le filtre correspondant aux données que vous voulez afficher. Pour plus d&#39;informations sur la construction des requêtes dans Adobe Campaign, reportez-vous à [cette section](../../platform/using/about-queries-in-campaign.md).

![](assets/s_ncs_advuser_report_wizard_029.png)

Ici, nous allons afficher la répartition par ville des destinataires répondant à la sélection.

![](assets/reporting_graph_with_2vars.png)

Le rendu sera par exemple :

![](assets/reporting_graph_with_2vars_preview.png)

### Exemple : utilisation d&#39;un filtre dans un tableau croisé dynamique {#example--use-a-filter-in-a-pivot-table}

Dans cet exemple, le filtre permettra de n&#39;afficher dans le tableau croisé dynamique que les clients non-parisiens, sans passer par une requête préalable.

Les étapes sont les suivantes :

1. Positionnez une page dans le diagramme et éditez-la.
1. Créez un tableau croisé dynamique.
1. Dans l&#39;onglet **[!UICONTROL Données]**, sélectionnez le cube à utiliser.
1. Cliquez sur le lien **[!UICONTROL Filtrer les données...]** et définissez la requête suivante afin de retirer Adobe de la liste des sociétés.

   ![](assets/s_ncs_advuser_report_display_03.png)

Le résultat sera que seuls les destinataires répondant aux critères de filtrage seront pris en compte dans le rapport.

![](assets/s_ncs_advuser_report_display_04.png)

## Utiliser les données du contexte {#using-context-data}

Lorsque vous souhaitez représenter les données sous forme de **[!UICONTROL tableau]** ou de **[!UICONTROL graphique]**, les données peuvent provenir du contexte du rapport.

Dans la page contenant le tableau ou le graphique, l&#39;onglet **[!UICONTROL Données]** permet de sélectionner la source des données.

![](assets/s_ncs_advuser_report_datasource_3.png)

* L’option **[!UICONTROL Nouvelle requête]** vous permet de créer une requête pour collecter des données. Pour plus d’informations, reportez-vous à la section [Définition d’un filtre direct sur les données](#defining-a-direct-filter-on-data).
* L&#39;option **[!UICONTROL Données du contexte]** permet d&#39;utiliser les données d&#39;entrée : le contexte du rapport correspond aux informations qui sont véhiculées dans la transition entrante de la page contenant le graphique ou le tableau. Ce contexte peut, par exemple, contenir les données collectées via une activité **[!UICONTROL Requête]** placée avant l&#39;activité **[!UICONTROL Page]**, et dans laquelle vous spécifiez la table et les champs sur lesquels doit porter le rapport.

Par exemple, dans une boîte de requête, construisez la requête suivante sur les destinataires :

![](assets/s_ncs_advuser_report_datasource_2.png)

Indiquez ensuite la source des données de votre rapport, ici : les **[!UICONTROL Données du contexte]**.

L&#39;emplacement des données est déduit automatiquement. Vous pouvez, au besoin, forcer le chemin des données.

![](assets/s_ncs_advuser_report_datasource_4.png)

Lorsque vous choisissez les données sur lesquelles doivent porter les statistiques, les champs disponibles correspondent aux données spécifiées dans la requête.

![](assets/s_ncs_advuser_report_datasource_1.png)

