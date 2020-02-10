---
title: '"Cas pratique : affichage d''un rapport sur les réponses à un questionnaire en ligne"'
seo-title: '"Cas pratique : affichage d''un rapport sur les réponses à un questionnaire en ligne"'
description: '"Cas pratique : affichage d''un rapport sur les réponses à un questionnaire en ligne"'
seo-description: null
page-status-flag: never-activated
uuid: 2c0a5b7d-c606-4bcb-9600-8f89e6fce32a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: 5404a227-6cfb-463b-9a56-af46a022eb38
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Cas pratique : affichage d&#39;un rapport sur les réponses à un questionnaire en ligne{#use-case-displaying-report-on-answers-to-an-online-survey}

Les réponses à des questionnaires Adobe Campaign peuvent être collectées et analysées dans des rapports dédiés.

Dans l&#39;exemple ci-dessous, nous allons collecter les réponses à un questionnaire en ligne et les afficher dans un rapport sous la forme d&#39;un tableau croisé dynamique.

Les étapes sont les suivantes :

1. Créer un workflow pour récupérer les réponses au questionnaire et les stocker dans une liste.
1. Créer un cube utilisant les données de la liste.
1. Créer un rapport avec un tableau croisé dynamique et consulter la répartition des réponses.

Avant de démarrer ce cas pratique, vous devez disposer d&#39;un questionnaire et d&#39;un jeu de réponses à analyser.

>[!NOTE]
>
>Ce cas pratique ne peut être mis en oeuvre que si vous avez acquis l&#39;option **Survey Manager**. Vérifiez votre contrat de licence.

## Etape 1 - Créer le workflow de collecte et stockage des données {#step-1---creating-the-data-collection-and-storage-workflow}

Pour collecter les réponses du questionnaire, les étapes sont les suivantes :

1. Créez un processus et importez une **[!UICONTROL Answers to a survey]** activité. For more on using this activity, refer to [this section](../../web/using/publish--track-and-use-collected-data.md#using-the-collected-data).
1. Editez l&#39;activité et sélectionnez le questionnaire dont vous souhaitez analyser les réponses.
1. Activez l’ **[!UICONTROL Select all the answer data]** option pour collecter toutes les informations.

   ![](assets/reporting_usecase_1_01.png)

1. Sélectionnez les colonnes à extraire (ici : tous les champs archivés). Les réponses sont stockées dans ces champs.

   ![](assets/reporting_usecase_1_02.png)

1. Once the answer collection box is configured, position a **[!UICONTROL List update]** type activity to save the data.

   ![](assets/reporting_usecase_1_04.png)

   Dans cette activité, spécifiez la liste à mettre à jour et désactivez l’ **[!UICONTROL Purge and re-use the list if it exists (otherwise add to the list)]** option : les réponses sont ajoutées au tableau existant. Cette option vous permet de référencer la liste dans un cube. Le schéma lié à la liste ne sera pas recréé pour chaque mise à jour, ce qui garantit l&#39;intégrité du cube qui utilise cette liste.

   ![](assets/reporting_usecase_1_03.png)

1. Démarrez le workflow pour en valider la configuration.

   ![](assets/reporting_usecase_1_05.png)

   La liste spécifiée est alors créée et contient le schéma des réponses au questionnaire.

1. Ajoutez un planificateur afin d&#39;automatiser une collecte quotidienne des réponses et la mise à jour de la liste.

   Les activités **[!UICONTROL List update]** et **[!UICONTROL Scheduler]** les activités sont décrites en détail dans .

## Etape 2 - Créer le cube, ses mesures et ses indicateurs {#step-2---creating-the-cube--its-measures-and-its-indicators}

Vous pouvez ensuite créer le cube et paramétrer ses mesures : elles seront utilisées lors de la création des indicateurs. Ces indicateurs seront affichés dans le rapport. For more on creating and configuring cubes, refer to [About cubes](../../reporting/using/about-cubes.md).

Dans cet exemple, le cube est basé sur les données de la liste alimentée par le workflow créé à l&#39;étape précédente.

![](assets/reporting_usecase_2_01.png)

Définissez les dimensions et mesures à afficher dans le rapport. Ici, nous afficherons la date du contrat et le pays du participant.

![](assets/reporting_usecase_2_02.png)

The **[!UICONTROL Preview]** tab lets you control the rendering of the report.

## Etape 3 - Créer le rapport et paramétrer l&#39;affichage des données dans le tableau {#step-3---creating-the-report-and-configuring-the-data-layout-within-the-table}

Vous pouvez ensuite créer un rapport basé sur ce cube et en exploiter les données et les informations.

![](assets/reporting_usecase_3_01.png)

Adaptez les informations à afficher selon vos besoins.

![](assets/reporting_usecase_3_02.png)

