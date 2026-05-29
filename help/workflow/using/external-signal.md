---
product: campaign
title: Signal externe
description: En savoir plus sur l’activité de workflow de signal externe
feature: Workflows
hide: true
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
TQID: https://experienceleague.adobe.com/2fWd7-VtAc2x-MQm-o5rpGmDsrn6rszSfZxjVDzleTw
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 171
ht-degree: 81%

---

# Signal externe{#external-signal}



L&#39;activité **Signal externe** permet de déclencher l&#39;exécution d&#39;un ensemble de tâches dans un workflow par programmation.

Lorsqu’une tâche « Signal externe » est activée, elle est suspendue indéfiniment ou jusqu’à la fin de la période spécifiée. Sa transition est activée par l’appel SOAP **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete).** Le paramètre **[!UICONTROL complete]** permet de terminer la tâche, de sorte qu’elle ne réagira pas aux appels suivants.

Reportez-vous à la documentation en ligne sur les appels SOAP pour plus d&#39;information sur la fonction PostEvent.

Vous pouvez configurer cette activité afin de définir des événements en cas d’absence de signal. Pour cela, modifiez l’activité et cliquez sur l’onglet **[!UICONTROL Expiration]**. Cliquez sur le bouton **[!UICONTROL Insérer]** pour créer et configurer un événement.

![](assets/edit_signal.png)

Le paramétrage des expirations est présenté dans la section [Expirations](defining-approvals.md).

Le champ **Délai** permet de spécifier un délai d&#39;expiration exprimé dans l&#39;unité de votre choix. Voir [Attente](wait.md).

Chaque ligne représente un type d&#39;expiration et correspond à une transition.

![](assets/external_sign_diag.png)
