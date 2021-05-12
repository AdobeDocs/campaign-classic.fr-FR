---
solution: Campaign Classic
product: campaign
title: A propos des profils
description: A propos des profils
feature: Profils et audiences
role: Business Practitioner, Data Architect
level: Beginner
exl-id: 54f1ad6c-54b0-4448-8c38-806dd75c1dae
translation-type: ht
source-git-commit: c733b68a06fba9bb24cd1c1995ffc99a1277be87
workflow-type: ht
source-wordcount: '936'
ht-degree: 100%

---

# Prise en main des profils{#about-profiles}

Les profils sont centralisés dans la base de données Adobe Campaign. Il existe de nombreux mécanismes permettant d’acquérir des profils et créer cette base de données : collecte en ligne par le biais de formulaires Web, importation manuelle ou automatique de fichiers texte, réplication avec des bases de données d’entreprises ou d’autres systèmes d’information. Adobe Campaign vous permet d’intégrer des données d’historique marketing, des informations d’achat, des préférences, des données CRM et des données d’informations personnelles pertinentes dans une vue consolidée afin d’effectuer une analyse et de prendre des mesures.

Un « **Profil** » désigne un enregistrement d’informations (par exemple : un enregistrement dans la table nmsRecipient ou une table externe contenant un identifiant de cookie, un identifiant client, un identifiant mobile ou d’autres informations relatives à un canal particulier) représentant un client final, un prospect ou un lead.

Dans Adobe Campaign, les destinataires sont les profils par défaut ciblés pour l’envoi de diffusions (emails, SMS, etc.). Les données de destinataire stockées dans la base de données permettent de filtrer la cible qui recevra une diffusion donnée et d’ajouter des données de personnalisation dans le contenu de votre diffusion. D’autres types de profils existent dans la base de données. Ils sont conçus pour différents usages. Par exemple, les profils de contrôle servent à tester vos diffusions avant leur envoi vers la cible finale.

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
>L’import de fichiers et de formulaires web est présenté dans la section [Imports et exports génériques](../../platform/using/get-started-data-import-export.md).

## Profils et cibles {#profiles-and-targets}

Le lien **[!UICONTROL Profils et cibles]** permet d&#39;afficher les destinataires stockés dans la base de données Adobe Campaign. Vous pouvez créer un nouveau destinataire, en éditer un existant et accéder à son profil. Pour plus d&#39;informations, consultez [cette page](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

Il permet également d&#39;accéder :

* listes - [En savoir plus](../../platform/using/creating-and-managing-lists.md)
* services d’inscriptions - [En savoir plus](../../delivery/using/managing-subscriptions.md)
* applications Web - [En savoir plus](../../web/using/about-web-applications.md)
* importations et exportations (traitements) - [En savoir plus](../../platform/using/about-generic-imports-exports.md)
* workflows de ciblage - [En savoir plus](../../workflow/using/building-a-workflow.md#implementation-steps-)

La page des destinataires permet d&#39;effectuer les opérations courantes sur les profils : édition, mise à jour, ajout, suppression, tri.

Pour des manipulations de profils plus avancées, il est nécessaire d&#39;éditer l&#39;arborescence Adobe Campaign pour accéder à des fonctionnalités avancées. Pour cela, cliquez sur le lien **[!UICONTROL Explorateur]** depuis la page d&#39;accueil d&#39;Adobe Campaign.

Par défaut, les destinataires sont stockés dans le nœud **[!UICONTROL Profils et Cibles > Destinataires]** de l&#39;arborescence. Vous pouvez créer des destinataires depuis cette vue, mais aussi :

* trier et filtrer les profils de la base de données - [En savoir plus](../../platform/using/filtering-options.md)
* déplacer, copier ou enlever des profils de la base de données - [En savoir plus](../../platform/using/managing-profiles.md)
* modifier un profil - [En savoir plus](../../platform/using/updating-data.md)
* exporter des destinataires - [En savoir plus](../../platform/using/exporting-and-importing-profiles.md)
* créer des groupes de destinataires - [En savoir plus](../../platform/using/creating-and-managing-lists.md)

Pour accéder aux fonctionnalités avancées et aux paramétrages, vous devez cliquer sur l’icône **[!UICONTROL Explorateur]**.

![](assets/d_ncs_user_interface01.png)

La mise en page générale de l’explorateur Adobe Campaign est présentée sur [cette page](../../platform/using/adobe-campaign-explorer.md).

>[!NOTE]
>
>Vous pouvez également afficher une vue avancée de cette liste à partir de l’arborescence Adobe Campaign, en cliquant sur le lien **[!UICONTROL Profils et cibles > Destinataires]**. L’affichage de cette liste peut être paramétré selon vos besoins. Vous pouvez ajouter ou supprimer des colonnes, définir leur ordre, trier les données, etc. La configuration de l’affichage des listes est décrite sur [cette page](../../platform/using/adobe-campaign-ui-lists.md).
>
>Vous pouvez également définir des vues de destinataires. Pour plus d’informations sur cette fonctionnalité, consultez [cette section](../../platform/using/access-management-folders.md).

## Profils actifs {#active-profiles}

Les profils actifs sont les profils qui sont comptabilisés à des fins de facturation.

Le nombre de profils actifs est disponible pour les **instances marketing** uniquement. Il n’est pas disponible pour les instances d’exécution, c’est-à-dire les instances MID (mid-sourcing) et RT (Message Center / messagerie en temps réel).

Si vous êtes hébergé sur AWS, vous pouvez également surveiller le nombre de profils actifs utilisés sur vos instances directement depuis le panneau de contrôle. Pour plus d’informations à ce sujet, consultez la [documentation du panneau de contrôle](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html?lang=fr).

La facturation ne concerne que les profils **actifs**. Un profil est considéré comme actif s’il a été ciblé ou s’il a reçu des communications au cours des 12 derniers mois via n’importe quel canal.

Les profils exclus lors de la préparation de la diffusion (règles de typologie, quarantaines) ne sont pas pris en compte. Un profil qui a été ciblé par plusieurs diffusions ne sera comptabilisé qu&#39;une seule fois.

>[!NOTE]
>
>Les canaux Facebook et Twitter ne sont pas pris en compte.

Vous pouvez obtenir un aperçu du **[!UICONTROL Nombre de profils actifs]** depuis le menu Campaign **[!UICONTROL Administration > Gestion de campagne > Mesures des clients]**. La comptabilisation est réalisée par le [workflow technique](../../workflow/using/about-technical-workflows.md) **[!UICONTROL Nombre de profils de facturation actifs]** (**[!UICONTROL billingActiveContactCount]**), qui s&#39;exécute tous les jours et ajoute les nouvelles données au rapport existant pour la période en cours dans le menu **[!UICONTROL Mesures des clients]**. Chaque période dure 12 mois.

## Tutoriel vidéo {#create-profiles-video}

Découvrez comment accéder aux données de profil, trier et filtrer les profils et créer et gérer manuellement des profils.

Cette vidéo explique également la conformité d’Adobe Campaign Classic au RGPD.

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

D’autres vidéos pratiques sur Campaign Classic sont disponibles [ici](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=fr).

**Voir aussi**

* [Gestion de la confidentialité dans Campaign](https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html)

* [Définir la population cible](../../delivery/using/define-the-right-audience.md)

* [Création de requêtes et de données de segment dans des workflows](../../workflow/using/targeting-data.md)

* [Sélectionner un mapping de ciblage](../../delivery/using/selecting-a-target-mapping.md)

* [Définir l&#39;audience : bonnes pratiques](../../delivery/using/define-the-right-audience.md)
