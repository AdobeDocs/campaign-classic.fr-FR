---
solution: Campaign Classic
product: campaign
title: Partage d'audiences avec Adobe Experience Cloud
description: Partage d'audiences avec Adobe Experience Cloud
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 61%

---


# Partage d&#39;audiences avec Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>Pour partager des audiences avec les solutions Adobe Experience Cloud, vous devez implémenter le système Identity Management Adobe. [En savoir plus sur IMS](../../integrations/using/about-adobe-id.md).

Avec Adobe Campaign, vous pouvez partager des audiences et des segments avec les solutions Adobe Experience Cloud et les services principaux. Deux options sont disponibles :

1. Envoyez des données de segment Adobe Experience Platform à Adobe Campaign. Pour mettre en oeuvre cette intégration, vous devez connecter votre plateforme de données clientes en temps réel à Campaign (RTCDP). [En savoir plus dans cette section](https://docs.adobe.com/content/help/fr-FR/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).


1. Integrate **Adobe Campaign** with **People core service** (also known as **Profiles &amp; Audiences core service**) or Adobe Audience Manager. Vous pourrez alors :

   * importer dans Adobe Campaign des audiences/segments provenant de différentes solutions d&#39;Adobe Experience Cloud. L&#39;import d&#39;audiences peut être réalisé depuis les listes dans Adobe Campaign.

   * exporter des listes sous la forme d’audiences partagées Adobe Experience Cloud. Ces audiences peuvent être exploitées dans les différentes solutions d’Adobe Experience Cloud que vous utilisez. L’export d’audiences peut être réalisé à la suite d’un ciblage dans un workflow, à l’aide d’une activité dédiée **[!UICONTROL Mise à jour d’audience partagée]**.

Cette intégration prend en charge deux types d’ID Adobe Experience Cloud :

* **Visitor ID** : ce type d&#39;identifiant permet de réconcilier des visiteurs Adobe Experience Cloud avec des destinataires Adobe Campaign.
* **Declared ID** : ce type d&#39;identifiant permet de réconcilier tout type de données avec des éléments de la base de données Adobe Campaign. Il est représenté dans Adobe Campaign sous la forme d&#39;une clé de réconciliation préalablement définie.
