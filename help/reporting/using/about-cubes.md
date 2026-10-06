---
product: campaign
title: À propos des cubes
description: Prise en main des cubes
feature: Reporting, Monitoring
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
hide: true
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
    internal-label: Dynamic reporting
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
    internal-label: Reporting interface
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 100%
---
# Prise en main des cubes{#about-cubes}



## Terminologie {#terminology}

Les cubes emploient une terminologie spécifique, consultez les termes utilisés ci-dessous.

* **Cube** : un cube est une représentation dʼinformations multidimensionnelles, il met à disposition des utilisateurs finaux des structures conçues pour des analyses interactives des données.

* **Table/schéma des faits** : la table des faits (ou le schéma des faits) contient les données brutes ou élémentaires sur lesquelles vont être construites les analyses. Il s’agit principalement de tables à gros volume (avec éventuellement des tables liées) et sur lesquelles les calculs peuvent être longs. Par exemple, une table des faits peut être : la table des broadlogs, la table des achats, etc.

* **Dimension** : les dimensions permettent de segmenter les données en groupes. Une fois créées, elles font office dʼaxes dʼanalyse. Dans la plupart des cas, pour une même dimension, plusieurs niveaux seront définis. Par exemple, pour une dimension temporelle, les niveaux seront les mois, jours, heures, minutes, etc. Cet ensemble de niveaux représente la hiérarchie de la dimension et permet dʼanalyser plus ou moins finement les données.

* **Mise en classe** : pour certains champs, vous pouvez définir une mise en classe afin de regrouper les valeurs et faciliter la lisibilité des informations. Les mises en classe sʼappliquent à des niveaux. Il est recommandé de définir une mise en classe lorsque les valeurs distinctes peuvent être nombreuses.

* **Mesure** : les mesures les plus fréquentes sont la somme, la moyenne, le maximum, le minimum, l’écart-type, etc. Les mesures peuvent être calculées, par exemple le taux dʼacceptation dʼune offre est le rapport entre le nombre de fois où une offre a été présentée et le nombre de fois où elle a été acceptée.

## Espace de travail des cubes {#cube-workspace}

Les cubes sont localisés sous le noeud **[!UICONTROL Administration > Paramétrage > Cubes]**.

![](assets/s_advuser_cube_node.png)

Les principaux contextes d&#39;utilisation des cubes sont les suivants :

* Les exports de données peuvent être réalisés directement dans un rapport, conçu à partir de l’onglet **[!UICONTROL Rapports]** de la plateforme Adobe Campaign.

  Pour cela, créez un nouveau rapport et sélectionnez le cube à utiliser.

  ![](assets/cube_create_new.png)

  Les cubes sont des modèles à partir desquels des rapports sont créés. Une fois le modèle sélectionné, cliquez sur le bouton **[!UICONTROL Créer]** pour paramétrer et visualiser le rapport correspondant.

  Vous pouvez alors adapter les mesures, modifier le mode d&#39;affichage ou configurer le tableau, puis afficher le rapport à partir du bouton central.

  ![](assets/cube_display_new.png)

* Vous pouvez également référencer un cube dans la boîte de **[!UICONTROL Requête]** d&#39;un rapport afin d&#39;en utiliser les indicateurs, comme dans l&#39;exemple ci-dessous :

  ![](assets/s_advuser_query_using_a_cube.png)

* Vous pouvez également insérer un tableau croisé dynamique basé sur un cube dans n&#39;importe quelle page d&#39;un rapport. Pour ce faire, référencez le cube à utiliser sous l’onglet **[!UICONTROL Données]** du tableau croisé dynamique de la page concernée.

  ![](assets/s_advuser_cube_in_report.png)

  Pour plus dʼinformations, consultez la section [Exploration des données dans un rapport](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report).
