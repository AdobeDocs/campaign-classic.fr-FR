---
title: Modèles d'hébergement
description: Discover - Modèles d’hébergement Campaign
page-status-flag: never-activated
uuid: a9e035d9-326b-4e14-8f05-a22fe38d172b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 3175b9ab-e305-4f19-8267-d6172fa07a2a
translation-type: tm+mt
source-git-commit: 24521f77d6d13f8469869fdd8445b46a8d215dad
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 98%

---


# Modèles d&#39;hébergement{#hosting-models}

Adobe Campaign propose trois modèles d’hébergement, ce qui offre la liberté de choisir le meilleur modèle ou les modèles qui répondent aux besoins de l’entreprise.

>[!NOTE]
>
>Pour les environnements hébergés par Adobe, les étapes principales d&#39;installation et de configuration ne peuvent être exécutées que par Adobe, comme la configuration du serveur et la personnalisation des fichiers de configuration d&#39;instance. Pour en savoir plus sur les principales différences entre les modes de déploiement, consultez [cette page](../../installation/using/capability-matrix.md).

* **Services gérés (hébergé)**

   Adobe Campaign peut être déployé en tant que service géré : tous les composants d&#39;Adobe Campaign, y compris l&#39;interface utilisateur, le moteur de gestion de l&#39;exécution et la base de données Campaign du client sont hébergés intégralement par Adobe, ce qui inclut l&#39;exécution des emails, les pages miroir, le serveur de tracking et les composants web orientés vers l&#39;extérieur, tels que la page de désabonnement/le centre de préférences et les landing pages. Adobe alloue jusqu&#39;à trois instances dans le cloud : développement, test et production. Les étapes d&#39;installation et de configuration pour ce modèle d&#39;hébergement sont présentées [dans cette section](../../installation/using/hosted-model.md).

   ![](assets/deployment_hosted.png)

* **On-premise**

   Adobe Campaign peut être déployé on-premise : tous les composants d&#39;Adobe Campaign, notamment l&#39;interface utilisateur, le moteur de gestion de l&#39;exécution et la base de données, résident sur site dans le centre de données du client. Dans ce modèle de déploiement, le client gère toutes les mises à jour et mises à niveau logicielles et matérielles. De plus, un administrateur de bases de données dédié doit réaliser des tâches de maintenance et d&#39;optimisation afin d&#39;assurer la gestion des instances Campaign. [Cette section](../../installation/using/before-starting.md) présente des instructions de déploiement destinées aux clients On-premise.

   ![](assets/deployment_onpremise.png)

* **Hybride**

   Lorsqu&#39;il est déployé en tant que modèle hybride, le logiciel de la solution Adobe Campaign réside On-premise sur le site du client, et la gestion de l&#39;exécution est fournie par Adobe sous la forme d&#39;un service cloud. L&#39;instance marketing Adobe Campaign est installée à l&#39;intérieur du pare-feu du client, de façon à ce que les informations d&#39;identification personnelles (PII) restent en interne et à ce que seules les données nécessaires pour personnaliser les emails soient envoyées au cloud pour l&#39;exécution des emails. L&#39;instance d&#39;exécution, hébergée dans le cloud, reçoit les demandes de l&#39;instance On-premise afin de diffuser les emails. Cette instance personnalise tous les emails et les diffuse. Aucune donnée de ce type n&#39;est stockée de manière permanente dans le cloud. Les étapes d&#39;installation et de configuration pour ce modèle d&#39;hébergement sont présentées [dans cette section](../../installation/using/hybrid-model.md).

   ![](assets/deployment_hybrid.png)

