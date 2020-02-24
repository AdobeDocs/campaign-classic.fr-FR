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

Ce rapport présente les statistiques d&#39;envoi des messages transactionnels ainsi que la répartition des erreurs. Vous pouvez cliquer sur un type d&#39;erreur pour afficher le détail. Ce rapport, destiné aux administrateurs techniques, est également accessible à partir de l&#39;univers **[!UICONTROL Supervision]** de l&#39;instance de pilotage.

![](assets/mc_reports_1.png)

Dans ce rapport, vous pouvez choisir d&#39;afficher les statistiques globales ou relatives à une instance d&#39;exécution en particulier. Il est également possible de filtrer les données par canal et sur une période spécifique. Les indicateurs affichés dans la partie **[!UICONTROL Indicateurs sur la période]** sont calculés sur la période sélectionnée :

* **[!UICONTROL Entrant (débit evt/h)]** : moyenne horaire du nombre d&#39;événements entrés dans la file Message Center.
* **[!UICONTROL Entrant (volume evt)]** : nombre d&#39;événements entrés dans la file Message Center.
* **[!UICONTROL Sortant (débit msg/h)]** : moyenne horaire du nombre d&#39;événements sortant avec succès de Message Center (envoyés par une diffusion).
* **[!UICONTROL Sortant (volume msg)]** : nombre d&#39;événements sortant avec succès de Message Center (envoyés par une diffusion).
* **[!UICONTROL Temps moyen d&#39;envoi (s)]** : temps moyen passé dans Message Center pour les événements traités avec succès. Ce calcul prend en compte le temps de traitement et le temps d&#39;envoi par les mta.
* **[!UICONTROL Taux d&#39;erreur]** : nombre d&#39;événements en erreur par rapport au nombre d&#39;événements entrés dans la file Message Center. Les erreurs suivantes sont prises en compte : erreur de routage, événement expiré (événement resté trop longtemps dans la file d&#39;attente), erreur de diffusion, ignoré par la diffusion (quarantaine, etc.).

>[!NOTE]
>
>Les seuils d’avertissement (orange) et d’alerte (rouge) peuvent être configurés dans l’assistant de déploiement. Reportez-vous à [Surveillance des seuils](../../message-center/using/monitoring-thresholds.md).

