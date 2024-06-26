---
product: campaign
title: À propos des Triggers Adobe Experience Cloud
description: Prise en main de la mise en œuvre des Triggers d’Adobe Experience Cloud
feature: Triggers
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: ht
source-wordcount: '398'
ht-degree: 100%

---

# Utilisation des triggers Campaign et Experience Cloud{#about-adobe-experience-triggers}

[!DNL Triggers] est une intégration entre Adobe Campaign et Adobe Analytics, qui utilise le pipeline. Le pipeline récupère les actions ou déclencheurs des utilisateurs de votre site web. Un abandon de panier est un exemple de déclencheur. Les déclencheurs sont traités dans Adobe Campaign pour envoyer des emails en temps quasi réel.

>[!CAUTION]
>
>Cette fonctionnalité ne fait pas partie des paramètres d’usine du produit. Pour cette implémentation, contactez votre représentant ou représentante Adobe, ou l’assistance clientèle. Vous pourrez alors suivre la procédure décrite dans cette [page](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] exécute des actions de marketing dans un court délai à la suite d’une action d’un utilisateur ou d’une utilisatrice. Le temps de réponse habituel est inférieur à une heure.

Il permet des intégrations plus agiles puisque la configuration est minimale et qu’un tiers n’est pas impliqué.
Il prend également en charge des volumes élevés de trafic sans affecter les performances des activités marketing. Par exemple, l’intégration peut traiter un million de déclencheurs par heure.

![](assets/do-not-localize/book.png)Découvrez comment [créer un déclencheur Experience Cloud](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html?lang=fr) et comment identifier, définir et surveiller les comportements critiques des consommateurs et consommatrices.

## Architecture de [!DNL Triggers]  {#triggers-architecture}

Le processus [!DNL pipelined] est toujours en cours d’exécution sur le serveur marketing d’Adobe Campaign. Il se connecte au pipeline, récupère les événements et les traite immédiatement.

![](assets/triggers_2.png)

Le processus [!DNL pipelined] se connecte à Experience Cloud à l’aide d’un service d’authentification et envoie une clé privée. Le service d’authentification renvoie un jeton. Le jeton est utilisé pour l’authentification lors de la récupération des événements.

## Conditions préalables {#adobe-io-prerequisites}

Avant de commencer cette implémentation, vérifiez que vous disposez des éléments suivants :

* un **identifiant d’organisation** valide : l’identifiant de l’organisation est l’identifiant unique dans Adobe Experience Cloud. Il est utilisé, entre autres, pour le service VisitorID et l’authentification unique (SSO) de l’IMS. [En savoir plus](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=fr)
* Un **accès développeur** à votre organisation. L’administrateur système de l’organisation doit suivre la procédure **Ajouter des développeurs à un profil de produit unique** présentée [dans cette page](https://helpx.adobe.com/fr/enterprise/using/manage-developers.html) pour fournir aux développeurs l’accès au profil du produit `Analytics - {tenantID}` Adobe Analytics associé aux Triggers.

## Étapes dʼimplémentation {#implement}

Pour implémenter Campaign et Experience Cloud Triggers, procédez comme suit :

1. Créez un project OAuth. [En savoir plus](oauth-technical-account.md#oauth-service)

1. Ajoutez vos informations d’identification de projet OAuth dans Adobe Campaign. [En savoir plus](oauth-technical-account.md#add-credentials)

1. Mettez à jour le type d’authentification du projet Developer Console dans le fichier de configuration **config-&lt; nom-instance >.xml** comme suit :

   ```
   <pipelined ... authType="imsJwtToken"  ... />
   ```

   Ensuite, exécutez `config -reload` et redémarrez [!DNL pipelined] pour que les modifications soient prises en compte.

