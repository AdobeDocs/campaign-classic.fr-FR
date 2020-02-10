---
title: Gestion des rapports
seo-title: Gestion des rapports
description: Gestion des rapports
seo-description: null
page-status-flag: never-activated
uuid: 3b8e6f11-4cbd-450e-871b-50fd0ead96db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 21777423-0c8a-4bb1-b210-972f660648bd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Gestion des rapports{#managing-reports}

Reports based on a schema that is specific to the default Adobe Campaign recipients (nm:recipient or schema linked) must be re-developed in order to take into account the data from the custom table and its tables linked via the target mapping (see the [Target mapping](../../configuration/using/target-mapping.md) section).

Pour créer des rapports, voir [cette section](../../reporting/using/about-reports-creation-in-campaign.md).

Dans certains cas, vous devrez également mettre en place de nouveaux cubes spécifiques à ces tables. Les cubes sont présentés dans [cette section](../../reporting/using/about-cubes.md).

Les rapports concernés sont les suivants :

* **[!UICONTROL Recent proposition tracking]** (Propositions récentes) : suivi des propositions en temps réel.
* **[!UICONTROL Breakdown of opens]** (openByUserAgent) : s’ouvre ventilé selon le logiciel utilisateur.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities) : analyse des activités de partage, des ouvertures et des abonnements par période.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryComments) : indicateurs de suivi pour une diffusion sur une application mobile.
* **[!UICONTROL Offer analysis]** (offerAnalysis) : analyse des offres par date et par canal.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution) : taux de réactivité pour les dernières livraisons.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution) : ventilation des abonnements actifs par application mobile.

