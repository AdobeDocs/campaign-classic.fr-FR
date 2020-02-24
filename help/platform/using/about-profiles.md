---
title: A propos des profils
seo-title: A propos des profils
description: A propos des profils
seo-description: null
page-status-flag: never-activated
uuid: 9a3fcb58-a356-4eee-bc26-c64825de5f99
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: 5addada8-0185-488f-9825-83f60981c139
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0ce6e5277c32bc18c20dca62e5b276f654d1ace5

---


# A propos des profils{#about-profiles}

## Types de profils {#profile-types}

Adobe Campaign vous permet de gérer des profils dans toutes les étapes de leur cycle de vie : création, import, ciblage, tracking des actions, mise à jour, etc.

Un profil correspond à une entrée dans la base de données. Il contient toutes les informations nécessaires au ciblage, à la qualification et au tracking des individus.

Les profils peuvent être identifiés selon leur espace de stockage. Ainsi, un profil peut correspondre à : un destinataire, un visiteur, un opérateur, un abonné, un prospect, etc.

## Profils de destinataires {#recipient-profiles}

Les destinataires des diffusions sont stockés dans la base de données sous forme de profils regroupant les informations qui leur sont attachées : nom, prénom, coordonnées, abonnements, diffusions, etc. Lorsque vous créez des campagnes, vous pouvez définir la cible des diffusions à partir d&#39;une sélection parmi les profils présents dans la base, selon des critères simples ou avancés.

Vous pouvez également créer des campagnes visant des destinataires dont les profils ne sont pas stockés dans la base de données mais dans des fichiers. Il s&#39;agit alors de diffusions dites &quot;externes&quot;. Pour plus d&#39;informations sur ce type de diffusions, consultez [cette page](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

Les principales méthodes pour créer des profils de destinataires sont les suivantes :

* saisie directe dans les écrans de l&#39;interface graphique,
* import de fichiers de destinataires,
* collecte en ligne, via des formulaires web.

>[!NOTE]
>
>To find out how files and web forms are imported, refer to [Generic imports and exports](../../platform/using/generic-imports-and-exports.md).

## Profils et cibles {#profiles-and-targets}

Le lien **[!UICONTROL Profils et cibles]** permet d&#39;afficher les destinataires stockés dans la base de données Adobe Campaign. Vous pouvez créer un nouveau destinataire, en éditer un existant et accéder à son profil. Pour plus d&#39;informations, consultez [cette page](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

Il permet également d&#39;accéder :

* listes; voir [Création et gestion des listes](../../platform/using/creating-and-managing-lists.md),
* aux services d&#39;abonnements, voir à ce sujet [cette page](../../delivery/using/managing-subscriptions.md),
* aux applications web, voir à ce sujet [cette page](../../web/using/about-web-applications.md),
* importations et exportations (emplois); se référer aux importations et exportations [génériques](../../platform/using/generic-imports-and-exports.md),
* aux workflows de ciblage, voir à ce sujet [cette page](../../workflow/using/building-a-workflow.md#implementation-steps-).

La page des destinataires permet d&#39;effectuer les opérations courantes sur les profils : édition, mise à jour, ajout, suppression, tri.

Pour des manipulations de profils plus avancées, il est nécessaire d&#39;éditer l&#39;arborescence Adobe Campaign pour accéder à des fonctionnalités avancées. Pour cela, cliquez sur le lien **[!UICONTROL Explorateur]** depuis la page d&#39;accueil d&#39;Adobe Campaign.

Par défaut, les destinataires sont stockés dans le nœud **[!UICONTROL Profils et Cibles > Destinataires]** de l&#39;arborescence. Vous pouvez créer des destinataires depuis cette vue, mais aussi :

* sort and filter the profiles of the database; see [Filtering options](../../platform/using/filtering-options.md),
* move, copy or delete profiles from the database; see [Managing profiles](../../platform/using/managing-profiles.md),
* mettre à jour les profils; voir [Mise à jour des données](../../platform/using/updating-data.md),
* destinataires de l&#39;exportation; voir [Exportation et importation de profils](../../platform/using/exporting-and-importing-profiles.md),
* créer des groupes de destinataires ; voir [Création et gestion des listes](../../platform/using/creating-and-managing-lists.md).

Pour accéder aux fonctionnalités avancées et aux paramétrages, vous devez cliquer sur l&#39;icône **[!UICONTROL Explorateur]**.

![](assets/d_ncs_user_interface01.png)

La présentation générale de l’explorateur Adobe Campaign est présentée dans [Utilisation d’Adobe Campaign Explorer](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer).

>[!NOTE]
>
>You can also display an advanced view of this list from the Adobe Campaign tree by clicking the **[!UICONTROL Profiles and targets > Recipients]** link. The list display can be configured to suit your needs. You can add or delete columns, define column order, sort data, etc. La configuration de l’affichage de liste est décrite dans [Utilisation de l’explorateur](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer)Adobe Campaign.
>
>Vous pouvez également définir les vues des destinataires. Pour plus d’informations sur cette fonctionnalité, voir [Dossiers et vues](../../platform/using/access-management.md#folders-and-views).

## Profils actifs {#active-profiles}

Les profils actifs sont les profils qui sont comptabilisés à des fins de facturation.

Un “**Profil**” désigne un enregistrement d&#39;informations (par exemple : un enregistrement dans la table nmsRecipient ou une table externe contenant un identifiant de cookie, un identifiant client, un identifiant mobile ou d&#39;autres informations relatives à un canal particulier) représentant un client final ou un prospect.

La facturation ne concerne que les profils **actifs**. Un profil est considéré comme actif s&#39;il a été ciblé ou s&#39;il a reçu des communications au cours des 12 derniers mois via n&#39;importe quel canal.

>[!NOTE]
>
>Les canaux Facebook et Twitter ne sont pas prises en compte.

Vous pouvez obtenir un aperçu du **[!UICONTROL Nombre de profils actifs]** depuis le menu **[!UICONTROL Administration > Gestion de campagne > Mesures des clients]**.

La comptabilisation est réalisée par le [workflow technique](../../workflow/using/delivery.md) **[!UICONTROL Nombre de profils de facturation actifs]** (**[!UICONTROL billingActiveContactCount]**), qui s&#39;exécute tous les jours et ajoute les nouvelles données au rapport existant pour la période en cours dans le menu **[!UICONTROL Mesures des clients]**. Chaque période dure 12 mois.

Les profils exclus lors de la préparation de la diffusion (règles de typologie, quarantaines) ne sont pas pris en compte. Un profil qui a été ciblé par plusieurs diffusions ne sera comptabilisé qu&#39;une seule fois.
