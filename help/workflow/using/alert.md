---
solution: Campaign Classic
product: campaign
title: Alerte
description: Alerte
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '84'
ht-degree: 100%

---


# Alerte{#alert}

Une activité de type **Alerte** envoie un message à un groupe d&#39;opérateurs. Son fonctionnement est le même qu&#39;une activité de type validation, mais ici, aucune réponse n&#39;est attendue.

![](assets/edit_alerte.png)

Une alerte n&#39;est pas persistante et n&#39;est donc pas visible depuis la console. Les opérateurs du groupe assigné doivent avoir une adresse de messagerie renseignée pour recevoir la notification. Le paramétrage de cette activité est similaire à celui d&#39;une **Validation**. Le modèle de diffusion par défaut utilisé pour notifier les opérateurs est &#39;alertAssignee&#39;.
