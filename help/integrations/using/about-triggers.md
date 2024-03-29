---
product: campaign
title: À propos des Triggers Adobe Experience Cloud
description: Prise en main de la mise en œuvre des Triggers d’Adobe Experience Cloud
feature: Triggers
badge-v7: label="v7" type="Informative" tooltip="S’applique à Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="S’applique également à Campaign v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 100%

---

# Utilisation des triggers Campaign et Experience Cloud{#about-adobe-experience-triggers}

[!DNL Triggers] est une intégration entre Adobe Campaign et Adobe Analytics, qui utilise le pipeline. Le pipeline récupère les actions ou déclencheurs des utilisateurs de votre site web. Un abandon de panier est un exemple de déclencheur. Les déclencheurs sont traités dans Adobe Campaign pour envoyer des emails en temps quasi réel.

>[!CAUTION]
>
>Cette fonctionnalité ne fait pas partie des paramètres d’usine du produit. Pour cette implémentation, vous devez d’abord ouvrir un ticket auprès de l’assistance Adobe. Vous pourrez alors suivre la procédure décrite dans cette [page](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] exécute des actions marketing dans un délai court après l’action d’un utilisateur. Le temps de réponse habituel est inférieur à une heure.

Il permet des intégrations plus agiles puisque la configuration est minimale et qu’un tiers n’est pas impliqué.
Il prend également en charge des volumes élevés de trafic sans affecter les performances des activités marketing. Par exemple, l’intégration peut traiter un million de déclencheurs par heure.

![](assets/do-not-localize/book.png)Découvrez comment [créer un déclencheur Experience Cloud](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html?lang=fr) et comment identifier, définir et surveiller les comportements critiques des consommateurs et consommatrices.

## Architecture de [!DNL Triggers]  {#triggers-architecture}

Le processus [!DNL pipelined] est toujours en cours d’exécution sur le serveur marketing d’Adobe Campaign. Il se connecte au pipeline, récupère les événements et les traite immédiatement.

![](assets/triggers_2.png)

Le processus [!DNL pipelined] se connecte à Experience Cloud à l’aide d’un service d’authentification et envoie une clé privée. Le service d’authentification renvoie un jeton. Le jeton est utilisé pour l’authentification lors de la récupération des événements.

Pour plus d&#39;informations sur l&#39;authentification, consultez cette [page](../../integrations/using/configuring-adobe-io.md).
