---
product: campaign
title: Temps de traitement Message Center
description: En savoir plus sur le rapport Temps de traitement Message Center
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
TQID: https://experienceleague.adobe.com/nESBoEHC7YU0SO4yJ0rscDa3E-ePk6yNbPKzusER7C4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: ht
source-wordcount: 253
ht-degree: 100%

---

# Temps de traitement Message Center {#message-center-processing-time}



Ce rapport présente les principaux indicateurs associés à la file d’attente en temps réel.

Ce rapport destiné aux administrateurs techniques est également accessible à partir de l&#39;onglet **[!UICONTROL Supervision]** de l&#39;instance de pilotage.

![](assets/mc_reports_2.png)

Comme pour le rapport **[!UICONTROL Qualité de service Message Center]**, vous pouvez choisir d’afficher les statistiques globales ou relatives à une instance d’exécution particulière.Vous pouvez également filtrer les données par canal et sur une période spécifique.

Les indicateurs affichés dans la section **[!UICONTROL Indicateurs sur la période]** sont calculés sur la période sélectionnée :

* **[!UICONTROL Temps moyen dans la file (s)]** : temps moyen passé dans Message Center pour les événements traités avec succès.Seul le temps de traitement est pris en compte.
* **[!UICONTROL Temps moyen d’envoi des messages (s)]** : temps moyen passé dans Message Center pour les événements traités avec succès.Seul le temps de diffusion par le MTA est pris en compte.
* **[!UICONTROL Temps moyen de traitement (s)]** : temps moyen passé dans Message Center pour les événements traités avec succès.Le calcul prend en compte le temps de traitement et le temps d’envoi par le MTA.
* **[!UICONTROL Maximum des événements en file]** : nombre maximum d&#39;événements présents dans la file Message Center à un même moment.
* **[!UICONTROL Minimum des événements en file]** : nombre minimum d&#39;événements présents dans la file Message Center à un même moment.
* **[!UICONTROL Moyenne des événements en file]** : nombre moyen d&#39;événements présents dans la file Message Center à un même moment.

>[!NOTE]
>
>Les seuils d’avertissement (orange) et d’alerte (rouge) des indicateurs sont paramétrables dans l’assistant de déploiement d’Adobe Campaign. Voir [Seuils de suivi](../../message-center/using/additional-configurations.md#monitoring-thresholds).
