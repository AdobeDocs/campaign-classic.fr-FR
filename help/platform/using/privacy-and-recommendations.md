---
title: Confidentialité et recommandations
seo-title: Confidentialité et recommandations
description: Confidentialité et recommandations
seo-description: null
page-status-flag: never-activated
uuid: a044bbea-521d-4c1e-8aab-7d51a87fc94b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 14369acf-9149-4649-947a-c16289e35eb6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be148d7cd55097b9014d2f4d3b095c65a5ca8c54
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 91%

---


# Confidentialité et recommandations{#privacy-and-recommendations}

## A propos de la confidentialité et du consentement {#about-privacy-and-consent}

 Adobe Campaign est un outil puissant pour collecter et traiter de très grands volumes de données, notamment des informations personnelles. Nous incitons tous les utilisateurs d’Adobe Campaign à travailler en respectant la législation (APD - autorités publiques indépendantes, loi CAN-SPAM aux États-Unis, Directive européenne sur la protection de la vie privée dans le secteur des communications électroniques, RGPD européen, CCPA, etc.), à utiliser les informations personnelles de manière responsable et éthique et à s’abstenir d’envoyer des emails, des notifications push et des messages SMS non sollicités (« spam »). Nous croyons fermement aux principes du consentement (permission marketing) pour fidéliser le client et offrir une valeur ajoutée tout au long de sa durée de vie et nous interdisons donc strictement l’utilisation d’Adobe Campaign pour l’envoi de messages non sollicités.

Voir à ce sujet la [politique de confidentialité d’Adobe Experience Cloud](https://www.adobe.com/privacy/marketing-cloud.html).

Prenez le temps de consulter la [liste de contrôle de sécurité et de confidentialité](https://docs.campaign.adobe.com/doc/AC/getting_started/FR/security.html) afin de connaître les principaux éléments à vérifier en termes de sécurité et de confidentialité.

## Gestion de la confidentialité {#privacy-management}

Adobe Campaign offre un ensemble d&#39;outils pour vous aider à vous conformer aux règlements sur la protection des renseignements personnels (RGMD, ACCP, etc.).

Le RGPD (Règlement général sur la protection des données) est la loi de l&#39;Union européenne (UE) sur la protection de la vie privée. Il harmonise et modernise les exigences en matière de protection des données. Le règlement s’applique aux clients Adobe Campaign qui détiennent des données pour des personnes concernées résidant dans l’UE.

Le CCPA (California Consumer Privacy Act) fournit aux résidents de la Californie de nouveaux droits relatifs aux informations personnelles et impose des responsabilités en matière de protection des données à certaines entités qui exercent des activités en Californie.

Outre la gestion du consentement, les paramètres de conservation des données et la gestion des droits, nous incluons, en tant que responsable du traitement des données, d’autres fonctionnalités pour faciliter votre préparation à certaines demandes d’accès à des informations personnelles en tant que contrôleur de données.

In [this article](https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html), you will learn how Adobe Campaign helps you manage the different Privacy key features: Right to Access, Right to be Forgotten, consent, data retention and user roles. Vous trouverez également les meilleures pratiques, pour vous aider à respecter votre vie privée lors de l&#39;utilisation de notre solution.

## Cookies et fonctionnalités de tracking {#cookies-and-tracking-capabilities}

Grâce à ses fonctionnalités de tracking, Adobe Campaign permet de suivre la navigation des destinataires de ses diffusions sur un site web. Pour cela, Adobe Campaign utilise des cookies de session et des cookies permanents.

La directive européenne 2009/136/CE &quot;Vie Privée et Communication Electronique&quot; et le règlement général sur la protection des données prévoient que les entreprises doivent recueillir le consentement des utilisateurs de leur site web préalablement à toute installation de cookies. Vous devez informer les utilisateurs de vos sites soumis au web tracking via une zone de demande de consentement (par exemple en surimpression sur la page) proposant une case à cocher pour autoriser l&#39;installation de cookies, ou afficher une bannière en haut de la première page visitée, etc. Les fenêtres de type pop-up sont à éviter car elles sont souvent bloquées par les navigateurs.

Il est possible de configurer la gestion du tracking des utilisateurs pour les applications web et les landing pages à l&#39;aide d&#39;une bannière d&#39;opt-out. Pour plus d&#39;informations, consultez [cette page](../../web/using/web-application-tracking-opt-out.md).

Adobe Campaign utilise deux types de cookies :

1. Un cookie de session (nlid) : il contient l&#39;identifiant de l&#39;email envoyé au contact (broadlogId) et l&#39;identifiant du modèle de message (deliveryId). Il est déposé lorsque le contact clique sur une URL contenue dans un email envoyé par Adobe Campaign et permet de suivre son comportement sur le web. Ce cookie de session est effacé automatiquement à la fermeture du navigateur. Le contact a la possibilité d&#39;en interdire le dépôt en adaptant les paramètres de son navigateur.
1. Un cookie permanent (uuid230) : il permet d&#39;identifier un internaute qui interagit avec Adobe Campaign, lors de ses visites sur un site web. Il est utilisé par Adobe Campaign pour comptabiliser le nombre de clics et calculer une estimation du taux de transfert lors d&#39;une opération marketing. Il est déposé lorsque le contact clique dans un email, remplit un formulaire Adobe Campaign ou lors de l&#39;appel au moteur d&#39;interaction entrant. L&#39;internaute a la possibilité de le supprimer ou d&#39;en empêcher le dépôt en adaptant les paramètres de son navigateur.

## Intégrité de la base de données {#database-integrity}

Adobe Campaign est un logiciel d&#39;une grande richesse fonctionnelle. Cette richesse requiert l&#39;utilisation d&#39;une base de données de structure complexe. La base contient un nombre important de tables, champs, liens et index. Certaines tables intermédiaires ne sont pas affichées par l&#39;interface graphique. Certains liens, champs et index sont automatiquement créés, supprimés ou modifiés par le logiciel. Seules les interfaces prévues par Adobe Campaign (interface graphique, programme d&#39;import, module serveur, module web, serveurs de diffusion, ajout de champ, extension de la base, etc.) sont à même de modifier le contenu de la base de données tout en respectant son intégrité.

**Vous ne devez jamais modifier le contenu ou la structure de la base de données par d&#39;autres moyens que ceux prévus dans le logiciel**. De telles modifications ont une forte probabilité d&#39;entraîner la corruption de la base de données avec des manifestations telles que : perte ou modification involontaire de données ou de liens, création de liens ou enregistrements fantômes, messages d&#39;erreur graves, etc. Les altérations de la base de données résultant de ce type de manipulations entraînent la résiliation de la garantie et du support technique fournis par Adobe Campaign.

Dans le cas du système Adobe Campaign, toutes les informations sont en permanence stockées dans la base de données. Sa disponibilité conditionne le bon fonctionnement de tout le système Adobe Campaign : modules web d&#39;inscription, administration, désinscription, écrans d&#39;administration, file d&#39;attente de diffusion, mécanismes d&#39;optimisation de la diffusion, etc.

## Apache Tomcat {#apache-tomcat}

Adobe Campaign inclut Apache Tomcat, un logiciel développé par l&#39;Apache Software Foundation ([http://www.apache.org/](https://www.apache.org/)).
