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

Les rapports se basant sur un schéma spécifique aux destinataires par défaut d&#39;Adobe Campaign (nms:recipient ou schéma lié) doivent être redéveloppés afin de prendre en compte les données de la table personnalisée et de ses tables liées via le mapping de ciblage (voir la section [Mapping de ciblage](../../configuration/using/target-mapping.md)).

Pour créer des rapports, voir [cette section](../../reporting/using/about-reports-creation-in-campaign.md).

Dans certains cas, vous devrez également mettre en place de nouveaux cubes spécifiques à ces tables. Les cubes sont présentés dans [cette section](../../reporting/using/about-cubes.md).

Les rapports concernés sont les suivants :

* **[!UICONTROL Suivi des propositions récentes]** (recentPropositions) : suivi en temps réél des propositions.
* **[!UICONTROL Répartition des ouvertures]** (opensByUserAgent) : répartition des ouvertures selon les logiciels utilisateur.
* **[!UICONTROL Statistiques des activités de partage]** (forwardActivities) : analyse des partages, ouvertures et abonnements par périodes de temps.
* **[!UICONTROL Indicateurs de tracking]** (mobileAppDeliveryFeedback) : indicateurs de tracking d&#39;une diffusion sur une application mobile.
* **[!UICONTROL Analyse des offres]** (offerAnalysis) : analyse des offres par date et canal.
* **[!UICONTROL Taux de réactivité]** (mobileAppReactivityRate) : taux de réactivité des dernières diffusions.
* **[!UICONTROL Répartition des abonnements]** (mobileAppDistribution) répartition des abonnements actifs par application mobile.

