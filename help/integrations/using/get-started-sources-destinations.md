---
solution: Campaign Classic
product: campaign
title: Commencer avec les sources et les destinations
description: En savoir plus sur les sources et les destinations Adobe Experience Platform.
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: b4da54c122e75a175f6f586a05955b3dfed00c1e
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 1%

---


# Commencer avec Sources et Destinations {#rtcdp}

## A propos des sources et des destinations

Adobe Experience Platform vous permet de partager des données entre Campaign Classic et plateforme de données client en temps réel (RTCDP) Adobe. Cela vous permet de cible des audiences Adobe Experience Platform dans vos Workflows de campagne, puis de renvoyer à l’Adobe les données de la plate-forme de données client en temps réel liées à ces audiences, telles que les envois, les ouvertures et les clics.

* Avec **Destinations**, ingérer les audiences de Adobe Experience Platform dans le Campaign Classic. Cela vous permet d’activer vos données connues et inconnues pour vos campagnes marketing.
* Avec **Sources**, exportez les données du Campaign Classic (par exemple, envoie, ouvre, clics) dans Adobe Experience Platform. Cela vous permet de centraliser les données que vous collectez à partir de sources disparates dans un seul et même endroit, et d&#39;utiliser les connaissances acquises pour en faire plus.

>[!IMPORTANT]
>
>Gardez à l’esprit les limites d’enregistrement SFTP, les limites d’enregistrement de base de données et les limites de profil principal conformément à votre contrat Adobe Campaign lors de cette intégration.

Pour un aperçu plus détaillé de la plate-forme de données client en temps réel, des destinations et des sources d’Adobe, reportez-vous aux pages suivantes :

* [Plateforme de données clientes Adobe en temps réel](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html)
* [Documentation sur les destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html)
* [Documentation des sources](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html)

## Connecter le Campaign Classic à Adobe Experience Platform

Pour pouvoir partager des données entre Adobe Experience Platform et Campaign Classic, vous devez d&#39;abord connecter Adobe Campaign en tant que **destination** et connecter votre enregistrement blob AWS S3 ou Azure en tant que **source** dans la plateforme d&#39;expérience d&#39;Adobe.

Une fois les connecteurs configurés, vous pouvez configurer une importation ou une exportation de données dans le Campaign Classic à l’aide de workflows.

![](assets/rtcdp-schema.png)

Pour plus d&#39;informations sur la configuration de ces processus d&#39;importation et d&#39;exportation, reportez-vous aux sections suivantes :

* [Incorporer des segments Adobe Experience Platform dans Campaign](../../integrations/using/ingest-aep-data.md)
* [Exporter des données de Campaign vers Adobe Experience Platform](../../integrations/using/export-campaign-data.md)
