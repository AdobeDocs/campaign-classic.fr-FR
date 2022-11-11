---
product: campaign
title: Gestion des rapports
description: Gestion des rapports
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
source-git-commit: 1635366b9e1302acd3d8997312bf07d5c1a68982
workflow-type: ht
source-wordcount: '164'
ht-degree: 100%

---

# Gestion des rapports{#managing-reports}

![](../../assets/common.svg)

Les rapports se basant sur un schéma spécifique aux destinataires par défaut d&#39;Adobe Campaign (nms:recipient ou schéma lié) doivent être redéveloppés afin de prendre en compte les données de la table personnalisée et de ses tables liées via le mapping de ciblage (voir la section [Mapping de ciblage](../../configuration/using/target-mapping.md)).

Pour créer des rapports, voir [cette section](../../reporting/using/about-reports-creation-in-campaign.md).

Dans certains cas, vous devrez également mettre en place de nouveaux cubes spécifiques à ces tables. Les cubes sont présentés dans [cette section](../../reporting/using/ac-cubes.md).

Les rapports concernés sont les suivants :

* **[!UICONTROL Suivi des propositions récentes]** (recentPropositions) : suivi en temps réél des propositions.
* **[!UICONTROL Répartition des ouvertures]** (opensByUserAgent) : répartition des ouvertures selon les logiciels utilisateur.
* **[!UICONTROL Statistiques des activités de partage]** (forwardActivities) : analyse des partages, ouvertures et abonnements par périodes de temps.
* **[!UICONTROL Indicateurs de tracking]** (mobileAppDeliveryFeedback) : indicateurs de tracking d&#39;une diffusion sur une application mobile.
* **[!UICONTROL Analyse des offres]** (offerAnalysis) : analyse des offres par date et canal.
* **[!UICONTROL Taux de réactivité]** (mobileAppReactivityRate) : taux de réactivité des dernières diffusions.
* **[!UICONTROL Répartition des abonnements]** (mobileAppDistribution) répartition des abonnements actifs par application mobile.
