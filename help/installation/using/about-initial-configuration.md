---
product: campaign
title: À propos de la configuration initiale
description: À propos de la configuration initiale
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f77ba178-0dfb-4a2e-b33b-971765d42298
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '167'
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
