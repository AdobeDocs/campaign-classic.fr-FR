---
title: Créer les indicateurs
seo-title: Créer les indicateurs
description: Créer les indicateurs
seo-description: null
page-status-flag: never-activated
uuid: 3caaba6b-b6c8-4b64-b123-d7098e9ddc7a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: a5fc6c78-b4fb-41fd-a072-7be4ece3c554
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Créer les indicateurs{#creating-indicators}

Pour qu&#39;un cube puisse être exploité, vous devez identifier les dimensions et les mesures utiles et les créer au niveau du cube.

Les étapes de création d&#39;un cube sont les suivantes :

1. Sélectionnez le tableau de travail. Reportez-vous à [Sélection du tableau](#selecting-the-work-table)de travail.
1. Définissez des dimensions. Reportez-vous à [Définition des dimensions](#defining-dimensions).
1. Définissez des mesures. Reportez-vous à [Création d&#39;indicateurs](#building-indicators).
1. Créer des agrégats (facultatif). Reportez-vous à [Calcul et utilisation d’agrégats](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

L&#39;exemple ci-après permet de créer rapidement un cube simple et de l&#39;utiliser dans un rapport afin d&#39;en explorer les mesures.

Les étapes de réalisation sont présentées ci-après, les options et descriptions exhaustives sont présentées dans les autres sections de ce chapitre.

## Sélectionner la table de travail {#selecting-the-work-table}

To create a cube, click the **[!UICONTROL New]** button above the list of cubes.

![](assets/s_advuser_cube_create.png)

Sélectionnez le schéma des faits, c&#39;est-à-dire celui qui contient les éléments que vous souhaitez explorer. Dans notre exemple, nous allons sélectionner la table des **Destinataires**.

![](assets/s_advuser_cube_wz_02.png)

Click **[!UICONTROL Save]** to create the Cube: it will appear on the list of Cubes and may then be configured using the appropriate tabs.

Click the **[!UICONTROL Filter the source data...]** link to apply the calculations of this Cube to a select of data in the database.

![](assets/s_advuser_cube_wz_03.png)

## Définir des dimensions {#defining-dimensions}

Les dimensions correspondent à des axes d&#39;analyse qui sont définis pour chaque cube selon le schéma des faits auquel il se rapporte. Ce sont les dimensions explorées dans l&#39;analyse, comme par exemple le temps (année, mois, jour, etc.), une nomenclature de produits ou contrats (famille, référence, etc.), un segment de population (par ville, tranche d&#39;âge, statut, etc.).

These analysis axes are defined in the **[!UICONTROL Dimension]** tab of the Cube.

Click the **[!UICONTROL Add]** button to create a new dimension, then in the **[!UICONTROL Expression field]**, click the **[!UICONTROL Edit expression]** icon to select the field that contains the concerned data.

![](assets/s_advuser_cube_wz_04.png)

* Choisissez d&#39;abord l&#39;**Age** des destinataires. Pour ce champ, vous pouvez définir une mise en classe afin de regrouper les âges pour faciliter la lisibilité des informations. Il est recommandé de définir une mise en classe lorsque les valeurs distinctes peuvent être nombreuses.

   Pour ce faire, cochez l’ **[!UICONTROL Enable binning]** option. Les modes d’épinglage sont détaillés dans [Data Binning](../../reporting/using/concepts-and-methodology.md#data-binning).

   ![](assets/s_advuser_cube_wz_05.png)

* Ajoutez une dimension de type **Date**. Ici, nous allons d&#39;afficher les dates de création des profils de destinataires.

   To do this, click **[!UICONTROL Add]** and select the **[!UICONTROL Creation date]** field in the recipient table.

   ![](assets/s_advuser_cube_wz_06.png)

   Vous pouvez sélectionner le mode d&#39;affichage des dates. Pour cela, sélectionnez les niveaux à générer :

   ![](assets/s_advuser_cube_wz_07.png)

   Dans notre exemple, nous n&#39;afficherons que les années, mois et jours dans la mesure où il n&#39;est pas possible de travailler à la fois sur les semaines et les trimestres/mois : ces niveaux ne sont pas compatibles.

* Créez une autre dimension afin d&#39;analyser les données par rapport à la ville du destinataire.

   To do this, add a new dimension and select the city in the **[!UICONTROL Location]** node of the recipient schema.

   ![](assets/s_advuser_cube_wz_08.png)

   Vous pouvez activer la mise en classe afin de simplifier la lecture des informations et lier les valeurs à une valeur d&#39;énumération.

   ![](assets/s_advuser_cube_wz_09.png)

   Sélectionnez l&#39;énumération dans la liste déroulante.

   ![](assets/s_advuser_cube_wz_10.png)

   Seules les valeurs de l&#39;énumération s&#39;affichent. Les autres seront regroupées sous le libellé défini dans le **[!UICONTROL Label of the other values]** champ.

   Pour plus d’informations, reportez-vous à la section Gestion [dynamique des bacs](../../reporting/using/concepts-and-methodology.md#dynamically-managing-bins).

## Construire les indicateurs {#building-indicators}

Une fois les dimensions définies, vous devez spécifier un mode de calcul pour les valeurs à afficher dans les cellules. Pour ce faire, créez les indicateurs correspondants dans l’ **[!UICONTROL Measures]** onglet : créez autant de mesures que de colonnes à afficher dans le rapport qui utiliseront le cube.

Pour cela, les étapes sont les suivantes :

1. Cliquez sur le **[!UICONTROL Add]** bouton.
1. Sélectionnez le type de mesure et la formule à appliquer. Ici, nous allons compter le nombre de femmes parmi les destinataires.

   Our measure is based on the fact schema and uses the **[!UICONTROL Count]** operator.

   ![](assets/s_advuser_cube_wz_11.png)

   Le **[!UICONTROL Filter the measure data...]** lien vous permet de sélectionner uniquement des femmes. For more on defining measures and the available options, refer to [Defining measures](../../reporting/using/concepts-and-methodology.md#defining-measures).

   ![](assets/s_advuser_cube_wz_12.png)

1. Saisissez le libellé de la mesure et enregistrez-la.

   ![](assets/s_advuser_cube_wz_13.png)

1. Enregistrez le cube.

## Créer un rapport basé sur un cube {#creating-a-report-based-on-a-cube}

Une fois le cube paramétré, il peut être utilisé comme modèle pour créer un nouveau rapport.

Pour cela :

1. Click the **[!UICONTROL Create]** button of the **[!UICONTROL Reports]** universe and select the cube you have just created.

   ![](assets/s_advuser_cube_wz_14.png)

1. Click the **[!UICONTROL Create]** button to confirm: this will take you to the report configuration and viewing page.

   Par défaut, les deux premières dimensions disponibles sont proposées en colonne et en ligne mais aucune valeur n&#39;est affichée dans le tableau. Pour générer le tableau, cliquez sur l&#39;icône centrale :

   ![](assets/s_advuser_cube_wz_15.png)

1. Vous pouvez déplacer les dimensions d&#39;un axe à l&#39;autre, les supprimer, ajouter de nouvelles mesures, etc. Les opérations possibles sont décrites ici : [Utilisation de cubes pour explorer les données](../../reporting/using/using-cubes-to-explore-data.md).

   Pour cela, utilisez les icônes correspondantes.

   ![](assets/s_advuser_cube_wz_16.png)

