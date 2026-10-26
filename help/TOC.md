---
audience: end-user
breadcrumb-title: Documentation de Campaign Classic v7
product: campaign
title: Guide de Campaign Classic v7
user-guide-title: Guide de Campaign Classic v7
user-guide-description: Documentation du produit Adobe Campaign Classic v7.
sub-product: adobe campaign classic
type: Documentation
nudge: false
source-git-commit: 59d78c785d8984861fd537c2f64f82a7d2d77fbf
workflow-type: ht
source-wordcount: '1657'
ht-degree: 100%
---

# Documentation Adobe Campaign Classic v7 {#using}

+ [Documentation Campaign v7](campaign-classic-home.md)
+ Notes de mise à jour {#release-notes}
  + [Prise en main des mises à niveau](rn/using/rn-overview.md)
  + [Dernière version](rn/using/latest-release.md)
  + Versions précédentes {#previous-releases}
    + [2025](rn/using/release-2025.md)
    + [2024](rn/using/release-2024.md)
    + {hide-from-toc}[2023 - MASQUÉ](rn/using/release-2023.md)
    + {hide-from-toc}[2022 - MASQUÉ](rn/using/release-2022.md)
    + {hide-from-toc}[2021 - MASQUÉ](rn/using/release-2021.md)
    + {hide-from-toc}[[!DNL Gold Standard - HIDDEN]](rn/using/gold-standard.md)
  + [Fonctionnalités obsolètes](rn/using/deprecated-features.md)
  + [Matrice de compatibilité](rn/using/compatibility-matrix.md)
+ Commencer {#getting-started}
  + [Prise en main d’Adobe Campaign Classic](platform/using/about-adobe-campaign-classic.md)
  + [Lancement d’Adobe Campaign](platform/using/launching-adobe-campaign.md)
  + [Connecteurs Campaign](platform/using/about-connectors.md)
  + Questions fréquentes {#faq}
    + [Questions fréquentes sur Campaign Classic](platform/using/faq-campaign-classic-v7.md)
    + [Mise à niveau de build](platform/using/faq-build-upgrade.md)
  + Confidentialité {#privacy}
    + [Confidentialité et consentement](platform/using/privacy-and-recommendations.md)
    + [Gestion de la confidentialité](platform/using/privacy-management.md)
    + Demandes d&#39;accès à des informations personnelles {#privacy-requests}
      + [Créer et gérer les demandes d’accès à des informations personnelles](platform/using/privacy-requests-ui.md)
      + [Processus automatique de demande d&#39;accès à des informations personnelles](platform/using/privacy-requests-api.md)
    + [Droit d&#39;opposition (opt-out) à la vente des informations personnelles](platform/using/privacy-requests-ccpa.md)
  + Gestion des profils {#profile-management}
    + [À propos des profils](platform/using/about-profiles.md)
    + [Mettre à jour des données](platform/using/updating-data.md)
  + Importer et exporter des données {#importing-and-exporting-data}
    + Créer des imports et des exports génériques {#generic-imports-exports}
      + [Surveillance de l’exécution des traitements](platform/using/monitoring-jobs-execution.md)
      + [Exemples d&#39;import générique](platform/using/import-operations-samples.md)
    + Gérer le chiffrement et la compression des données {#managing-data-encryption-compression}
      + [Décompression ou déchiffrement d’un fichier avant traitement](platform/using/unzip-decrypt.md)
      + [Compression ou chiffrement d’un fichier avant traitement](platform/using/zip-encrypt.md)
    + Bonnes pratiques et résolution des problèmes {#best-practices}
      + [Bonnes pratiques en matière d&#39;import et d&#39;export](platform/using/import-export-best-practices.md)
      + [Bonnes pratiques et résolution des problèmes liés au serveur SFTP](platform/using/sftp-server-usage.md)
  + Autorisations {#permissions}
    + [Commencer avec les autorisations](platform/using/access-management.md)
    + Authentification native (héritée) {#native}
      + [Création et gestion d’opérateurs](platform/using/access-management-operators.md)
      + [Création et gestion de groupes](platform/using/access-management-groups.md)
  + Connecteurs CRM {#connectors}
    + [Prise en main des connecteurs CRM](platform/using/crm-connectors.md)
+ Créer et envoyer des messages {#sending-messages}
  + [Commencer avec les messages](delivery/using/communication-channels.md)
  + {hide-from-toc}[Paramètres de diffusion - MASQUÉ](delivery/using/delivery-settings.md)
  + Démarrage rapide {#key-steps-when-creating-a-delivery}
    + {hide-from-toc}[Envoyer la diffusion - MASQUÉ](delivery/using/steps-sending-the-delivery.md)
  + [Envoyer des e-mails](delivery/using/about-email-channel.md)
  + Envoyer un SMS {#sending-messages-on-mobiles}
    + Configurer le canal SMS {#sms-set-up}
      + [Configurer les SMS sur une instance autonome](delivery/using/sms-set-up.md)
      + [Configurer les SMS sur une infrastructure midsourcing](delivery/using/sms-set-up-mid.md)
      + [Protocole et paramètres du connecteur SMS](delivery/using/sms-protocol.md)
      + [Configuration supplémentaire](delivery/using/sms-send.md)
      + [Résolution des problèmes de SMS](delivery/using/troubleshooting-sms.md)
    + {hide-from-toc}[Migrer vers le connecteur SMPP générique étendu](delivery/using/unsupported-connector-migration.md)
  + [Envoyer des notifications push](delivery/using/about-mobile-app-channel.md)
  + Envoyer des notifications push {#sending-push-notifications}
    + Configurer l’application mobile{#configure-the-mobile-app}
      + {hide-from-toc}[Commencer avec la configuration de l’application - MASQUÉ](delivery/using/get-started-app-config.md)
      + {hide-from-toc}[Étapes de configuration pour iOS - MASQUÉ](delivery/using/configuring-the-mobile-application.md)
      + {hide-from-toc}[Étapes de configuration pour Android - MASQUÉ](delivery/using/configuring-the-mobile-application-android.md)
    + {hide-from-toc}[Résolution des problèmes - MASQUÉ](delivery/using/troubleshooting.md)
  + [Envoyer des courriers](delivery/using/about-direct-mail-channel.md)
  + Personnaliser les diffusions {#personalizing-deliveries}
    + [À propos de la personnalisation](delivery/using/about-personalization.md)
  + Utiliser des adresses de contrôle {#using-seed-addresses}
    + [Cas d’utilisation : sélectionner des adresses de contrôle selon des critères](delivery/using/use-case-selecting-seed-addresses-on-criteria.md)
    + [Cas d’utilisation : configurer la substitution des champs](delivery/using/use-case-configuring-the-field-substitution.md)
  + Tests A/B {#a-b-testing}
    + [Prise en main des tests A/B](delivery/using/get-started-a-b-testing.md)
    + [Configuration des tests AB](delivery/using/configuring-a-b-testing.md)
    + Cas d’utilisation {#use-case}
      + [À propos de ce cas d&#39;utilisation](delivery/using/a-b-testing-use-case.md)
      + [Création d’un workflow de ciblage](delivery/using/a-b-testing-uc-targeting-workflow.md)
      + [Configuration des échantillons de population](delivery/using/a-b-testing-uc-population-samples.md)
      + [Création des modèles de diffusion](delivery/using/a-b-testing-uc-delivery-templates.md)
      + [Configuration des diffusions](delivery/using/a-b-testing-uc-configuring-deliveries.md)
      + [Création du script](delivery/using/a-b-testing-uc-script.md)
      + [Définition de la diffusion finale](delivery/using/a-b-testing-uc-final-delivery.md)
      + [Démarrez le workflow](delivery/using/a-b-testing-uc-start-workflow.md)
      + [Analyse du résultat](delivery/using/a-b-testing-uc-analyzing.md)
  + Services et abonnements {#subscriptions-and-referrals}
    + [À propos des services et des abonnements](delivery/using/about-services-and-subscriptions.md)
    + [Gestion des abonnements](delivery/using/managing-subscriptions.md)
    + [Marketing viral et réseaux sociaux](delivery/using/viral-and-social-marketing.md)
  + Surveiller les diffusions {#monitoring-deliveries}
    + [Surveiller les performances de diffusion](delivery/using/about-delivery-monitoring.md)
    + [Suivre les messages](delivery/using/about-message-tracking.md)
    + [Performances des diffusions et résolution des problèmes](delivery/using/delivery-performance-troubleshooting.md)
    + [Diffusions en échec et gestion des quarantaines](delivery/using/delivery-failures-quarantine.md)
    + [Avancé : personnalisation des logs de diffusion](delivery/using/customize-delivery-logs.md)
  + Gestion de la délivrabilité {#deliverability-management}
    + [Qu’est-ce que la délivrabilité ?](delivery/using/about-deliverability.md)
    + [Rendu de la boîte de réception](delivery/using/inbox-rendering.md)
    + [Résolution des problèmes](delivery/using/deliverability-faq.md)
  + Module de gestion de contenu {#content-management}
    + [À propos de la gestion de contenu](delivery/using/about-content-management.md)
    + [Ressources et principes de la gestion de contenu](delivery/using/content-manager-resources-and-principles.md)
    + [Cas pratique : utiliser la gestion de contenu](delivery/using/use-case-creating-content-management.md)
    + [Schémas de données](delivery/using/data-schemas.md)
    + [Formulaires de saisie](delivery/using/input-forms.md)
    + [Mise en forme](delivery/using/formatting.md)
    + [Modèle de publication](delivery/using/publication-templates.md)
    + [Utilisation d’un modèle de contenu](delivery/using/using-a-content-template.md)
    + [Enrichissement du contenu](delivery/using/enriching-content.md)
    + [Automatisation par workflows](delivery/using/automating-via-workflows.md)
+ [Orchestrer des campagnes marketing](campaign/using/about-marketing-campaigns.md)
+ Gestion de la réaction {#response-manager}
  + [Prise en main de la gestion de la réaction](response/using/about-response-manager.md)
  + [Configuration](response/using/configuration.md)
  + [Modèles d&#39;hypothèse](response/using/hypothesis-templates.md)
  + [Création d’hypothèses](response/using/creating-hypotheses.md)
  + [Suivi des hypothèses](response/using/hypothesis-tracking.md)
+ Concevoir et partager des rapports {#reporting}
  + Commencer avec les rapports {#reporting-in-adobe-campaign}
    + [Bonnes pratiques en matière de reporting](reporting/using/best-practices.md)
  + Accéder aux rapports intégrés {#accessing-built-in-reports}
    + [À propos des rapports natifs](reporting/using/about-campaign-built-in-reports.md)
    + [Liste des rapports](reporting/using/list-of-reports.md)
  + Rapports sur les diffusions{#reports-on-deliveries}
    + [Calcul des indicateurs](reporting/using/indicator-calculation.md)
  + Analyser les populations {#analyzing-populations}
    + [Présentation de l’analyse descriptive](reporting/using/about-descriptive-analysis.md)
    + [Création de votre premier rapport d’analyse descriptive](reporting/using/using-the-descriptive-analysis-wizard.md)
    + [Gestion et configuration de votre rapport d’analyse](reporting/using/processing-a-report.md)
    + [Cas dʼutilisation de rapports d’analyse](reporting/using/use-cases.md)
  + Créer des rapports {#creating-new-reports}
    + [Étapes clés de la conception d’un rapport](reporting/using/about-reports-creation-in-campaign.md)
    + [Création d’un rapport](reporting/using/creating-a-new-report.md)
    + [Collecte des données à analyser](reporting/using/collecting-data-to-analyze.md)
    + [Utilisation du contexte](reporting/using/using-the-context.md)
    + [Création d’un tableau](reporting/using/creating-a-table.md)
    + [Création d’un graphique](reporting/using/creating-a-chart.md)
    + [Disposer les éléments](reporting/using/element-layout.md)
    + [Définition d’un contenu conditionnel](reporting/using/defining-a-conditional-content.md)
    + [Fonctionnalités avancées](reporting/using/advanced-functionalities.md)
    + [Propriétés du rapport](reporting/using/properties-of-the-report.md)
    + [Configuration de l’accès au rapport](reporting/using/configuring-access-to-the-report.md)
    + [Agir sur les rapports](reporting/using/actions-on-reports.md)
  + [Concevoir des rapports avec des cubes](reporting/using/ac-cubes.md)
+ Concevoir du contenu web {#designing-content}
  + Applications web {#web-applications}
    + [Prise en main des applications web](web/using/about-web-applications.md)
    + [Création d’une application web](web/using/creating-a-new-web-application.md)
    + [Conception d’une application web](web/using/designing-a-web-application.md)
    + [Cas d’utilisation : création de vues d’ensemble](web/using/use-cases-creating-overviews.md)
    + [Traduction d’une application web](web/using/translating-a-web-application.md)
    + [Tracking des visites sur une application web](web/using/tracking-a-web-application.md)
    + [Désinscription (opt-out) du tracking des applications web](web/using/web-application-tracking-opt-out.md)
  + Modifier du contenu HTML {#editing-html-content}
    + [Prise en main de l’éditeur HTML](web/using/about-campaign-html-editor.md)
    + [Gestion des modèles](web/using/template-management.md)
    + [Interface de l&#39;éditeur de contenu](web/using/content-editor-interface.md)
    + [Modification du contenu](web/using/editing-content.md)
    + [Bonnes pratiques relatives à l&#39;édition de contenu](web/using/content-editing-best-practices.md)
    + [Création d’une landing page](web/using/creating-a-landing-page.md)
    + [Cas d’utilisation : création d’une diffusion email](web/using/use-case-creating-an-email-delivery.md)
  + Formulaires web {#web-forms}
    + [Prise en main des formulaires web](web/using/about-web-forms.md)
    + [Utilisation d’un modèle de formulaire web](web/using/using-a-web-form-template.md)
    + [Ajout de champs à un formulaire web](web/using/adding-fields-to-a-web-form.md)
    + [Eléments statiques dans un formulaire web](web/using/static-elements-in-a-web-form.md)
    + [Définition de la disposition des formulaires web](web/using/defining-web-forms-layout.md)
    + [Rendu du formulaire](web/using/form-rendering.md)
    + [Définition de l’enchaînement des pages](web/using/defining-web-forms-page-sequencing.md)
    + [Enregistrement des réponses aux formulaires web](web/using/web-forms-answers.md)
    + [Publication d’un formulaire web](web/using/publishing-a-web-form.md)
    + [Définition des propriétés des formulaires web](web/using/defining-web-forms-properties.md)
    + [Traduction d’un formulaire web](web/using/translating-a-web-form.md)
    + [Cas pratiques : formulaires web](web/using/use-cases-web-forms.md)
+ Créer des questionnaires en ligne {#online-surveys}
  + [Prise en main des questionnaires](surveys/using/about-surveys.md)
  + [Étapes clés de création d’un questionnaire](surveys/using/getting-started-with-surveys.md)
  + [Conception d’un questionnaire](surveys/using/building-a-survey.md)
  + [Gestion des réponses](surveys/using/managing-answers.md)
  + [Publier, suivre et utiliser les données collectées](surveys/using/publish-track-and-use-collected-data.md)
  + [Configuration des questionnaires](surveys/using/configuring-surveys.md)
  + [Cas d’utilisation : création d’un formulaire de référence](surveys/using/use-case-creating-a-refer-a-friend-form.md)
  + [Cas d’utilisation : affichage d’un rapport sur les réponses à un questionnaire en ligne](surveys/using/use-case-displaying-report-on-answers-to-an-online-survey.md)
+ Intégrer à Adobe Experience Cloud {#integrating-with-adobe-experience-cloud}
  + [Commencer avec les intégrations de Campaign](integrations/using/about-campaign-integrations.md)
  + [Créer votre compte technique Adobe](integrations/using/oauth-technical-account.md)
  + Triggers Adobe Experience Cloud {#experience-triggers}
    + [Utilisation de  [!DNL Experience Cloud Triggers]](integrations/using/about-triggers.md)
    + [Configuration du pipeline](integrations/using/configuring-pipeline.md)
    + [Configuration d’événements pour une implémentation personnalisée](integrations/using/events.md)
    + [Surveillance du pipeline](integrations/using/pipeline-monitoring.md)
    + [Dépannage du pipeline](integrations/using/pipeline-troubleshooting.md)
  + Sources et destinations Adobe Experience Platform {#aep-sources-destinations}
    + [Utilisation des sources et des destinations](integrations/using/get-started-sources-destinations.md)
    + [Ingérer des audiences Adobe Experience Platform dans Campaign](integrations/using/ingest-aep-data.md)
    + [Exporter des données de Campaign vers Adobe Experience Platform](integrations/using/export-campaign-data.md)
  + Connecteur Adobe Analytics{#analytics-connector}
    + [Prise en main du connecteur Adobe Analytics](integrations/using/gs-aa.md)
    + [Approvisionnement du connecteur Adobe Analytics](integrations/using/adobe-analytics-provisioning.md)
  + Partage d’audiences {#audience-sharing}
    + [Partage des audiences avec [!DNL Adobe Experience Cloud]](integrations/using/sharing-audiences-with-adobe-experience-cloud.md)
    + [Envoi d’une requête à Adobe](integrations/using/submitting-request-to-adobe.md)
    + [Configuration de l’intégration des audiences partagées dans [!DNL Adobe Campaign]](integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
    + {hide-from-toc}[Résolution des problèmes](integrations/using/troubleshooting.md)
    + [Importation et exportation des audiences](integrations/using/importing-and-exporting-audiences.md)
  + Partage de ressources {#asset-sharing}
    + [Partage de ressources avec [!DNL Adobe Experience Cloud]](integrations/using/sharing-assets-with-adobe-experience-cloud.md)
    + [Configuration de l’accès à [!DNL Assets]](integrations/using/configuring-access-to-assets.md)
    + [Insertion d’une ressource partagée](integrations/using/inserting-a-shared-asset.md)
  + Adobe Experience Manager {#adobe-experience-manager}
    + [Utilisation d’ [!DNL Adobe Experience Manager]](integrations/using/about-adobe-experience-manager.md)
    + [Configuration de l’intégration](integrations/using/configuring-the-integration.md)
    + [Création d’une [!DNL Experience Manager] newsletter](integrations/using/creating-an-experience-manager-newsletter.md)
  + Adobe Target {#adobe-target}
    + [Utilisation d’ [!DNL Adobe Target]](integrations/using/integrating-with-adobe-target.md)
    + [Configuration de l’intégration avec [!DNL Adobe Target]](integrations/using/configuring-the-integration-with-adobe-target.md)
    + [Insertion d’une image dynamique](integrations/using/inserting-a-dynamic-image.md)
  + Connecteur ACS {#acs-connector}
    + {hide-from-toc}[Commencer avec  [!DNL ACS Connector]  - MASQUÉ](integrations/using/acs-connector-principles-and-data-cycle.md)
    + {hide-from-toc}[Synchroniser des profils - MASQUÉ](integrations/using/synchronizing-profiles.md)
    + {hide-from-toc}[Synchroniser des audiences - MASQUÉ](integrations/using/synchronizing-audiences.md)
    + {hide-from-toc}[Synchroniser des applications web - MASQUÉ](integrations/using/synchronizing-web-applications.md)
    + {hide-from-toc}[Résoudre des problèmes liés au  [!DNL ACS Connector]  - MASQUÉ](integrations/using/troubleshooting-the-acs-connector.md)
+ [Automatiser avec des workflows](workflow/using/about-workflows.md)
+ Gestion des offres {#managing-offers}
  + Commencer avec Interaction {#interaction-overview}
    + [Interaction et la gestion des offres](interaction/using/interaction-and-offer-management.md)
  + Gérer le catalogue d’offres {#managing-an-offer-catalog}
    + [Validation et activation d’une offre](interaction/using/approving-and-activating-an-offer.md)
    + [Gestion des modèles d’offre](interaction/using/managing-offer-templates.md)
    + [Gestion de la présentation des offres](interaction/using/managing-offer-presentation.md)
  + Simulation d’offres{#simulating-offers}
    + [À propos de la simulation des offres](interaction/using/about-offers-simulation.md)
    + [Paramètres d&#39;exécution](interaction/using/execution-settings.md)
    + [Périmètre de la simulation](interaction/using/simulation-scope.md)
    + [Suivi des simulations](interaction/using/simulation-tracking.md)
  + Paramètres avancés {#advanced-parameters}
    + [Utilisation des paramètres avancés](interaction/using/using-advanced-parameters.md)
    + [Additional data](interaction/using/additional-data.md)
    + [Exemple d&#39;extension](interaction/using/extension-example.md)
    + [Création d’un environnement de test](interaction/using/creating-a-test-environment.md)
    + [Modifier le comportement standard du moteur](interaction/using/hooks.md)
    + [Architectures réparties](interaction/using/distributed-architectures.md)
    + [Configuration du buffer de données](installation/using/interaction-data-buffer.md)
  + Cas d’utilisation {#case-study}
    + [Règles de présentation](interaction/using/presentation-rules.md)
    + [Offres sur canal entrant](interaction/using/offers-on-an-inbound-channel.md)
    + [Offres sur canal sortant](interaction/using/offers-on-an-outbound-channel.md)
+ Messages transactionnels {#transactional-messaging}
  + [Commencer avec les messages transactionnels](message-center/using/about-transactional-messaging.md)
  + Configurer les messages transactionnels {#configure-transactional-messaging}
    + [Architecture des messages transactionnels](message-center/using/transactional-messaging-architecture.md)
    + [Configuration des instances](message-center/using/configuring-instances.md)
    + [Paramétrages additionnels](message-center/using/additional-configurations.md)
  + Modèles de message {#message-templates}
    + [Test de modèles de message](message-center/using/testing-message-templates.md)
  + [Cas d’utilisation](message-center/using/transactional-email-with-attachments.md)
+ Intégrer aux médias sociaux {#integrating-with-social-media}
  + [À propos du marketing des médias sociaux](social/using/about-social-marketing.md)
+ Guide d’installation et de configuration {#installing-campaign-classic}
  + Principes d’architecture {#architecture-and-hosting-models}
    + [Architecture générale](installation/using/general-architecture.md)
    + Modèles d’hébergement{#hosting-models-lp}
      + [Modèles d’hébergement Campaign](installation/using/hosting-models.md)
      + [Matrice des fonctionnalités](installation/using/capability-matrix.md)
  + Types de déploiements {#deployment-types}
    + [À propos des types de déploiement](installation/using/about-deployment-types.md)
    + [Déploiement Stand-alone](installation/using/standalone-deployment.md)
    + [Déploiement Standard](installation/using/standard-deployment.md)
    + [Déploiement Entreprise](installation/using/enterprise-deployment.md)
    + [Déploiement Mid-sourcing](installation/using/mid-sourcing-deployment.md)
    + [Power Booster et Power Cluster](installation/using/power-booster-and-power-cluster.md)
  + Paramètres relatifs à la sécurité et à la confidentialité {#security-privacy}
    + [Liste de contrôle relative à la sécurité et à la confidentialité](installation/using/get-started-security-privacy.md)
    + [Personnalisation et confidentialité](installation/using/privacy.md)
    + [Gestion des accès sécurisés](installation/using/access-management.md)
    + [Instructions relatives aux scripts et au codage](installation/using/scripting-coding-guidelines.md)
    + [Réseau, base de données et SSL/TLS](installation/using/network-database.md)
    + [Paramètres de sécurité du serveur](installation/using/server-configuration.md)
    + [Paramètres de sécurité du serveur web](installation/using/web-server-configuration.md)
  + Installer Campaign (On-premise){#install-campaign-on-prem}
    + Instructions de déploiement {#deployment-guidelines}
      + [Serveur de base de données](installation/using/database.md)
      + [Serveur applicatif](installation/using/application-server.md)
      + [Serveur de messagerie](installation/using/messaging-server.md)
      + [Configuration réseau](installation/using/network-configuration.md)
    + Campaign sous Windows {#installing-campaign-in-windows}
      + [Commencer](installation/using/prerequisites-of-campaign-installation-in-windows.md)
      + [Installation du serveur](installation/using/installing-the-server.md)
      + [Intégration dans un serveur web (Windows)](installation/using/integration-into-a-web-server-for-windows.md)
      + [Disponibilité de la console cliente pour Windows](installation/using/client-console-availability-for-windows.md)
    + Campaign sous Linux {#installing-campaign-in-linux}
      + [Conditions préalables](installation/using/prerequisites-of-campaign-installation-in-linux.md)
      + [Installation de packages](installation/using/installing-packages-with-linux.md)
      + [Intégration dans un serveur web](installation/using/integration-into-a-web-server-for-linux.md)
    + [Gestion des fuseaux horaires](installation/using/time-zone-management.md)
    + [Installation d’un serveur de midsourcing](installation/using/mid-sourcing-server.md)
    + Déployer Campaign (On-premise) {#initial-configuration}
      + [Principales étapes](installation/using/about-initial-configuration.md)
      + [Création d’une instance et connexion](installation/using/creating-an-instance-and-logging-on.md)
      + [Créer et paramétrer la base de données](installation/using/creating-and-configuring-the-database.md)
      + [Déploiement d’une instance](installation/using/deploying-an-instance.md)
      + [Installation de packages natifs](installation/using/installing-campaign-standard-packages.md)
  + Configurer Campaign {#additional-configurations}
    + [Paramétrage du serveur Campaign](installation/using/configuring-campaign-server.md)
    + [Définition de zones de sécurité](installation/using/security-zones.md)
    + [Définition des autorisations d’URL](installation/using/url-permissions.md)
    + [Fichiers et ressources](installation/using/file-res-management.md)
    + [Configurer Tomcat](installation/using/configure-tomcat.md)
    + [Configurer les paramètres de diffusion](installation/using/configure-delivery-settings.md)
    + [Configurations techniques du canal e-mail](installation/using/email-deliverability.md)
    + {hide-from-toc}[Utilisation de serveurs MX avec Campaign](installation/using/using-mx-servers.md)
    + [Configuration du Cci d’email](installation/using/email-archiving.md)
    + [Configuration de SpamAssassin](installation/using/configuring-spamassassin.md)
  + Se connecter à Campaign{#connect-to-campaign}
    + [Installer la console cliente](installation/using/installing-the-client-console.md)
    + Se connecter via un Adobe ID {#connecting-via-an-adobe-id}
      + [À propos de [!DNL Adobe ID]](integrations/using/about-adobe-id.md)
      + [Configuration d’Adobe [!DNL IMS]](integrations/using/configuring-ims.md)
      + [Implémentation d’Adobe [!DNL IMS]](integrations/using/implementing-ims.md)
      + [Dépanner IMS](integrations/using/ims-troubleshooting.md)
    + [Connexion via LDAP](installation/using/connecting-through-ldap.md)
  + Connecter Campaign à des systèmes externes {#accessing-external-database}
    + [Configurer des comptes externes](installation/using/external-accounts.md)
    + Configurer Federated Data Access{#configure-fda}
      + [Prise en main de Federated Data Access](installation/using/about-fda.md)
      + [Bonnes pratiques et limites](installation/using/fda-best-practices.md)
      + Directives de configuration {#config-databases}
        + [Étapes de configuration](installation/using/configure-fda.md)
        + [Configurer Amazon Redshift](installation/using/configure-fda-redshift.md)
        + [Configurer Azure Synapse](installation/using/configure-fda-synapse.md)
        + [Configurer Google BigQuery](installation/using/configure-fda-google-big-query.md)
        + [Configurer Hadoop](installation/using/configure-fda-hadoop.md)
        + [Configurer Microsoft SQL Server](installation/using/configure-fda-sql.md)
        + [Configurer Netezza](installation/using/configure-fda-netezza.md)
        + [Configurer Oracle](installation/using/configure-fda-oracle.md)
        + [Configurer PostgreSQL](installation/using/configure-fda-postgresql.md)
        + [Configurer SAP HANA](installation/using/configure-fda-sap-hana.md)
        + [Configurer Snowflake](installation/using/configure-fda-snowflake.md)
        + [Configurer Sybase IQ](installation/using/configure-fda-sybase.md)
        + [Configurer Teradata](installation/using/configure-fda-teradata.md)
        + [Configurer Vertica Analytics](installation/using/configure-fda-vertica.md)
    + [Droits d’accès distants](installation/using/remote-database-access-rights.md)
    + [Connexion à la base de données](installation/using/connecting-to-database.md)
    + [Création du schéma de données](installation/using/creating-data-schema.md)
    + [Définition du mapping des données](installation/using/defining-data-mapping.md)
  + Annexes {#appendices}
    + [Fichier de configuration du serveur](installation/using/the-server-configuration-file.md)
    + [Points d’entrée réseau Campaign](installation/using/campaign-network-endpoints.md)
    + [Lignes de commande](installation/using/command-lines.md)
    + [Création d’instances](installation/using/creating-new-instances.md)
    + [Liste des options de Campaign](installation/using/configuring-campaign-options.md)
    + {hide-from-toc}[Désinstaller Campaign](installation/using/uninstalling-campaign.md)
    + [Installation de nouvelles polices](installation/using/install-fonts.md)
+ Guide de surveillance {#monitoring-campaign-classic}
  + Introduction {#introduction}
    + [Avant-propos](production/using/foreword.md)
    + [Architecture générale](production/using/general-architecture.md)
    + [Directives de su](production/using/monitoring-guidelines.md)
  + Procédures d’exploitation {#production-procedures}
    + [Principe de configuration](production/using/configuration-principle.md)
    + [Principe de fonctionnement](production/using/operating-principle.md)
    + [Administration](production/using/administration.md)
    + [Configuration](production/using/configuration.md)
    + [Fichiers de log](production/using/log-files.md)
    + [Surveillance des processus](production/using/monitoring-processes.md)
    + [Commandes usuelles](production/using/usual-commands.md)
    + [Journal d’audit](production/using/audit-trail.md)
  + Traitement des données {#data-processing}
    + [Sauvegarde](production/using/backup.md)
    + [Restauration](production/using/restoration.md)
    + [Duplication d&#39;environnements](production/using/duplicating-environments.md)
    + [Workflow de nettoyage de la base de données](production/using/database-cleanup-workflow.md)
  + Mettre à jour Adobe Campaign {#updating-adobe-campaign}
    + [Introduction](production/using/introduction.md)
    + [Exécution d’une mise à niveau de build](production/using/build-upgrade.md)
    + [Procédure de mise à niveau (On-Premise)](production/using/upgrading.md)
    + [Basculement vers Unicode](production/using/switching-to-unicode.md)
    + {hide-from-toc}[Procédures de migration](production/using/migration-procedures.md)
  + Maintenance de la base de données {#database-maintenance}
    + [Recommandations](production/using/recommendations.md)
    + [Tables à maintenir](production/using/tables-to-maintain.md)
    + [Types de maintenance](production/using/types-of-maintenance.md)
    + [Recommandations spécifiques au SGBDR](production/using/rdbms-specific-recommendations.md)
    + [Objets d&#39;application](production/using/application-objects.md)
  + Résolution des problèmes {#troubleshooting-toc}
    + [Vue d’ensemble de la résolution des problèmes de production](production/using/troubleshooting.md)
    + Questions courantes et générales {#common-general-issues-toc}
      + [Modules et problèmes courants](production/using/modules-and-frequent-issues.md)
      + [Exécution des workflows](production/using/workflow-execution.md)
      + [Perte de mot de passe](production/using/lost-password.md)
      + [Mise à jour de la console](production/using/console-update.md)
    + Résolution des problèmes liés aux diffusions {#delivery-troubleshooting-toc}
      + [Problèmes de performance et de débit](production/using/performance-and-throughput-issues.md)
      + [Problèmes liés à l&#39;affichage des images](production/using/image-display-issues.md)
      + [Images absentes](production/using/images-missing.md)
      + [Fichiers temporaires](production/using/temporary-files.md)
    + Utilisation des logs {#working-with-log-toc}
      + [Précision des logs](production/using/log-precision.md)
      + [Problèmes relatifs aux logs de tracking](production/using/tracking-logs-issues.md)
    + Problèmes de base de données {#database-issues-toc}
      + [Performances de la base de données](production/using/database-performances.md)
      + [Encodage de la base Oracle](production/using/encoding-of-the-oracle-database.md)
    + Améliorations de la connexion {#connection-improvements-toc}
      + [Connexion impossible](production/using/failure-to-connect.md)
      + [Seuil de connexions](production/using/connection-thresholds.md)
    + Résolution des problèmes techniques {#technical-troubleshooting-toc}
      + [Stack trace sous Linux](production/using/stack-trace-in-linux.md)
      + [Comportement des JSP](production/using/jsp-behavior.md)
      + [Localisation de la version de Tomcat](production/using/locate-tomcat-version.md)
+ Guide de développement {#configuring-campaign-classic}
  + [Packages de données](platform/using/working-with-data-packages.md)
  + Modèle de données {#data-model}
    + [Description du modèle de données](configuration/using/data-model-description.md)
    + [Bonnes pratiques](configuration/using/data-model-best-practices.md)
  + Utiliser les schémas {#schema-reference}
    + [Prise en main des schémas](configuration/using/about-schema-reference.md)
    + [Structure d&#39;un schéma](configuration/using/schema-structure.md)
    + [Mapping de la base de données](configuration/using/database-mapping.md)
    + [Gestion des clés](configuration/using/database-keys.md)
    + Éléments et attributs {#elements-attributes}
      + [Introduction](configuration/using/schema-introduction.md)
      + [Attribut](configuration/using/schema/attribute.md)
      + [Compute string](configuration/using/schema/compute-string.md)
      + [Condition](configuration/using/schema/condition.md)
      + [Index de base de données](configuration/using/schema/db-index.md)
      + [Élément](configuration/using/schema/element.md)
      + [Énumération](configuration/using/schema/enumeration.md)
      + [Aide](configuration/using/schema/help.md)
      + [Jointure](configuration/using/schema/join.md)
      + [Clé](configuration/using/schema/key.md)
      + [Keyfield](configuration/using/schema/keyfield.md)
      + [Méthodologie](configuration/using/schema/method.md)
      + [Méthodes](configuration/using/schema/methods.md)
      + [Param](configuration/using/schema/param.md)
      + [Paramètres](configuration/using/schema/parameters.md)
      + [SrcSchema](configuration/using/schema/srcschema.md)
      + [SysFilter](configuration/using/schema/sysfilter.md)
      + [Valeur](configuration/using/schema/value.md)
  + Modification des schémas {#editing-schemas}
    + [Schéma d&#39;une table existante](configuration/using/schema-of-an-existing-table.md)
    + [Extension d&#39;un schéma](configuration/using/extending-a-schema.md)
    + [Mettre à jour la structure de la base de données](configuration/using/updating-the-database-structure.md)
    + [Nouvel assistant d’ajout de champs](configuration/using/new-field-wizard.md)
    + [Structure d’un schéma de données](configuration/using/structure-of-a-data-schema.md)
    + [Régénération des schémas](configuration/using/regenerating-schemas.md)
    + [Exemples d&#39;édition de schémas](configuration/using/examples-of-schemas-edition.md)
  + Formulaires de saisie {#input-forms}
    + [Modifier des formulaires](configuration/using/editing-forms.md)
  + API {#api}
    + [À propos des services web](configuration/using/about-web-services.md)
    + [Appels Web Service](configuration/using/web-service-calls.md)
    + [API orientées données](configuration/using/data-oriented-apis.md)
    + [API orientées métier](configuration/using/business-oriented-apis.md)
    + [Implémenter des méthodes SOAP](configuration/using/implementing-soap-methods.md)
    + [Méthodes SOAP en JavaScript](configuration/using/soap-methods-in-javascript.md)
    + [Ajout d&#39;autres fonctions SQL](configuration/using/adding-additional-sql-functions.md)
  + Arborescence de navigation {#navigation-hierarchy}
    + [Configuration de la hiérarchie de l’explorateur](configuration/using/configuration.md)
    + [Modification de la hiérarchie de l’explorateur](configuration/using/edition.md)
  + Utiliser un tableau des destinataires personnalisé {#use-a-custom-recipient-table}
    + [À propos de la table des destinataires personnalisée](configuration/using/about-custom-recipient-table.md)
    + [Caractéristiques du schéma](configuration/using/schema-characteristics.md)
    + [Mapping de ciblage](configuration/using/target-mapping.md)
    + [Configuration de l&#39;interface](configuration/using/configuring-the-interface.md)
    + [Adresses de contrôle](configuration/using/seed-addresses.md)
    + [Création de filtres](configuration/using/creating-filters.md)
    + [Création d&#39;une liste de profils avec un workflow](configuration/using/creating-a-profile-list-with-a-workflow.md)
    + [Gestion des workflows](configuration/using/managing-workflows.md)
    + [Gestion des rapports](configuration/using/managing-reports.md)
  + Mise en place du tracking web {#setting-up-web-tracking}
    + [À propos du tracking web](configuration/using/about-web-tracking.md)
    + [Mode de tracking web](configuration/using/web-tracking-mode.md)
    + [Balise de tracking web : définition](configuration/using/web-tracking-tag-definition.md)
    + [Etapes de mise en place](configuration/using/setup-stages.md)
    + [Paramètres supplémentaires](configuration/using/additional-parameters.md)
    + [Créer les balises de tracking web](configuration/using/creating-web-tracking-tags.md)
    + [Insertion des balises sur votre site](configuration/using/inserting-tags-in-your-site.md)
    + [Collecter toutes les visites](configuration/using/collecting-all-visits.md)
    + [Tracking anonyme](configuration/using/anonymous-tracking.md)
+ Guide de migration {#migrating-to-a-new-version}
  + {hide-from-toc}[Migrer vers Adobe Campaign v7](migration/using/about-migration.md)
  + Procédure de migration {#migration-procedure}
    + {hide-from-toc}[Prérequis](migration/using/before-starting-migration.md)
    + {hide-from-toc}[À propos des tests de migration](migration/using/testing-the-migration.md)
    + {hide-from-toc}[Adapter votre configuration](migration/using/configuring-your-platform.md)
  + Démarrer la migration {#migrating-to-adobe-campaign-7}
    + {hide-from-toc}[Migrer une plateforme Microsoft Windows](migration/using/migrating-in-windows-for-adobe-campaign-7.md)
    + {hide-from-toc}[Migrer une plateforme Linux](migration/using/migrating-in-linux-for-adobe-campaign-v7.md)
  + {hide-from-toc}[Procédure de restauration](migration/using/about-rollback.md)
+ Notes techniques {#technotes}
  + [Recommandations relatives au dimensionnement du matériel](technotes/using/hardware-sizing.md)
  + [Envoyer avec le MTA amélioré](delivery/using/sending-with-enhanced-mta.md)
  + [Activité de workflow de SMS entrants pour une infrastructure de midsourcing](technotes/using/inbound-sms-wf.md)
  + Mettre à niveau vers IMS{#ims}
    + [Transition vers Adobe IMS](technotes/using/ac-ims.md)
    + [Migrer les utilisateurs et utilisatrices vers IMS](technotes/using/migrate-users-to-ims.md)
    + [Migrer un opérateur ou une opératrice technique vers Developer Console](technotes/using/ims-migration.md)
    + [Impact de l’interface après la migration IMS](technotes/using/impact-ims-migration.md)
  + Mises à niveau et compatibilité{#technote-migration}
    + [Activer Microsoft Edge Chromium](technotes/using/edge-chromium.md)
    + {hide-from-toc}[Nouveau serveur de délivrabilité](technotes/using/deliverability-server.md)
    + {hide-from-toc}[Mise à niveau de la sécurité d’Apache](technotes/using/acc-apache-upgrade.md)
    + {hide-from-toc}[Mises à niveau du système en 2023](technotes/using/tech-stack-upgrade.md)
    + {hide-from-toc}[Mises à jour dʼIMS](technotes/using/ims-updates.md)
    + {hide-from-toc}[Migrer vers l’API Adobe Analytics 2.0](technotes/using/analytics-2-migration.md)
  + Emails et notifications push{#technotes-email}
    + [Protection de la confidentialité des emails sur Apple iOS](technotes/using/apple-mail-app-privacy-protection.md)
    + [Mise à jour du certificat iOS](technotes/using/ios-certificate-update.md)
    + {hide-from-toc}[Mise à jour des URL suivies](technotes/using/tracked-urls.md)
  + Migration vers Adobe Managed Services{#dc-migration}
    + [Migration vers le cloud public](technotes/using/dc-migration.md)
    + [FAQ](technotes/using/dc-migration-faq.md)
  + [Fonctions basées sur GCM](technotes/using/gcm-functions.md)
+ [Panneau de contrôle Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=fr)
