---
title: Accès aux campagnes marketing
seo-title: Accès aux campagnes marketing
description: Accès aux campagnes marketing
seo-description: null
page-status-flag: never-activated
uuid: a482be37-61bb-4588-9dfb-f9c3ee5a1930
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: about-marketing-campaigns
discoiquuid: 8e7eb53c-bbe2-4bd4-8581-c2a63a3dc84e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# Accès aux campagnes marketing{#accessing-marketing-campaigns}

Adobe Campaign vous permet de créer, paramétrer, exécuter et analyser les campagnes marketing. Toutes les opérations marketing peuvent être gérées depuis un centre de pilotage unifié.

## Notions de base sur l&#39;espace de travail {#workspace-basics}

### Page d&#39;accueil  {#home-page}

Une fois connecté à Adobe Campaign, vous accédez à la page d&#39;accueil.

![](assets/campaign_global_view.png)

Cliquez sur les liens de la barre de navigation pour accéder aux différents univers.

Les éléments de campagne se trouvent dans l’univers **[!UICONTROL Campagnes]** : vous trouverez ici un aperçu des programmes et campagnes marketing ainsi que de leurs sous-ensembles. Un programme de marketing est constitué de campagnes, composées de livraisons, de tâches, de ressources liées, etc. Dans le cadre de la gestion des campagnes marketing à l’aide de Campaign, les informations concernant les livraisons, les budgets, les réviseurs et les documents liés sont disponibles dans les campagnes.

Le bloc de navigation de l&#39;univers **[!UICONTROL Campagnes]** offre plusieurs entrées, selon les modules installés sur l&#39;instance. Par exemple, vous pouvez accéder aux éléments suivants :

* **Calendrier** de campagne : calendrier des plans, des programmes marketing, des livraisons et des campagnes. Reportez-vous au calendrier [](#campaign-calendar)des campagnes.
* **Opérations** : accès aux campagnes contenues dans l&#39;ensemble des programmes marketing.
* **Diffusions** : accès aux diffusions contenues dans les opérations.
* **Applications Web** : accès aux applications Web (formulaires, enquêtes, etc.).

>[!NOTE]
>
>L&#39;ergonomie générale de la console Adobe Campaign, ainsi que les permissions et les fonctionnalités de gestion des profils, sont présentées dans [cette section](../../platform/using/adobe-campaign-workspace.md).
>
>Les fonctionnalités relatives aux canaux et aux diffusions sont présentées dans [cette section](../../delivery/using/communication-channels.md).

### Calendrier des campagnes {#campaign-calendar}

Chaque opération s&#39;inscrit dans un programme, lui-même inscrit dans un plan. Les plans, programmes et leurs opérations sont accessibles à partir du menu **[!UICONTROL Calendrier des campagnes]** de l&#39;univers **Campagnes**.

Pour éditer un plan, un programme, une opération ou une diffusion, cliquez sur son nom dans le calendrier, puis sur le lien **[!UICONTROL Ouvrir...]**. L&#39;élément visé est alors affiché dans un nouvel onglet, comme dans l&#39;exemple ci-dessous :

![](assets/d_ncs_user_interface_hierar.png)

Vous pouvez filtrer les informations affichées dans le calendrier des campagnes. Pour cela, cliquez sur le lien **[!UICONTROL Filtrer]** et sélectionnez les critères de filtrage.

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>Lorsque vous filtrez sur une date, toutes les opérations dont la date de début est postérieure à la date indiquée et/ou dont la date de fin est antérieure à la date indiquée seront affichées. Les dates doivent être sélectionnées au travers des calendriers proposés à droite de chacun des champs.

Vous pouvez également utiliser le champ **[!UICONTROL Rechercher]** pour filtrer les éléments affichés.

Les icônes associées à chaque élément vous permettent de visualiser son statut : terminé, en cours, en édition, etc.

### Navigation dans un programme marketing {#browsing-in-a-marketing-program}

Grâce à Campaign, vous pouvez gérer un ensemble de programmes composés de différentes campagnes marketing. Chaque campagne (ou opération) contient des diffusions, et les traitements et ressources associés.

#### Naviguer dans un programme {#browsing-a-program}

Lorsque vous éditez un programme, utilisez les onglets présentés ci-dessous pour naviguer et le paramétrer.

* L&#39;onglet **Planning** affiche le calendrier du programme sur un mois, une semaine ou une journée selon que vous cliquez sur l&#39;un des onglets dans l&#39;en-tête du calendrier.

   Au besoin, vous pouvez créer une opération, un programme ou une tâche depuis cette vue.

   ![](assets/s_ncs_user_interface_campaign02.png)

* L&#39;onglet **Edition** vous permet de modifier le programme : son nom, ses dates de début et fin, son budget, ses documents associés, etc.

   ![](assets/s_ncs_user_interface_campaign05.png)

#### Parcourir les opérations {#browsing-campaigns}

Vous pouvez accéder aux opérations à partir du calendrier des campagnes, de l&#39;onglet **[!UICONTROL Planning]** du programme ou à partir de la liste des opérations.

1. Depuis le calendrier des campagnes, sélectionnez l&#39;opération à afficher puis cliquez sur le lien **[!UICONTROL Ouvrir]**.

   ![](assets/campaign_planning_edit_op.png)

   L&#39;opération est alors éditée dans un nouvel onglet, comme dans l&#39;exemple ci-dessous :

   ![](assets/campaign_op_edit.png)

1. Depuis l&#39;onglet **[!UICONTROL Planning]** du programme, le mode d&#39;édition est le même que depuis le calendrier des campagnes.
1. Depuis le lien **[!UICONTROL Opérations]** de l&#39;univers des **[!UICONTROL Campagnes]**, cliquez sur le nom de l&#39;opération à éditer.

   ![](assets/campaign_edit_from_list.png)

### Piloter une opération {#controlling-a-campaign}

#### Tableau de bord {#dashboard}

Pour chaque opération, les traitements, ressources et diffusions sont centralisés dans un écran unique - le tableau de bord - qui permet de gérer les actions marketing dans un mode collaboratif.

Le tableau de bord d&#39;une opération est utilisé comme une interface de pilotage. Il permet d&#39;accéder directement aux principales étapes de création et de gestion de l&#39;opération : diffusions, fichiers d&#39;extraction, notifications, budgets, etc.

![](assets/s_ncs_user_op_board_start_del.png)

Avec Adobe Campaign, vous pouvez mettre en place des processus collaboratifs pour la réalisation, mais aussi pour la validation des différentes étapes des campagnes marketing et communication : validation du budget, de la cible, du contenu, etc.

![](assets/s_ncs_user_op_board_validate.png)

>[!NOTE]
>
>The configuration of campaign templates is presented in [Campaign templates](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

#### Planning {#schedule}

Une opération centralise un ensemble de diffusions. Pour chaque opération, le planning propose une vue globale de tous ses composants : il permet de visualiser les tâches et diffusions et d&#39;y accéder facilement.

![](assets/campaign_planning_tab.png)

#### Forum {#forum}

Pour chaque opération, les intervenants peuvent échanger des messages via un forum dédié.

For more on this, refer to [Discussion forums](../../campaign/using/discussion-forums.md).

#### Rapports {#reports}

Le lien **[!UICONTROL Rapports]** permet d&#39;accéder aux rapports de l&#39;opération.

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>Les rapports sont présentés dans [cette section](../../reporting/using/about-adobe-campaign-reporting-tools.md).

#### Configuration {#configuration}

Les opérations sont créées à partir de modèles d&#39;opérations : vous pouvez paramétrer des modèles réutilisables pour lesquels certaines options sont sélectionnées et certains paramétrages seront déjà enregistrés. Pour chaque opération, les fonctionnalités suivantes sont proposées :

* Référence aux documents et aux ressources : vous pouvez associer des documents à la campagne (brève, rapport, images, etc.). Tous les formats de document sont pris en charge. Voir [Gestion des documents](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)associés.
* Définition des coûts : pour chaque campagne, Adobe Campaign vous permet de définir les entrées de coût et les structures de calcul des coûts qui peuvent être utilisées lors de la création de la campagne marketing.Par exemple : frais d&#39;impression, utilisation d&#39;une agence externe, location de chambres, etc. Voir [Définition des catégories](../../campaign/using/providers--stocks-and-budgets.md#defining-cost-categories)de coûts.
* Définition d&#39;objectifs : vous pouvez définir des objectifs à réaliser dans le cadre d&#39;une opération. Ces objectifs sont quantifiables, par exemple : nombre d&#39;inscrits à atteindre, chiffre d&#39;affaire à réaliser, etc. Ces informations sont ensuite exploitées dans les rapports sur les opérations.
* Managing seed addresses (for more on this, refer to [this section](../../delivery/using/about-seed-addresses.md)) and control groups (refer to [Defining a control group](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)).
* Gestion des approbations : vous pouvez sélectionner les traitements à approuver et, si nécessaire, sélectionner les opérateurs ou groupes d’opérateurs de révision. See [Checking and approving deliveries](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

>[!NOTE]
>
>Vous pouvez accéder aux paramétrages de l&#39;opération, et, au besoin, les modifier, à partir du lien **[!UICONTROL Paramètres avancés de l&#39;opération...]** disponible dans l&#39;onglet **[!UICONTROL Edition.]** Pour plus d’informations sur la définition de paramètres au niveau de la campagne afin que les remises héritent automatiquement des valeurs, voir [notre note technique](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Setparametersatthecampaignlevelsodeliveriesinheritvaluesautomatically).

## Utiliser l&#39;interface web {#using-the-web-interface-}

Vous pouvez accéder aux écrans de la console Adobe Campaign par l&#39;intermédiaire d&#39;un navigateur Internet pour visualiser l&#39;ensemble des opérations et leurs diffusions, les rapports et les informations relatives aux profils de votre base. Cet accès ne vous permet pas de créer des enregistrements. Vous pouvez cependant consulter et, selon les permissions associées à votre profil d&#39;opérateur, agir sur les données de la base. Ainsi, vous pouvez par exemple valider les contenus et ciblages de vos opérations, relancer ou interrompre une diffusion, etc.

1. Connectez-vous comme vous le faites habituellement via https://`<your instance>:<port>/view/home`.
1. Utilisez les menus pour accéder aux vues d&#39;ensemble.

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

Les validations (de la cible ou du contenu d&#39;une diffusion par exemple) peuvent être réalisées au travers d&#39;un accès Web.

![](assets/campaign_web_interface_validation.png)

Vous pouvez également utiliser le lien contenu dans les messages de notification. Pour plus d&#39;informations, reportez-vous à la section [Vérification et approbation des livraisons](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).
