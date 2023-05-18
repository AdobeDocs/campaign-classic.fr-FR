---
product: campaign
title: Matrice des fonctionnalités Campaign On-premise, hybride et hébergé
description: Découvrez les principales différences entre les déploiements hébergés et On-premise
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: a2c425a8-9bde-4259-9140-5ada5397ed5f
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Matrice des fonctionnalités par modèle{#capability-matrix-per-model}



Adobe Campaign Classic est fourni avec un ensemble de modules et d&#39;options. La disponibilité de ces modules et leur utilisation peuvent dépendre du type de déploiement de votre installation. Cet article présente des détails sur les principales différences de certaines fonctionnalités entre les déploiements entièrement hébergés (Managed Services) et On-premise.

Cette page présente les principales différences entre les déploiements hébergés (Managed Services) et On-premise. Les spécificités des déploiements hybrides dépendent des éléments hébergés par Adobe et hébergés dans vos locaux.

Les différents modèles d&#39;hébergement sont présentés [dans cette section](../../installation/using/hosting-models.md).

## Disponibilité par modèle de déploiement {#capability-matrix}

| Fonctionnalités | Hébergé | Hybride | On-premise | Détails |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configuration du serveur Campaign | À la demande | Disponible | Disponible | [En savoir plus](../../installation/using/the-server-configuration-file.md) |
| Email Cci | À la demande | À la demande | Disponible | [En savoir plus](../../installation/using/email-archiving.md) |
| Gérer l&#39;instance d&#39;exécution Message Center | À la demande | À la demande | Disponible | [En savoir plus](../../message-center/using/about-transactional-messaging.md) |
| Gestion de la plateforme de mid-sourcing | À la demande | À la demande | Disponible | [En savoir plus](../../installation/using/mid-sourcing-server.md) |
| Inbox Rendering via Litmus | À la demande | À la demande | Disponible | [En savoir plus](../../delivery/using/inbox-rendering.md) |
| Intégration avec IMS (Adobe ID) | À la demande | À la demande | À la demande | [En savoir plus](../../integrations/using/about-adobe-id.md) |
| Chiffrement/déchiffrement des données pour les transferts de fichiers | À la demande | Disponible | Disponible | [En savoir plus](../../platform/using/unzip-decrypt.md) |
| Compression/décompression de fichiers | À la demande | Disponible | Disponible | [En savoir plus](../../platform/using/unzip-decrypt.md) |
| Délégation du nom de domaine | À la demande | À la demande | Non disponible | [En savoir plus](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=fr) |
| Installation de SpamAssassin | À la demande | Disponible | Disponible | [En savoir plus](../../delivery/using/spamassassin.md) |
| Accès aux rapports de délivrabilité | Disponible | À la demande | Disponible | [En savoir plus](../../delivery/using/monitoring-deliverability.md) |
| Configuration de l&#39;identification LDAP | Non disponible | Disponible | Disponible | [En savoir plus](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

Adobe Campaign propose l&#39;option **Federated Data Access** (FDA) afin d&#39;exploiter des informations stockées dans une ou plusieurs bases de données externes : vous pouvez accéder à des données externes sans modifier la structure des données d&#39;Adobe Campaign. [En savoir plus](../../installation/using/about-fda.md)

>[!CAUTION]
>
>Les systèmes de base de données externes compatibles dépendent de votre modèle d’hébergement. En savoir plus sur la [Matrice de compatibilité de Campaign](../../rn/using/compatibility-matrix.md).

**Voir aussi**

* [Matrice de compatibilité](../../rn/using/compatibility-matrix.md)
* [Notes de mise à jour](../../rn/using/latest-release.md)
* [Mises à niveau de Campaign Classic](../../rn/using/rn-overview.md)
* [Fonctionnalités obsolètes et supprimées](../../rn/using/deprecated-features.md)
* [Versions [!DNL Gold Standard]](../../rn/using/gold-standard.md)
