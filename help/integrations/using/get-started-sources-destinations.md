---
product: campaign
title: Commencer avec les sources et les destinations
description: En savoir plus sur les sources et les destinations d’Adobe Experience Platform
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 8cee52c7-ea56-4701-8ebb-eb18afffea51
TQID: https://experienceleague.adobe.com/xPpBR6NrQ315FIw1beLnw4c0gyLzEoYWzIXDljDg9H4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: c3bf7e1e-1db5-4c72-9293-e2f0b1ab73d0id: eb007b6d-6e57-46ab-9485-3f24d6102304
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 313
ht-degree: 100%

---

# Utilisation des sources et des destinations {#rtcdp}



## À propos des sources et des destinations

Adobe Experience Platform permet de partager des données entre Campaign Classic et Adobe Real-time Customer Data Platform (RTCDP). Vous pouvez ainsi cibler des audiences Adobe Experience Platform dans vos workflows Campaign, puis renvoyer à Adobe Real-time Customer Data Platform les données liées à ces audiences, notamment les envois, les ouvertures et les clics.

* Avec **Destinations**, ingérez les audiences d&#39;Adobe Experience Platform dans Campaign Classic. Il est ainsi possible d&#39;activer vos données connues et inconnues pour vos opérations marketing.
* Avec **Sources**, exportez les données de Campaign Classic (par exemple, envois, ouvertures, clics) dans Adobe Experience Platform. Vous pouvez ainsi centraliser les données collectées à partir de sources disparates dans un seul et même endroit, et utiliser les informations acquises pour faire davantage.

>[!IMPORTANT]
>
>Lorsque vous utilisez cette fonctionnalité, gardez à l&#39;esprit les limites du stockage SFTP, les limites du stockage en base de données, et les limites des profils actifs en fonction de votre contrat Adobe Campaign.

Pour un aperçu plus détaillé d’Adobe Real-time Customer Data Platform, des destinations et des sources, consultez les pages suivantes :

* [Adobe Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html?lang=fr)
* [Documentation sur les destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=fr)
* [Documentation sur les sources](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=fr)

## Connecter Campaign Classic à Adobe Experience Platform

Pour pouvoir partager des données entre Adobe Experience Platform et Campaign Classic, vous devez d&#39;abord connecter Adobe Campaign en tant que **destination** et connecter votre emplacement de stockage AWS S3 ou Azure Blob en tant que **source** dans Adobe Experience Platform.

Une fois les connecteurs configurés, vous pouvez configurer un import ou un export de données dans Campaign Classic à l&#39;aide de workflows.

![](assets/rtcdp-schema.png)

Pour plus d&#39;informations sur la configuration de ces processus d&#39;import et d&#39;export, reportez-vous aux sections suivantes :

* [Ingérer des segments Adobe Experience Platform dans Campaign](../../integrations/using/ingest-aep-data.md)
* [Exporter des données de Campaign vers Adobe Experience Platform](../../integrations/using/export-campaign-data.md)
