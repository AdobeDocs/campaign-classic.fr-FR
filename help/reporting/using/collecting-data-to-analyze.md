---
title: Collecter les données à analyser
seo-title: Collecter les données à analyser
description: Collecter les données à analyser
seo-description: null
page-status-flag: never-activated
uuid: 5a611786-6e56-4fce-b232-dd8428f3a5f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 594a333d-1fc3-49a0-b3f6-7ea8fa4321e9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0c41cf2f35495a1514642e47f0b7146d8dd50946

---


# Collecter les données à analyser{#collecting-data-to-analyze}

The data to be used for building the report can be selected directly in the report page (for more on this, refer to [Using the context](../../reporting/using/using-the-context.md)) or collected via one or more queries.

Dans cette activité, trois méthodes distinctes sont proposées :

1. Construire une requête sur les données de la base.
1. Exploiter les données contenues dans une liste.
1. Utiliser les données d&#39;un Cube existant.

Le choix de l&#39;une ou l&#39;autre des méthodes dépend du type de calcul à réaliser, du volume des données à manipuler, de leur pérennité, etc. Tous ces paramètres doivent être étudiés avec précision afin de ne pas surcharger la base Adobe Campaign et d&#39;optimiser la génération et la manipulation des rapports créés. Reportez-vous à ce propos à [cette page](../../reporting/using/best-practices.md#optimizing-report-creation).

In all cases, data is collected via a **[!UICONTROL Query]** type activity.

![](assets/reporting_query_edit.png)

Ce mode de sélection des données est pertinent lorsque les données du rapport doivent être collectées ou créées à l’aide des données de la base de données. Dans certains cas, vous pouvez également sélectionner les données directement à partir des éléments utilisés dans le rapport. Par exemple, lorsque vous insérez un graphique, vous pouvez sélectionner directement les données source. Pour plus d’informations, voir [Utilisation du contexte](../../reporting/using/using-the-context.md).

## Utiliser un schéma de la base {#using-the-data-from-a-schema}

Pour utiliser directement les données associées à un schéma de la base, sélectionnez l&#39;option correspondante dans l&#39;éditeur de requête puis paramétrez la requête à appliquer.

L&#39;exemple suivant permet de collecter le nombre de destinataires de chaque pays, parmi les profils de la base. Ils pourront ensuite être affichés dans un rapport sous la forme d&#39;un tableau.

![](assets/reporting_query_from_schema.png)

## Utiliser une liste importée {#using-an-imported-list}

Pour créer un rapport, vous pouvez utiliser les données d&#39;une liste de données importées.

To do this, select the **[!UICONTROL Use an imported list]** option in the query box and select the concerned list.

![](assets/reporting_query_from_list.png)

Click the **[!UICONTROL Edit query...]** link to define the data to collect among the elements in this list for building the report.

## Utiliser un cube {#using-a-cube}

Vous pouvez sélectionner un cube afin de définir la requête.

![](assets/reporting_query_from_cube.png)

Les cubes permettent d&#39;étendre les capacités d&#39;exploration et d&#39;analyse des données de la base, tout en simplifiant le paramétrage des rapports et tables pour les utilisateurs finaux : il suffit de sélectionner un cube existant, entièrement paramétré, pour en exploiter les calculs, mesures et statistiques. Pour plus d&#39;informations sur la création de cubes, consultez [cette section](../../reporting/using/about-cubes.md).

Click the **[!UICONTROL Edit query...]** link and select the indicators that you want to display or use in your report.

![](assets/reporting_query_from_cube_edit_query.png)

## Options de fitrage dans les requêtes {#filtering-options-in-the-queries}

Les données doivent être filtrées afin de ne pas exécuter de requêtes sur l&#39;ensemble de la base de données.

### Filtrage simplifié {#simplified-filter}

You can select the **[!UICONTROL Filter automatically with the context]** option to make the report accessible via a specific node of the tree such as a list, a recipient, or a delivery.

L’ **[!UICONTROL Filter with the folder]** option vous permet de spécifier un dossier et de ne prendre en compte que son contenu. Vous pouvez ainsi filtrer les données du rapport afin de n’afficher que les données de l’un des dossiers de l’arborescence, comme illustré ci-dessous :

![](assets/reporting_control_folder.png)

### Limiter la taille des données collectées {#limiting-the-amount-of-data-collected}

Paramétrez le nombre d&#39;enregistrements à extraire via la requête à l&#39;aide des options de limitation de résultat :

* **[!UICONTROL Limit to first record]** pour extraire un résultat,
* **[!UICONTROL Size]** pour extraire un nombre défini d’enregistrements.

