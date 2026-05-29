---
product: campaign
title: 'Cas pratique : affichage d''un rapport sur les réponses à un questionnaire en ligne'
description: 'Cas pratique : affichage d''un rapport sur les réponses à un questionnaire en ligne'
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Surveys
exl-id: 6be12518-86d1-4a13-bbc2-b2ec5141b505
TQID: https://experienceleague.adobe.com/8JCloZIvg2WQsoFoEq6zYnDcrUOSBXCXlrkF2hY0xhc
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
subfeature_v2:
  - id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281
  - id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 518
ht-degree: 74%

---

# Cas d’utilisation : affichage d’un rapport sur les réponses à un questionnaire en ligne{#use-case-displaying-report-on-answers-to-an-online-survey}



Les réponses à des questionnaires Adobe Campaign peuvent être collectées et analysées dans des rapports dédiés.

Dans l&#39;exemple ci-dessous, nous allons collecter les réponses à un questionnaire en ligne et les afficher dans un rapport sous la forme d&#39;un tableau croisé dynamique.

Les étapes sont les suivantes :

1. Créer un workflow pour récupérer les réponses au questionnaire et les stocker dans une liste.
1. Créer un cube utilisant les données de la liste.
1. Créer un rapport avec un tableau croisé dynamique et consulter la répartition des réponses.

Avant de démarrer ce cas pratique, vous devez disposer d&#39;un questionnaire et d&#39;un jeu de réponses à analyser.

>[!NOTE]
>
>Ce cas pratique ne peut être implémenté que si vous avez acquis l&#39;option **Survey Manager**. Veuillez vérifier votre accord de licence.

## Etape 1 - Créer le workflow de collecte et stockage des données {#step-1---creating-the-data-collection-and-storage-workflow}

Pour collecter les réponses du questionnaire, les étapes sont les suivantes :

1. Créez un workflow et positionnez une activité **[!UICONTROL Réponses à un questionnaire]**. Pour plus d’informations sur cette activité, consultez [cette section](../../surveys/using/publish-track-and-use-collected-data.md#using-the-collected-data).
1. Editez l&#39;activité et sélectionnez le questionnaire dont vous souhaitez analyser les réponses.
1. Activez l&#39;option **[!UICONTROL Sélectionner toutes les données des réponses]** afin de collecter toutes les informations.

   ![](assets/reporting_usecase_1_01.png)

1. Sélectionnez ensuite les colonnes à extraire (ici : tous les champs archivés). Ce sont les champs qui contiennent les réponses.

   ![](assets/reporting_usecase_1_02.png)

1. Une fois la boîte de collecte des réponses paramétrée, positionnez une activité de type **[!UICONTROL Mise à jour de liste]** pour sauvegarder ces données.

   ![](assets/reporting_usecase_1_04.png)

   Dans cette activité, indiquez la liste à mettre à jour et désélectionnez l&#39;option **[!UICONTROL Purger puis réutiliser la liste si elle existe (sinon la compléter)]** : les réponses sont ajoutées à la table existante. Cette option permet de référencer la liste dans un cube. Le schéma associé à la liste ne sera pas regénéré à chaque mise à jour, ce qui garantit l&#39;intégrité du cube utilisant cette liste.

   ![](assets/reporting_usecase_1_03.png)

1. Démarrez le workflow pour en valider la configuration.

   ![](assets/reporting_usecase_1_05.png)

   La liste spécifiée est alors créée et contient le schéma des réponses au questionnaire.

1. Ajoutez un planificateur afin d&#39;automatiser une collecte quotidienne des réponses et la mise à jour de la liste.

   Les activités **[!UICONTROL Mise à jour de liste]** et **[!UICONTROL Planificateur]** sont présentées dans la section.

## Etape 2 - Créer le cube, ses mesures et ses indicateurs {#step-2---creating-the-cube--its-measures-and-its-indicators}

Vous pouvez ensuite créer le cube et paramétrer ses mesures : elles seront utilisées lors de la création des indicateurs. Ces indicateurs seront affichés dans le rapport. La création et le paramétrage des cubes sont présentés dans la section [À propos des cubes](../../reporting/using/ac-cubes.md).

Dans cet exemple, le cube est basé sur les données de la liste alimentée par le workflow créé à l&#39;étape précédente.

![](assets/reporting_usecase_2_01.png)

Définissez les dimensions et les mesures à afficher dans le rapport. Ici, nous souhaitons afficher la date du contrat et le pays du répondant.

![](assets/reporting_usecase_2_02.png)

L&#39;onglet **[!UICONTROL Prévisualisation]** permet de contrôler le rendu du rapport.

## Étape 3 - Créer le rapport et paramétrer la disposition des données dans le tableau {#step-3---creating-the-report-and-configuring-the-data-layout-within-the-table}

Vous pouvez ensuite créer un rapport basé sur ce cube et en exploiter les données et les informations.

![](assets/reporting_usecase_3_01.png)

Adaptez les informations à afficher selon vos besoins.

![](assets/reporting_usecase_3_02.png)
