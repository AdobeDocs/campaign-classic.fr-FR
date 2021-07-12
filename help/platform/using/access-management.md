---
product: campaign
title: Prise en main des permissions
description: Découvrez comment octroyer l’accès aux fonctionnalités Campaign
feature: Gestion des accès
role: User, Admin
level: Beginner
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: 6c28e6cd78ce7a8ee5c0dc7e671de780787b9f57
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 100%

---

# Prise en main des autorisations{#access-management}

Adobe Campaign vous permet de définir et gérer les permissions attribuées aux différents opérateurs. Les permissions sont un ensemble de droits et restrictions qui autorisent ou interdisent :

* l&#39;accès à certaines fonctionnalités (via les droits nommés),
* l&#39;accès à certains enregistrements,
* la création, modification et/ou suppression des enregistrements (actions, contacts, campagnes, groupes, etc.).

Les permissions s&#39;appliquent à des profils d&#39;opérateurs ou à des groupes d&#39;opérateurs.

Elles sont complétées par des paramètres de sécurité liés au mode de connexion de l’opérateur à Adobe Campaign. En savoir plus sur les zones de sécurité dans [cette page](../../installation/using/security-zones.md).

Vous pouvez accorder deux types de permissions à un utilisateur :

* Vous pouvez définir des groupes d&#39;opérateurs auxquels vous attribuez des droits, puis associer les opérateurs à un ou plusieurs groupes. Ce mode de fonctionnement permet de mutualiser les permissions et d&#39;uniformiser les profils des opérateurs. Il permet également de faciliter la gestion et la maintenance des profils. La création et la gestion des groupes sont présentées dans [cette section](access-management-groups.md).

* Vous pouvez directement attribuer des droits nommés aux utilisateurs, dans certains cas pour surcharger les droits attribués via les groupes. Ces droits sont présentés sur [cette page](access-management-named-rights.md).

>[!NOTE]
>
>Avant de commencer à définir les permissions, Adobe vous recommande de lire la [Liste de contrôle relative à la configuration de la sécurité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html).

Découvrez comment octroyer l’accès et configurer des permissions dans les sections suivantes :

* [Création d’opérateurs](access-management-operators.md)

* [Définition de groupes](access-management-groups.md)

* [Ajout de droits nommés](access-management-named-rights.md)

* [Gestion de l’accès aux dossiers Campaign](access-management-folders.md)

* [Matrice des droits d’accès](access-management-named-rights.md#access-rights-matrix)


Voir aussi :

* [Gestion des permissions relatives aux workflows](../../workflow/using/managing-rights.md)
* [Gestion des permissions pour le marketing distribué](../../campaign/using/about-distributed-marketing.md#operators-and-entities)
* [Gestion des permissions relatives au module d’interaction](../../interaction/using/operator-profiles.md)
* [Filtrage de l’accès aux schémas](../../configuration/using/filtering-schemas.md)
* [Restriction de l’affichage des PII](../../configuration/using/restricting-pii-view.md)
