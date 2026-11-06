---
keywords: Campaign Classic;accueil;thèmes populaires
product: campaign
title: Documentation du produit Adobe Campaign Classic v7
exl-id: 6b3f1689-80de-49fd-b7ee-7a2a1931d157
TQID: 'https://experienceleague.adobe.com/Q6Oc24mo-1qDAxCWu2lGT4UvRLXB78Tr5X4sb2kHFw8'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
    internal-label: APIs
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: c1f8b6661065c8d5c75e38d80f6986e0c6fbdfa8
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 62%
---
# Documentation de Campaign Classic v7 {#campaign-classic-documentation}

Cette documentation couvre Campaign Classic v7 pour les déploiements **on-premise et hybrides** : installation, configuration, mises à niveau, opérations et fonctionnalités spécifiques à la v7. Si votre instance est hébergée par Adobe (Managed Cloud Services), reportez-vous à la documentation de [Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/campaign-home){target="_blank"}. Le contenu que Campaign v8 documente de la même manière n’est plus dupliqué ici : consultez la section [&#x200B; De v7 à v8](#from-v7-to-v8).

<!--![](platform/using/assets/do-not-localize/banner_acc_doc.jpg) -->

## Nouveautés

Découvrez en primeur les dernières améliorations apportées à la documentation et au produit Adobe Campaign Classic v7. Pour obtenir la liste complète des fonctionnalités, des améliorations et des correctifs, consultez les [notes de mise à jour](rn/using/latest-release.md).

>[!BEGINTABS]


>[!TAB La version d’octobre 2026 est en ligne !]

La version 7.4.5 de Campaign Classic du 26 octobre (build 9420) fournit des correctifs pour le compte externe Analytics, les diffusions bloquées dans le statut En attente de personnalisation , l’utilisation du serveur CPU , les échecs de mise à jour intermittente du modèle de données , l’erreur de vérification du spam lors de la création de la diffusion et la mise en quarantaine des soft bounces récurrents.

[![Image](assets/do-not-localize/learn-more-button.svg)](rn/using/latest-release.md)

>[!TAB Passer à Adobe IMS]

Pour renforcer la sécurité et le processus d’authentification, Adobe Campaign recommande vivement de migrer le mode d’authentification de l’utilisateur final et de l’utilisatrice finale et de passer de l’authentification native par nom d’utilisateur ou d’utilisatrice/mot de passe au système de gestion des identités (IMS) Adobe.

[![Image](assets/do-not-localize/learn-more-button.svg)](technotes/using/ac-ims.md)


>[!ENDTABS]

## Principes de base

<table style="table-layout:fixed">
  <tr style="border: 0;">
    <td>
    <a href="platform/using/launching-adobe-campaign.md"><img src="assets/do-not-localize/start-launch.png"></a></a>
    <div><strong>Lancer Adobe Campaign</strong><br/> Découvrez comment lancer la console cliente Campaign et vous connecter à votre ou vos serveurs d’applications Campaign.</div>
    </td>
    <td>
    <a href="platform/using/about-profiles.md"><img src="assets/do-not-localize/start-profiles.png"></a>
    <div><strong>Ajouter et gérer des profils</strong><br/> Découvrez la gestion des profils dans la base de données d’Adobe Campaign v7. Ajoutez des profils manuellement ou importez-les, affinez les données client et personnalisez vos campagnes en toute facilité.</div>
    </td>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank"><img src="assets/do-not-localize/start-workflows.jpeg"></a>
    <div><strong>Automatiser à l’aide des workflows</strong><br/> Découvrez comment tirer parti des workflows pour concevoir des processus, notamment la segmentation, l’exécution de campagnes, le traitement de fichiers, la participation humaine, etc.
    </div></td>
    <td>
    <a href="delivery/using/communication-channels.md"><img src="assets/do-not-localize/start-deliveries.jpeg"></a>
    <div><strong>Créer des diffusions</strong><br/> Découvrez comment envoyer des messages sur différents canaux, tels que les e-mails, les SMS, les notifications push, etc.</div>
    </td>
  </tr>
  <tr style="border: 0;">
    <td align="center"><a href="platform/using/launching-adobe-campaign.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="platform/using/about-profiles.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="delivery/using/communication-channels.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    </tr>
</table>

## Accéder à la documentation

<table style="table-layout:auto">
  <tr style="border: 0;">
    <td>
      <img src="assets/do-not-localize/icon-start.svg" width="35px">
    <br/>
      <strong>Commencer</strong><br/><a href="https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/new/campaign-ui" target="_blank">Interface d’utilisation</a> (documentation de Campaign v8) – <a href="platform/using/launching-adobe-campaign.md">Se connecter à Campaign</a> – <a href="https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/data/import" target="_blank">Importer et exporter des données</a> (documentation de Campaign v8) – <a href="platform/using/access-management.md">Autorisations</a>
    </td>
    <td>
      <img src="assets/do-not-localize/icon-experience.svg" width="35px">
    <br/>
      <strong>Expérience client</strong><br/><a href="https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank">Automatisation avec des workflows</a> (documentation de Campaign v8) - <a href="https://experienceleague.adobe.com/fr/docs/campaign/automation/campaign-orchestration/set-up-campaigns" target="_blank">Campagne marketing</a> - <a href="interaction/using/interaction-and-offer-management.md">Interaction et gestion des offres</a> - <a href="delivery/using/about-personalization.md">Personalization</a> - <a href="https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/analytics/reports/gs-reporting" target="_blank">Reporting</a> (documentation de Campaign v8)
    </td>
    <td>
      <img src="assets/do-not-localize/icon-send.svg" width="35px">
    <br/>
      <strong>Envoyer des messages</strong><br/><a href="delivery/using/communication-channels.md">Canaux de communication</a> – <a href="https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/create-message" target="_blank">Envoyer des BAT</a> (documentation de Campaign v8) – <a href="delivery/using/get-started-a-b-testing.md">Tests AB</a> – <a href="https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/analytics/tracking/tracking" target="_blank">Suivi des messages</a> – <a href="delivery/using/about-deliverability.md">Délivrabilité</a> – <a href="message-center/using/about-transactional-messaging.md">Messages transactionnels</a>
    </td>
  </tr>
  <tr style="border: 0;">
    <td>
      <img src="assets/do-not-localize/icon_profile-audience.svg" width="35px">
      <br/>
      <strong>Profils et audiences</strong><br/> <a href="https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/audience/create-audiences/create-audiences" target="_blank">Créer des listes</a> (documentation de Campaign v8) – <a href="delivery/using/about-services-and-subscriptions.md">Services et abonnements</a> – <a href="platform/using/privacy-management.md">Confidentialité et consentement</a>
    </td>
    <td>
      <img src="assets/do-not-localize/icon-configure.svg" width="35px">
      <br/>
      <strong>Architecture et configuration</strong><br/><a href="production/using/general-architecture.md">Principes d’architecture</a> – <a href="production/using/build-upgrade.md">Mise à niveau d’un build</a> – <a href="production/using/configuration.md">Configurer Campaign</a> – <a href="installation/using/external-accounts.md">Se connecter à des systèmes externes</a>
    </td>
    <td>
      <img src="assets/do-not-localize/icon-dev.svg" width="35px">
      <br/>
      <strong>Ressources pour les développeurs</strong><br/><a href="https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/developer/datamodel" target="_blank">Description du modèle de données</a> (documentation de Campaign v8) - <a href="configuration/using/about-schema-reference.md">Structure du schéma</a> - <a href="configuration/using/editing-forms.md">Formulaires de saisie</a> - <a href="configuration/using/about-web-services.md">API</a> - <a href="https://experienceleague.adobe.com/fr/tools/campaign-api">Documentation de référence JSAPI</a> - <a href="configuration/using/about-custom-recipient-table.md">Table de destinataires personnalisée</a>
    </td>
  </tr>
</table>

## De v7 à v8 {#from-v7-to-v8}

Le contenu documenté dans la documentation de Campaign v8 a été supprimé de la documentation v7. Utilisez cette table pour le trouver.

| Si vous recherchez... | Accédez à la documentation de Campaign v8 . |
| --- | --- |
| Interface utilisateur d’ | [Découvrir l’interface utilisateur](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/new/campaign-ui){target="_blank"} |
| Profils, listes, import et export | [Importer des profils et des données](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/data/import){target="_blank"} |
| Workflows | [À propos des workflows](https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows){target="_blank"} |
| Campagnes marketing | [Prise en main des campagnes marketing](https://experienceleague.adobe.com/en/docs/campaign/automation/campaign-orchestration/set-up-campaigns){target="_blank"} |
| Création et envoi de diffusions | [Créer un message](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/send/create-message){target="_blank"} |
| Rapports intégrés | [Prise en main du reporting](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/analytics/reports/gs-reporting){target="_blank"} |
| Autorisations | [Prise en main des autorisations](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/permissions/gs-permissions){target="_blank"} |
| Formulaires de saisie | [Prise en main des formulaires de saisie](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/developer/schemas-forms/forms){target="_blank"} |

## Autres ressources

[Description du produit Adobe Campaign](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"} – [Matrice de compatibilité](rn/using/compatibility-matrix.md) – [Tutoriels](https://experienceleague.adobe.com/fr/docs/campaign-classic-learn/tutorials/overview.html?lang=fr){target="_blank"} – [Panneau de contrôle pour Campaign](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=fr){target="_blank"} – [Pixels de suivi des e-mails et recommandations CNIL](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/new/cnil-pixel-tracking){target="_blank"}
