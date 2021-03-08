---
solution: Campaign Classic
product: campaign
title: Temps traitement Message Center
description: Temps traitement Message Center
audience: message-center
content-type: reference
topic-tags: reports
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 87%

---


# Temps traitement Message Center{#message-center-processing-time}

Ce rapport présente les principaux indicateurs liés à la file d&#39;attente en temps réel. Ce rapport, destiné aux administrateurs techniques, est également accessible via l&#39;onglet **[!UICONTROL Surveillance]** de l&#39;instance de pilotage.

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
>Les seuils d&#39;avertissement (orange) et d&#39;alerte (rouge) des indicateurs sont paramétrables dans l&#39;assistant de déploiement d&#39;Adobe Campaign. Voir la section [Seuils de suivi](../../message-center/using/monitoring-thresholds.md).

