---
title: Migrer les opérateurs et opératrices de Campaign vers Adobe Identity Management System (IMS)
description: Découvrez comment migrer les opérateurs et opératrices Campaign vers Adobe Identity Management System (IMS).
exl-id: f01948c7-b523-492d-a4e8-67f4adde5fc5
TQID: 'https://experienceleague.adobe.com/drpNkA9cj7Prid--GixHMQ48CO7ZC9qqX4w5fnTiD88'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
    internal-label: APIs
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 4bc1e76d129c6a6aa15b7e3915232043bd6f4286
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 87%
---
# Migrer les opérateurs et opératrices de Campaign vers Adobe Identity Management System (IMS) {#migrate-users-to-ims}

Dans le cadre de ses efforts constants pour renforcer la sécurité et le processus d’authentification, Adobe Campaign recommande vivement de migrer le mode d’authentification de l’utilisateur ou de l’utilisatrice, et de passer de l’authentification native par nom d’utilisateur ou d’utilisatrice/mot de passe à Adobe Identity Management System (IMS). Tous les opérateurs et opératrices doivent implémenter [Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"} pour se connecter à Campaign.

En savoir plus à propos de cette migration sur [cette page](ac-ims.md).

## Qu’est-ce qui a changé ? {#move-to-ims-changes}

Avec Campaign Classic, les utilisateurs et utilisatrices standard pouvaient déjà se connecter à la console cliente Adobe Campaign à l’aide de leur Adobe ID, via le système IMS (Adobe Identity Management System). Toutefois, les connexions par nom d’utilisateur ou d’utilisatrice/mot de passe sont toujours possibles. Elles ne seront plus autorisées dans Campaign v8.

En outre, dans le cadre des mesures visant à renforcer la sécurité et le processus d’authentification, l’application cliente Adobe Campaign appelle désormais les API Campaign directement à l’aide du jeton de compte technique IMS. La migration des opérateurs et opératrices techniques est présentée dans un article dédié, disponible sur [cette page](ims-migration.md).

Cette modification a déjà pris effet dans Campaign Classic v7 et sera **obligatoire** lors de la migration vers Campaign v8.

Adobe vous aide dans cet effort de migration. Vous trouverez le contexte détaillé et les instructions étape par étape dans l’article ci-dessous.

## Cela vous concerne-t-il ?{#migrate-ims-impacts}

Cette procédure s’applique à tous les utilisateurs et à toutes les utilisatrices de Campaign qui ne se connectent pas déjà à Campaign avec leur Adobe ID.

Si les opérateurs et opératrices de votre entreprise se connectent à la console cliente Campaign à l’aide de leur nom d’utilisateur ou d’utilisatrice/mot de passe (c’est-à-dire via une authentification native), cette étape vous concerne et vous devez migrer ces opérateurs et opératrices vers Adobe IMS comme décrit ci-dessous.

La migration vers [Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"} est un impératif de sécurité pour rendre vos environnements sécurisés et normalisés. En effet, la plupart des autres solutions et applications Adobe Experience Cloud sont déjà sur IMS.

Cette modification s’applique à partir de Campaign Classic v7.4.1 (et des dernières [versions compatibles avec la migration IMS](ac-ims.md#ims-versions)). Elle est **obligatoire** pour migrer vers Adobe Campaign v8.

>[!IMPORTANT]
>
>**Conséquences de l’accès au Panneau de contrôle**
>
>Une fois vos utilisateurs et utilisatrices migrés vers IMS, tout profil de produit dans Adobe Admin Console contenant le mot « admin » dans son nom (par exemple, « Administrateurs », « Administratrices », « admin », « admins », « admin d’approbation », etc.) accordera automatiquement l’accès au Panneau de Contrôle Campaign. Le Panneau de contrôle est un outil en libre-service qui permet d’apporter d’importantes modifications aux instances de Campaign.
>
>Examinez attentivement les conventions de nommage de votre profil de produit pour vous assurer que seules les personnes autorisées aient accès au Panneau de contrôle. En savoir plus sur la gestion des autorisations du Panneau de contrôle dans la [documentation sur le Panneau de contrôle](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=fr){target="_blank"}.


## Comment migrer des environnements hybrides et On-Premise ? {#ims-migration-procedure-on-prem}

Les étapes clés de cette migration sont répertoriées ci-dessous :

1. Mettez à niveau vos environnements vers Campaign v7.4.1 (ou une [version compatible avec la migration IMS](#ims-versions)).
1. Après la mise à niveau, vous pouvez toujours créer de nouveaux utilisateurs et de nouvelles utilisatrices avec les deux méthodes, en tant qu’utilisateur natif ou utilisatrice native ou avec IMS.
1. Votre administrateur ou administratrice Campaign interne doit configurer Adobe IMS comme décrit dans [cette section](../../integrations/using/configuring-ims.md).
1. Ajoutez ensuite des adresses e-mails uniques à tous les utilisateurs natifs et à toutes les utilisatrices natives sur la console cliente Campaign. Cette étape est détaillée dans [cette section](https://experienceleague.adobe.com/fr/docs/campaign/technotes-ac/tn-new/migrate-users-to-ims#ims-migration-id){target="_blank"} (documentation de Campaign v8).
1. Créez des utilisateurs, des utilisatrices et des profils de produits dans Adobe Admin Console, comme indiqué dans la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html?lang=fr){target="_blank"}.
1. Activez l’option **Se connecter avec un Adobe ID** pour tous les opérateurs et opératrices.
1. Implémentez Adobe IMS pour votre connexion, comme décrit dans [cette page](../../integrations/using/implementing-ims.md).

Vous pouvez désormais migrer vos opérateurs et opératrices techniques vers Adobe Developer Console, comme décrit dans [cette note technique](ims-migration.md).

## Forum aux questions {#ims-migration-faq}

Pour obtenir des réponses aux questions courantes sur la migration (création d’utilisateurs après la migration, ajout d’e-mails pour les utilisateurs natifs, connexion via IMS, temps d’arrêt, organisations qui utilisent déjà IMS, affichage du type d’authentification des opérateurs), reportez-vous à la note technique [Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/technotes-ac/tn-new/migrate-users-to-ims#ims-migration-faq){target=_blank} (documentation de Campaign v8).

>[!MORELIKETHIS]
>
>* [Migration des utilisateurs et des utilisatrices techniques vers Adobe Developer Console](ims-migration.md)
>* [Notes de mise à jour d’Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [Présentation d’Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"}
