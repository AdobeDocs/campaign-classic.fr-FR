---
product: campaign
title: Prise en main des autorisations
description: Découvrez comment octroyer l’accès aux fonctionnalités Campaign
badge: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: ht
source-wordcount: '309'
ht-degree: 100%

---

# Commencer avec les autorisations{#access-management}


>[!CAUTION]
>
>À partir de Campaign Classic v7.3.1, l’ensemble des opérateurs et opératrices doivent utiliser le [système de gestion des identités Adobe (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"} pour se connecter à Campaign.
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
> * Avant de commencer à définir les autorisations, Adobe vous recommande de lire la [Liste de contrôle relative à la configuration de la sécurité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html).
> * Pour en savoir plus sur les autorisations, consultez l’explication détaillée dans la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}.

<!--

Learn how to grant access and set up permissions in these sections:

* [Create operators](access-management-operators.md)

* [Define groups](access-management-groups.md)

* [Add Named rights](access-management-named-rights.md)

* [Manage Campaign folder access](access-management-folders.md)

* [Access rights matrix](access-management-named-rights.md#access-rights-matrix)


See also:

* [Manage permissions for workflows](../../workflow/using/managing-rights.md)
* [Manage permissions for distributed marketing](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [Manage permissions for the interaction module](../../interaction/using/operator-profiles.md)
* [Filter access to schemas](../../configuration/using/filtering-schemas.md)
* [Restricting PI view](../../configuration/using/restricting-pii-view.md)
-->