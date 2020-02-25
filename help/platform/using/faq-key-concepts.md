---
title: Principaux concepts
seo-title: FAQ sur les fonctionnalités de campagne
description: FAQ sur Campaign Classic
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8ef56aa04a3ecc94e9e3dda24562760d6a93739d

---


# Principaux concepts {#key-concepts}

Découvrez les principales étapes pour démarrer avec Adobe Campaign.

## Can I connect to Campaign Classic with an Adobe ID? {#can-i-connect-to-campaign-classic-with-an-adobe-id-}

Grâce à l&#39;intégration avec l&#39;IMS (Adobe Identity Management System), les utilisateurs peuvent se connecter à la console Adobe Campaign à partir de leur Adobe ID. Cette intégration apporte les avantages suivants :

* utilisation d&#39;un même identifiant pour toutes les solutions Experience Cloud
* mémorisation de la connexion lors de l&#39;utilisation d&#39;Adobe Campaign avec les différentes intégrations
* politique de gestion de mot de passe plus sécurisée
* utilisation de comptes de type Federated ID (fournisseur d&#39;identité externe)

[Cliquez ici pour en savoir plus](../../integrations/using/about-adobe-id.md) sur l&#39;accès à Campaign Classic avec un Adobe ID.

## What is my version of Campaign? {#what-is-my-version-of-campaign-}

Vérifiez les [numéros de version et de build](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) depuis le menu **Aide > A propos...** de la console cliente de Campaign.

## What are the differences when working on-premise vs. in a hosted environment? {#what-are-the-differences-when-working-on-premise-vs--in-a-hosted-environment-}

Adobe Campaign Classic est proposé avec un ensemble de modules et d&#39;options. La disponibilité de ces modules et leur configuration peuvent dépendre du [type de déploiement](../../installation/using/hosting-models.md) de votre installation : hébergé (services gérés) ou on-premise.

[Pour en savoir plus, cliquez ici](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## How can I set up user permissions? {#how-can-i-set-up-user-permissions-}

En tant qu&#39;administrateur de Campaign, vous pouvez configurer des permissions pour les utilisateurs de votre organisation.

Il s&#39;agit d&#39;un ensemble de droits et de restrictions qui autorisent ou refusent :

* l&#39;accès à certaines fonctionnalités ;
* l&#39;accès à certaines données ;
* la création, la modification et/ou la suppression de données.

[Cliquez ici pour en savoir plus](../../platform/using/access-management.md) sur les permissions utilisateur.

## Comment assurer la conformité de la confidentialité avec Campaign ? {#how-to-be-gdpr-compliant-with-campaign-}

Adobe Campaign propose un ensemble d’outils pour vous aider à respecter la vie privée dans le cadre du RDCM et de l’ACCP.

Consultez [ce document](https://helpx.adobe.com/campaign/kb/campaign-privacy-overview.html) afin de connaître les outils et les fonctionnalités proposés par Adobe Campaign, ainsi que les bonnes pratiques, pour respecter le RGPD lors de l&#39;utilisation de notre service. Les étapes de mise en oeuvre de Campaign Classic sont décrites dans [cet article](https://helpx.adobe.com/campaign/kb/acc-privacy.html).

## What are Campaign user interface concepts I should know? {#what-are-campaign-user-interface-concepts-i-should-know-}

Consultez [cette section](../../platform/using/adobe-campaign-workspace.md) pour en savoir plus sur les notions fondamentales de l&#39;espace de travail Adobe Campaign. Vous pouvez également regarder [cette vidéo](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/interface-overview.html).

## How can I select the audience of my messages? {#how-can-i-select-the-target-population-of-my-messages-}

Avec Adobe Campaign, vous pouvez utiliser différentes stratégies pour créer des audiences et sélectionner des destinataires cibles.

[Pour en savoir plus, cliquez ici](../../delivery/using/steps-defining-the-target-population.md).

## What is a workflow? {#what-is-a-workflow-}

Adobe Campaign contient des workflows pour orchestrer l&#39;ensemble des processus et tâches dans les différents modules du serveur applicatif. Cet environnement graphique complet permet de concevoir des processus englobant segmentation, exécution de campagnes, traitement de fichiers, participation humaine, etc. Le moteur de workflow exécute et assure le tracking de ces processus.

Un workflow permet par exemple de télécharger un fichier depuis un serveur, de le décompresser et d&#39;importer ses enregistrements dans la base de données Adobe Campaign.

Un workflow peut également faire intervenir des opérateurs afin de notifier ou valider une opération ou faire un choix. Ainsi, il est possible de créer une action de diffusion, d&#39;assigner une tâche à un ou plusieurs opérateurs qui seront chargés de saisir son contenu ou spécifier sa cible, puis de faire valider le BAT avant de démarrer la diffusion.

[Cliquez ici pour en savoir plus](../../workflow/using/about-workflows.md) sur les workflows. Vous pouvez également consulter les [bonnes pratiques en matière de workflow](../../workflow/using/building-a-workflow.md).

## How to create and send a first email? {#how-to-create-and-send-a-first-email-}

[Pour en savoir plus, cliquez ici](../../delivery/using/about-email-channel.md) ou [regardez cette vidéo](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/creating-a-campaign-and-an-email.html) pour créer un email dans une campagne.

## How to send SMS messages? {#how-to-send-sms-messages-}

Découvrez comment configurer votre plateforme et envoyer des SMS dans [cette section](../../delivery/using/sms-channel.md).

## How to send push notifications? {#how-to-send-push-notifications-}

Découvrez comment utiliser Adobe Campaign pour [envoyer une notification push personnalisée](../../delivery/using/creating-notifications.md) à des appareils iOS et Android via des applications.

## How to design and share an online survey? {#how-to-design-and-share-an-online-survey-}

Découvrez comment [créer un questionnaire en ligne](../../web/using/getting-started-with-surveys.md) et quelles sont les principales étapes pour le concevoir et le publier avec Campaign Classic.

## How to create landing page? {#how-to-create-landing-page-}

Vous pouvez le Digital Content Editor Adobe Campaign pour concevoir une landing page et définir le mappage avec les champs de la base de données

[Pour en savoir plus, cliquez ici](../../web/using/creating-a-landing-page.md).

## How can I track deliveries? {#how-can-i-track-deliveries-}

Vous pouvez effectuer un tracking des diffusions envoyées avec Campaign Classic via des [rapports de diffusion](../../reporting/using/delivery-reports.md) dédiés et les suivre ensuite.

En savoir plus sur la gestion du suivi dans Campaign dans [cette page](https://helpx.adobe.com/campaign/kb/acc-tracking.html).

## What are security best practices (on-premise)? {#what-are-security-best-practices--on-premise--}

Consultez la [Liste de contrôle relative à la configuration de la sécurité](https://helpx.adobe.com/campaign/kb/acc-security.html) pour découvrir les éléments essentiels à contrôler en ce qui concerne le renforcement et la configuration de la sécurité pour les déploiements on-premise.

## How to translate an error message? {#how-to-translate-an-error-message-}

Un message d&#39;erreur est affiché dans une langue étrangère ? Tous les messages d&#39;erreur et leur traduction sont répertoriés dans [cette page](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html).

## Can I create a webform and collect answers in Campaign? {#can-i-create-a-webform-and-collect-answers-in-campaign-}

Découvrez comment [créer un formulaire](../../web/using/about-web-forms.md)Web : concevoir, tester, publier un formulaire Web et recueillir des réponses.

## Is there a list of deprecated features and versions? {#is-there-a-list-of-deprecated-features-and-versions-}

Adobe évalue constamment les fonctionnalités du produit et prévoit au fil du temps de remplacer certaines d’entre elles par des versions plus puissantes, ou décide de mettre à nouveau en œuvre certaines parties pour mieux se préparer aux attentes ou aux extensions futures. Comme Campaign fonctionne avec des outils tiers, la compatibilité est mise à jour régulièrement, afin de mettre en œuvre les versions prises en charge uniquement.

[Pour en savoir plus, cliquez ici](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html).

## Are there new documentation updates and help materials released? {#are-there-new-documentation-updates-and-help-materials-released-}

Les dernières mises à jour apportées à la documentation de Campaign Classic sont répertoriées sur [cette page](https://docs.adobe.com/content/help/en/campaign-classic/using/documentation-updates.html).

Vous pouvez également vous reporter aux dernières notes techniques répertoriées sur [cette page](https://helpx.adobe.com/campaign/kb/article-list.html).
