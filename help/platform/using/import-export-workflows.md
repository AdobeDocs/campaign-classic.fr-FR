---
product: campaign
title: Import et export de données à l'aide de workflows
description: Découvrez comment importer et exporter des données à l'aide de workflows dans Campaign.
feature: Data Management, Workflows
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 266ecd49-7101-4ff1-941f-1f9b39b44955
TQID: https://experienceleague.adobe.com/BfLvRPWrFBvVTQ0OfUu-sTcbZKXMDfB4HcF4STvzrRI
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 98
ht-degree: 64%

---

# Import et export de données à l’aide de workflows {#import-export-workflows}



## Collecter des données {#collecting-data-workflows}

Les workflows peuvent être un moyen utile d’automatiser certains de vos processus d’importation. Que vous importiez des données à partir d’un fichier local ou d’un serveur SFTP, vous pouvez utiliser des workflows pour normaliser vos procédures de gestion des données.

>[!NOTE]
>
>Pour en savoir plus sur l’import et l’export de données à l’aide de workflows, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/audience/add-profiles/import-profiles){target=_blank}.


<!--
### Use data from a list: Read list {#using-data-from-a-list--read-list}

The data sent in a workflow can come from lists whereby the data has been prepared and structured beforehand.

This list may have been directly created in Adobe Campaign or imported by the **[!UICONTROL Import a list]** option. For more on this option, refer to this [page](../../platform/using/about-generic-imports-exports.md).

For more on using the read list activity in a workflow, refer to [this page](../../workflow/using/read-list.md).

### Load data from a file {#loading-data-from-a-file}

The data processed in a workflow can be extracted from a structured file so that it can be imported into Adobe Campaign.

A description of the loading data activity can be found in the [Data loading (file)](../../workflow/using/data-loading-file.md) section.

Example of structured file to import:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

Once data has been collected you can use it in your workflows, for example to enrich a delivery or update the database. For more on this, refer to [this page](../../workflow/using/how-to-use-workflow-data.md).

## Export data {#exporting-data-via-a-workflow}

Workflows can be a useful way to automate some of your export processes or to export precise sets of data after using some of the available data management activities available to transform your data.

Export operations are performed using a **[!UICONTROL Data extraction (file) activity]**. For more on how to configure and use the activity, refer to [this page](../../workflow/using/extraction-file.md).
-->