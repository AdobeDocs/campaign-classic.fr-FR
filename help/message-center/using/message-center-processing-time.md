---
title: Temps traitement Message Center
seo-title: Temps traitement Message Center
description: Temps traitement Message Center
seo-description: null
page-status-flag: never-activated
uuid: 06aca2c2-33c0-4839-bee4-fd838c49ce76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: reports
discoiquuid: d1f591d2-95e8-4d99-bc60-955c96b532eb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Temps traitement Message Center{#message-center-processing-time}

Ce rapport affiche les principaux indicateurs relatifs à la file d&#39;attente en temps réel. Ce rapport, destiné aux administrateurs techniques, est également accessible via l’ **[!UICONTROL Monitoring]** univers de l’instance de contrôle.

![](assets/mc_reports_2.png)

Tout comme pour le **[!UICONTROL Message Center service level]** rapport, vous pouvez choisir d’afficher les statistiques globales ou celles relatives à une instance d’exécution particulière. Vous pouvez également filtrer les données par canal et sur une période spécifique. Les indicateurs affichés dans la **[!UICONTROL Indicators over the period]** section sont calculés sur la période sélectionnée :

* **[!UICONTROL Average queuing time]** : durée moyenne de traitement des événements dans le Centre de messages. Seul le temps de traitement est pris en compte.
* **[!UICONTROL Average message sending time (s)]** : durée moyenne de traitement des événements dans le Centre de messages. Seul le délai de livraison du courrier est pris en compte.
* **[!UICONTROL Average processing time (s)]** : durée moyenne de traitement des événements dans le Centre de messages. Le calcul prend en compte le temps de traitement et le temps d’envoi mta.
* **[!UICONTROL Maximum number of queued events]** : nombre maximal d’événements présents dans la file d’attente du Centre de messages à un moment donné.
* **[!UICONTROL Minimum number of queued events]** : nombre minimum d’événements présents dans la file d’attente du Centre de messages à un moment donné.
* **[!UICONTROL Average number of queued events]** : nombre moyen d’événements présents dans la file d’attente du Centre de messages à un moment donné.

>[!NOTE]
>
>Les seuils d’avertissement (orange) et d’alerte (rouge) peuvent être configurés dans l’assistant de déploiement d’Adobe Campaign. Reportez-vous à [Surveillance des seuils](../../message-center/using/monitoring-thresholds.md).

