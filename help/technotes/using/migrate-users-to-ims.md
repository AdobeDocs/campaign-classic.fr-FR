---
title: Migrer les opérateurs et opératrices de Campaign vers Adobe Identity Management System (IMS)
description: Découvrez comment migrer les opérateurs et opératrices Campaign vers Adobe Identity Management System (IMS).
exl-id: f01948c7-b523-492d-a4e8-67f4adde5fc5
source-git-commit: 02ecc0e6bb3bd361f512baeefc9e0f2271063387
workflow-type: tm+mt
source-wordcount: '1217'
ht-degree: 86%

---

# Migrer les opérateurs et opératrices de Campaign vers Adobe Identity Management System (IMS) {#migrate-users-to-ims}

Dans le cadre de ses efforts constants pour renforcer la sécurité et le processus d’authentification, Adobe Campaign recommande vivement de migrer le mode d’authentification de l’utilisateur ou de l’utilisatrice, et de passer de l’authentification native par nom d’utilisateur ou d’utilisatrice/mot de passe à Adobe Identity Management System (IMS). Tous les opérateurs doivent implémenter [Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"} pour se connecter à Campaign.

En savoir plus à propos de cette migration sur [cette page](ac-ims.md).

## Qu’est-ce qui a changé ? {#move-to-ims-changes}

Avec Campaign Classic, les utilisateurs et utilisatrices standard pouvaient déjà se connecter à la console cliente Adobe Campaign à l’aide de leur Adobe ID, via le système IMS (Adobe Identity Management System). Toutefois, les connexions par nom d’utilisateur ou d’utilisatrice/mot de passe sont toujours possibles. Elles ne seront plus autorisées dans Campaign v8.

En outre, dans le cadre des mesures visant à renforcer la sécurité et le processus d’authentification, l’application cliente Adobe Campaign appelle désormais les API Campaign directement à l’aide du jeton de compte technique IMS. La migration des opérateurs et opératrices techniques est présentée dans un article dédié, disponible sur [cette page](ims-migration.md).

Cette modification a déjà pris effet dans Campaign Classic v7 et sera **obligatoire** lors de la migration vers Campaign v8.

Adobe vous aide dans cet effort de migration. Vous trouverez le contexte détaillé et les instructions étape par étape dans l’article ci-dessous.

## Cela vous concerne-t-il ?{#migrate-ims-impacts}

Cette procédure s’applique à tous les utilisateurs et à toutes les utilisatrices de Campaign qui ne se connectent pas déjà à Campaign avec leur Adobe ID.

Si les opérateurs et opératrices de votre entreprise se connectent à la console cliente Campaign à l’aide de leur nom d’utilisateur ou d’utilisatrice/mot de passe (c’est-à-dire via une authentification native), cette étape vous concerne et vous devez migrer ces opérateurs et opératrices vers Adobe IMS comme décrit ci-dessous.

La migration vers [Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"} est un impératif de sécurité pour rendre vos environnements sécurisés et normalisés, car la plupart des autres solutions et applications Adobe Experience Cloud sont déjà sur IMS.

Cette modification s’applique à partir de Campaign Classic v7.4.1 (et des dernières [versions compatibles avec la migration IMS](ac-ims.md#ims-versions)). Elle est **obligatoire** pour migrer vers Adobe Campaign v8.

>[!IMPORTANT]
>
>**Impact sur l&#39;accès au Panneau de Contrôle**
>
>Une fois que vous avez migré vos utilisateurs vers IMS, sachez que tout profil de produit dans le Adobe Admin Console contenant le mot « admin » dans son nom (tel que « Administrateurs », « admin », « admins », « administrateur de validation », etc.) accordera automatiquement l’accès au Panneau de Contrôle Campaign. Panneau de Contrôle est un outil en libre-service qui permet d’apporter des modifications importantes aux instances de Campaign.
>
>Examinez attentivement les conventions de dénomination de votre profil de produit pour vous assurer que seuls les utilisateurs autorisés ont accès à Panneau de Contrôle. En savoir plus sur la gestion des autorisations de Panneau de Contrôle dans la documentation du Panneau de Contrôle [&#128279;](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html){target="_blank"}.


## Comment migrer les environnements hébergés et Managed Services ? {#ims-migration-procedure}

### Conditions préalables {#ims-migration-prerequisites}

Avant de commencer le processus de migration, contactez la personne responsable de la gestion de votre transition Adobe (pour les clientes et clients disposant d’un environnement Managed Services) ou l’assistance clientèle d’Adobe (pour les clientes et clients disposant d’un environnement hébergé) afin que les équipes techniques d’Adobe puissent migrer vos groupes d’opérateurs et d’opératrices existants et vos droits nommés vers Adobe Identity Management System (IMS).

### Principales étapes {#ims-migration-steps}

Les étapes clés de cette migration sont répertoriées ci-dessous :

1. Adobe met à niveau vos environnements vers Campaign v7.4.1 (ou une [version compatible avec la migration IMS](ac-ims.md#ims-versions)).
1. Après la mise à niveau, vous pouvez toujours créer de nouveaux utilisateurs et de nouvelles utilisatrices avec les deux méthodes, en tant qu’utilisateur natif ou utilisatrice native ou avec IMS.
1. Votre administrateur ou administratrice Campaign interne doit ajouter des adresses e-mails uniques à chaque utilisateur natif ou utilisatrice native sur la console cliente Campaign et envoyer une confirmation à la personne représentante d’Adobe ou à l’assistance clientèle d’Adobe une fois l’opération terminée.  Cette étape est détaillée dans [cette section](#ims-migration-id).
1. Contactez la personne représentante d’Adobe ou l’assistance clientèle d’Adobe pour sécuriser la date à laquelle Adobe procédera à la migration automatisée pour vos utilisateurs et utilisatrices non techniques (opérateurs et opératrices) et vos profils de produits. Cette étape nécessite une fenêtre d’une heure et n’entraîne aucune interruption de vos services.
1. Votre administrateur ou administratrice Campaign interne valide ces modifications et fournit une validation. Après cette migration, vous ne devez plus créer d’opérateur ou d’opératrice qui s’authentifierait avec son identifiant et son mot de passe.

Vous pouvez désormais migrer vos opérateurs et opératrices techniques vers Adobe Developer Console, comme décrit dans [cette note technique](ims-migration.md).

Une fois la migration terminée, confirmez la réussite de l’opération auprès de la personne responsable de votre transition Adobe (pour les utilisateurs et utilisatrices disposant d’un environnement Managed Services) ou via l’assistance clientèle d’Adobe (pour les clientes et clients disposant d’un environnement hébergé). Le processus de migration est alors terminé. Votre environnement est ensuite sécurisé et normalisé.


## Comment migrer des environnements hybrides et On-Premise ? {#ims-migration-procedure-on-prem}

Les étapes clés de cette migration sont répertoriées ci-dessous :

1. Mettez à niveau vos environnements vers Campaign v7.4.1 (ou une [version compatible avec la migration IMS](#ims-versions)).
1. Après la mise à niveau, vous pouvez toujours créer de nouveaux utilisateurs et de nouvelles utilisatrices avec les deux méthodes, en tant qu’utilisateur natif ou utilisatrice native ou avec IMS.
1. Votre administrateur ou administratrice Campaign interne doit configurer Adobe IMS comme décrit dans [cette section](../../integrations/using/configuring-ims.md).
1. Ajoutez ensuite des adresses e-mails uniques à tous les utilisateurs natifs et à toutes les utilisatrices natives sur la console cliente Campaign. Cette étape est détaillée dans [cette section](#ims-migration-id).
1. Créez des utilisateurs et des profils de produits dans Adobe Admin Console, comme décrit dans la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html?lang=fr){target="_blank"}.
1. Activez l’option **Se connecter avec un Adobe ID** pour tous les opérateurs et opératrices.
1. Implémentez Adobe IMS pour votre connexion, comme décrit dans [cette page](../../integrations/using/implementing-ims.md).

Vous pouvez désormais migrer vos opérateurs et opératrices techniques vers Adobe Developer Console, comme décrit dans [cette note technique](ims-migration.md).


## Forum aux questions {#ims-migration-faq}

### Comment créer des utilisateurs et utilisatrices après la migration ? {#ims-migration-native}

Adobe recommande de ne créer que des utilisateurs et utilisatrices IMS après la mise à niveau vers Campaign Classic v7.4.1 (ou une [version compatible avec la migration IMS](#ims-versions)).
À compter de Campaign v7.4.1, vous pouvez empêcher la création d’opérateurs et d’opératrices natifs en mettant à jour la configuration de votre instance, comme décrit sur [cette page](impact-ims-migration.md).

En tant qu’administrateur ou administratrice Campaign, vous pouvez accorder des autorisations aux utilisateurs et utilisatrices de votre entreprise via Adobe Admin Console et la console cliente Campaign. Les utilisateurs et utilisatrices peuvent se connecter à Adobe Campaign au moyen de leur Adobe ID. Découvrez comment configurer des autorisations avec IMS dans [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=fr){target="_blank"}.

### Comment ajouter des e-mails pour les personnes natives actuelles ? {#ims-migration-id}

En tant qu’administrateur ou administratrice Campaign, vous devez ajouter des ID d’e-mail à toutes les personnes natives à partir de la console cliente. Pour ce faire, suivez les étapes ci-après :

1. Connectez-vous à la console cliente et accédez à **Administration > Gestion des accès > Opérateurs**.
1. Sélectionnez l’opérateur ou l’opératrice à mettre à jour dans la liste.
1. Saisissez l’e-mail de l’opérateur ou de l’opératrice dans la section **Points de contact** du formulaire.
1. Enregistrez vos modifications.

<!--You can also import a CSV file to update all your operator profiles with their email.-->


### Comment se connecter à Campaign via IMS ? {#ims-migration-log}

Découvrez comment vous connecter à Campaign avec votre Adobe ID dans [cette section](../../integrations/using/implementing-ims.md).

### Y aura-t-il un temps d’arrêt pendant cette migration ? {#ims-migration-downtime}

Pour finaliser la migration des clientes et clients disposant d’un environnement hébergé ou Managed Services (migrer les personnes et les profils de produits), Adobe nécessite une fenêtre d’une heure sans temps d’arrêt sur aucune de vos instances (workflows, etc.).

Pendant ce délai, tous les utilisateurs et toutes les utilisatrices de Campaign doivent se déconnecter et se reconnecter avec leur Adobe ID une fois la migration vers IMS terminée.

Adobe recommande vivement que toutes les personnes soient déconnectées pendant la période de migration.

### Les utilisateurs et utilisatrices de mon entreprise utilisent déjà IMS. Dois-je encore effectuer la migration IMS ?{#ims-migration-needed}

Cette migration comporte deux aspects : la migration des utilisateurs finaux et utilisatrices finales et la migration des utilisateurs et utilisatrices techniques (utilisée dans les API de votre code personnalisé).

Si tous vos utilisateurs et utilisatrices (opérateurs et opératrices Campaign) utilisent IMS, vous devrez tout de même contacter la personne représentante d’Adobe/le service clientèle d’Adobe pour planifier la migration des profils de produits. Cependant, vous devez toujours migrer les utilisateurs et utilisatrices techniques que vous avez peut-être utilisés dans le code personnalisé. En savoir plus sur [cette page](ims-migration.md).

### Affichage du type d’authentification de vos opérateurs

Découvrez comment afficher le type d’authentification de vos opérateurs dans Campaign :

1. Dans l’**Explorateur**, accédez à **Administration** `>` **Gestion des accès** `>` **Opérateurs**.

1. Cliquez avec le bouton droit sur la ligne d’en-tête et sélectionnez le menu **Configurer la liste**.

   ![](assets/ims_2.png)

1. Ajoutez **Compte désactivé** et **Type d’authentification** comme **Colonnes de sortie**.

   ![](assets/ims_1.png)

Vous pouvez maintenant voir la liste de vos **Opérateurs** et leur **Type d’authentification**.

![](assets/ims_3.png)


>[!MORELIKETHIS]
>
>* [Migration des utilisateurs et des utilisatrices techniques vers Adobe Developer Console](ims-migration.md)
>* [Notes de mise à jour d’Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [En quoi consiste Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"}
