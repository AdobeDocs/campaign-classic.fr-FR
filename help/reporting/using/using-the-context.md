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

Lorsque vous souhaitez représenter des données sous la forme **[!UICONTROL tables]** ou **[!UICONTROL charts]**, elles peuvent provenir de deux sources : une nouvelle requête (voir [Définition d’un filtre direct sur les données](#defining-a-direct-filter-on-data)) ou le contexte du rapport (voir [Utilisation de données](#using-context-data)contextuelles).

## Définir un filtre direct sur les données {#defining-a-direct-filter-on-data}

### Filtrer les données {#filtering-data}

L’utilisation d’une activité de **[!UICONTROL Query]** type n’est pas obligatoire lors de la création d’un rapport. Les données peuvent être filtrées directement dans les tableaux et les graphiques qui composent le rapport.

Ainsi, vous pouvez sélectionner les données à afficher dans le rapport directement depuis l&#39;activité **[!UICONTROL Page]** du rapport.

To do this, click the **[!UICONTROL Filter data...]** link in the **[!UICONTROL Data]** tab: this link lets you access the expressions editor to define a query on the data to be analyzed.

![](assets/reporting_filter_data_from_page.png)

### Exemple : utilisation d&#39;un filtre dans un graphique {#example--use-a-filter-in-a-chart}

Dans l&#39;exemple suivant, le graphique ne doit afficher que les profils de destinataires vivant en France et qui ont effectué des achats pendant l&#39;année.

Pour définir ce filtre, placez une page dans le graphique et modifiez-la. Cliquez sur le **[!UICONTROL Filter data]** lien et créez le filtre correspondant aux données à afficher. Pour plus d&#39;informations sur la construction des requêtes dans Adobe Campaign, reportez-vous à [cette section](../../platform/using/about-queries-in-campaign.md).

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
1. Go to the **[!UICONTROL Data]** tab and select the cube to be used.
1. Click the **[!UICONTROL Filter data...]** link and define the following query to remove Adobe from the list of companies.

   ![](assets/s_ncs_advuser_report_display_03.png)

Le résultat sera que seuls les destinataires répondant aux critères de filtrage seront pris en compte dans le rapport.

![](assets/s_ncs_advuser_report_display_04.png)

## Utiliser les données du contexte {#using-context-data}

To represent data in the form of a **[!UICONTROL table]** or a **[!UICONTROL chart]**, the data can come from the report context.

In the page that contains the table or the chart, the **[!UICONTROL Data]** tab lets you select the data source.

![](assets/s_ncs_advuser_report_datasource_3.png)

* Cette **[!UICONTROL New query]** option vous permet de créer une requête pour collecter des données. Pour plus d’informations, reportez-vous à la section [Définition d’un filtre direct sur les données](#defining-a-direct-filter-on-data).
* L’ **[!UICONTROL Context data]** option vous permet d’utiliser les données d’entrée : le contexte du rapport coïncide avec les informations contenues dans la transition entrante de la page qui contient le graphique ou le tableau. Ce contexte peut, par exemple, contenir des données collectées via une **[!UICONTROL Query]** activité placée avant l’ **[!UICONTROL Page]** activité et pour lesquelles vous devez spécifier le tableau et les champs concernés par le rapport.

Par exemple, dans une boîte de requête, construisez la requête suivante sur les destinataires :

![](assets/s_ncs_advuser_report_datasource_2.png)

Then indicate the source of the data in your report, in this case: **[!UICONTROL Data from the context]**.

L&#39;emplacement des données est déduit automatiquement. Vous pouvez, au besoin, forcer le chemin des données.

![](assets/s_ncs_advuser_report_datasource_4.png)

Lorsque vous choisissez les données sur lesquelles doivent porter les statistiques, les champs disponibles correspondent aux données spécifiées dans la requête.

![](assets/s_ncs_advuser_report_datasource_1.png)

