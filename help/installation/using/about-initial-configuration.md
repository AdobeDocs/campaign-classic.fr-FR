---
product: campaign
title: À propos de la configuration initiale
description: À propos de la configuration initiale
feature: Installation, Configuration
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/fr/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f77ba178-0dfb-4a2e-b33b-971765d42298
TQID: 'https://experienceleague.adobe.com/rQT-wcpjGzyYfEV3thGlY0WD7Po-A08yD0pGMr13p7s'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: ht
source-wordcount: '185'
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
