---
solution: Campaign Classic
product: campaign
title: Signal externe
description: En savoir plus sur l’activité de workflow de signal externe
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '171'
ht-degree: 100%

---

# Signal externe{#external-signal}

L&#39;activité **Signal externe** permet de déclencher l&#39;exécution d&#39;un ensemble de tâches dans un workflow par programmation.

Lorsqu’une tâche « Signal externe » est activée, elle est suspendue indéfiniment ou jusqu’à la fin de la période spécifiée. Sa transition est activée par l’appel SOAP **PostEvent(sessionToken, workflowId, activité, transition, paramètres, terminer).** Le paramètre **[!UICONTROL complet]** permet à la tâche d’être terminée. Il ne réagira donc pas aux appels suivants.

Reportez-vous à la documentation en ligne sur les appels SOAP pour plus d&#39;information sur la fonction PostEvent.

Vous pouvez paramétrer cette activité afin de définir des événements en cas de non-réception de signal. Pour cela, éditez l&#39;activité et cliquez sur l&#39;onglet **[!UICONTROL Expiration]**. Cliquez sur le bouton **[!UICONTROL Ajouter]** pour créer et paramétrer un événement.

![](assets/edit_signal.png)

Le paramétrage des expirations est présenté dans la section [Expirations](../../workflow/using/defining-approvals.md).

Le champ **Délai** permet de spécifier un délai d&#39;expiration exprimé dans l&#39;unité de votre choix. Voir [Attente](../../workflow/using/wait.md).

Chaque ligne représente un type d&#39;expiration et correspond à une transition.

![](assets/external_sign_diag.png)
