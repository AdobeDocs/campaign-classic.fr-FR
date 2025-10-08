---
product: campaign
title: Prise en main des autorisations
description: Découvrez comment octroyer l’accès aux fonctionnalités Campaign
badge: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: 34f875f583dd81c2229b66f3344f23965532e802
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 64%

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

>[!BEGINTABS]

>[!TAB Documentation sur les autorisations]

Pour en savoir plus sur les **autorisations dans Adobe Campaign**, reportez-vous à la documentation de **[Campaign v8 (console)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=fr#_blank){target=_blank}**.

[![Image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=fr#_blank){target=_blank}


>[!TAB Gérer les autorisations sur les dossiers]

Pour savoir comment définir des **autorisations sur les dossiers**, reportez-vous à la documentation de **[Campaign v8 (console)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}**.

[![Image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}


>[!TAB  Authentification native ]

L’authentification native avec le nom d’utilisateur/mot de passe est toujours disponible dans Campaign v7. Toutefois, pour renforcer la sécurité et le processus d’authentification, Adobe Campaign recommande vivement de [migrer le mode d’authentification de l’utilisateur final](../../technotes/using/ac-ims.md) de l’authentification native par nom d’utilisateur/mot de passe vers Adobe Identity Management System (IMS). Notez que dans Campaign v8, la connexion avec un utilisateur/mot de passe (ou authentification native) n’est pas autorisée.

[![Image](../../assets/do-not-localize/learn-more-button.svg)](../../technotes/using/ac-ims.md)


>[!ENDTABS]



<!--
The permissions apply to operator profiles or operator groups.

They are completed by safety parameters linked to the operator's connection mode to Adobe Campaign. For more about security zones in [this page](../../installation/using/security-zones.md).

There are two types of permissions you can grant to a user:

* You can define groups of operators to which you attribute rights, then associate the operators with one or more groups. This enables you to reuse rights and make operator profiles more consistent. It also facilitates the management and maintenance of profiles. Group creation and management are presented in [this section](access-management-groups.md).

* You can attribute named rights directly to users, in some cases to overload the rights allocated via groups. These rights are presented in [this page](access-management-named-rights.md).

>[!NOTE]
>
> * Before starting defining permissions, Adobe recommends you to read the [Security configuration checklist](https://helpx.adobe.com/campaign/kb/acc-security.html).
> * To learn more about permissions, please refer to the detailed explanation on the [Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}.

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