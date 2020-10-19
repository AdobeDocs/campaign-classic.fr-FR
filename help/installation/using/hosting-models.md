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
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 33%

---


# Modèles d&#39;hébergement{#hosting-models}

Adobe Campaign propose trois modèles d’hébergement, ce qui offre la liberté de choisir le meilleur modèle ou les modèles qui répondent aux besoins de l’entreprise.

>[!NOTE]
>
>Pour les environnements hébergés par Adobe, les étapes principales d&#39;installation et de configuration ne peuvent être exécutées que par Adobe, comme la configuration du serveur et la personnalisation des fichiers de configuration d&#39;instance. Pour en savoir plus sur les principales différences entre les modes de déploiement, consultez [cet article](https://helpx.adobe.com/fr/campaign/kb/acc-on-prem-vs-hosted.html).

* **Services gérés (hébergé)**

   Adobe Campaign can be deployed as a Managed Service: all components of Adobe Campaign, including the user interface, the execution management engine, and the customer&#39;s Campaign database are fully hosted by Adobe, including email execution, mirror pages, tracking server, and externally-facing web components such as unsubscribe page/preference center and landing pages. Adobe allocates up to three instances in the Cloud---Development, Test/Stage, and Production. The installation and configuration steps for this hosting model are presented [in this section](../../installation/using/hosted-model.md).

   ![](assets/deployment_hosted.png)

* **On-premise**

   Adobe Campaign peut être déployé on-premise : tous les composants d’Adobe Campaign, notamment l’interface utilisateur, le moteur de gestion de l’exécution et la base de données, résident sur site dans le centre de données du client. Dans ce modèle de déploiement, le client gère toutes les mises à jour et mises à niveau logicielles et matérielles. De plus, un administrateur de bases de données dédié doit réaliser des tâches de maintenance et d’optimisation afin d’assurer la gestion des instances Campaign. Cette section [](../../installation/using/before-starting.md)présente des instructions de déploiement destinées aux clients sur site.

   ![](assets/deployment_onpremise.png)

* **Hybride**

   When deployed as a hybrid model, the Adobe Campaign solution software resides on-premise at the customer site, and execution management is delivered as a cloud service by Adobe. Adobe Campaign marketing instance is installed inside a customer&#39;s firewall, so personally identifiable information (PII) remains in-house and only data required to personalize emails is sent to the Cloud for email execution. The execution instance, hosted in the Cloud, receives the requests from the On-Premise instance to deliver emails. This instance personalizes all the emails and delivers them. No data of any kind is permanently stored in the cloud. The installation and configuration steps for this hosting model are presented [in this section](../../installation/using/hybrid-model.md).

   ![](assets/deployment_hybrid.png)

