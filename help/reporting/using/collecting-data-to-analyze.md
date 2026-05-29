---
product: campaign
title: Collecte des données à analyser
description: Collecte des données à analyser
feature: Reporting, Monitoring
badge: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
exl-id: cf621374-88f9-4def-8bea-87e0ea69ecd3
TQID: https://experienceleague.adobe.com/fk2YgX6UDVDTKH7v2Lcq01QAK7tElhnPkSvrpn25nzk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
feature_v2:
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
  - id: cfda811a-e413-43a4-adf0-7370888f5cfc
  - id: afe938ea-bc18-44a4-a3fb-03e1031466cb
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 533
ht-degree: 76%

---

# Collecte des données à analyser{#collecting-data-to-analyze}



Les données qui vont être utilisées pour construire le rapport peuvent être sélectionnées directement au niveau de la page du rapport (voir à ce propos la section [Utiliser le contexte](../../reporting/using/using-the-context.md)) ou collectées via une ou plusieurs requêtes.

Dans cette activité, trois méthodes distinctes sont proposées :

1. Construire une requête sur les données de la base.
1. Exploiter les données contenues dans une liste.
1. Utiliser les données d&#39;un Cube existant.

Le choix de l&#39;une ou l&#39;autre des méthodes dépend du type de calcul à réaliser, du volume des données à manipuler, de leur pérennité, etc. Tous ces paramètres doivent être étudiés avec précision afin de ne pas surcharger la base de données Adobe Campaign, et d’optimiser la génération et la manipulation des rapports créés. Pour plus d’informations, consultez [cette page](../../reporting/using/best-practices.md#optimizing-report-creation).

Dans tous les cas, les données sont collectées au travers d&#39;une activité de type **[!UICONTROL Requête]**.

![](assets/reporting_query_edit.png)

Ce mode de sélection des données est pertinent lorsque les données du rapport doivent être collectées ou créées à l’aide des données de la base de données. Dans certains cas, vous pouvez également sélectionner les données directement à partir des éléments utilisés dans le rapport. Par exemple, lorsque vous insérez un graphique, vous pouvez sélectionner directement les données sources. Voir à ce sujet la section [Utiliser le contexte](../../reporting/using/using-the-context.md).

## Utilisation des données provenant dʼun schéma {#using-the-data-from-a-schema}

Pour utiliser directement les données associées à un schéma de la base, sélectionnez l&#39;option correspondante dans le requêteur puis paramétrez la requête à appliquer.

L’exemple suivant permet de collecter le nombre de destinataires pour chaque pays, parmi les profils de la base de données. Elles peuvent ensuite être affichées dans un rapport sous la forme d’un tableau.

![](assets/reporting_query_from_schema.png)

## Utilisation dʼune liste importée {#using-an-imported-list}

Pour créer un rapport, vous pouvez utiliser les données d&#39;une liste de données importées.

Pour cela, sélectionnez l&#39;option **[!UICONTROL Utiliser une liste importée]** dans la boîte de requête puis sélectionnez la liste concernée.

![](assets/reporting_query_from_list.png)

Cliquez sur le lien **[!UICONTROL Editer la requête...]** pour définir les données à collecter parmi les éléments de cette liste, pour la construction du rapport.

## Utilisation dʼun cube {#using-a-cube}

Vous pouvez sélectionner un cube afin de définir la requête.

![](assets/reporting_query_from_cube.png)

Les cubes permettent d&#39;étendre les capacités d&#39;exploration et d&#39;analyse des données de la base, tout en simplifiant le paramétrage des rapports et tables pour les utilisateurs finaux : il suffit de sélectionner un cube existant, entièrement paramétré, pour en exploiter les calculs, mesures et statistiques. Pour plus d&#39;informations sur la création de cubes, consultez [cette section](../../reporting/using/ac-cubes.md).

Cliquez sur le lien **[!UICONTROL Editer la requête...]** et sélectionnez les indicateurs que vous souhaitez afficher ou exploiter dans votre rapport.

![](assets/reporting_query_from_cube_edit_query.png)

## Options de fitrage dans les requêtes {#filtering-options-in-the-queries}

Les données doivent être filtrées afin de ne pas exécuter de requêtes sur l&#39;ensemble de la base de données.

### Filtrage simplifié {#simplified-filter}

Vous pouvez sélectionner l&#39;option **[!UICONTROL Filtrer automatiquement avec le contexte]** pour rendre le rapport accessible depuis un noeud spécifique de l&#39;arborescence comme une liste, un destinataire, une diffusion.

L&#39;option **[!UICONTROL Filtrer avec le dossier]** permet de définir un dossier spécifique et de ne prendre en compte que son contenu. Vous pouvez ainsi filtrer les données du rapport pour n&#39;afficher que celles d&#39;un des dossiers de l&#39;arborescence, comme ci-dessous :

![](assets/reporting_control_folder.png)

### Limitation de la taille des données collectées {#limiting-the-amount-of-data-collected}

Paramétrez le nombre d&#39;enregistrements à extraire via la requête à l&#39;aide des options de limitation de résultat :

* **[!UICONTROL Limiter au premier enregistrement]** pour extraire un seul résultat,
* **[!UICONTROL Taille]** pour extraire un nombre d&#39;enregistrements précis.
