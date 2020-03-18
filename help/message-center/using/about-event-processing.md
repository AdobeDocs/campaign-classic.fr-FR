---
title: A propos du traitement des événements
seo-title: A propos du traitement des événements
description: A propos du traitement des événements
seo-description: null
page-status-flag: never-activated
uuid: 6c3e02b3-0d4d-4661-952a-e4915ca9ef92
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: a78c9986-7c49-47db-99a0-9f0949c4dee7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ceb5b2fdcd0dfca28412534ed3417367026f71d0

---


# A propos du traitement des événements{#about-event-processing}

Dans le cadre de la messagerie transactionnelle, un est généré par un système d&#39;information externe et est envoyé à   par l&#39;intermédiaire des méthodes **[!UICONTROL PushEvent]** et **[!UICONTROL PushEvents]** (reportez-vous à la description [du](../../message-center/using/event-description.md)du--). Il contient des données liées au  du, telles que son type (confirmation de commande ou création de compte sur un site Web, par exemple), son adresse électronique ou son numéro de téléphone mobile, ainsi que d’autres informations qui vous permettent d’enrichir et de personnaliser le  avant de vous. Il peut s’agir des coordonnées du client, de la langue du message ou du .

Exemple de données d&#39;un événement :

![](assets/messagecenter_events_request_001.png)

Le processus de traitement des événements des messages transactionnels est le suivant :

1. Collecte des événements,
1. Acheminement de l&#39;événement vers un modèle de message,
1. Enrichissement de l&#39;événement avec des données de personnalisation,
1. Exécution des diffusions,
1. Recyclage des événements dont la diffusion associée a échoué (cette étape peut être réalisée à l&#39;aide d&#39;un workflow Adobe Campaign).

## Etat des {#event-statuses}

L’historique ****, sous **[!UICONTROL Message Center]** > **[!UICONTROL Event history]** , regroupe tous les traités  en un seul et même . Ils peuvent être classés par  ou par **statut**. Ces états sont les suivants :

* **En attente** : l&#39;événement peut être :

   * un qui vient d&#39;être collecté et qui n&#39;a pas encore été traité. La **[!UICONTROL Number of errors]** colonne affiche la valeur 0. Le modèle de courrier électronique n’a pas encore été lié.
   * un traité mais dont la confirmation est erronée. La **[!UICONTROL Number of errors]** colonne affiche une valeur qui n’est pas 0. Pour savoir quand ce sera traité à nouveau, consultez la **[!UICONTROL Process requested on]** colonne.

* **En attente de diffusion** : l&#39;événement a été traité et le modèle de diffusion est associé. L&#39;email est en attente de diffusion. Le processus de diffusion classique est appliqué. Pour plus de détails, vous pouvez ouvrir la diffusion en question. Voir [Delivery](../../delivery/using/about-message-tracking.md).
* **Envoyé**, **Ignoré** et **Erreur de diffusion** : ces statuts de diffusion sont récupérés par le workflow **updateEventsStatus** qui collecte les statuts des diffusions. Pour plus de détails, vous pouvez ouvrir la diffusion concernée.
* **Evénement non pris en charge** : la phase de routage de Message Center a échoué. Par exemple, Adobe Campaign n&#39;a pas trouvé l&#39;email qui sert de modèle pour l&#39;événement.
* **Evénement expiré**: le nombre maximum de tentatives d&#39;envoi a été atteint. L&#39;événement est considéré comme nul.
