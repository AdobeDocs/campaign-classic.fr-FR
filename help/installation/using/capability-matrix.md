---
title: Matrice des capacités Campaign sur site, hybride et hébergée
description: Découvrir les principales différences entre les déploiements hébergés et sur site
page-status-flag: never-activated
uuid: d1c786a1-2691-4966-9108-059004050464
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 582f7ac6-cebe-4b47-8730-bbc16fd6b1bd
translation-type: tm+mt
source-git-commit: c2e1b4cf7051b7f1b9d5f2db0d9f51a733ca2abc
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 24%

---


# Matrice des capacités par modèle d’hébergement {#capability-matrix-per-model}

Adobe Campaign Classic est fourni avec un ensemble de modules et d&#39;options. La disponibilité de ces modules et leur utilisation peuvent dépendre du type de déploiement de votre installation. Cet article présente quelques détails sur les principales différences de certaines fonctionnalités entre les déploiements entièrement hébergés (Managed Services) et sur site.

Cette page présente les principales différences entre les déploiements hébergés (Managed Services) et sur site. Les spécificités des déploiements hybrides dépendent des éléments hébergés par Adobe et hébergés dans vos locaux.

The different hosting models are introduced [in this section](../../installation/using/hosting-models.md).

## Matrice des capacités{#capability-matrix}

| Fonctionnalité | Hébergé | Hybride | On-premise | Détails |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configuration du serveur Campaign | À la demande | Disponible | Disponible | Le fichier[de configuration du](../../installation/using/the-server-configuration-file.md)serveur ne peut être modifié que par Adobe pour les clients hébergés. |
| Email BCC | À la demande | À la demande | Disponible | Pour les architectures hébergées et hybrides, contactez le responsable de votre compte pour activer le contrôle de compte par courrier électronique. Pour les installations sur site, suivez les instructions de la documentation. [En savoir plus](../../installation/using/email-archiving.md) |
| Gérer l&#39;instance d&#39;exécution du centre de messages | À la demande | À la demande | Disponible | Pour les déploiements hébergés, certains paramètres, tels que la création d’utilisateurs sur instance d&#39;exécution, ne peuvent être effectués que par Adobe. [En savoir plus](../../message-center/using/about-transactional-messaging.md) |
| Gestion de la plate-forme de Midsourcing | À la demande | À la demande | Disponible | Les plateformes de midsourcing hébergées par Adobe ne peuvent être configurées que par Adobe. |
| Rendu de la boîte de réception via Litmus | À la demande | À la demande | Disponible | Vous avez besoin d&#39;un compte Litmus. Vous devez contacter l’Adobe pour obtenir les détails nécessaires ou effectuer la configuration du rendu de la boîte de réception. [En savoir plus](../../delivery/using/inbox-rendering.md) |
| Intégration avec IMS (Adobe ID) | À la demande | À la demande | À la demande | L&#39;approvisionnement IMS est effectué par Adobe. Cette intégration est une condition préalable pour les intégrations Adobe Experience Cloud. [En savoir plus](../../integrations/using/about-adobe-id.md) |
| Chiffrement/déchiffrement des données pour les transferts de fichiers | À la demande | Disponible | Disponible | L’activation du prétraitement ou du post-traitement des fichiers nécessite l’installation de l’utilitaire nécessaire sur le serveur Adobe Campaign. Les clients hébergés peuvent utiliser le Panneau de Contrôle Campaign. [En savoir plus](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Zipping/Unzipped files | Disponible à la demande | Disponible | L’activation du prétraitement ou du post-traitement des fichiers nécessite l’installation de l’utilitaire nécessaire sur le serveur Adobe Campaign. Les clients hébergés peuvent utiliser le Panneau de Contrôle Campaign. [En savoir plus](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Délégation du nom de domaine | À la demande | À la demande | Non disponible | [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/domain-name-delegation.html) |
| Installation de SpamAssassin | À la demande | Disponible | Disponible | L&#39;installation de SpamAssassin nécessite la modification du fichier de configuration du serveur. [En savoir plus](../../delivery/using/spamassassin.md) |
| Accès aux rapports de délivrabilité | Disponible | À la demande | Disponible | Dans certains déploiements hybrides, les rapports de délivrabilité ne sont pas accessibles à partir de l’instance marketing. |
| Configuration de l’authentification LDAP | Non disponible | Disponible | Disponible | La configuration LDAP est uniquement possible pour les installations de type on-premise ou hybride. [En savoir plus](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

Adobe Campaign propose l’option **Federated Data Access** (FDA) afin d’exploiter des informations stockées dans une ou plusieurs bases de données externes : vous pouvez accéder à des données externes sans modifier la structure des données d’Adobe Campaign. [En savoir plus](../../platform/using/about-fda.md)

>[!CAUTION]
>
>Accessing an external database via FDA is only possible for on-premise or hybrid installations, except with the [Snowflake connector](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake).


**Voir aussi**

* [Matrice de compatibilité](../../rn/using/compatibility-matrix.md)
* [Notes de mise à jour](../../rn/using/latest-release.md)
* [Mise à niveau des Campaign Classic](../../rn/using/rn-overview.md)
* [Fonctionnalités obsolètes et supprimées](../../rn/using/deprecated-features.md)
* [Versions Gold Standard](../../rn/using/gold-standard.md)
* [Programme](https://helpx.adobe.com/fr/campaign/kb/gold-standard.html)Gold Standard.
