---
product: campaign
title: Prérequis pour l’installation de Campaign sous Windows
description: Prérequis pour l’installation de Campaign sous Windows
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
badge-v7-prem: label="on-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: a7cf59cc-9260-4109-af4c-b2e2a9c999da
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 95%

---

# Prise en main de l’installation de Campaign sous Windows {#prerequisites-of-campaign-installation-in-windows}



La configuration technique et logicielle requise pour l&#39;installation d&#39;Adobe Campaign est présentée dans la [Matrice de compatibilité](../../rn/using/compatibility-matrix.md).

Le processus d’installation d’un serveur Adobe Campaign, pour un usage multi-instances, est décrit ci-après, dans la section [Installation du serveur](../../installation/using/installing-the-server.md).

Les étapes principales sont les suivantes :

1. installation du serveur applicatif, voir la section [Exécution du programme d’installation](../../installation/using/installing-the-server.md#executing-the-installation-program) ;
1. intégration avec un serveur web (facultatif, selon les composants déployés), voir la section [Configuration du serveur Web IIS](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

Une fois les étapes d’installation terminées, vous devez configurer les instances, la base de données et le serveur. Voir à ce sujet la section [À propos de la configuration initiale](../../installation/using/about-initial-configuration.md).

>[!NOTE]
>
>Lors du déploiement d&#39;Adobe Campaign dans un environnement Windows, les utilisateurs disposant des droits d&#39;accès nécessaires peuvent utiliser la syntaxe UNC (Universal/Uniform Naming Convention) pour les chemins d&#39;accès lors des manipulations de fichiers sur le réseau.
