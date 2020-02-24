---
title: Partage d'audiences avec Adobe Experience Cloud
seo-title: Partage d'audiences avec Adobe Experience Cloud
description: Partage d'audiences avec Adobe Experience Cloud
seo-description: null
page-status-flag: never-activated
uuid: 24ac3463-69ab-48b4-85e0-4fe1948bf5ed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 8f295058-5a78-4512-9bdf-d5f022457e10
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 418a36cd51106dae2b4201c8b5abda9b05285a18

---


# Partage d&#39;audiences avec Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!NOTE]
>
>L&#39;utilisation de cette intégration nécessite qu&#39;IMS soit mis en œuvre. Voir à ce propos la section sur [IMS](../../integrations/using/about-adobe-id.md).

Adobe Campaign vous permet d&#39;échanger et de partager des audiences/segments avec les différentes solutions d&#39;Adobe Experience Cloud et les core services. En intégrant **Adobe Campaign** avec **People core service** (également appelé **Profiles &amp; Audiences core service**) ou Adobe Audience Manager, vous pouvez :

* importer dans Adobe Campaign des audiences/segments provenant de différentes solutions d&#39;Adobe Experience Cloud. L&#39;import d&#39;audiences peut être réalisé depuis les listes dans Adobe Campaign.
* exporter des listes sous la forme d’audiences partagées Adobe Experience Cloud. Ces audiences peuvent être exploitées dans les différentes solutions d’Adobe Experience Cloud que vous utilisez. L’export d’audiences peut être réalisé à la suite d’un ciblage dans un workflow, à l’aide d’une activité dédiée **[!UICONTROL Mise à jour d’audience partagée]**.

>[!CAUTION]
>
>L&#39;import d&#39;audiences dans Adobe Campaign peut être soumis à des restrictions légales en fonction du type des données.

L&#39;intégration prend en charge deux types d&#39;identifiants Adobe Experience Cloud :

* **Visitor ID** : ce type d&#39;identifiant permet de réconcilier des visiteurs Adobe Experience Cloud avec des destinataires Adobe Campaign.
* **Declared ID** : ce type d&#39;identifiant permet de réconcilier tout type de données avec des éléments de la base de données Adobe Campaign. Il est représenté dans Adobe Campaign sous la forme d&#39;une clé de réconciliation préalablement définie.
