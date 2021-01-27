---
solution: Campaign Classic
product: campaign
title: Import et export de données à l'aide de workflows
description: Découvrez comment importer et exporter des données à l’aide de workflows dans le Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 72%

---


# Import et export de données à l&#39;aide de workflows {#import-export-workflows}

## Collecter des données {#collecting-data-workflows}

Les workflows peuvent être utiles pour automatiser certains de vos imports. Que vous importiez des données à partir d&#39;un fichier local ou d&#39;un serveur SFTP, vous pouvez utiliser des workflows pour standardiser vos procédures de Data Management.

### Utiliser les données d&#39;une liste : Lecture de Liste {#using-data-from-a-list--read-list}

Les données traitées dans un workflow peuvent provenir de listes dont les données ont été préparées et structurées au préalable.

Ces listes peuvent avoir été constituées directement dans Adobe Campaign ou importées via l&#39;option **[!UICONTROL Importer une liste]**. Pour plus d&#39;informations sur cette option, consultez cette [page](../../platform/using/about-generic-imports-exports.md).

Pour plus d&#39;informations sur l&#39;utilisation de l&#39;activité de liste lue dans un flux de travail, consultez [cette page](../../workflow/using/read-list.md).

### Charger des données depuis un fichier {#loading-data-from-a-file}

Les données traitées dans un workflow peuvent êtes extraites d&#39;un fichier structuré pour qu&#39;il puisse être importé dans Adobe Campaign.

Une description de l&#39;activité de chargement de fichier est disponible dans la section [Chargement (fichier)](../../workflow/using/data-loading--file-.md).

Voici un exemple de fichier structuré à importer :

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

Une fois les données collectées, vous pouvez les utiliser dans vos workflows, par exemple pour enrichir une diffusion ou mettre à jour la base de données. Consultez [cette page](../../workflow/using/how-to-use-workflow-data.md) pour plus d’informations.

## export des données {#exporting-data-via-a-workflow}

Les workflows peuvent être utiles pour automatiser certains de vos exports ou exporter des jeux de données précis après avoir utilisé certaines des activités de gestion des données disponibles pour transformer vos données.

Les opérations d’exportation sont effectuées à l’aide d’une activité **[!UICONTROL extraction de données (fichier)]**. Pour plus d&#39;informations sur la configuration et l&#39;utilisation de l&#39;activité, consultez [cette page](../../workflow/using/extraction--file-.md).
