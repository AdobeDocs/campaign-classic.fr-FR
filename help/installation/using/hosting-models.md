---
solution: Campaign Classic
product: campaign
title: Modèles d'hébergement
description: Découvrez les modèles d’hébergement de Campaign
feature: Vue d’ensemble
role: Architecte
level: Débutant
translation-type: tm+mt
source-git-commit: 09bd634142f643206c38ac5f881302a5d489ecaf
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 51%

---


# Modèles d&#39;hébergement{#hosting-models}

Adobe Campaign propose trois modèles d’hébergement, ce qui offre la liberté de choisir le meilleur modèle ou les modèles qui répondent aux besoins de l’entreprise.

>[!NOTE]
>
>Pour les environnements hébergés par Adobe, les étapes principales d&#39;installation et de configuration ne peuvent être exécutées que par Adobe, comme la configuration du serveur et la personnalisation des fichiers de configuration d&#39;instance. Pour en savoir plus sur les principales différences entre les modes de déploiement, consultez [cette page](../../installation/using/capability-matrix.md).

## Managed Services / Hébergé

Adobe Campaign peut être déployé en tant que service géré : tous les composants d’Adobe Campaign, y compris l’interface utilisateur, le moteur de gestion de l’exécution et la base de données Campaign du client, sont entièrement hébergés par Adobe, y compris l’exécution des courriers électroniques, les pages miroir, le serveur de suivi et les composants Web externes, tels que le désabonnement du centre de pages/préférences et des landings page.

![](assets/deployment_hosted.png)

En tant que client hébergé, la plupart des étapes d&#39;installation et de configuration sont effectuées par Adobe. Vous pouvez accéder aux sections suivantes pour personnaliser votre mise en œuvre :

* Configurer les URL de suivi et de page miroir par marque. Pour les messages transactionnels, consultez [cette section](../../message-center/using/configuring-multibranding.md).
* Installation de la console cliente : consultez [cette section](../../installation/using/installing-the-client-console.md).
* Pour en savoir plus sur les outils de délivrabilité et les meilleures pratiques, consultez la [documentation détaillée](../../delivery/using/about-deliverability.md).
* Configuration des options de Campaign : consultez [cette section](../../installation/using/configuring-campaign-options.md).
* Configuration des connecteurs CRM : consultez [cette section](../../platform/using/crm-connectors.md).

## On-premise

Adobe Campaign peut être déployé on-premise : tous les composants d’Adobe Campaign, notamment l’interface utilisateur, le moteur de gestion de l’exécution et la base de données, résident sur site dans le centre de données du client. Dans ce modèle de déploiement, le client gère toutes les mises à jour et mises à niveau logicielles et matérielles. De plus, un administrateur de bases de données dédié doit réaliser des tâches de maintenance et d’optimisation afin d’assurer la gestion des instances Campaign.

![](assets/deployment_onpremise.png)

En tant que client On-premise, avant de commencer le déploiement de Campaign Classic, familiarisez-vous avec les recommandations et prérequis suivants:

* Lisez la [matrice de compatibilité](../../rn/using/compatibility-matrix.md) qui liste toutes les versions des systèmes et composants pris en charge pour Adobe Campaign.
* Selon votre environnement, lisez les [conditions préalables pour Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) et [conditions préalables pour Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md).
* Découvrez les recommandations relatives aux moteurs de base de données [dans cette section](../../installation/using/database.md).
* Vérifiez que les couches d&#39;accès à la base de données requises sont installées sur le serveur et accessibles à partir du compte Adobe Campaign. [En savoir plus](../../installation/using/application-server.md).
* Configurez vos réseaux lorsque certains processus doivent communiquer avec d&#39;autres ou accéder au réseau local et à Internet. Cela signifie que certains ports TCP doivent être ouverts pour ces processus. [En savoir ](../../installation/using/network-configuration.md) plus sur les exigences de configuration réseau.
* Consultez [Campaign Security and Privacy checklist](https://helpx.adobe.com/fr/campaign/kb/acc-security.html).
* Consultez les instructions générales pour estimer les besoins matériels en termes de déploiement sur site [dans cet article](https://helpx.adobe.com/fr/campaign/kb/hardware-sizing-guide.html).

## Hybride

Lorsqu’il est déployé en tant que modèle hybride, le logiciel de la solution Adobe Campaign réside sur site sur le site du client et la gestion de l’exécution est fournie en tant que service cloud par Adobe. L’instance de marketing Adobe Campaign est installée à l’intérieur du pare-feu d’un client. Les informations d’identification personnelle restent donc en interne et seules les données requises pour personnaliser les courriers électroniques sont envoyées au Cloud pour exécution par courrier électronique. L’instance d&#39;exécution, hébergée dans le Cloud, reçoit les requêtes de l’instance locale pour diffuser des courriers électroniques. Cette instance personnalise tous les e-mails et les envoie. Aucune donnée de quelque nature que ce soit n’est stockée de manière permanente dans le cloud.

![](assets/deployment_hybrid.png)

En tant que client hybride, la plupart des étapes d&#39;installation et de configuration sont effectuées par Adobe. Vous pouvez accéder aux sections suivantes pour personnaliser votre implémentation :

* Configuration des messages transactionnels : consultez [cette section](../../message-center/using/transactional-messaging-architecture.md).
* Configurez les URL de suivi et de page miroir par marque. Pour les messages transactionnels, consultez [cette section](../../message-center/using/configuring-multibranding.md).
* Installation de la console cliente : consultez [cette section](../../installation/using/installing-the-client-console.md).
* Installez les packages natifs : consultez [cette section](../../installation/using/installing-campaign-standard-packages.md).
* Délivrabilité : configuration des [règles MX](../../installation/using/email-deliverability.md#mx-configuration) et des [formats des emails](../../installation/using/email-deliverability.md#managing-email-formats). Pour en savoir plus sur les outils de délivrabilité et les meilleures pratiques, consultez la [documentation détaillée](../../delivery/using/about-deliverability.md).
* Configuration des options de Campaign : consultez [cette section](../../installation/using/configuring-campaign-options.md).
* Configuration d&#39;une base de données externe (Federated Data Access) : consultez [cette section](../../installation/using/about-fda.md).
* Configuration des connecteurs CRM : consultez [cette section](../../platform/using/crm-connectors.md).
* Pour en savoir plus sur les principes de déploiement Mid-sourcing, consultez [cette section](../../installation/using/mid-sourcing-deployment.md).
