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

Ce rapport affiche les principaux indicateurs relatifs à la file d&#39;attente temps réel. Ce rapport, destiné aux administrateurs techniques, est également accessible à partir de l&#39;univers **[!UICONTROL Supervision]** de l&#39;instance de pilotage.

![](assets/mc_reports_2.png)

Comme pour le rapport **[!UICONTROL Qualité de service Message Center]**, vous pouvez choisir d&#39;afficher les statistiques globales ou relatives à une instance d&#39;exécution en particulier. Il est également possible de filtrer les données par canal et sur une période spécifique. Les indicateurs affichés dans la partie **[!UICONTROL Indicateurs sur la période]** sont calculés sur la période sélectionnée :

* **[!UICONTROL Temps moyen dans la file (s)]** : temps moyen passé dans Message Center pour les événements traités avec succès. Seul le temps de traitement est pris en compte.
* **[!UICONTROL Temps moyen d&#39;envoi des messages (s)]** : temps moyen passé dans Message Center pour les événements traités avec succès. Seul le temps d&#39;envoi par les mta est pris en compte.
* **[!UICONTROL Temps moyen de traitement (s)]** : temps moyen passé dans Message Center pour les événements traités avec succès. Ce calcul prend en compte le temps de traitement et le temps d&#39;envoi par les mta.
* **[!UICONTROL Maximum des événements en file]** : nombre maximum d&#39;événements présents dans la file Message Center à un même moment.
* **[!UICONTROL Minimum des événements en file]** : nombre minimum d&#39;événements présents dans la file Message Center à un même moment.
* **[!UICONTROL Moyenne des événements en file]** : nombre moyen d&#39;événements présents dans la file Message Center à un même moment.

>[!NOTE]
>
>Les seuils d’avertissement (orange) et d’alerte (rouge) peuvent être configurés dans l’assistant de déploiement d’Adobe Campaign. Reportez-vous à [Surveillance des seuils](../../message-center/using/monitoring-thresholds.md).

