---
solution: Campaign Classic
product: campaign
title: Exécution de la diffusion
description: Exécution de la diffusion
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 5bc6c8a824929c6a61cf562fc961e5bdd1867837
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 97%

---


# Exécution de la diffusion{#delivery-execution}

## Envoi du message transactionnel {#transactional-message-send}

Concernant l’instance d’exécution, une fois que l’étape d’enrichissement a été effectuée et qu’un modèle de diffusion a été lié à l’événement, la diffusion est envoyée.

>[!NOTE]
>
>Le MTA donne la priorité au traitement des messages transactionnels par rapport à toute autre diffusion.

Toutes les diffusions sont regroupées dans le dossier **[!UICONTROL Administration > Exploitation > Message Center > Défaut > Diffusions]**.

![](assets/messagecenter_deliveries_execinstances_001.png)

Par défaut, elles sont classées dans un sous-dossier correspondant au mois d&#39;envoi. Ce classement peut être modifié dans les propriétés du modèle de message comme illustré ci-dessous.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Pour les installations hébergées ou hybrides, si vous avez effectué la mise à niveau vers le MTA amélioré d’Adobe Campaign, tous les messages transactionnels peuvent également être envoyés avec celui-ci pour optimiser la délivrabilité, le débit et la gestion des bounces. Tous les impacts sont identiques à ceux des messages marketing standard et sont présentés dans le document sur le [MTA amélioré d’Adobe Campaign](https://helpx.adobe.com/fr/campaign/kb/acc-campaign-enhanced-mta.html).

<!--## Transactional message monitoring {#transactional-message-monitoring}

To monitor your transactional messages, check the delivery logs. Accessing the delivery logs is presented in [this section](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history).

The transactional deliveries sent from the execution instance are synchronized back to the control instance as follows.

Let's take a [delivery template](../../message-center/using/introduction.md) labelled *Template_1*.

1. An event corresponding to *Template_1* is received on the execution instance.
1. The **Processing real time events** (rtEventsProcessing) workflow processes the event and searches for an existing delivery for the current month.

    >[!NOTE]
    >
    >If not found, a new delivery is created and the event is assigned to the new delivery.

1. The transactional email is sent and the delivery status changes to **[!UICONTROL Sent]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and updates the delivery logs on the control instance.
1. The control instance searches for an existing delivery for week 40 (2020-09-28_Template_1).

    >[!NOTE]
    >
    >If not found, a new delivery is created.

1. The week after, an inbound bounce is received for the event.
1. The status of the event changes to **[!UICONTROL Delivery failed]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and searches for a delivery for week 41 (2020-10-05_Template_1) to update the delivery logs. The delivery logs are then linked to a new delivery for the current week.

To summarize, the deliveries weekly accumulate the events based on the latest event update, and not on the event creation date.

Therefore, when extracting transactional messaging delivery logs from the control instance, the delivery ID associated with each delivery log ID changes every week.-->