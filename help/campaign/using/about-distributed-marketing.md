---
title: A propos du marketing distribué
seo-title: A propos du marketing distribué
description: A propos du marketing distribué
seo-description: null
page-status-flag: never-activated
uuid: 7f7ece67-c644-4072-a06c-c5b49f3acb5d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 6d694f5c-1d1f-4686-b3bf-8697d919a0c8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# A propos du marketing distribué{#about-distributed-marketing}

## Introduction {#introduction}

Adobe Campaign propose une application de marketing **distribué** pour la mise en oeuvre de campagnes de coopération entre des entités centrales (siège social, départements marketing, etc.) et des entités locales (points de vente, agences régionales, etc.). Cette coopération est basée sur un espace de travail partagé appelé **[!UICONTROL list of campaign packages]**, où des modèles et instances de campagne créés de manière centralisée sont proposés aux entités locales.

L&#39;entité centrale propose aux entités locales des opérations auxquelles elles peuvent participer. Ces opérations sont matérialisées par des kits, qui peuvent être associés à des opérations locales ou collaboratives. Pour participer, l&#39;entité locale doit faire une commande d&#39;opération et cette commande doit être validée.

>[!CAUTION]
>
>Le module Distributed Marketing est une option de **Campaign**. Vérifiez votre contrat de licence.

## Terminologie {#terminology}

### Entité centrale {#central-entities}

Une entité centrale regroupe les opérateurs marketing chargés de définir la communication et d&#39;assister les entités locales dans la réalisation de leur campagne marketing.

L&#39;entité centrale peut, grâce au module de Marketing Distribué :

* mettre en place des kits de campagne marketing à destination des entités locales,
* favoriser l&#39;autonomie des entités locales dans le choix de leurs communications envers leurs clients/prospects, leur ciblage, leur contenu, etc.,
* gérer et maîtriser les coûts,
* animer un réseau d&#39;agences.

### Entité locale {#local-entities}

Une entité locale correspond à une agence, un magasin ou un groupe d&#39;opérateurs locaux spécifiques (responsables de pays ou de régions, responsables de marques, etc.).

Le Marketing Distribué permet aux entités locales d&#39;avoir plus d&#39;autonomie tout en optimisant les coûts de réalisation.

### Localisation {#localization}

La localisation est la capacité pour une entité locale de modifier la cible et le contenu d&#39;une opération. Le niveau de localisation possible dépend du type d&#39;opération et de la mise en oeuvre.

### Liste des kits d&#39;opération {#list-of-campaign-packages}

La liste des kits d&#39;opération regroupe les opérations qui sont disponibles pour les entités locales.

### Kit d&#39;opération {#campaign-package}

Modèle (ou instance d&#39;opération) créé par une entité centrale et mis à disposition d&#39;un ensemble d&#39;entités locales.

### Opération locale {#local-campaign}

Une campagne locale est une instance créée à partir d’un modèle référencé dans la liste de **[!UICONTROL campaign packages]** avec un calendrier **d’exécution** spécifique. Son objectif est de répondre à un besoin de communication local en utilisant un modèle de campagne qui a été configuré et configuré par l&#39;entité centrale.

Le degré d&#39;autonomie de l&#39;entité locale dépend de la mise en oeuvre utilisée.

Reportez-vous à [Création d&#39;une campagne](../../campaign/using/creating-a-local-campaign.md)locale.

### Opération collaborative {#collaborative-campaign}

Une opération collaborative est une opération dont le **planning d&#39;exécution est défini** par l&#39;entité centrale. Les entités locales sont libres de participer ou non à l&#39;opération. En fonction du paramétrage de l&#39;opération, le contenu et la cible peuvent être localisés par l&#39;entité locale. Il existe plusieurs types d&#39;opérations collaboratives :

* **[!UICONTROL Collaborative campaign (by form)]**: recommandé pour les campagnes impliquant jusqu’à 300 entités locales. L&#39;entité locale peut entrer des paramètres prédéfinis pour le ciblage et la personnalisation du contenu dans un formulaire Web. Le formulaire peut être un formulaire Adobe Campaign ou un formulaire externe (client extranet). Un administrateur fonctionnel peut définir et configurer le formulaire en fonction d’un modèle de formulaire défini par l’intégrateur. Pour commander la campagne, l&#39;entité locale a simplement besoin d&#39;un accès Web.
* **[!UICONTROL Collaborative campaign (by campaign)]**: recommandé pour les campagnes destinées à des dizaines d’entités locales. Ce type de campagne crée des campagnes enfants pour chaque entité locale. Une fois la campagne **[!UICONTROL collaborative campaign (by campaign)]** approuvée par l’entité centrale, elle est mise à la disposition de l’entité locale, qui peut la modifier. L’exécution est automatiquement synchronisée entre les campagnes parents et enfants. L&#39;entité locale doit avoir accès à une instance pour commander une campagne et y participer.
* **[!UICONTROL Collaborative campaign (by target approval)]**: recommandé pour les campagnes ciblant plusieurs milliers d’entités locales. L&#39;entité locale reçoit une liste de contacts prédéfinie par l&#39;entité centrale. L&#39;entité locale décide de conserver ou non certains contacts en fonction du contenu de la campagne, via un formulaire Web. Les entités locales sont déduites de la liste des contacts sélectionnés. Pour participer à la campagne, l&#39;entité locale a simplement besoin d&#39;un accès Web.
* **[!UICONTROL Collaborative campaign (simple)]**: ce mode garantit la compatibilité avec les processus d’exécution spécifiques des versions précédentes.

Reportez-vous à [Création d’une campagne](../../campaign/using/creating-a-collaborative-campaign.md)collaborative.

### Commande de kits d&#39;opération {#ordering-campaign-packages}

L&#39;inscription d&#39;une entité locale à une opération se traduit par la création d&#39;une commande qui regroupe toutes les informations relatives à la localisation de la campagne.

## Espace de travail {#workspace}

The list of campaign packages can be accessed from the **Campaigns** universe: click the **[!UICONTROL Campaign packages]** link.

![](assets/mkg_dist_home_local_op.png)

Pour chaque opérateur local, cette fenêtre permet de visualiser les opérations disponibles pour son agence locale.

Pour les agences centrales, cette fenêtre affiche tous les kits disponibles dans la liste des kits d&#39;opération et propose des liens supplémentaires afin d&#39;agir sur la liste.

## Opérateurs et entités {#operators-and-entities}

Start by specifying the central and local entity operators via the **[!UICONTROL Access management]** folder.

![](assets/s_advuser_mkg_dist_tree.png)

### Les opérateurs {#operators}

Vous devez créer des opérateurs centraux et des opérateurs locaux.

Central operators must belong to the **[!UICONTROL Central management]** operator group or have the **[!UICONTROL CENTRAL]** named right.

Local operators must belong to the **[!UICONTROL Local management]** operator group or have the **[!UICONTROL LOCAL]** named right. Ils doivent également être liés à leur entité locale.

![](assets/s_advuser_mkg_dist_local_create.png)

### Entités organisationnelles {#organizational-entities}

Pour créer une entité d&#39;organisation, cliquez sur le **[!UICONTROL Administration > Access management > Organizational entities]** noeud et cliquez sur l&#39; **[!UICONTROL New]** icône au-dessus de la liste des entités.

![](assets/s_advuser_mkg_dist_local_list.png)

Chaque entité organisationnelle contient des informations d&#39;identification (étiquette, nom interne, coordonnées, etc.) et des groupes impliqués dans le processus d&#39;approbation des commandes. Ces valeurs sont définies dans la **[!UICONTROL Notifications and approvals]** section de l’ **[!UICONTROL General]** onglet.

* Vous devez définir un groupe de notification des kits : les opérateurs de ce groupe recevront un message de notification lorsqu&#39;un nouveau kit sera ajouté à la liste des kits d&#39;opération et lorsqu&#39;une opération est disponible.
* Vous devez également sélectionner le groupe d&#39;opérateurs responsables de la validation des commandes, c&#39;est-à-dire chargés de valider les opérations commandées par l&#39;entité locale.
* Sélectionnez enfin le groupe d&#39;opérateurs chargés de la validation de l&#39;opération locale (validation de la cible, du contenu, du budget, etc.). Ce groupe peut être surchargé lors de la commande d&#39;une opération, si le modèle le permet.

>[!NOTE]
>
>The approval process is presented in the [Approval process](../../campaign/using/creating-a-local-campaign.md#approval-process) section.

## Mise en oeuvre {#implementation}

Les opérations de Marketing Distribué sont créées et publiées par l&#39;entité centrale, puis peuvent être utilisées par les entités locales autant que par l&#39;entité centrale, selon les besoins.

Les étapes de mise en oeuvre dépendent du type de kit d&#39;opération utilisé et du niveau de délégation au niveau des entités locales.

### Côté intégrateur {#integrator-side}

1. Créer les entités locales.
1. Associer les destinataires aux opérateurs en charge des entités locales.

   ![](assets/mkg_dist_local_entity_association.png)

1. Définir les droits et les règles de navigation pour les entités locales.
1. Définir l&#39;ensemble des champs nécessaires à la localisation des campagnes :

   * la définition de la cible et sa taille maximale,
   * la définition du contenu,
   * le planning d&#39;exécution (date de contact et date d&#39;extraction), **pour les opérations locales seulement**,
   * l&#39;extension du schéma des commandes avec l&#39;ensemble des champs additionnels nécessaires.

1. Créer un modèle de formulaire Web (Adobe Campaign ou extranet client) qui permet d&#39;exposer les paramètres de localisation, d&#39;évaluer la cible et le budget ; ainsi que de prévisualiser le contenu et valider la commande.

   Pour les **opérations collaboratives par validation de la cible**, créer la table où seront enregistrées les validations pour chaque entité locale.

### Côté administrateur fonctionnel {#functional-administrator-side}

Ces étapes doivent être réalisées à chaque création d&#39;opération.

1. Mettre à jour le formulaire avec les champs utilisés pour la localisation de la campagne.
1. Créer une instance à partir du modèle d&#39;opération approprié (opération collaborative) ou dupliquer le modèle d&#39;opération (opération locale).
1. Paramétrer l&#39;opération avec les champs de localisation et la référence du formulaire.
1. Publiez l&#39;opération.

### Côté opérateur local {#local-operator-side}

Ces étapes doivent être réalisées à chaque opération.

1. A la réception de la notification de disponibilité du kit d&#39;opération, définir la localisation éventuelle de l&#39;opération.
1. Evaluer la cible, le budget, etc..
1. Prévisualiser le contenu de l&#39;opération.
1. Commander l&#39;opération.

