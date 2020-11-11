---
title: Workflows techniques
seo-title: Workflows techniques
description: Workflows techniques
seo-description: null
page-status-flag: never-activated
uuid: dfd1b180-86b5-4740-9bad-a0e210f433c5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 2e648e63-06d2-4e8f-9934-066a41d18eac
translation-type: ht
source-git-commit: f7527a2d9b76e34fbaa2c9471c44a7a1e7e074d7
workflow-type: ht
source-wordcount: '345'
ht-degree: 100%

---


# Workflows techniques{#technical-workflows}

Vous devez vous assurer que les workflows techniques de l&#39;instance de pilotage et des différentes instances d&#39;exécution sont bien créés et démarrés avant de procéder au déploiement des modèles de messages transactionnels.

Les différents workflows techniques associés aux messages transactionnels (Message Center) sont répartis entre l&#39;instance de pilotage et la ou les instances d&#39;exécution.

## Workflows de l&#39;instance de pilotage {#control-instance-workflows}

Sur l&#39;instance de pilotage, qu&#39;une ou plusieurs instances d&#39;exécution soient enregistrées, vous devez créer un workflow d&#39;archivage pour chaque compte externe d&#39;**[!UICONTROL instance d&#39;exécution Message Center]**. Cliquez sur le bouton **[!UICONTROL Créer le workflow d&#39;archivage]** pour créer et démarrer le processus.

![](assets/messagecenter_archiving_002.png)

Ces workflows sont ensuite accessibles à partir du dossier **Administration > Production > Message Center**. Une fois créés, les workflows d&#39;archivage sont automatiquement démarrés.

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

## Workflows de l&#39;instance d&#39;exécution {#execution-instance-workflows}

Sur la ou les instances d&#39;exécution, les workflows techniques des messages transactionnels sont accessibles depuis le dossier **Administration > Exploitation > Message Center**. Vous devez simplement les démarrer. La liste des workflows est la suivante :

* **[!UICONTROL Traitement des événements batch]** (nom interne : **[!UICONTROL batchEventsProcessing]**) : ce workflow permet de répartir les événements batch dans une file d&#39;attente avant qu&#39;ils ne soient associés à un modèle de message.
* **[!UICONTROL Traitement des événements temps réel]** (nom interne : **[!UICONTROL rtEventsProcessing]**) : ce workflow permet de répartir les événements temps réel dans une file d&#39;attente avant qu&#39;ils ne soient associés à un modèle de message.
* **[!UICONTROL Mise à jour du statut des événements]** (nom interne : **[!UICONTROL updateEventsStatus]**) : ce workflow permet d&#39;attribuer un statut à l&#39;événement.

   Les statuts d&#39;un événement sont les suivants :

   * **[!UICONTROL En attente]** : l&#39;événement se trouve dans la file d&#39;attente. Aucun modèle de message ne lui a encore été associé.
   * **[!UICONTROL En attente de diffusion]** : l&#39;événement est dans la file d&#39;attente, un modèle de message lui a été associé et il est en cours de traitement par la diffusion.
   * **[!UICONTROL Envoyé]** : ce statut est copié depuis les logs de diffusion. Il signifie que la diffusion a été envoyée.
   * **[!UICONTROL Ignoré par la diffusion]** : ce statut est copié depuis les logs de diffusion. Il signifie que la diffusion a été ignorée.
   * **[!UICONTROL Erreur de diffusion]** : ce statut est copié depuis les logs de diffusion. Il signifie que la diffusion a échoué.
   * **[!UICONTROL Evénement non pris en charge]** : l&#39;association de l&#39;événement à un modèle de message a échoué. L&#39;événement ne sera pas retraité.

