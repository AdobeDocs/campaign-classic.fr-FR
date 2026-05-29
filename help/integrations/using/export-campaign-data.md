---
product: campaign
title: Exporter des données de Campaign vers Adobe Experience Platform
description: Découvrez comment exporter des données de Campaign Classic vers Adobe Experience Platform
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 8d1404c5-030b-47fe-a4c3-e72f15f09bbb
TQID: https://experienceleague.adobe.com/K3aSUw9KkEbo4lUPYW4jxCmLul-ShLy-gwZ71VZBrcA
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 542
ht-degree: 100%

---

# Exporter des données de Campaign vers Adobe Experience Platform {#sources}



Pour exporter des données de Campaign Classic vers Adobe Real-time Customer Data Platform (RTCDP), vous devez d&#39;abord créer un workflow dans Campaign Classic pour exporter les données que vous souhaitez partager vers votre emplacement de stockage S3 ou Azure Blob.

Une fois le workflow configuré et les données envoyées à votre emplacement de stockage, vous devez connecter votre emplacement de stockage S3 ou Azure Blob en tant que **Source** dans Adobe Experience Platform.

>[!NOTE]
>
>Veuillez noter que nous vous recommandons d’exporter uniquement les données générées par Campaign (par exemple, envois, ouvertures, clics, etc.) vers Adobe Experience Platform. Les données ingérées à partir d’une source tierce (telle que votre CRM) doivent être importées directement dans Adobe Experience Platform.

## Création d&#39;un workflow d&#39;export dans Campaign Classic

Pour exporter des données de Campaign Classic vers votre emplacement de stockage S3 ou Azure Blob, vous devez créer un workflow pour cibler les données à exporter et les envoyer vers votre emplacement de stockage.

Pour ce faire, ajoutez et configurez les éléments suivants :

* Une activité **[!UICONTROL Extraction (fichier)]** pour extraire les données ciblées dans un fichier CSV. Pour plus d’informations sur la configuration de cette activité, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/automation/workflows/wf-activities/action-activities/extraction-file.html?lang=fr){target="_blank"}.

  ![](assets/rtcdp-extract-file.png)

* Une activité **[!UICONTROL Transfert de fichier]** pour transférer le fichier CSV vers votre emplacement de stockage. Pour plus d’informations sur la configuration de cette activité, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html?lang=fr){target="_blank"}.

  ![](assets/rtcdp-file-transfer.png)

Par exemple, le workflow ci-dessous extrait régulièrement les logs dans un fichier CSV, puis transfère ce fichier vers un emplacement de stockage.

![](assets/aep-export.png)

## Connecter votre emplacement de stockage en tant que source

Les étapes principales pour connecter votre emplacement de stockage S3 ou Azure Blob en tant que **Source** dans Adobe Experience Platform sont énumérées ci-dessous. Des informations détaillées sur chacune de ces étapes sont disponibles dans la [documentation des connecteurs source](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=fr).

1. Dans le menu **[!UICONTROL Sources]** d’Adobe Experience Platform, créez une connexion vers votre emplacement de stockage :

   * [Créer une connexion source Amazon S3](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/s3.html?lang=fr)
   * [Connecteur Azure Blob](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/cloud-storage/blob.html?lang=fr)

   >[!NOTE]
   >
   >L&#39;emplacement de l&#39;enregistrement peut être Amazon S3, SFTP avec mot de passe, SFTP avec clé SSH ou des connexions Azure Blob. La méthode préférée pour envoyer des données vers Adobe Campaign est via Amazon S3 ou Azure Blob :

   ![](assets/rtcdp-connector.png)

1. Configurez un flux de données pour une connexion par lots vers l’espace de stockage. Un flux de données est une tâche planifiée qui récupère et ingère des données issues de l’emplacement de stockage pour obtenir un jeu de données Adobe Experience Platform. Cette procédure permet de configurer l’ingestion des données depuis votre emplacement de stockage, y compris la sélection des données et le mapping des champs CSV avec un schéma XDM.

   Des informations détaillées sont disponibles dans [cette page](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html?lang=fr).

   ![](assets/rtcdp-map-xdm.png)

1. Une fois la source configurée, Adobe Experience Platform importe le fichier à partir de l’emplacement de stockage que vous avez indiqué.

   Cette opération peut être planifiée en fonction de vos besoins. Il est recommandé d’effectuer l’exportation jusqu’à 6 fois par jour, selon la charge déjà présente sur l’instance.
