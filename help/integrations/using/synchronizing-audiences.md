---
title: Synchronisation des audiences
seo-title: Synchronisation des audiences
description: Synchronisation des audiences
seo-description: null
page-status-flag: never-activated
uuid: eda67bf7-8a0a-4240-8b31-de364be5d572
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 749a084e-69ee-46b4-b09b-cb91bb1da3cd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Synchronisation des audiences{#synchronizing-audiences}

Vous pouvez créer une liste complexe à l&#39;aide des fonctionnalités avancées de Campaign v7 et la partager de façon transparente en tant qu&#39;audience directement et en temps réel avec Campaign Standard (y compris, les données additionnelles). L&#39;utilisateur d&#39;Adobe Campaign peut ensuite utiliser l&#39;audience dans Adobe Campaign Standard.

Un ciblage complexe impliquant des données additionnelles qui ne sont pas répliquées dans Campaign Standard n&#39;est possible qu&#39;avec Campaign v7.

Vous pouvez également simplement partager des listes de destinataires ou de données provenant d&#39;un connecteur tel que Microsoft Dynamics avec Campaign Standard.

Ce cas pratique montre comment préparer la cible de votre diffusion dans Campaign v7 et la réutiliser avec ses données additionnelles dans une diffusion créée et envoyée dans Adobe Campaign Standard.

>[!NOTE]
>
>Vous pouvez également enrichir les données à l&#39;aide d&#39;agrégats et de collections dans Adobe Campaign Standard si toutes les données dont vous avez besoin sont déjà répliquées.

## Prérequis {#prerequisites}

Pour ce faire, les éléments suivants sont nécessaires :

* Destinataires stockés dans la base de données Campaign v7 et synchronisés avec Campaign Standard. Reportez-vous à la section [Synchronisation des profils](../../integrations/using/synchronizing-profiles.md) .
* Des données additionnelles telles que des abonnements ou des transactions stockées dans des tables associées à nms:recipients dans la base de données de Campaign v7. Ces données peuvent provenir de tables personnalisées ou de schémas d&#39;usine de Campaign v7. Par défaut, ces données ne sont pas accessibles dans Campaign Standard, car elles ne sont pas synchronisées.
* Droits d&#39;exécution de workflows dans Campaign v7 et Campaign Standard.
* Droits de création et d&#39;exécution d&#39;une diffusion dans Campaign Standard.

## Créer un workflow de ciblage avec des données additionnelles dans Campaign v7 {#create-a-targeting-workflow-with-additional-data-in-campaign-v7}

Un ciblage complexe impliquant des données additionnelles qui ne sont pas répliquées dans Campaign Standard n&#39;est possible qu&#39;avec Campaign v7.

Une fois que la cible et ses données additionnelles ont été définies, il est possible d&#39;enregistrer la cible en tant que liste pouvant être partagée avec Campaign Standard.

>[!NOTE]
>
>Il s&#39;agit d&#39;un exemple. En fonction de vos besoins, vous pouvez simplement lancer des requêtes sur une liste de destinataires et la partager avec ACS sans appliquer d&#39;autres traitements. Vous pouvez également utiliser d&#39;autres activités de gestion des données pour préparer la cible finale.

Pour obtenir l&#39;audience finale et ses données additionnelles :

1. Créez un nouveau flux de travail à partir de **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. Ajoutez une **[!UICONTROL Query]** activité et sélectionnez les destinataires auxquels vous souhaitez envoyer le courrier électronique final. Par exemple, tous les bénéficiaires âgés de 18 à 30 ans et vivant en France.

   ![](assets/acs_connect_query1.png)

1. Ajoutez des données additionnelles issues de la requête. Pour plus d&#39;informations, reportez-vous à la section [Ajouter des données](../../workflow/using/query.md#adding-data).

   Cet exemple montre comment ajouter un agrégat pour comptabiliser le nombre de diffusions reçues par un destinataires au cours d&#39;une année.

   Dans la **[!UICONTROL Query]**, sélectionnez **[!UICONTROL Add data...]**.

   ![](assets/acs_connect_query2.png)

1. Sélectionnez **[!UICONTROL Data linked to the filtering dimension]** puis cliquez sur **[!UICONTROL Next]**.

   ![](assets/acs_connect_query3.png)

1. Choisissez **[!UICONTROL Data linked to the filtering dimension]** puis sélectionnez le **[!UICONTROL Recipient delivery logs]** noeud et cliquez sur **[!UICONTROL Next]**.

   ![](assets/acs_connect_query4.png)

1. Sélectionnez **[!UICONTROL Aggregates]** dans le **[!UICONTROL Data collected]** champ et cliquez sur **[!UICONTROL Next]**.

   ![](assets/acs_connect_query5.png)

1. Add a filtering condition to only take into account logs that were created during the last 365 days and click **[!UICONTROL Next]**.

   ![](assets/acs_connect_query6.png)

1. Définissez les colonnes de sortie. Dans le cas présent, seule la colonne permettant de compter le nombre de diffusions est nécessaire. Pour la définir :

   * Select **[!UICONTROL Add]** on the right of the window.
   * Dans la **[!UICONTROL Select field]** fenêtre, cliquez sur **[!UICONTROL Advanced selection]**.
   * Sélectionnez **[!UICONTROL Aggregate]**, puis **[!UICONTROL Count]**. Sélectionnez l’ **[!UICONTROL Distinct]** option, puis cliquez sur **[!UICONTROL Next]**.
   * Dans la liste des champs, sélectionnez le champ utilisé pour la fonction **Count** . Choisissez un champ qui sera toujours renseigné, par exemple le **[!UICONTROL Primary key]** champ, puis cliquez sur **[!UICONTROL Finish]**.
   * Modifiez l’expression dans la **[!UICONTROL Alias]** colonne. Cet alias vous permettra de récupérer facilement la colonne ajoutée dans la remise finale. Par exemple, **les livraisons** NB.
   * Cliquez sur **[!UICONTROL Finish]** et enregistrez la configuration de l’ **[!UICONTROL Query]** activité.
   ![](assets/acs_connect_query7.png)

1. Enregistrez le workflow. La section suivante montre comment partager la population avec ACS.

## Partager la cible avec Campaign Standard {#share-the-target-with-campaign-standard}

Once the target population is defined, you can share it with ACS through a **[!UICONTROL List update]** activity.

1. In the workflow created previously, add a **[!UICONTROL List update]** activity and specify the list you want to update or create.

   Spécifiez le dossier dans lequel vous souhaitez enregistrer la liste dans Campaign v7. Les listes sont soumises au mappage de dossiers défini lors de l’implémentation, ce qui peut avoir un impact sur leur visibilité une fois partagées dans Campaign Standard. Reportez-vous à la section Conversion [des](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion) droits.

1. Vérifiez que l’ **[!UICONTROL Share with ACS]** option est cochée. Elle est vérifiée par défaut.

   ![](assets/acs_connect_listupdate1.png)

1. Enregistrez et exécutez le workflow.

   La cible et ses données additionnelles sont enregistrées dans une liste, dans Campaign v7, et sont immédiatement partagées en tant qu&#39;audience de type liste dans Campaign Standard. Seuls les profils qui ont été répliqués sont partagés avec ACS.

Si une erreur se produit sur l’ **[!UICONTROL List update]** activité, cela signifie que la synchronisation avec Campaign Standard peut avoir échoué. Pour plus d’informations sur ce qui s’est passé, accédez à **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Ce dossier contient les processus de synchronisation déclenchés par l’exécution de l’ **[!UICONTROL List update]** activité. Reportez-vous à la section [Résolution des problèmes du connecteur](../../integrations/using/troubleshooting-the-acs-connector.md) ACS.

## Récupérer les données dans Campaign Standard et les utiliser dans une diffusion {#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}

Une fois que le workflow de ciblage a été exécuté dans Campaign v7, l&#39;audience de type liste est accessible en lecture seule dans le menu **[!UICONTROL Audiences]** de Campaign Standard.

![](assets/acs_connect_deliveryworkflow_audience.png)

En créant un workflow de diffusion dans Campaign Standard, vous pourrez ensuite utiliser cette audience et ses données additionnelles dans une diffusion.

1. Create a new workflow from the **[!UICONTROL Marketing activities]** menu.
1. Add a **[!UICONTROL Read audience]** activity and select the audience you previously shared from Campaign v7.

   Cette activité est utilisée pour récupérer les données de l’audience sélectionnée. Vous pouvez également en appliquer un supplémentaire **[!UICONTROL Source Filtering]** si nécessaire en utilisant l’onglet correspondant de cette activité.

1. Add an **[!UICONTROL Email delivery]** activity and configure it as any other [email delivery activity](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html).
1. Ouvrez le contenu de la diffusion.
1. Ajouter un champ de personnalisation Recherchez le **[!UICONTROL Additional data (targetData)]** noeud dans la fenêtre contextuelle. Ce noeud contient les données supplémentaires de l’audience qui ont été calculées dans le processus de ciblage initial. Vous pouvez les utiliser comme tout autre champ de personnalisation.

   Dans cet exemple, les données additionnelles provenant du workflow de ciblage d&#39;origine sont le nombre de diffusions envoyées à chaque destinataire au cours des 365 dernier jours. L&#39;alias NBdeliveries spécifié dans le workflow de ciblage est visible ici.

   ![](assets/acs_connect_deliveryworkflow_targetdata.png)

1. Enregistrez la diffusion et le workflow.

   Le workflow est prêt à être exécuté. La diffusion sera analysée et prête à être envoyée.

   ![](assets/acs_connect_deliveryworkflow_ready.png)

## Envoyer et suivre votre diffusion {#send-and-monitor-your-delivery}

Lorsque la diffusion et son contenu sont prêts, envoyez la diffusion, comme décrit en détail dans [cette section](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html):

1. Exécutez le workflow de diffusion. Cette étape prépare l&#39;envoi de l&#39;email.
1. Dans le tableau de bord de la diffusion, validez manuellement l&#39;envoi de la diffusion.
1. Examinez les rapports et les logs de la diffusion :

   * **Dans Campaign Standard** : accédez aux [rapports](https://docs.adobe.com/content/help/en/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html) et [logs](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html) relatifs à la diffusion comme pour toute autre diffusion.
   * **Dans Campaign v7 et Campaign Standard** : les identifiants des diffusions, les broadLogs et les logs de tracking des emails sont synchronisés dans Campaign v7. Vous obtenez alors une vue à 360° de vos campagnes marketing depuis Campaign v7.

      Les quarantaines sont automatiquement synchronisées avec Campaign v7. Ainsi, les informations de non-délivrabilité peuvent être prises en compte pour le prochain ciblage effectué dans Campaign v7.

      Pour plus d&#39;informations sur la gestion des quarantaines dans Campaign Standard, reportez-vous à [cette section](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html).

