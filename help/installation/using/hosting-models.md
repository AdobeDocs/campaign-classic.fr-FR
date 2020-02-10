---
title: Modèles d'hébergement
seo-title: Modèles d'hébergement
description: Modèles d'hébergement
seo-description: null
page-status-flag: never-activated
uuid: a9e035d9-326b-4e14-8f05-a22fe38d172b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 3175b9ab-e305-4f19-8267-d6172fa07a2a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Modèles d&#39;hébergement{#hosting-models}

Adobe Campaign propose trois modèles d’hébergement, ce qui offre la liberté de choisir le meilleur modèle ou les modèles qui répondent aux besoins de l’entreprise.

>[!NOTE]
>
>Les principales étapes d’installation et de configuration ne peuvent être réalisées que par Adobe pour les déploiements hébergés par Adobe, par exemple pour configurer les fichiers de configuration de l’instance et du serveur. Pour plus d’informations sur les principales différences entre les modes de déploiement, reportez-vous à [cet article](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html). Si vous disposez d’un modèle hébergé ou hybride, consultez cette [section](../../installation/using/about-hybrid-and-hosted-models.md).

* **Services gérés (hébergé)**

   Adobe Campaign peut être déployé en tant que service géré : tous les composants d’Adobe Campaign, y compris l’interface utilisateur, le moteur de gestion de l’exécution et la base de données Campaign du client sont hébergés intégralement par Adobe, ce qui inclut l’exécution des emails, les pages miroir, le serveur de tracking et les composants web orientés vers l’extérieur, tels que la page de désabonnement/le centre de préférences et les landing pages. Adobe alloue jusqu’à trois instances dans le cloud : développement, test et production. Les étapes d’installation et de configuration pour ce modèle d’hébergement sont présentées dans cette [section](../../installation/using/hosted-model.md).

   ![](assets/deployment_hosted.png)

* **On-premise**

   Adobe Campaign peut être déployé on-premise : tous les composants d’Adobe Campaign, notamment l’interface utilisateur, le moteur de gestion de l’exécution et la base de données, résident sur site dans le centre de données du client. Dans ce modèle de déploiement, le client gère toutes les mises à jour et mises à niveau logicielles et matérielles. De plus, un administrateur de bases de données dédié doit réaliser des tâches de maintenance et d’optimisation afin d’assurer la gestion des instances Campaign.

   ![](assets/deployment_onpremise.png)

* **Hybride**

   Lorsqu’il est déployé en tant que modèle hybride, le logiciel de la solution Adobe Campaign réside on-premise sur le site du client, et la gestion de l’exécution est fournie par Adobe sous la forme d’un service cloud. L’instance marketing Adobe Campaign est installée à l’intérieur du pare-feu du client, de façon à ce que les informations d’identification personnelles (PII) restent en interne et à ce que seules les données nécessaires pour personnaliser les emails soient envoyées au cloud pour l’exécution des emails. L’instance d’exécution, hébergée dans le cloud, reçoit les demandes de l’instance on-premise afin de diffuser les emails. Cette instance personnalise tous les emails et les diffuse. Aucune donnée de ce type n’est stockée de manière permanente dans le cloud. Les étapes d’installation et de configuration pour ce modèle d’hébergement sont présentées dans cette [section](../../installation/using/hybrid-model.md).

   ![](assets/deployment_hybrid.png)

