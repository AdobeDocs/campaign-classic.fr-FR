---
solution: Campaign Classic
product: campaign
title: Prise en main de l'import et de l'export de données
description: En savoir plus sur l’importation et l’exportation de données en Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 37cc6cd8b71ec82cd4e6a910d6664a51ed5c091e
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 13%

---


# Prise en main de l&#39;import et de l&#39;export de données {#get-started-data-import-export}

Adobe Campaign Classic fournit des fonctionnalités de data Management qui vous permettent d’importer et d’exporter des données. Ces opérations peuvent être effectuées à l’aide de workflows ou d’importations et d’exportations génériques.

>[!IMPORTANT]
>
>Veuillez garder à l&#39;esprit l&#39;enregistrement SFTP, l&#39;enregistrement de base de données et les limites principales de profil, conformément à votre contrat Adobe Campaign, tout en utilisant cette fonctionnalité.

## Workflows {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Les** flux de travaux constituent un moyen utile d’automatiser vos processus d’importation. Que vous importiez des données à partir d’un fichier local ou d’un SFTP, elles vous permettent de normaliser vos procédures de data Management.

Avec les workflows, les opérations d&#39;importation et d&#39;exportation peuvent être répétées automatiquement selon un calendrier, par exemple pour automatiser l&#39;échange de données entre plusieurs systèmes d&#39;information.

Voir à ce propos [cette section](../../platform/using/import-export-workflows.md).

## Imports et exports génériques {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

De plus, Campaign Classic fournit des **importations et exportations génériques** qui vous permettent de créer des tâches d&#39;importation ou d&#39;exportation occasionnelles.

Les importations et exportations sont configurées dans des modèles dédiés, que vous pouvez configurer et utiliser pour lancer et surveiller les tâches d’importation et d’exportation.

Pour en savoir plus sur les importations et exportations génériques, consultez [cette section](../../platform/using/about-generic-imports-exports.md).

>[!IMPORTANT]
>Les importations et les exportations génériques ne devraient être utilisées que pour des opérations occasionnelles. Pour assurer la cohérence des données et améliorer l’efficacité, il est recommandé d’effectuer les opérations d’importation et d’exportation à l’aide de workflows.

## Chiffrement et compression des données {#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

Campaign Classic vous permet d’importer des fichiers compressés ou chiffrés et d’exporter des fichiers compressés ou chiffrés.

Ces opérations sont effectuées dans des workflows, en appliquant des étapes de prétraitement aux données que vous souhaitez exploiter.

Voir à ce propos les sections suivantes :

* [Décompresser ou déchiffrer un fichier](../../platform/using/unzip-decrypt.md)
* [Compresser ou crypter un fichier](../../platform/using/zip-encrypt.md)

## Bonnes pratiques et résolution des problèmes {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

Plusieurs [bonnes pratiques](../../platform/using/import-export-best-practices.md) doivent être suivies lors des opérations d&#39;importation et d&#39;exportation afin d&#39;assurer la cohérence des données dans la base de données et d&#39;éviter les erreurs communes lors de la mise à jour ou de l&#39;exportation.

De plus, des recommandations et des problèmes courants liés à l’utilisation des serveurs SFTP sont disponibles dans [cette section](../../platform/using/sftp-server-usage.md).
