---
title: Modification de la source de données
description: En savoir plus sur l’activité Modification de la source de données
audience: workflow
content-type: reference
topic-tags: targeting-activities
source-git-commit: 9fc4add3f12e3f06b031c4969bd8409c67e4359e
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 60%

---

# Modification de la source de données {#change-data-source}

>[!NOTE]
>
> L&#39;activité **[!UICONTROL Modifier la source de données]** n&#39;est disponible qu&#39;avec le package **[!UICONTROL Accès aux données externes (Federated Data Access)]**. Pour plus d’informations sur les packages standard de Adobe Campaign Classic, consultez cette [page](../../installation/using/installing-campaign-standard-packages.md).

L&#39;activité **[!UICONTROL Modifier la source de données]** permet de modifier la source de données d&#39;un workflow **[!UICONTROL Table de travail]**. Vous bénéficiez ainsi d’une plus grande flexibilité pour gérer les données entre différentes sources de données, telles que FDA, FFDA et base de données locale.

La **[!UICONTROL table de travail]** permet au workflow Adobe Campaign Classic de gérer les données et de partager les données avec les activités du workflow.
Par défaut, la **[!UICONTROL table de travail]** est créée dans la même base de données que la source des données sur lesquelles nous effectuons une requête.

Par exemple, lors de l’interrogation de la table **[!UICONTROL Profils]** stockée dans la base de données cloud, vous allez créer une **[!UICONTROL table de travail]** sur la même base de données cloud.
Pour modifier ce paramètre, vous pouvez ajouter l’activité **[!UICONTROL Modifier la source de données]** afin de choisir une autre source de données pour votre **[!UICONTROL table de travail]**.

Notez que lorsque vous utilisez l’activité **[!UICONTROL Modifier la source de données]**, vous devez revenir à la base de données cloud pour continuer l’exécution des workflows.

Pour utiliser l’activité **[!UICONTROL Modifier la source de données]** :

1. Créez un workflow.

1. Interrogez vos destinataires ciblés avec une activité **[!UICONTROL Requête]**.

   Pour plus d&#39;informations sur l&#39;activité **[!UICONTROL Requête]**, consultez cette [page](../../workflow/using/query.md#creating-a-query).

1. Depuis l’onglet **[!UICONTROL Ciblage]**, ajoutez une activité **[!UICONTROL Modifier la source de données]** .

   ![](assets/change-data-source.png)

1. Double-cliquez sur votre activité **[!UICONTROL Modifier la source de données]** pour sélectionner **[!UICONTROL Source de données par défaut]**.

   La table de travail, qui contient le résultat de votre requête, est ensuite déplacée vers la base de données PostgreSQL par défaut.

   ![](assets/change-data-source_2.png)

1. Dans l’onglet **[!UICONTROL Actions]**, effectuez un glisser-déposer d’une activité **[!UICONTROL Code JavaScript]** pour réaliser des opérations unitaires sur la table de travail.

   Pour plus d&#39;informations sur l&#39;activité **[!UICONTROL Code JavaScript]**, consultez la page [Code JavaScript et Code JavaScript avancé](../../workflow/using/sql-code-and-javascript-code.md#javascript-code) .

1. Ajoutez une autre activité **[!UICONTROL Modifier la source de données]** pour revenir à la base de données cloud.

1. Double-cliquez sur votre activité et sélectionnez **[!UICONTROL Principal compte externe FDA]** puis le compte externe **[!UICONTROL Base externe]** correspondant.

   ![](assets/change-data-source_3.png)

1. Vous pouvez maintenant démarrer votre workflow.
