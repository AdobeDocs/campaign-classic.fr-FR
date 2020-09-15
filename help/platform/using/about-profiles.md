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
source-git-commit: 762a6ba3fdad9c30407bf807f2cd8076796f98c2
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 97%

---


# A propos des profils{#about-profiles}

Les profils (clients, prospects, abonnés aux newsletters, etc.) sont centralisés dans la base de données d&#39;Adobe Campaign. De multiples mécanismes d&#39;acquisition de profils et de constitution de cette base sont possibles : collecte en ligne via des formulaires web, imports manuels ou automatisés de fichiers texte, réplication avec bases de données ou autre système d&#39;information de l&#39;entreprise. Adobe Campaign vous permet d’intégrer des données d’historique marketing, des informations d’achat, des préférences, des données CRM et des données d’informations personnelles pertinentes dans une vue consolidée afin d’effectuer une analyse et de prendre des mesures.

Dans Adobe Campaign, les destinataires sont les profils par défaut ciblés pour l&#39;envoi des diffusions (emails, SMS, etc.). Grâce aux données de destinataires stockées dans la base de données, vous pourrez filtrer la cible qui recevra toute diffusion donnée et ajouter les données de personnalisation à votre contenu de diffusion. Il existe d&#39;autres types de profils dans la base de données qui sont conçus pour d&#39;autres utilisations. Par exemple, les profils d&#39;adresses de contrôle sont destinés à tester votre diffusions avant leur envoi à la cible finale.

![](assets/do-not-localize/how-to-video.png) [Comprendre le concept des profils en vidéo](#create-profiles-video)

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
>L’import de fichiers et de formulaires web est présenté dans la section [Imports et exports génériques](../../platform/using/generic-imports-and-exports.md).

## Profils et cibles {#profiles-and-targets}

Le lien **[!UICONTROL Profils et cibles]** permet d&#39;afficher les destinataires stockés dans la base de données Adobe Campaign. Vous pouvez créer un nouveau destinataire, en éditer un existant et accéder à son profil. Pour plus d&#39;informations, consultez [cette page](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

Il permet également d&#39;accéder :

* aux listes ; voir à ce sujet [Créer et gérer des listes](../../platform/using/creating-and-managing-lists.md),
* aux services d&#39;abonnements, voir à ce sujet [cette page](../../delivery/using/managing-subscriptions.md),
* aux applications web, voir à ce sujet [cette page](../../web/using/about-web-applications.md),
* aux imports et exports (traitements) ; voir à ce propos [Imports et exports génériques](../../platform/using/generic-imports-and-exports.md),
* aux workflows de ciblage, voir à ce sujet [cette page](../../workflow/using/building-a-workflow.md#implementation-steps-).

La page des destinataires permet d&#39;effectuer les opérations courantes sur les profils : édition, mise à jour, ajout, suppression, tri.

Pour des manipulations de profils plus avancées, il est nécessaire d&#39;éditer l&#39;arborescence Adobe Campaign pour accéder à des fonctionnalités avancées. Pour cela, cliquez sur le lien **[!UICONTROL Explorateur]** depuis la page d&#39;accueil d&#39;Adobe Campaign.

Par défaut, les destinataires sont stockés dans le nœud **[!UICONTROL Profils et Cibles > Destinataires]** de l&#39;arborescence. Vous pouvez créer des destinataires depuis cette vue, mais aussi :

* trier et filtrer les profils de la base ; voir [Options de filtrage](../../platform/using/filtering-options.md),
* déplacer, copier ou enlever des profils de la base ; voir [Gestion de profils](../../platform/using/managing-profiles.md),
* mettre à jour les profils ; voir [Mise à jour de données](../../platform/using/updating-data.md),
* exporter des destinataires ; voir [Exporter et importer des profils](../../platform/using/exporting-and-importing-profiles.md),
* créer des groupes de destinataires ; voir [Créer et gérer des listes](../../platform/using/creating-and-managing-lists.md).

Pour accéder aux fonctionnalités avancées et aux paramétrages, vous devez cliquer sur l&#39;icône **[!UICONTROL Explorateur]**.

![](assets/d_ncs_user_interface01.png)

La disposition générale de l’explorateur Adobe Campaign est présentée dans [Utiliser l’explorateur Adobe Campaign](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer).

>[!NOTE]
>
>Vous pouvez également afficher une vue avancée de cette liste à partir de l’arborescence Adobe Campaign, en cliquant sur le lien **[!UICONTROL Profils et cibles > Destinataires]**. L’affichage de cette liste peut être paramétré selon vos besoins. Vous pouvez ajouter ou supprimer des colonnes, définir leur ordre, trier les données, etc. Le paramétrage de l’affichage des listes est présentée dans [Utiliser l’explorateur Adobe Campaign](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer).
>
>Vous pouvez également définir des vues de destinataires. Pour plus d’informations sur cette fonctionnalité, voir [Les dossiers et les vues](../../platform/using/access-management.md#folders-and-views).

## Profils actifs {#active-profiles}

Les profils actifs sont les profils qui sont comptabilisés à des fins de facturation.

>[!NOTE]
>
>Si vous êtes hébergé sur AWS et que vous utilisez Campaign Classic à partir du build 8931, vous pouvez également surveiller le nombre de profils actifs utilisés sur vos instances directement depuis le panneau de contrôle. Pour plus d’informations à ce sujet, consultez la [documentation du Panneau de contrôle](https://docs.adobe.com/content/help/fr-FR/control-panel/using/performance-monitoring/active-profiles-monitoring.html).
>
>Notez que le nombre de profils Principaux est disponible pour les instances **** Marketing uniquement. Il n’est pas disponible pour les Instances d&#39;exécution, c’est-à-dire les instances MID (milieu de l’approvisionnement) et RT (centre de messages / messagerie en temps réel).

Un “**Profil**” désigne un enregistrement d&#39;informations (par exemple : un enregistrement dans la table nmsRecipient ou une table externe contenant un identifiant de cookie, un identifiant client, un identifiant mobile ou d&#39;autres informations relatives à un canal particulier) représentant un client final ou un prospect.

La facturation ne concerne que les profils **actifs**. Un profil est considéré comme actif s&#39;il a été ciblé ou s&#39;il a reçu des communications au cours des 12 derniers mois via n&#39;importe quel canal.

Les profils exclus lors de la préparation de la diffusion (règles de typologie, quarantaines) ne sont pas pris en compte. Un profil qui a été ciblé par plusieurs diffusions ne sera comptabilisé qu&#39;une seule fois.

>[!NOTE]
>
>Les canaux Facebook et Twitter ne sont pas pris en compte.

Vous pouvez obtenir un aperçu du **[!UICONTROL Nombre de profils actifs]** depuis le menu Campaign Standard **[!UICONTROL Administration > Gestion de campagne > Mesures des clients]**. La comptabilisation est réalisée par le [workflow technique](../../workflow/using/deliveries.md) **[!UICONTROL Nombre de profils de facturation actifs]** (**[!UICONTROL billingActiveContactCount]**), qui s&#39;exécute tous les jours et ajoute les nouvelles données au rapport existant pour la période en cours dans le menu **[!UICONTROL Mesures des clients]**. Chaque période dure 12 mois.

## Comment créer et gérer des profils {#create-profiles-video}

Découvrez comment accéder aux données de profil, trier et filtrer les profils et créer et gérer manuellement des profils.

Cette vidéo explique également la conformité d’Adobe Campaign Classic au RGPD.

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

**Voir aussi**

* [Gestion de la confidentialité dans Campaign](https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html)

* [Définir la population cible](../../delivery/using/define-the-right-audience.md)

* [Création de requêtes et de données de segment dans des workflows](../../workflow/using/targeting-data.md)

* [Sélectionner un mapping de ciblage](../../delivery/using/selecting-a-target-mapping.md)

* [Définir l&#39;audience : bonnes pratiques](../../delivery/using/define-the-right-audience.md)
