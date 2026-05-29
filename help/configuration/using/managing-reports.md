---
product: campaign
title: Gérer des rapports
description: Gérer des rapports
feature: Reporting, Configuration
role: Developer
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
TQID: https://experienceleague.adobe.com/LA4v5oODC9n5K2Ttox9SF7lwcGQOU7IDEvL1P4Sls-4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 174
ht-degree: 100%

---

# Gérer des rapports{#managing-reports}



Les rapports se basant sur un schéma spécifique aux personnes destinataires par défaut d’Adobe Campaign (nms:recipient ou schéma lié) doivent être redéveloppés afin de prendre en compte les données de la table personnalisée et de ses tables liées via le mapping de ciblage (consulter la section [Mapping de ciblage](../../configuration/using/target-mapping.md)).

Pour créer des rapports, consultez [cette section](../../reporting/using/about-reports-creation-in-campaign.md).

Dans certains cas, vous devrez également mettre en place de nouveaux cubes spécifiques à ces tables. Les cubes sont présentés dans [cette section](../../reporting/using/ac-cubes.md).

Les rapports concernés sont les suivants :

* **[!UICONTROL Suivi des propositions récentes]** (recentPropositions) : suivi en temps réél des propositions.
* **[!UICONTROL Répartition des ouvertures]** (opensByUserAgent) : répartition des ouvertures selon les logiciels utilisateur.
* **[!UICONTROL Statistiques des activités de partage]** (forwardActivities) : analyse des partages, ouvertures et abonnements par périodes de temps.
* **[!UICONTROL Indicateurs de tracking]** (mobileAppDeliveryFeedback) : indicateurs de tracking d&#39;une diffusion sur une application mobile.
* **[!UICONTROL Analyse des offres]** (offerAnalysis) : analyse des offres par date et canal.
* **[!UICONTROL Taux de réactivité]** (mobileAppReactivityRate) : taux de réactivité des dernières diffusions.
* **[!UICONTROL Répartition des abonnements]** (mobileAppDistribution) répartition des abonnements actifs par application mobile.
