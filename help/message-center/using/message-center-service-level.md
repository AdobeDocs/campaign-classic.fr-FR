---
title: Qualité de service Message Center
seo-title: Qualité de service Message Center
description: Qualité de service Message Center
seo-description: null
page-status-flag: never-activated
uuid: 8e363706-292b-40db-97bc-d41b41910556
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: reports
discoiquuid: e46a4e87-6c02-4b9c-bf6d-bb4e785e78fa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Qualité de service Message Center{#message-center-service-level}

Ce rapport affiche les statistiques de remise relatives aux messages transactionnels ainsi que la ventilation des erreurs. Vous pouvez cliquer sur un type d’erreur pour afficher ses détails. Ce rapport, destiné aux administrateurs techniques, est également accessible via l’ **[!UICONTROL Monitoring]** univers de l’instance de contrôle.

![](assets/mc_reports_1.png)

Dans ce rapport, vous pouvez choisir d’afficher les statistiques globales ou celles relatives à une instance d’exécution particulière.Vous pouvez également filtrer les données par canal et sur une période spécifique. Les indicateurs affichés dans la **[!UICONTROL Indicators over the period]** section sont calculés sur la période sélectionnée :

* **[!UICONTROL Incoming (throughput event/h)]** : nombre horaire moyen d’événements entrés dans la file d’attente du Centre de messages.
* **[!UICONTROL Incoming (event vol)]** : nombre d’événements entrés dans la file d’attente du Centre des messages.
* **[!UICONTROL Outgoing (throughput msg/h)]** : nombre horaire moyen d’événements de centre de messages sortants réussis (envoyés par une remise).
* **[!UICONTROL Outgoing (msg vol)]** : nombre d’événements Message Center sortants (envoyés par une remise).
* **[!UICONTROL Average sending time (seconds)]** : temps moyen passé dans le Centre de messages pour les événements traités avec succès. Le calcul prend en compte le temps de traitement et le temps d’envoi mta.
* **[!UICONTROL Error rate]** : nombre d’événements avec des erreurs par rapport au nombre d’événements entrés dans la file d’attente du Centre de messages. Les erreurs suivantes sont prises en compte : erreur de routage, événement arrivé à expiration (événement qui a été trop long dans la file d&#39;attente), erreur de remise, ignorée par la diffusion (quarantaine, etc.).

>[!NOTE]
>
>Les seuils d’avertissement (orange) et d’alerte (rouge) peuvent être configurés dans l’assistant de déploiement. Reportez-vous à [Surveillance des seuils](../../message-center/using/monitoring-thresholds.md).

