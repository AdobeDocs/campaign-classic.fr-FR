---
product: campaign
title: À propos de la configuration initiale
description: À propos de la configuration initiale
feature: Installation, Configuration
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
badge-v7-prem: label="On-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f77ba178-0dfb-4a2e-b33b-971765d42298
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 100%

---

# Étapes clés de configuration et de déploiement de votre instance{#about-initial-configuration}



Une fois l’installation d’Adobe Campaign terminée, vous devez en effectuer la configuration pour garantir son bon fonctionnement, selon vos contraintes et votre architecture technique. Les étapes de configuration d’une instance Adobe Campaign sont présentées dans ce chapitre. Elles s’enchaînent dans l’ordre suivant :

1. Pour créer l’instance et la connexion associée, consultez la section [Création d’une instance et connexion](../../installation/using/creating-an-instance-and-logging-on.md).
1. Pour créer et configurer la base de données, consultez la section [Création et configuration de la base de données](../../installation/using/creating-and-configuring-the-database.md).
1. Pour configurer le serveur Adobe Campaign, consultez la section [Configuration du serveur Campaign](../../installation/using/configuring-campaign-server.md).
1. Pour déployer l’instance, consultez la section [Déploiement d’une instance](../../installation/using/deploying-an-instance.md).

La configuration de l’instance implique l’activation des processus (web, mta, wfserver, etc.) à démarrer sur le serveur et la configuration des modules pour l’envoi des e-mails, le tracking, etc. Pour chaque instance, les processus Adobe Campaign sont activés sur le serveur. Pour plus d’informations à ce sujet, consultez [cette section](../../installation/using/configuring-campaign-server.md#enabling-processes).

Des paramétrages complémentaires au niveau de chaque instance peuvent être nécessaires, selon les modules utilisés, votre architecture et vos besoins et afin d’optimiser le fonctionnement d’Adobe Campaign.
