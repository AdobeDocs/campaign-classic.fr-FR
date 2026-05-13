---
product: campaign
title: Accès aux campagnes marketing
description: Accès aux campagnes marketing
role: User
feature: Campaigns, Cross Channel Orchestration
hide: true
exl-id: 1278bda1-f83c-4d38-8042-e6611755cf36
TQID: https://experienceleague.adobe.com/BSnBL3-RQ5UUgRFlU3RsNP7CLJrBHgjxHDLtvVvmtAg
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616a
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 1216
ht-degree: 82%

---

# Accès aux campagnes marketing{#accessing-marketing-campaigns}

Adobe Campaign vous permet de créer, configurer, exécuter et analyser des campagnes marketing. Toutes les campagnes marketing peuvent être gérées à partir d’un centre de contrôle unifié.

## Notions de base sur l&#39;espace de travail {#workspace-basics}

### Page d&#39;accueil {#home-page}

Dans Adobe Campaign, parcourez les différentes fonctionnalités à l&#39;aide des liens dans la barre de navigation.


![](assets/campaign_global_view.png)


Les éléments d&#39;une campagne se trouvent dans l&#39;onglet **[!UICONTROL Campagnes]** : vous y trouverez une vue d&#39;ensemble des programmes et des campagnes marketing ainsi que de leurs sous-ensembles. Un programme marketing est constitué de campagnes, elles-mêmes constituées de diffusions, de tâches, de ressources liées, etc. Dans le contexte de Marketing Campaign Management à l&#39;aide de Campaign, les informations concernant les diffusions, les budgets, les réviseurs et les documents liés sont disponibles dans chaque campagne.

Le bloc de **[!UICONTROL Navigation]** de l&#39;onglet **[!UICONTROL Campagnes]** offre diverses entrées en fonction des modules installés sur l&#39;instance. Vous pouvez, par exemple, accéder aux éléments suivants :

* **Calendrier des campagnes** : calendrier des plans, des programmes marketing, des diffusions et des campagnes. Voir à ce sujet la section [Calendrier des campagnes](#campaign-calendar).
* **Opérations** : accès aux campagnes contenues dans l&#39;ensemble des programmes marketing.
* **Diffusions** : accès aux diffusions contenues dans les opérations.
* **Applications Web** : accès aux applications web (formulaires, landing pages, etc.)

>[!NOTE]
>
>L’ergonomie générale de la console Adobe Campaign, ainsi que les autorisations et les fonctionnalités de gestion des profils, sont présentées dans [cette section](../../platform/using/adobe-campaign-workspace.md).
>
>Les fonctionnalités relatives aux canaux et aux diffusions sont présentées dans la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=fr){target="_blank"}.

### Calendrier des campagnes {#campaign-calendar}

Chaque campagne appartient à un programme qui appartient à son tour à un plan. Les plans, programmes et campagnes sont accessibles via le menu **[!UICONTROL Calendrier des campagnes]** dans l&#39;onglet **Campagnes**.

Pour éditer un plan, un programme, une campagne ou une diffusion, cliquez sur son nom dans le calendrier, puis sur le lien **[!UICONTROL Ouvrir...]**. L&#39;élément visé est alors affiché dans un nouvel onglet, comme dans l&#39;exemple ci-dessous :

![](assets/d_ncs_user_interface_hierar.png)

Vous pouvez filtrer les informations affichées dans le calendrier des campagnes. Pour cela, cliquez sur le lien **[!UICONTROL Filtrer]** et sélectionnez les critères de filtrage.

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>Lorsque vous filtrez sur une date, toutes les campagnes dont la date de début est postérieure à la date spécifiée et/ou dont la date de fin est antérieure à la date spécifiée sont affichées. Sélectionnez les dates à l&#39;aide des calendriers proposés à droite de chaque champ.

Vous pouvez également utiliser le champ **[!UICONTROL Rechercher]** pour filtrer les éléments affichés.

Les icônes associées à chaque élément vous permettent de visualiser son statut : terminé, en cours, en édition, etc.

### Navigation dans un programme marketing {#browsing-in-a-marketing-program}

Campaign permet de gérer un ensemble de programmes composés de différentes campagnes marketing. Chaque campagne contient des diffusions, ainsi que les processus et ressources associés.

#### Naviguer dans un programme {#browsing-a-program}

Lorsque vous éditez un programme, utilisez les onglets présentés ci-dessous pour naviguer et le paramétrer.

* L’onglet **Planning** affiche le calendrier du programme sur un mois, une semaine ou une journée selon l’onglet sur lequel vous avez cliqué dans l’en-tête du calendrier.

  Au besoin, vous pouvez créer une opération, un programme ou une tâche depuis cette vue.

  ![](assets/s_ncs_user_interface_campaign02.png)

* L’onglet **Modifier** vous permet de modifier le programme : son nom, ses dates de début et fin, son budget, ses documents associés, etc.

  ![](assets/s_ncs_user_interface_campaign05.png)

#### Parcourir les opérations {#browsing-campaigns}

Vous pouvez accéder aux opérations à partir du calendrier des campagnes, de l&#39;onglet **[!UICONTROL Planning]** du programme ou à partir de la liste des opérations.

1. Depuis le calendrier des campagnes, sélectionnez l&#39;opération à afficher puis cliquez sur le lien **[!UICONTROL Ouvrir]**.

   ![](assets/campaign_planning_edit_op.png)

   L&#39;opération est alors éditée dans un nouvel onglet, comme dans l&#39;exemple ci-dessous :

   ![](assets/campaign_op_edit.png)

1. Depuis l&#39;onglet **[!UICONTROL Planning]** du programme, le mode d&#39;édition est le même que depuis le calendrier des campagnes.
1. Depuis le lien **[!UICONTROL Opérations]** de l&#39;onglet **[!UICONTROL Campagnes]**, cliquez sur le nom de l&#39;opération à modifier.

   ![](assets/campaign_edit_from_list.png)

### Piloter une opération {#controlling-a-campaign}

#### Tableau de bord {#dashboard}

Pour chaque opération, les traitements, ressources et diffusions sont centralisés dans un écran unique - le tableau de bord - qui permet de gérer les actions marketing dans un mode collaboratif.

Le tableau de bord d’une campagne est utilisé comme interface de contrôle. Il accède directement aux principales étapes de création et de gestion des campagnes : diffusions, fichiers d&#39;extraction, notifications, budgets, etc.

![](assets/s_ncs_user_op_board_start_del.png)

Avec Adobe Campaign, vous pouvez mettre en place des processus collaboratifs pour la réalisation, mais aussi pour la validation des différentes étapes des campagnes marketing et communication : validation du budget, de la cible, du contenu, etc.

![](assets/s_ncs_user_op_board_validate.png)

>[!NOTE]
>
>Le paramétrage des modèles d&#39;opération est présenté dans la section [Modèles d&#39;opération](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

#### Planning {#schedule}

Une campagne centralise un ensemble de diffusions. Pour chaque campagne, le planning propose une vue globale de tous les composants : vous pouvez afficher les tâches et les diffusions, et y accéder facilement.

![](assets/campaign_planning_tab.png)

#### Forum {#forum}

Pour chaque campagne, les opérateurs et opératrices peuvent échanger des messages via un forum dédié.

Pour en savoir plus, consultez les [forums de discussion](../../mrm/using/discussion-forums.md).

#### Rapports {#reports}

Le lien **[!UICONTROL Rapports]** permet d&#39;accéder aux rapports de l&#39;opération.

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>Les rapports sont présentés dans [cette section](../../reporting/using/about-adobe-campaign-reporting-tools.md).

#### Configuration {#configuration}

Les campagnes sont créées à l’aide de modèles de campagne. Vous pouvez configurer des modèles réutilisables pour lesquels certaines options sont sélectionnées et d’autres paramètres sont déjà enregistrés. Pour chaque campagne, les fonctionnalités suivantes sont proposées :

* Référencement des [documents et ressources](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents) : vous pouvez associer des documents à la campagne (brief, rapport, images, etc.). Tous les formats de document sont pris en charge.
* Définition des coûts : pour chaque campagne, Adobe Campaign vous permet de définir des [postes de coûts et structures de calcul des coûts](../../campaign/using/providers-stocks-and-budgets.md#defining-cost-categories) qui pourront être utilisés lors de la création de la campagne marketing. Par exemple : coûts d&#39;impression, recours à une agence externe, location de salle.
* Définition d&#39;objectifs : vous pouvez définir des objectifs à réaliser dans le cadre d&#39;une campagne. Ces objectifs sont quantifiables, par exemple : nombre d&#39;abonnés à atteindre, chiffre d&#39;affaires à réaliser, etc. Ces informations sont ensuite exploitées dans les rapports sur les campagnes.
* Gestion des [adresses de contrôle](../../delivery/using/about-seed-addresses.md) et des [populations témoins](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)
* Gestion des validations : vous pouvez sélectionner les traitements qui feront l&#39;objet d&#39;une validation et éventuellement sélectionner les opérateurs ou groupes d&#39;opérateurs validants. [En savoir plus](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)

>[!NOTE]
>
>Pour accéder aux configurations de la campagne et y apporter des modifications, cliquez sur le lien **[!UICONTROL Paramètres avancés de la campagne…]** dans l’onglet **[!UICONTROL Edition]**.

## Utiliser l&#39;interface web {#using-the-web-interface-}

Vous pouvez accéder aux écrans de la console Adobe Campaign à partir d’un navigateur Internet afin de visualiser l’ensemble des campagnes et diffusions, ainsi que les rapports et informations relatifs aux profils de votre base de données. Cet accès ne permet pas la création d’enregistrements. En fonction des droits de l’opérateur ou de l’opératrice, vous pouvez afficher et/ou agir sur les données présentes dans la base de données. Vous pouvez par exemple approuver le contenu et le ciblage d’une campagne, relancer ou arrêter une diffusion, etc.

1. Connectez-vous comme vous le faites habituellement à l&#39;aide de l&#39;adresse https://`<your instance>:<port>/view/home`.
1. Utilisez les menus pour accéder aux vues d&#39;ensemble.

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

Outre la navigation dans les campagnes et leur affichage, vous pouvez effectuer les tâches suivantes :

* Surveillance de l’activité sur une instance
* Participation aux processus de validation, par exemple, validation ou refus du contenu d’une diffusion
* Exécution d’autres actions rapides, par exemple mis en pause d’un workflow
* Accès à toutes les fonctionnalités de rapport
* Participation aux discussions de forum

Ce tableau résume les actions que vous pouvez effectuer sur les campagnes à partir d’un navigateur :

| Page  | Action |
| --- | --- |
| Liste des campagnes, diffusions, offres, etc. | Suppression d’un élément de liste |
| Campagne | Annulation d’une campagne |
| Diffusion | Valider le contenu et la cible de la diffusion<br/>Envoyer le contenu de la diffusion<br/>Confirmer une diffusion<br/>Mettre en pause et arrêter une diffusion |
| Application web | Créer une application web<br/>Modifier le contenu et les propriétés de l’application<br/>Enregistrer le contenu de l’application en tant que modèle<br/>Publier l’application |
| Offre | Valider le contenu et l’éligibilité de l’offre<br/>Désactiver une offre en ligne |
| Tâche | Terminer une tâche<br/>Annuler une tâche |
| Ressource marketing | Approuver une ressource<br/>Verrouiller et déverrouiller une ressource |
| Kits de campagne | Soumettre un package pour validation<br/>Valider ou refuser un package<br/>Annuler un package |
| Commande de campagne | Créer une commande<br/>Accepter ou refuser une commande <!-- Je n'ai pas pu créer de campaign order pour vérifier cela. Peut-on accéder à ces fonctionnalités depuis l'accès web ? --> |
| Stock | Supprimer des données de stock |
| Simulation d’offres | Démarrer et arrêter une simulation |
| Workflow de ciblage | Démarrer, mettre en pause et arrêter un workflow |
| Rapport | Enregistrer les données actives dans l’historique du rapport |
| Forum | Ajouter une discussion<br/>Répondre à un message dans une discussion<br/>Suivre une discussion et s’en désabonner |

### Validations

Les validations (de la cible ou du contenu d&#39;une diffusion, par exemple) peuvent être réalisées par le biais d&#39;un accès web.

![](assets/campaign_web_interface_validation.png)

Vous pouvez également utiliser le lien contenu dans les messages de notification. Pour plus d&#39;informations, reportez-vous à la section [Contrôler et valider les diffusions](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).
