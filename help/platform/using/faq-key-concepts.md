---
product: campaign
title: Principaux concepts
description: FAQ Campaign Classic
feature: Troubleshooting
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: f0d884ae-0789-4ad9-a8fa-adeffbb560ea
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 100%

---

# Principaux concepts {#key-concepts}



Découvrez les principales étapes pour démarrer avec Adobe Campaign.

## Est-il possible de se connecter à Campaign Classic à l&#39;aide d&#39;un Adobe ID ? {#can-i-connect-to-campaign-classic-with-an-adobe-id-}

Grâce à l&#39;intégration avec l&#39;IMS (Adobe IDentity Management System), les utilisateurs peuvent se connecter à la console Adobe Campaign à partir de leur Adobe ID. Cette intégration apporte les avantages suivants :

* utilisation d&#39;un même identifiant pour toutes les solutions Experience Cloud
* mémorisation de la connexion lors de l&#39;utilisation d&#39;Adobe Campaign avec les différentes intégrations
* politique de gestion de mot de passe plus sécurisée
* utilisation de comptes de type Federated ID (fournisseur d&#39;identité externe)

[Cliquez ici pour en savoir plus](../../integrations/using/about-adobe-id.md) sur l&#39;accès à Campaign Classic avec un Adobe ID.

## Quelle est ma version de Campaign ? {#what-is-my-version-of-campaign-}

Vérifiez les [numéros de version et de build](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) depuis le menu **Aide > A propos...** de la console cliente de Campaign.

## Quelles sont les différences entre un environnement on-premise et un environnement hébergé ? {#what-are-the-differences-when-working-on-premise-vs--in-a-hosted-environment-}

Adobe Campaign Classic est fourni avec un ensemble de modules et d&#39;options. La disponibilité de ces modules et leur configuration peuvent dépendre du [type de déploiement](../../installation/using/hosting-models.md) de votre installation : hébergée (Managed Services), hybride ou sur site (on-premise).

[Pour en savoir plus, cliquez ici](../../installation/using/capability-matrix.md).

## Comment configurer les autorisations utilisateur ? {#how-can-i-set-up-user-permissions-}

En tant qu&#39;administrateur de Campaign, vous pouvez configurer des autorisations pour les utilisateurs de votre organisation.

Il s&#39;agit d&#39;un ensemble de droits et de restrictions qui autorisent ou refusent :

* l&#39;accès à certaines fonctionnalités ;
* l&#39;accès à certaines données ;
* la création, la modification et/ou la suppression de données.

[Cliquez ici pour en savoir plus](../../platform/using/access-management.md) sur les autorisations utilisateur.

## Comment assurer la conformité de la confidentialité avec Campaign ?  {#how-to-be-gdpr-compliant-with-campaign-}

Adobe Campaign propose un ensemble d’outils pour vous aider à respecter la vie privée dans le cadre du RGPD et de la CCPA.

Consultez [ce document](privacy-and-recommendations.md) afin de connaître les outils et les fonctionnalités proposés par Adobe Campaign, ainsi que les bonnes pratiques, pour respecter le RGPD lors de l&#39;utilisation de notre service. Les étapes de mise en œuvre de Campaign Classic sont décrites dans [cet article](https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html).

## Quelles notions concernant l&#39;interface utilisateur de Campaign faut-il connaître ?  {#what-are-campaign-user-interface-concepts-i-should-know-}

Lisez [cette section](../../platform/using/adobe-campaign-workspace.md) pour en savoir plus sur les bases de l&#39;espace de travail Adobe Campaign.

![](assets/do-not-localize/how-to-video.png) [Découvrir l&#39;espace de travail Campaign en vidéo](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/getting-started/exploring-the-adobe-campaign-classic-user-interface.html?lang=fr)

## Comment sélectionner l’audience de mes messages ?  {#how-can-i-select-the-target-population-of-my-messages-}

Avec Adobe Campaign, vous pouvez utiliser différentes stratégies pour créer des audiences et sélectionner des destinataires cibles.

[Pour en savoir plus, cliquez ici](../../delivery/using/steps-defining-the-target-population.md).

## Qu’est-ce qu&#39;un workflow ?  {#what-is-a-workflow-}

Adobe Campaign contient des workflows pour orchestrer l&#39;ensemble des processus et tâches dans les différents modules du serveur applicatif. Cet environnement graphique complet permet de concevoir des processus englobant segmentation, exécution de campagnes, traitement de fichiers, participation humaine, etc. Le moteur de workflow exécute et assure le tracking de ces processus.

Un workflow permet par exemple de télécharger un fichier depuis un serveur, de le décompresser et d&#39;importer ses enregistrements dans la base de données Adobe Campaign.

Un workflow peut également faire intervenir des opérateurs afin de notifier ou valider une opération ou faire un choix. Ainsi, il est possible de créer une action de diffusion, d&#39;assigner une tâche à un ou plusieurs opérateurs qui seront chargés de saisir son contenu ou spécifier sa cible, puis de faire valider le BAT avant de démarrer la diffusion.

[Cliquez ici pour en savoir plus](../../workflow/using/about-workflows.md) sur les workflows. Vous pouvez également consulter les [bonnes pratiques en matière de workflow](../../workflow/using/building-a-workflow.md).

## Comment créer et envoyer un premier email ?  {#how-to-create-and-send-a-first-email-}

[Pour en savoir plus, cliquez ici](../../delivery/using/about-email-channel.md).

![](assets/do-not-localize/how-to-video.png) [Découvrez cette fonctionnalité en vidéo](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/getting-started/creating-a-campaign-and-an-email.html?lang=fr)

## Comment envoyer des SMS ?  {#how-to-send-sms-messages-}

Découvrez comment configurer votre plateforme et envoyer des SMS dans [cette section](../../delivery/using/sms-channel.md).

## Comment envoyer des notifications push ?  {#how-to-send-push-notifications-}

Découvrez comment utiliser Adobe Campaign pour [envoyer une notification push personnalisée](../../delivery/using/create-notifications-ios.md) à des appareils iOS et Android via des applications.

## Comment concevoir et partager un questionnaire en ligne ?  {#how-to-design-and-share-an-online-survey-}

Découvrez comment [créer un questionnaire en ligne](../../surveys/using/getting-started-with-surveys.md) et quelles sont les principales étapes pour le concevoir et le publier avec Campaign Classic.

## Comment créer une landing page ?  {#how-to-create-landing-page-}

Vous pouvez utiliser le Digital Content Editor d’Adobe Campaign pour concevoir une landing page et définir le mapping avec les champs de la base de données

[Pour en savoir plus, cliquez ici](../../web/using/creating-a-landing-page.md).

## Comment effectuer un tracking des diffusions ?  {#how-can-i-track-deliveries-}

Vous pouvez effectuer un tracking des diffusions envoyées avec Campaign Classic via des [rapports de diffusion](../../reporting/using/delivery-reports.md) dédiés et les suivre ensuite.

En savoir plus sur la gestion du suivi dans Campaign dans [cette page](https://helpx.adobe.com/fr/campaign/kb/acc-tracking.html).

## Quelles sont les bonnes pratiques en matière de sécurité (on-premise) ?  {#what-are-security-best-practices--on-premise--}

Consultez la [liste de contrôle relative à la configuration de la sécurité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html) pour découvrir les éléments essentiels à contrôler en ce qui concerne le renforcement et la configuration de la sécurité pour les déploiements on-premise.

## Comment traduire un message d’erreur ?  {#how-to-translate-an-error-message-}

Un message d&#39;erreur est affiché dans une langue étrangère ? Tous les messages d&#39;erreur et leur traduction sont répertoriés dans [cette page](https://experienceleague.adobe.com/developer/campaign-errors/error_codes.html?lang=fr).

## Est-il possible de créer un formulaire web et collecter les réponses dans Campaign ?  {#can-i-create-a-webform-and-collect-answers-in-campaign-}

Découvrez comment [créer un formulaire web](../../web/using/about-web-forms.md) : concevoir, tester, publier un formulaire web et collecter des réponses.

## Existe-t-il une liste des fonctionnalités et versions obsolètes ?  {#is-there-a-list-of-deprecated-features-and-versions-}

Adobe évalue constamment les fonctionnalités du produit et prévoit au fil du temps de remplacer certaines d’entre elles par des versions plus puissantes, ou décide de mettre à nouveau en œuvre certaines parties pour mieux se préparer aux attentes ou aux extensions futures. Comme Campaign fonctionne avec des outils tiers, la compatibilité est mise à jour régulièrement, afin de mettre en œuvre les versions prises en charge uniquement.

[Pour en savoir plus, cliquez ici](../../rn/using/deprecated-features.md).

## De nouvelles mises à jour de la documentation et des documents d&#39;aide sont-ils publiés ? {#are-there-new-documentation-updates-and-help-materials-released-}

Les dernières mises à jour apportées à la documentation de Campaign Classic sont répertoriées sur [cette page](https://experienceleague.adobe.com/docs/campaign-classic/using/documentation-updates.html?lang=fr).

Vous pouvez également vous reporter aux dernières notes techniques répertoriées sur [cette page](https://helpx.adobe.com/fr/campaign/kb/article-list.html).
