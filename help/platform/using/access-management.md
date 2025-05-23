---
product: campaign
title: Prise en main des autorisations
description: Découvrez comment octroyer l’accès aux fonctionnalités Campaign
badge: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: 2759d65150299e4fa679ea986df8136cd9525370
workflow-type: ht
source-wordcount: '342'
ht-degree: 100%

---

# Commencer avec les autorisations{#access-management}


>[!CAUTION]
>
>Lors du démarrage de Campaign Classic v7.3.1, l’ensemble des opérateurs et opératrices doivent utiliser [Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"} pour se connecter à Campaign.
>
>Dans le cadre de ses efforts constants pour renforcer la sécurité et le processus d’authentification, Adobe Campaign recommande vivement de faire passer le mode d’authentification de l’ensemble des opérateurs et opératrices de l’authentification native par nom d’utilisateur/mot de passe à Adobe Identity Management System (IMS). Découvrez comment effectuer la migration de vos opérateurs et opératrices sur [cette page](../../technotes/using/migrate-users-to-ims.md).
> 
>À l’issue de cette migration, notez que la section suivante ne s’applique plus. Découvrez comment configurer des autorisations avec Adobe IMS dans la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=fr){target="_blank"}.


Adobe Campaign permet de définir et de gérer les droits attribués aux différents opérateurs. Ces ensembles de droits et de restrictions permettent d&#39;autoriser ou de refuser :

* l&#39;accès à certaines fonctionnalités (via les droits nommés),
* l&#39;accès à certains enregistrements,
* la création, modification et/ou suppression des enregistrements (actions, contacts, campagnes, groupes, etc.).

Les autorisations s&#39;appliquent à des profils d&#39;opérateurs ou à des groupes d&#39;opérateurs.

Elles sont complétées par des paramètres de sécurité liés au mode de connexion de l’opérateur à Adobe Campaign. En savoir plus sur les zones de sécurité dans [cette page](../../installation/using/security-zones.md).

Vous pouvez accorder deux types d&#39;autorisations à un utilisateur :

* Vous pouvez définir des groupes d&#39;opérateurs auxquels vous attribuez des droits, puis associer les opérateurs à un ou plusieurs groupes. Ce mode de fonctionnement permet de mutualiser les autorisations et d&#39;uniformiser les profils des opérateurs. Cela facilite également la gestion et la maintenance des profils. La création et la gestion des groupes sont présentées dans [cette section](access-management-groups.md).

* Vous pouvez directement attribuer des droits nommés aux utilisateurs, dans certains cas pour surcharger les droits attribués via les groupes. Ces droits sont présentés sur [cette page](access-management-named-rights.md).

>[!NOTE]
>
>Avant de commencer à définir les autorisations, Adobe vous recommande de lire la [Liste de contrôle relative à la configuration de la sécurité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html).

Découvrez comment octroyer l’accès et configurer des autorisations dans les sections suivantes :

* [Création d’opérateurs](access-management-operators.md)

* [Définition de groupes](access-management-groups.md)

* [Ajout de droits nommés](access-management-named-rights.md)

* [Gestion de l’accès aux dossiers Campaign](access-management-folders.md)

* [Matrice des droits d’accès](access-management-named-rights.md#access-rights-matrix)


Voir aussi :

* [Gestion des autorisations relatives aux workflows](../../workflow/using/managing-rights.md)
* [Gestion des autorisations pour le marketing distribué](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [Gestion des autorisations relatives au module d’interaction](../../interaction/using/operator-profiles.md)
* [Filtrage de l’accès aux schémas](../../configuration/using/filtering-schemas.md)
* [Restriction de l’affichage des PII](../../configuration/using/restricting-pii-view.md)
