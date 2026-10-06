---
product: campaign
title: Niveau de service Message Center
description: En savoir plus sur le rapport Niveau de service Message Center
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: b8dc9891-84c8-445d-ad6a-d06048c8faaf
TQID: 'https://experienceleague.adobe.com/v9s-xydUk-4cNxNYSAj1HLCOOscZhpQDP-bSJt9mUzg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 100%
---
# Qualité de service Message Center {#message-center-service-level}



Ce rapport affiche les statistiques de diffusion relatives aux messages transactionnels, ainsi que la répartition des erreurs. Vous pouvez cliquer sur un type d’erreur pour en afficher les détails.

Ce rapport destiné aux administrateurs techniques est également accessible à partir de l&#39;onglet **[!UICONTROL Supervision]** de l&#39;instance de pilotage.

![](assets/mc_reports_1.png)

Dans ce rapport, vous pouvez choisir d’afficher les statistiques globales ou relatives à une instance d’exécution particulière. Vous pouvez également filtrer les données par canal et sur une période spécifique.

Les indicateurs affichés dans la section **[!UICONTROL Indicateurs sur la période]** sont calculés sur la période sélectionnée :

* **[!UICONTROL Entrant (débit evt/h)]** : moyenne horaire du nombre d&#39;événements entrés dans la file Message Center.
* **[!UICONTROL Entrant (volume evt)]** : nombre d&#39;événements entrés dans la file Message Center.
* **[!UICONTROL Sortant (débit msg/h)]** : moyenne horaire du nombre d&#39;événements sortant avec succès de Message Center (envoyés par une diffusion).
* **[!UICONTROL Sortant (volume msg)]** : nombre d&#39;événements sortant avec succès de Message Center (envoyés par une diffusion).
* **[!UICONTROL Temps moyen d’envoi (secondes)]** : temps moyen passé dans Message Center pour les événements traités avec succès. Le calcul prend en compte le temps de traitement et le temps d’envoi par le MTA.
* **[!UICONTROL Taux d’erreur]** : nombre d’événements avec des erreurs par rapport au nombre d’événements entrés dans la file d’attente Message Center. Les erreurs suivantes sont prises en compte : erreur de routage, événement expiré (événement resté trop longtemps dans la file d’attente), erreur de diffusion, ignoré par la diffusion (quarantaine, etc.).

>[!NOTE]
>
>Les seuils d&#39;avertissement (orange) et d&#39;alerte (rouge) des indicateurs sont paramétrables dans l&#39;assistant de déploiement. Voir [S](../../message-center/using/additional-configurations.md#monitoring-thresholds).
