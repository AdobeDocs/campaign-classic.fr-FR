---
title: Cycle de vie d'un workflow
description: En savoir plus sur le cycle de vie d’un processus.
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 96%

---


# Cycle de vie d&#39;un workflow {#workflow-life-cycle}

Le cycle de vie d&#39;un workflow comporte trois grandes étapes.

* **En édition**

   C&#39;est la phase de conception initiale : lorsqu&#39;un nouveau workflow est créé, il est en état d&#39;édition. Un tel workflow n&#39;est pas encore pris en charge par le serveur, il peut donc être modifié sans risque.

* **Démarré**

   Une fois la phase de conception terminée, le workflow peut être démarré. Dans cette phase, l&#39;instance est prise en charge par le serveur, les tâches élémentaires sont exécutées. Le workflow peut encore être modifié, mais avec certaines précautions.

* **Terminé**

   Un workflow est terminé lorsqu&#39;il n&#39;a plus de tâche en cours ou lorsqu&#39;un opérateur a arrêté explicitement l&#39;instance.

Par exemple, dans le workflow ci-dessous, les activités **Début** et **Diffusion** sont entourées tandis que l&#39;activité **Validation** clignote.

![](assets/new-workflow-6.png)

Cela signifie que les deux premières activités ont été exécutées avec succès et que la validation est en cours, c&#39;est-à-dire que l&#39;activité est créée mais pas encore complétée.

Les caractères **574 - Ok** affichés au-dessus de la transition suivant l&#39;activité **Diffusion** signifient que la préparation de la diffusion a ciblé 574 destinataires et que l&#39;opération s&#39;est déroulée correctement. Ces informations, ajoutées sur les transitions au moment de l&#39;exécution, sont calculées par les activités traitant des données.

Le workflow est donc démarré et attend la décision d&#39;un opérateur du groupe spécifié dans l&#39;activité **Validation**. Les opérateurs du groupe ayant un email ou un numéro de téléphone mobile renseigné sont notifiés via ce média.

La gestion des opérateurs est présentée dans cette [section](../../platform/using/access-management.md).

Pour plus d&#39;informations sur la manière de surveiller vos workflows, voir [cette section](../../workflow/using/monitoring-workflow-execution.md).
