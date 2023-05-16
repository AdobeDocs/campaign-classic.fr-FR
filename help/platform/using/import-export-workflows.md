---
product: campaign
title: Import et export de données à l'aide de workflows
description: Découvrez comment importer et exporter des données à l'aide de workflows dans Campaign 
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 266ecd49-7101-4ff1-941f-1f9b39b44955
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 100%

---

# Import et export de données à l’aide de workflows {#import-export-workflows}



## Collecter des données {#collecting-data-workflows}

Les workflows peuvent être utiles pour automatiser certains de vos imports. Que vous importiez des données à partir d&#39;un fichier local ou d&#39;un serveur SFTP, vous pouvez utiliser des workflows pour standardiser vos procédures de Data Management.

### Utiliser les données d’une liste : lecture de liste {#using-data-from-a-list--read-list}

Les données traitées dans un workflow peuvent provenir de listes dont les données ont été préparées et structurées au préalable.

Ces listes peuvent avoir été constituées directement dans Adobe Campaign ou importées via l&#39;option **[!UICONTROL Importer une liste]**. Pour plus d&#39;informations sur cette option, consultez cette [page](../../platform/using/about-generic-imports-exports.md).

Pour plus d&#39;informations sur l&#39;utilisation de l&#39;activité de lecture de liste dans un workflow, consultez [cette page](../../workflow/using/read-list.md).

### Charger des données depuis un fichier {#loading-data-from-a-file}

Les données traitées dans un workflow peuvent êtes extraites d&#39;un fichier structuré pour qu&#39;elles puissent être importées dans Adobe Campaign.

Une description de l&#39;activité de chargement de fichier est disponible dans la section [Chargement (fichier)](../../workflow/using/data-loading--file-.md).

Voici un exemple de fichier structuré à importer :

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

Une fois les données collectées, vous pouvez les utiliser dans vos workflows, par exemple pour enrichir une diffusion ou mettre à jour la base de données. Consultez [cette page](../../workflow/using/how-to-use-workflow-data.md) pour plus d&#39;informations.

## Exporter des données {#exporting-data-via-a-workflow}

Les workflows peuvent être utiles pour automatiser certains de vos exports ou exporter des jeux de données précis après avoir utilisé certaines des activités de gestion des données disponibles pour transformer vos données.

Les opérations d&#39;export sont effectuées à l&#39;aide d&#39;une **[!UICONTROL activité Extraction de données (fichier)]**. Pour plus d&#39;informations sur la configuration et l&#39;utilisation de cette activité, consultez [cette page](../../workflow/using/extraction--file-.md).
