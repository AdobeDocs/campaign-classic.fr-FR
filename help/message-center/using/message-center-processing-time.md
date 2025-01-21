---
product: campaign
title: Temps de traitement Message Center
description: En savoir plus sur le rapport Temps de traitement Message Center
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 100%

---

# Temps de traitement Message Center {#message-center-processing-time}



Ce rapport présente les principaux indicateurs associés à la file d&#39;attente en temps réel.

Ce rapport destiné aux administrateurs techniques est également accessible à partir de l&#39;onglet **[!UICONTROL Supervision]** de l&#39;instance de pilotage.

![](assets/mc_reports_2.png)

Comme pour le rapport **[!UICONTROL Qualité de service Message Center]**, vous pouvez choisir d&#39;afficher les statistiques globales ou relatives à une instance d&#39;exécution particulière. Vous pouvez également filtrer les données par canal et sur une période spécifique.

Les indicateurs affichés dans la section **[!UICONTROL Indicateurs sur la période]** sont calculés sur la période sélectionnée :

* **[!UICONTROL Temps moyen dans la file (s)]** : temps moyen passé dans Message Center pour les événements traités avec succès. Seul le temps de traitement est pris en compte.
* **[!UICONTROL Temps moyen d&#39;envoi des messages (s)]** : temps moyen passé dans Message Center pour les événements traités avec succès. Seul le temps d&#39;envoi par les mta est pris en compte.
* **[!UICONTROL Temps moyen de traitement (s)]** : temps moyen passé dans Message Center pour les événements traités avec succès. Ce calcul prend en compte le temps de traitement et le temps d&#39;envoi par les mta.
* **[!UICONTROL Maximum des événements en file]** : nombre maximum d&#39;événements présents dans la file Message Center à un même moment.
* **[!UICONTROL Minimum des événements en file]** : nombre minimum d&#39;événements présents dans la file Message Center à un même moment.
* **[!UICONTROL Moyenne des événements en file]** : nombre moyen d&#39;événements présents dans la file Message Center à un même moment.

>[!NOTE]
>
>Les seuils d’avertissement (orange) et d’alerte (rouge) des indicateurs sont paramétrables dans l’assistant de déploiement d’Adobe Campaign. Voir [Seuils de suivi](../../message-center/using/additional-configurations.md#monitoring-thresholds).
