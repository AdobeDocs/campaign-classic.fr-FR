---
product: campaign
title: Commencer avec l'import et de l'export de données
description: En savoir plus sur l'import et l'export de données dans Campaign
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d6055d97-75fc-4ed7-89bd-8336157454eb
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 100%

---

# Prise en main de l&#39;import et de l&#39;export de données {#get-started-data-import-export}



Adobe Campaign Classic fournit des fonctionnalités de gestion des données qui vous permettent d&#39;importer et d&#39;exporter des données. Ces opérations peuvent être effectuées à l&#39;aide de workflows ou d&#39;imports et d&#39;exports génériques.

>[!IMPORTANT]
>
>Lorsque vous utilisez cette fonctionnalité, gardez à l&#39;esprit les limites du stockage SFTP, du stockage en base de données et des profils actifs en fonction de votre contrat Adobe Campaign.

## Workflows {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

Les **workflows** constituent un moyen utile d&#39;automatiser vos processus d&#39;import. Que vous importiez des données à partir d&#39;un fichier local ou d&#39;un SFTP, ils vous permettent de standardiser vos procédures de gestion des données.

Avec les workflows, les opérations d&#39;import et d&#39;export peuvent être répétées automatiquement selon un planning, par exemple pour automatiser l&#39;échange de données entre plusieurs systèmes d&#39;informations.

Voir à ce propos [cette section](../../platform/using/import-export-workflows.md).

## Imports et exports génériques {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

En outre, Campaign Classic fournit des **imports et exports génériques** qui vous permettent de créer des tâches d&#39;import ou d&#39;export occasionnelles.

Les imports et exports sont configurés dans des modèles dédiés, que vous pouvez configurer et utiliser pour lancer et surveiller les tâches d&#39;import et d&#39;export.

Pour en savoir plus sur les imports et exports génériques, consultez [cette section](../../platform/using/about-generic-imports-exports.md).

>[!IMPORTANT]
>Les imports et exports génériques ne devraient être utilisés que pour des opérations occasionnelles. Pour assurer la cohérence des données et améliorer l&#39;efficacité, il est recommandé d&#39;effectuer les opérations d&#39;import et d&#39;export à l&#39;aide de workflows.

## Chiffrement et compression des données {#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

Campaign Classic vous permet d&#39;importer ou d&#39;exporter des fichiers compressés ou chiffrés.

Ces opérations sont effectuées dans des workflows, en appliquant des étapes de pré-traitement aux données que vous souhaitez utiliser.

Voir à ce propos les sections suivantes :

* [Décompresser ou déchiffrer un fichier](../../platform/using/unzip-decrypt.md)
* [Compresser ou chiffrer un fichier](../../platform/using/zip-encrypt.md)

## Bonnes pratiques et résolution des problèmes {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

Vous devez suivre plusieurs [bonnes pratiques](../../platform/using/import-export-best-practices.md) lors des opérations d’import et d’export afin d’assurer la cohérence des données dans la base de données et d’éviter les erreurs courantes lors des opérations de mise à jour ou d’export.

De plus, des recommandations et des problèmes courants liés à l’utilisation des serveurs SFTP sont disponibles dans [cette section](../../platform/using/sftp-server-usage.md).
