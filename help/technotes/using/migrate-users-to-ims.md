---
title: Migrer les opérateurs et opératrices de Campaign vers Adobe Identity Management System (IMS)
description: Découvrez comment migrer les opérateurs et opératrices Campaign vers Adobe Identity Management System (IMS).
source-git-commit: 18166dd389847d6b844ed478e19c42e457abeb80
workflow-type: tm+mt
source-wordcount: '1153'
ht-degree: 40%

---

# Migrer les opérateurs et opératrices de Campaign vers Adobe Identity Management System (IMS) {#migrate-users-to-ims}

Dans le cadre de l’effort visant à renforcer la sécurité et le processus d’authentification, Adobe Campaign recommande vivement de migrer le mode d’authentification de l’utilisateur final de l’authentification native login/password vers Adobe Identity Management System (IMS). Tous les opérateurs doivent implémenter [Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"} pour vous connecter à Campaign.

Notez que dans Campaign v8, la connexion avec l’utilisateur/mot de passe (ou authentification native) ne sera plus autorisée. **Adobe recommande d&#39;effectuer cette migration dans Campaign v7.3.5 afin de pouvoir migrer en douceur vers Campaign v8.**

Cet article décrit les étapes à suivre pour migrer un opérateur ou une opératrice technique vers un compte technique sur Adobe Developer Console.

## Qu’est-ce qui a changé ?{#move-to-ims-changes}

Avec Campaign Classic, tous les utilisateurs standard peuvent déjà se connecter à la console cliente Adobe Campaign à l’aide de leur Adobe ID, via Adobe Identity Management System (IMS). Toutefois, les connexions utilisateur/mot de passe sont toujours disponibles. Cela ne sera plus autorisé avec Campaign v8.

En outre, dans le cadre des mesures visant à renforcer la sécurité et le processus d’authentification, l’application cliente Adobe Campaign appelle désormais les API Campaign directement à l’aide du jeton de compte technique IMS. La migration des opérateurs et opératrices techniques est présentée dans un article dédié, disponible sur [cette page](ims-migration.md).

Cette modification est déjà applicable dans Campaign Classic v7 et sera **mandatory** pour passer à Campaign v8.

## Cela vous concerne-t-il ?{#migrate-ims-impacts}

Cette procédure s&#39;applique à tous les utilisateurs de Campaign qui ne se connectent pas déjà à Campaign avec leur Adobe ID.

Si les opérateurs et opératrices de votre entreprise se connectent à la console cliente Campaign à l’aide de leur nom d’utilisateur/mot de passe (c’est-à-dire via une l’authentification native), vous êtes affecté et vous devez migrer ces opérateurs vers Adobe IMS, comme décrit ci-dessous.

La migration vers [Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"} est un impératif de sécurité visant à sécuriser et normaliser vos environnements, car la plupart des autres solutions et applications Adobe Experience Cloud sont déjà sur IMS.

## Comment migrer les environnements hébergés et Managed Services ? {#ims-migration-procedure}

### Conditions préalables {#ims-migration-prerequisites}

Avant de commencer le processus de migration, vous devez contacter votre gestionnaire de transition Adobe (pour les clients Managed Services) ou l’Adobe de l’assistance clientèle (pour les autres clients hébergés), afin que les équipes techniques d’Adobe puissent migrer vos groupes d’opérateurs existants et vos droits nommés vers Adobe Identity Management System (IMS).

### Principales étapes {#ims-migration-steps}

Les étapes clés de cette migration sont répertoriées ci-dessous :

1. Adobe met à niveau vos environnements vers Campaign v7.3.5.
1. Après la mise à niveau, vous pouvez toujours créer de nouveaux utilisateurs et de nouvelles utilisatrices avec les deux méthodes, en tant qu’utilisateur natif ou utilisatrice native ou avec IMS.
1. Votre administrateur Campaign interne doit ajouter des emails uniques à tous les utilisateurs natifs sur la console cliente Campaign et confirmer auprès de votre représentant Adobe/l’assistance clientèle que vous avez terminé.  Cette étape est détaillée dans [cette section](#ims-migration-id).
1. Contactez votre représentant d’Adobe/l’assistance clientèle pour sécuriser une date d’Adobe afin d’exécuter la migration automatisée pour vos utilisateurs (opérateurs) et profils de produits non techniques. Cette étape nécessite une fenêtre d’une heure sans temps d’arrêt pour l’un de vos services.
1. Votre administrateur ou administratrice Campaign interne valide ces modifications et fournit une validation. Après cette migration, vous ne devez plus créer d’opérateur ou d’opératrice qui s’authentifierait avec son identifiant et son mot de passe.

Vous pouvez également migrer votre ou vos opérateurs techniques vers la console Adobe Developer, comme décrit dans la section [cette technote](ims-migration.md).

Une fois la migration terminée, confirmez auprès de votre Gestionnaire de transition Adobe (pour les utilisateurs de Managed Services) ou de l’Adobe de l’assistance clientèle (pour les clients hébergés). Adobe marque ensuite la migration comme terminée. Votre environnement est ensuite sécurisé et normalisé.


## Comment migrer des environnements hybrides et On-Premise ? {#ims-migration-procedure-on-prem}

Les étapes clés de cette migration sont répertoriées ci-dessous :

1. Mettez à niveau vos environnements vers Campaign v7.3.5.
1. Après la mise à niveau, vous pouvez toujours créer de nouveaux utilisateurs et de nouvelles utilisatrices avec les deux méthodes, en tant qu’utilisateur natif ou utilisatrice native ou avec IMS.
1. Votre administrateur Campaign interne doit configurer Adobe IMS comme décrit dans la section [cette section](../../integrations/using/configuring-ims.md).
1. Ajoutez ensuite des emails uniques à tous les utilisateurs natifs sur la console cliente Campaign. Cette étape est détaillée dans [cette section](#ims-migration-id).
1. Créez des utilisateurs et des profils de produit dans Adobe Admin Console, comme décrit dans la section [Documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html){target="_blank"}.
1. Activez la variable **Connexion à Adobe ID** pour tous les opérateurs.
1. Implémentez Adobe IMS pour votre connexion, comme décrit dans la section [cette page](../../integrations/using/implementing-ims.md).

Vous pouvez également migrer votre ou vos opérateurs techniques vers la console Adobe Developer, comme décrit dans la section [cette technote](ims-migration.md).


## Questions fréquentes {#ims-migration-faq}

### Quand puis-je démarrer la migration ? {#ims-migration-start}

Une recommandation pour la migration vers [Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"} est de mettre à niveau votre environnement vers Campaign Classic v7.3.5.

Vous pouvez démarrer la migration IMS sur votre environnement intermédiaire, une fois qu’elle a été mise à niveau vers Campaign Classic v7.3.5, et planifier en conséquence l’environnement de production.

### Que se passe-t-il après l&#39;upgrade de build vers Campaign Classic v7.3.5 ? {#ims-migration-after-upgrade}

Une fois que vos environnements ont été mis à niveau vers Campaign Classic v7.3.5, vous pouvez lancer votre transition vers [Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"}.

### Quand la migration est-elle terminée ? {#ims-migration-end}

Une fois la migration des utilisateurs finaux et la migration des utilisateurs techniques vers Adobe Identity Management System (IMS) terminée, vous devez contacter votre représentant d’Adobe/le service clientèle afin que l’Adobe puisse marquer votre migration comme terminée.

### Comment créer des utlisateurs et utilisatrices après la migration ? {#ims-migration-native}

Adobe recommande de ne créer que les utilisateurs IMS après la mise à niveau vers Campaign Classic v7.3.5.

En tant qu’administrateur ou administratrice Campaign, vous pouvez accorder des autorisations aux utilisateurs et utilisatrices de votre entreprise via Adobe Admin Console et la console cliente Campaign. Les utilisateurs et utilisatrices peuvent se connecter à Adobe Campaign au moyen de leur Adobe ID. Découvrez comment configurer des autorisations avec IMS dans [Documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=fr){target="_blank"}.

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

Pour les clients hébergés et Managed Services, afin de finaliser la migration (migrer les utilisateurs et les profils de produits), l&#39;Adobe nécessite une fenêtre d&#39;une heure sans temps d&#39;arrêt sur aucune de vos instances (workflows, etc.).

Pendant ce délai, tous les utilisateurs et toutes les utilisatrices de Campaign doivent se déconnecter et se reconnecter avec leur Adobe ID une fois la migration vers IMS terminée.

Adobe recommande vivement que toutes les personnes soient déconnectées pendant la période de migration.

### Les utilisateurs de mon entreprise utilisent déjà IMS. Dois-je encore effectuer la migration IMS ?{#ims-migration-needed}

Cette migration comporte deux aspects : la migration des utilisateurs finaux (plus les profils de produit) et la migration des utilisateurs techniques (utilisée dans les API dans votre code personnalisé).

Si tous vos utilisateurs (opérateurs Campaign) utilisent IMS, vous devrez tout de même contacter votre représentant Adobe/le service clientèle pour planifier la migration des profils de produits. Vous devrez également migrer les utilisateurs techniques que vous avez peut-être utilisés dans le code personnalisé. En savoir plus sur [cette page](ims-migration.md).

## Liens utiles {#ims-useful-links}

* [Migration des utilisateurs et utilisatrices techniques vers Adobe Developer Console](ims-migration.md)
* [Notes de mise à jour d’Adobe Campaign v8](../../rn/using/latest-release.md)
* [Présentation d’Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"}
