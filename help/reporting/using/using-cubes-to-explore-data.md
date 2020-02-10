---
title: Utiliser des cubes pour explorer les données
seo-title: Utiliser des cubes pour explorer les données
description: Utiliser des cubes pour explorer les données
seo-description: null
page-status-flag: never-activated
uuid: ba15e7dc-0a3b-48cf-971a-7a89b8b9c9f7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: e1ab1e82-8194-40a8-8df3-e7cfbaa3e777
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Utiliser des cubes pour explorer les données{#using-cubes-to-explore-data}

Marketing Analytics permet de simplifier la création de rapports ainsi que l&#39;identification et la sélection de données de la base via l&#39;utilisation des cubes. Vous pouvez ainsi :

* Créer des rapports basés sur des cubes. La procédure est décrite dans la section [Explorer les données dans un rapport](#exploring-the-data-in-a-report).
* Collecter des données de la base et les regrouper dans des listes, par exemple pour identifier et construire les cibles des diffusions. Voir à ce propos la section [Construire une population cible](#building-a-target-population).
* Insérer un tableau croisé dynamique dans un rapport, au sein duquel vous référencez un cube existant. Voir à ce sujet la section [Insérer un tableau croisé dynamique dans un rapport](#inserting-a-pivot-table-into-a-report).

>[!NOTE]
>
>Marketing Analytics est nécessaire pour créer ou modifier des cubes. Voir à ce sujet la section [A propos des cubes](../../reporting/using/about-cubes.md).

## Explorer les données dans un rapport {#exploring-the-data-in-a-report}

### Etape 1 - Création d&#39;un rapport basé sur un cube {#step-1---creating-a-report-based-on-a-cube}

To create a report based on a cube, click the **[!UICONTROL Create]** button in the **[!UICONTROL Reports]** universe and select the cube you want to use.

La procédure est décrite dans la section [Créer un rapport basé sur un cube](../../reporting/using/creating-indicators.md#creating-a-report-based-on-a-cube).

### Etape 2 - Sélection des lignes et colonnes {#step-2---selecting-lines-and-columns}

L&#39;affichage par défaut propose alors les deux premières dimensions du cube (dans notre exemple : l&#39;âge et la ville).

The **[!UICONTROL Add]** buttons on each axis enable you to add dimensions.

![](assets/s_advuser_cube_in_report_03.png)

1. Pour ajouter une dimension, cliquez sur le bouton de la ligne ou de la colonne concernée :
1. Sélectionnez la dimension à ajouter dans le tableau, parmi celles disponibles :

   ![](assets/s_advuser_cube_in_report_04.png)

1. Sélectionnez ensuite les paramètres de cette dimension.

   ![](assets/s_advuser_cube_in_report_04b.png)

   Les paramètres dépendent du type de données de la dimension sélectionnée.

   Par exemple, pour les dates, plusieurs niveaux peuvent être disponibles. Voir à ce propos [Affichage des mesures](../../reporting/using/concepts-and-methodology.md#displaying-measures).

   Les options proposées sont alors les suivantes :

   ![](assets/s_advuser_cube_in_report_config2.png)

   Vous pouvez, au choix :

   * Déplier les données au chargement : les valeurs seront alors affichées par défaut à chaque actualisation du rapport (valeur par défaut : non).
   * Afficher le total en fin de ligne : pour les données affichées en colonne, une options supplémentaire est proposée afin d&#39;afficher le total en fin de ligne : une colonne supplémentaire est alors ajoutée dans le tableau (valeur par défaut : oui).
   * Appliquer un tri : les valeurs de la colonne peuvent être triées par valeur, par libellé, ou selon une mesure (valeur par défaut : par valeur).
   * Afficher les valeurs dans l&#39;ordre ascendant (a-z, 0-9) ou descendant (z-a, 9-0).
   * Modifier le nombre de colonnes à afficher au chargement (par défaut : 200).

1. Cliquez sur **[!UICONTROL Ok]** pour confirmer l&#39;insertion : la dimension est alors ajoutée parmi les dimensions existantes.

   The yellow banner above the table shows that you have made changes: click the **[!UICONTROL Save]** button to save them.

   ![](assets/s_advuser_cube_in_report_04c.png)

### Etape 3 - Paramétrage des mesures à afficher {#step-3---configuring-the-measures-to-display}

Une fois les lignes et colonnes positionnées, indiquez les mesures que vous souhaitez afficher ainsi que leur mode d&#39;affichage.

Par défaut, une seule mesure est affichée. Pour ajouter ou paramétrez les mesures :

1. Cliquez sur le **[!UICONTROL Measures]** bouton.

   ![](assets/s_advuser_cube_in_report_05.png)

1. The **[!UICONTROL Use a measure]** button enables you to select one of the existing measures.

   ![](assets/s_advuser_cube_in_report_08.png)

   Sélectionnez les informations que vous souhaitez afficher et le type de formatage à utiliser. La liste des options dépend du type de mesure paramétré.

   ![](assets/s_advuser_cube_in_report_09.png)

   La configuration générale des mesures est également disponible via l’ **[!UICONTROL Edit the configuration of the pivot table]** icône de l’en-tête.

   ![](assets/s_advuser_cube_in_report_config_02.png)

   Vous pouvez notamment choisir d&#39;afficher ou non les libellés des mesures. Voir à ce propos [Configuration de l&#39;affichage](../../reporting/using/concepts-and-methodology.md#configuring-the-display).

1. Il est possible de construire de nouvelles mesures en utilisant les mesures existantes. Pour ce faire, cliquez sur **[!UICONTROL Create a measure]** et configurez-le.

   ![](assets/s_advuser_cube_in_report_config_02a.png)

   Les types de mesures possibles sont les suivantes :

   * Combinaison de mesures : ce type de mesure permet de construire la nouvelle mesure à partir de mesures existantes.

      Entre ces mesures, les opérateurs disponibles sont : somme, différence, multiplication et taux.

   * Proportion : ce type de mesure permet de calculer le nombre d&#39;enregistrements mesurés pour une dimension donnée. Vous pouvez calculer la proportionnalité par rapport à une dimension ou une sous-dimension.
   * Variation : cette mesure permet de calculer la variation des valeurs d&#39;un niveau.
   * Ecart à la moyenne : ce type de mesure permet de calculer les écarts dans chaque groupe de cellules correspondantes, par rapport à la moyenne des valeurs. Vous pouvez par exemple comparer le volume des ventes pour chaque segment existant.
   La mesure créée est alors ajoutée dans le rapport.

   ![](assets/s_advuser_cube_in_report_config_02b.png)

   Une fois que vous avez créé une mesure, vous pouvez la modifier et, si nécessaire, modifier sa configuration. Pour ce faire, cliquez sur le **[!UICONTROL Measures]** bouton, puis accédez à l&#39;onglet de la mesure à modifier.

   Cliquez ensuite **[!UICONTROL Edit the dynamic measure]** sur pour accéder au menu des paramètres.

## Construire une population cible {#building-a-target-population}

Les rapports construits à partir des cubes permettent de collecter des données de la base et les sauvegarder dans une liste.

Pour cela, vous pouvez les ajouter à un panier, dont le contenu sera exporté.

Pour regrouper une population dans une liste, les étapes sont les suivantes :

1. Click the cells that contain the population to be collected to select them, then click the **[!UICONTROL Add to cart]** icon.

   ![](assets/s_advuser_cube_in_report_config_02c.png)

   Répétez l&#39;opération autant de fois que nécessaire, pour collecter les différents profils.

1. Click the **[!UICONTROL Show cart]** button to view its content before running the export.

   ![](assets/s_advuser_cube_in_report_config_02d.png)

1. The **[!UICONTROL Export]** button lets you group the items in the cart into a list.

   Vous devez indiquer le nom de la liste et le type d&#39;export à réaliser.

   ![](assets/s-advuser_cube_in_report_config_02e.png)

   Click **[!UICONTROL Start]** to run the export.

1. Une fois l&#39;export terminé, un message vous en confirme la bonne exécution, ainsi que le nombre d&#39;enregistrements traités.

   ![](assets/s_advuser_cube_in_report_config_02f.png)

   Vous pouvez choisir de conserver le contenu du panier ou de le vider.

   La liste correspondante est accessible via l&#39; **[!UICONTROL Profiles and targets]** univers.

   ![](assets/s_advuser_cube_in_report_config_02g.png)

## Insérer un tableau croisé dynamique dans un rapport {#inserting-a-pivot-table-into-a-report}

Pour créer un tableau qui explore les données d&#39;un cube, les étapes sont les suivantes :

1. Créez un nouveau rapport, avec une seule page, et insérez un tableau pivot dynamique. Voir à ce propos [cette page](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table).

   ![](assets/s_advuser_cube_in_report_01.png)

1. In the **[!UICONTROL Data]** tab of the page, select a cube to process the dimensions it contains and display calculated measures.

   ![](assets/s_advuser_cube_in_report_02.png)

   Vous pourrez ainsi construire le rapport à afficher. Voir à ce propos la section [Etape 2 - Sélection des lignes et colonnes](#step-2---selecting-lines-and-columns).

