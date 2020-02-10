---
title: Signal externe
seo-title: Signal externe
description: Signal externe
seo-description: null
page-status-flag: never-activated
uuid: dbe6624a-70cf-4ac4-adfd-bc72db9bb3f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 3739593f-056c-4165-87ef-63c812bd3c43
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Signal externe{#external-signal}

L&#39;activité **Signal externe** permet de déclencher l&#39;exécution d&#39;un ensemble de tâches dans un workflow par programmation.

Lorsqu’une tâche &quot;Signal externe&quot; est activée, elle est suspendue indéfiniment ou jusqu’à la fin de la période spécifiée. Sa transition est activée par l’appel SOAP **PostEvent(sessionToken, workflowId, activité, transition, paramètres, complete).** Le **[!UICONTROL complete]** paramètre permet à la tâche d’être terminée, de sorte qu’elle ne réagira pas aux appels suivants.

Reportez-vous à la documentation en ligne sur les appels SOAP pour plus d&#39;information sur la fonction PostEvent.

Vous pouvez configurer cette activité afin de définir des événements si aucun signal n’est reçu. Pour ce faire, modifiez l’activité et cliquez sur l’ **[!UICONTROL Expiration]** onglet. Cliquez sur le **[!UICONTROL Insert]** bouton pour créer et configurer un événement.

![](assets/edit_signal.png)

The configuration of expirations is detailed in [Expirations](../../workflow/using/executing-a-workflow.md#expirations).

The **Delay** field lets you specify an expiration delay in the units of your choice. Voir [Attendre](../../workflow/using/wait.md).

Chaque ligne représente un type d&#39;expiration et correspond à une transition.

![](assets/external_sign_diag.png)

