---
solution: Campaign Classic
product: campaign
title: Incorporer des segments Adobe Experience Platform dans Campaign
description: Découvrez comment intégrer des audiences Adobe Experience Platform dans le Campaign Classic.
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: 9b3254c16eed784846db87d27f9f5de009dafdc3
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# Incorporer des segments Adobe Experience Platform dans Campaign {#destinations}

Pour importer Adobe Experience Platform dans Campaign et les utiliser dans vos workflows, vous devez d&#39;abord connecter Adobe Campaign en tant que Adobe Experience Platform **Destination** et le configurer avec le segment à exporter.

Une fois la destination configurée, les données sont exportées vers votre emplacement d’enregistrement et vous devez créer un processus dédié dans le Campaign Classic pour les assimiler.

## Connecter Adobe Campaign en tant que destination

Dans la plate-forme Adobe Experience, configurez une connexion avec Adobe Campaign en sélectionnant un emplacement d’enregistrement pour les segments exportés. Cette procédure vous permet également de sélectionner les segments à exporter et de spécifier des champs XDM supplémentaires à inclure.

Pour plus d&#39;informations à ce sujet, consultez la [documentation sur les destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).

Une fois la destination configurée, Adobe Experience Platform crée un fichier .txt ou .csv délimité par des tabulations à l’emplacement de l’enregistrement que vous avez fourni. Cette opération est planifiée et exécutée une fois par 24h.

Vous pouvez désormais configurer un processus Campaign Classic pour assimiler le segment dans Campaign.

## Création d’un processus d’importation dans le Campaign Classic

Une fois que le Campaign Classic a été configuré en tant que destination, vous devez créer un processus dédié pour importer le fichier qui a été exporté par Adobe Experience Platform.

Pour ce faire, vous devez ajouter et configurer une activité **[!UICONTROL Transfert de fichier]**. Pour plus d&#39;informations sur la configuration de cette activité, consultez [cette section](../../workflow/using/file-transfer.md).

![](assets/rtcdp-file-transfer.png)

Vous pouvez ensuite créer votre processus en fonction de vos besoins (mettre à jour la base de données à l’aide des données de segment, envoyer des diffusions entre canaux au segment, etc.)

Par exemple, le flux de travail ci-dessous télécharge quotidiennement le fichier depuis l’emplacement de votre enregistrement, puis met à jour la base de données Campaign avec les données de segment.

![](assets/rtcdp-workflow.png)
