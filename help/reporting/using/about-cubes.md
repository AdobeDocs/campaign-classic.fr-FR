---
product: campaign
title: Prise en main des cubes
description: Prise en main des cubes
feature: Reporting
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: ht
source-wordcount: '735'
ht-degree: 100%

---

# Prise en main des cubes{#about-cubes}

![](../../assets/common.svg)

L&#39;exploration des données de la base est proposée à travers le module **Marketing Analytics**. Elle permet d&#39;analyser et de mesurer les données, de calculer des statistiques, ainsi que de simplifier et d&#39;optimiser la création et le calcul des rapports. En complément, Marketing Analytics permet de créer des rapports et d&#39;y construire des populations cibles. Une fois identifiées, les populations sont stockées dans des listes, qui peuvent ensuite être exploitées dans Adobe Campaign (ciblage, segmentation, etc.).

Les cubes sont utilisés pour la génération de certains rapports natifs, notamment les rapports de diffusion (suivi des diffusions, clics, ouvertures, etc.). Les rapports basés sur les cubes ne doivent être utilisés en standard que pour des volumes de données inférieurs à 5 millions de lignes de faits.

Vous pouvez ainsi d&#39;étendre les capacités d&#39;exploration et d&#39;analyse des données de la base, tout en simplifiant le paramétrage des rapports et tableaux pour les utilisateurs finaux : ils n&#39;ont plus qu&#39;à sélectionner un cube existant, entièrement paramétré, lors de la création de leur rapport ou tableau pour en exploiter les calculs, mesures et statistiques.

Une fois créés et paramétrés, les cubes sont utilisés dans les boîtes de requête des rapports et les applications Web. Ils peuvent être exploités et manipulés au sein de tableaux croisés dynamiques.

>[!CAUTION]
>
>**Marketing Analytics** est un module d&#39;Adobe Campaign. Il doit être installé sur votre instance pour que vous puissiez utiliser les fonctionnalités décrites ci-après.

Le module Marketing Analytics de Campaign vous permet de :

1. Créer des cubes

   * agrégez et stockez des données dans une table de travail afin de pré-calculer des indicateurs, selon les besoins de lʼutilisateur,
   * réduisez le volume des données impliquées dans les différents calculs utilisés dans les rapports et dans les requêtes, afin dʼoptimiser grandement les temps de calcul des indicateurs.
   * simplifiez lʼaccès aux données, permettez aux utilisateurs de manipuler des données pré-agrégées ou non, selon différentes dimensions.

   Pour plus dʼinformations à ce sujet, consultez la section [Création dʼindicateurs](../../reporting/using/creating-indicators.md).

1. Création de tableaux croisés dynamiques

   * explorez les données calculées, les mesures configurées,
   * sélectionnez les données à afficher et leur mode dʼaffichage,
   * personnalisez les mesures et les indicateurs utilisés,
   * proposez des outils dʼanalyse interactive à des utilisateurs sans connaissances techniques.

   Pour plus dʼinformations à ce sujet, consultez la section [Utilisation de cubes pour explorer les données](../../reporting/using/using-cubes-to-explore-data.md).

1. Construire des requêtes à partir des données calculées et agrégées dans un cube.
1. Identifier des populations et les référencer dans des listes.

## Terminologie {#terminology}

Les cubes emploient une terminologie spécifique, consultez les termes utilisés ci-dessous.

* **Cube** : un cube est une représentation dʼinformations multidimensionnelles, il met à disposition des utilisateurs finaux des structures conçues pour des analyses interactives des données.

* **Table/schéma des faits** : la table des faits (ou le schéma des faits) contient les données brutes ou élémentaires sur lesquelles vont être construites les analyses. Il s’agit principalement de tables à gros volume (avec éventuellement des tables liées) et sur lesquelles les calculs peuvent être longs. Par exemple, une table des faits peut être : la table des broadlogs, la table des achats, etc.

* **Dimension** : les dimensions permettent de segmenter les données en groupes. Une fois créées, elles font office dʼaxes dʼanalyse. Dans la plupart des cas, pour une même dimension, plusieurs niveaux seront définis. Par exemple, pour une dimension temporelle, les niveaux seront les mois, jours, heures, minutes, etc. Cet ensemble de niveaux représente la hiérarchie de la dimension et permet dʼanalyser plus ou moins finement les données.

* **Mise en classe** : pour certains champs, vous pouvez définir une mise en classe afin de regrouper les valeurs et faciliter la lisibilité des informations. Les mises en classe sʼappliquent à des niveaux. Il est recommandé de définir une mise en classe lorsque les valeurs distinctes peuvent être nombreuses.

* **Mesure** : les mesures courantes sont la somme, la moyenne, le maximum, le minimum, lʼécart-type, etc. Les mesures peuvent être calculées, par exemple le taux dʼacceptation dʼune offre sera le rapport entre le nombre de fois où une offre a été présentée et le nombre de fois où elle a été acceptée.

## Espace de travail des cubes {#cube-workspace}

Les cubes sont localisés sous le noeud **[!UICONTROL Administration > Paramétrage > Cubes]**.

![](assets/s_advuser_cube_node.png)

Les principaux contextes d&#39;utilisation des cubes sont les suivants :

* Les exports de données peuvent être réalisés directement dans un rapport, conçu à partir de l’onglet **[!UICONTROL Rapports]** de la plateforme Adobe Campaign.

   Pour cela, créez un nouveau rapport et sélectionnez le cube à utiliser.

   ![](assets/cube_create_new.png)

   Les cubes apparaissent comme des modèles à partir desquels sont créés les rapports. Une fois le modèle sélectionné, cliquez sur le bouton **[!UICONTROL Créer]** pour paramétrer et visualiser le rapport correspondant.

   Vous pouvez alors adapter les mesures, modifier le mode d&#39;affichage ou configurer le tableau, puis afficher le rapport à partir du bouton central.

   ![](assets/cube_display_new.png)

* Vous pouvez également référencer un cube dans la boîte de **[!UICONTROL Requête]** d&#39;un rapport afin d&#39;en utiliser les indicateurs, comme dans l&#39;exemple ci-dessous :

   ![](assets/s_advuser_query_using_a_cube.png)

* Vous pouvez également insérer un tableau croisé dynamique basé sur un cube dans n&#39;importe quelle page d&#39;un rapport. Pour cela, référencez le cube à utiliser dans l&#39;onglet **[!UICONTROL Données]** du tableau croisé dynamique de la page concernée.

   ![](assets/s_advuser_cube_in_report.png)

   Pour plus dʼinformations, consultez la section [Exploration des données dans un rapport](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report).
