---
solution: Campaign Classic
product: campaign
title: Prise en main des autorisations
description: Découvrez comment accorder l'accès aux fonctionnalités Campaign
audience: platform
content-type: reference
topic-tags: administration-basics
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 63%

---


# Prise en main des autorisations{#access-management}

Adobe Campaign vous permet de définir et gérer les permissions attribuées aux différents opérateurs. Les permissions sont un ensemble de droits et restrictions qui autorisent ou interdisent :

* l&#39;accès à certaines fonctionnalités (via les droits nommés),
* l&#39;accès à certains enregistrements,
* la création, modification et/ou suppression des enregistrements (actions, contacts, campagnes, groupes, etc.).

Les permissions s&#39;appliquent à des profils d&#39;opérateurs ou à des groupes d&#39;opérateurs.

Ils sont complétés par des paramètres de sécurité liés au mode de connexion de l&#39;opérateur à Adobe Campaign. Pour en savoir plus sur les zones de sécurité dans [cette page](../../installation/using/security-zones.md).

Vous pouvez accorder deux types de permissions à un utilisateur :

* Vous pouvez définir des groupes d&#39;opérateurs auxquels vous attribuez des droits, puis associer les opérateurs à un ou plusieurs groupes. Ce mode de fonctionnement permet de mutualiser les permissions et d&#39;uniformiser les profils des opérateurs. Il permet également de faciliter la gestion et la maintenance des profils. La création et la gestion des groupes sont présentées dans [cette section](access-management-groups.md).

* Vous pouvez attribuer directement des droits nommés aux utilisateurs, éventuellement pour surcharger les droits attribués via les groupes. Ces droits sont présentés dans [cette page](access-management-named-rights.md).

>[!NOTE]
>
>Avant de commencer à définir les permissions, Adobe vous recommande de lire la [Liste de contrôle relative à la configuration de la sécurité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html).

Découvrez comment accorder l’accès et configurer des autorisations dans ces sections :

* [Créer des opérateurs](access-management-operators.md)

* [Définir des groupes](access-management-groups.md)

* [Droits nommés d&#39;Ajoute](access-management-named-rights.md)

* [Gérer l’accès au dossier Campaign](access-management-folders.md)

* [Matrice des droits d&#39;accès](access-management-named-rights.md#access-rights-matrix)


Voir aussi :

* [Gérer les autorisations pour les workflows](../../workflow/using/managing-rights.md)
* [Gérer les autorisations pour le marketing distribué](../../campaign/using/about-distributed-marketing.md#operators-and-entities)
* [Gérer les autorisations pour le module d’interaction](../../interaction/using/operator-profiles.md)
* [Filtrer l&#39;accès aux schémas](../../configuration/using/filtering-schemas.md)
* [Limitation de la vue PI](../../configuration/using/restricting-pii-view.md)
