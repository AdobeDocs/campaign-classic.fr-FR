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
translation-type: ht
source-git-commit: a3b5378c2e67b9982fa425f32e14e0b1c66e1bf3
workflow-type: ht
source-wordcount: '1751'
ht-degree: 100%

---


# Informations personnelles et consentement{#privacy-and-recommendations}

## Recommandations générales {#general-recommendations}

Adobe Campaign est un outil puissant pour collecter et traiter de très grands volumes de données, notamment des informations personnelles et des données sensibles. C’est pourquoi la confidentialité doit être gérée avec soin.

* Utilisez toujours les informations personnelles de façon éthique et responsable.

* N’envoyez pas d’emails, de notifications Push ni de SMS non sollicités (« spam »). Adobe croit fermement aux principes du consentement (permission marketing) pour fidéliser le client et offrir une valeur ajoutée tout au long de sa durée de vie et interdit donc strictement l’utilisation d’Adobe Campaign pour l’envoi de messages non sollicités.

Prenez le temps de consulter la [liste de contrôle de sécurité et de confidentialité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html) afin de connaître les principaux éléments à vérifier en termes de sécurité et de confidentialité.

### Règlements relatifs à la confidentialité {#privacy-regulations}

Pour gérer correctement la confidentialité et les données personnelles, travaillez dans le cadre des législations applicables à la ou aux région(s) où vous opérez. Ces règlements comprennent :
* [RGPD](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_fr) (Règlement général européen sur la protection des données)
* [DPA](https://www.gov.uk/data-protection) (mise en œuvre du RGPD au Royaume-Uni)
* [Directive européenne sur la protection de la vie privée et les communications électroniques](https://eur-lex.europa.eu/legal-content/FR/TXT/?uri=CELEX:02002L0058-20091219)
* [CAN-SPAM Act](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business) (loi des États-Unis fixant les règles et les exigences pour les emails commerciaux)
* [CCPA](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5.&amp;part=4.&amp;chapter=&amp;article=) (California Consumer Privacy Act, loi californienne sur la protection des données)
* [PDPA](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/) (loi thaïlandaise sur la protection des données personnelles)
* [LGPD](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf) (loi brésilienne générale sur la protection des données) - entrera en vigueur le 16 août 2020

>[!NOTE]
>
>Pour plus d’informations sur la façon dont le RGPD, le CCPA, la PDPA et la LGPD s’appliquent à Adobe Campaign, consultez [cette page](https://helpx.adobe.com/fr/campaign/kb/campaign-privacy-overview.html#whatisgdpr).

### Confidentialité d’Adobe Experience Cloud {#experience-cloud-privacy}

Adobe Campaign fait partie des solutions Adobe Experience Cloud. La façon dont la confidentialité est gérée dans Campaign obéit aux principes généraux d’Experience Cloud, tels que :

* **Informations collectées lors de l’utilisation d’Adobe Experience Cloud**

   En tant que société utilisant les solutions Adobe Experience Cloud, vous choisissez les informations à collecter et à envoyer à votre compte Adobe Experience Cloud. Parmi les types d’informations pouvant être collectées, citons l’activité de navigation web, les adresses IP, les informations d’emplacement des périphériques mobiles, les taux de succès des campagnes, les articles achetés ou placés dans le panier, etc.

   >[!NOTE]
   >
   >Comme pour tous les produits Adobe, Campaign collecte des informations sur les utilisateurs des applications et des sites web. Pour plus d’informations à ce sujet, consultez la [Politique de confidentialité d’Adobe](https://www.adobe.com/fr/privacy/policy.html).

* **Utilisation d’Adobe Experience Cloud pour la collecte d’informations**

   * Les solutions Adobe Experience Cloud utilisent des cookies et des technologies similaires, telles que des balises web (également appelées pixels), pour vous permettre de collecter des informations. Pour plus d’informations sur les cookies et les fonctionnalités de tracking d’Adobe Campaign, consultez [cette section](#tracking-capabilities).
   * Vous pouvez également utiliser les technologies Adobe Experience Cloud dans vos applications mobiles. Pour plus d’informations sur l’envoi de diffusions mobiles avec Campaign, reportez-vous à la page [canal SMS](../../delivery/using/sms-channel.md) et [canal d’application mobile](../../delivery/using/about-mobile-app-channel.md).

* **Choix de confidentialité de vos utilisateurs concernant votre utilisation d’Adobe Experience Cloud**

   Adobe vous demande de fournir à vos clients des politiques de confidentialité décrivant :

   * Vos pratiques de confidentialité en rapport avec Adobe Experience Cloud
   * Comment les utilisateurs peuvent-ils définir leurs préférences pour la collecte ou l’utilisation de leurs informations en relation avec Adobe Experience Cloud ?

   >[!NOTE]
   >
   >En ce qui concerne tous les produits Adobe, les utilisateurs de Campaign peuvent se désinscrire du partage des informations collectées à leur sujet par le biais des applications et des sites web. Pour plus d’informations à ce sujet, consultez la [FAQ sur l’utilisation d’Adobe Experience Cloud](https://www.adobe.com/fr/privacy/experience-cloud-usage-info-faq.html).

Pour plus d’informations sur la confidentialité dans Adobe Experience Cloud, consultez [cette page](https://www.adobe.com/fr/privacy/marketing-cloud.html).

## Données personnelles et personnes {#personal-data}

Lors de la gestion de la confidentialité, il est important de définir quelles données doivent être traitées avec soin et par qui.
* Les **données personnelles** sont des informations qui peuvent identifier directement ou indirectement un individu vivant.
* Les **données personnelles sensibles** regroupent les renseignements relatifs à la race, aux opinions politiques, aux croyances religieuses, aux antécédents criminels, aux données génétiques, aux données sur la santé, à l’orientation sexuelle, aux données biométriques ainsi qu’à l’appartenance à un syndicat.

Les [principales législations](#privacy-regulations) se réfèrent aux différentes entités qui gèrent les données comme suit :
* Les **contrôleurs de données** correspondent aux autorités qui déterminent les moyens et les objectifs de la collecte, de l’utilisation et du partage des données personnelles.
* Les **responsables du traitement des données** correspondent aux individus ou parties qui collectent, utilisent ou partagent les données personnelles, conformément aux instructions du contrôleur de données.
* Les **titulaires de données** sont les personnes vivantes dont les données personnelles sont collectées, utilisées ou partagées, et qui peuvent être identifiées, directement ou indirectement, par référence à ces données personnelles.

Par conséquent, en tant que société de collecte et de partage de données personnelles, vous êtes le contrôleur de données, vos clients sont les titulaires de données et Adobe Campaign agit comme responsable du traitement des données lors du traitement des données personnelles, conformément à vos instructions. Notez qu’en tant que contrôleur de données, il vous appartient de gérer les relations avec les titulaires de données, par exemple lors de la gestion des [demandes d’accès à des informations personnelles](#privacy-requests).

Lors de l’intégration de Campaign à d’autres solutions Experience Cloud dans lesquelles des audiences peuvent être transférées d’un système à un autre, comme [Adobe Analytics](../../platform/using/adobe-analytics-data-connector.md), [Audience Manager ou People core service](../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md), [Campaign Standard](../../integrations/using/synchronizing-audiences.md), ou avec d’autres solutions par l’intermédiaire de [connecteurs CRM](../../platform/using/crm-connectors.md), vous devez veiller à la protection des données personnelles.

## Acquisition de données {#data-acquisition}

Adobe Campaign vous permet de collecter des données, y compris des informations personnelles et sensibles. Il est donc essentiel que vous receviez et surveilliez le consentement de vos destinataires.

* Demandez toujours aux destinataires d’accepter de recevoir des communications. Pour ce faire, continuez à honorer les demandes d’exclusion le plus rapidement possible et vérifiez le consentement par le biais d’un processus de double opt-in. Pour plus d’informations à ce sujet, voir [Créer un formulaire d’abonnement avec double opt-in](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).
* N’importez pas de listes frauduleuses et utilisez des adresses de contrôle pour vérifier que votre fichier client n’est pas utilisé de façon frauduleuse. Pour plus d’informations à ce sujet, voir [A propos des adresses de contrôle](../../delivery/using/about-seed-addresses.md).
* Grâce à la gestion du consentement et des droits, vous pouvez suivre les préférences de vos destinataires et gérer les personnes qui, au sein de votre organisation, peuvent accéder aux différentes données. Pour plus d’informations à ce sujet, consultez [cette section](#consent).
* Faciliter et gérer les demandes d’accès à des informations personnelles de vos destinataires Pour plus d’informations à ce sujet, consultez [cette section](#privacy-requests).

## Gestion de la confidentialité {#privacy-management}

La gestion de la confidentialité se rapporte à tous les processus et outils qui peuvent vous aider à vous conformer aux règlements sur la protection des renseignements personnels (RGPD, CCPA, etc.). Découvrez un aperçu de ce qu’implique la gestion de la confidentialité sur [cette page](https://helpx.adobe.com/fr/campaign/kb/campaign-privacy-overview.html).

Adobe Campaign vous propose divers ensembles de fonctionnalités dédiées à la gestion de la confidentialité :
* Gestion du consentement, rétention des données et rôles utilisateur. Reportez-vous à [cette section](#consent).
* Demandes d’accès à des informations personnelles (droit d’accès et droit à l’oubli). Reportez-vous à [cette section](#privacy-requests).
* Droit d’opposition (opt-out) à la vente des informations personnelles (spécifique au CCPA). Reportez-vous à [cette section](https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html#ccpa).

Les principales fonctionnalités de confidentialité de Campaign et des exemples de personnes impliquées sont présentés dans [cette section](https://helpx.adobe.com/fr/campaign/kb/campaign-privacy-more.html#gdprpersonasandflow).


### Consentement, conservation des données et rôles {#consent}

A l’origine, Adobe Campaign offre des fonctionnalités importantes qui sont essentielles à la confidentialité :

* **Gestion du consentement** : grâce au processus de gestion des abonnements, vous pouvez gérer vos préférences de destinataires et déterminer quels destinataires ont choisi quel type d’abonnement. Pour plus d’informations à ce sujet, consultez la section [A propos des abonnements](../../delivery/using/about-services-and-subscriptions.md).
* **Conservation des données** : toutes les tables de journalisation standard natives comportent des périodes de rétention prédéfinies, limitant généralement le stockage de leurs données à 6 mois maximum. Des périodes de conservation supplémentaires peuvent être définies avec les workflows. Pour plus d’informations à ce sujet, contactez les consultants Adobe ou les administrateurs techniques.
* **Gestion des droits** : Adobe Campaign permet de gérer les droits assignés aux divers opérateurs Campaign par l’intermédiaire de différents rôles préconfigurés ou personnalisés. Cela vous permet de gérer qui dans votre société peut accéder à différents types de données, les modifier ou les exporter. Pour plus d’informations à ce sujet, consultez la section [A propos de la gestion des accès](../../platform/using/access-management.md).

Pour plus d’informations sur ces fonctionnalités et sur la façon de les gérer dans Adobe Campaign, consultez [cette page](https://helpx.adobe.com/fr/campaign/kb/campaign-privacy-overview.html#consent).

### Demandes d’accès à des informations personnelles {#privacy-requests}

Adobe Campaign fournit des fonctionnalités supplémentaires pour vous aider à vous préparer, en tant que contrôleur de données, à gérer certaines demandes d’accès à des informations personnelles :

* Le **droit d’accès** est le droit pour le titulaire de données d’obtenir du contrôleur de données la confirmation que les données personnelles le concernant sont ou non traitées, et lorsqu’elles le sont, où et à quelles fins.

* Le **droit à l’oubli** (demande de suppression) autorise le titulaire de données à effacer ses données personnelles.

>[!NOTE]
>
>Cet ensemble d’outils vous aide à respecter les exigences relatives à la confidentialité énoncées par le RGPD, le CCPA, la PDPA et la LGPD. Pour plus d’informations sur ces différentes réglementations, consultez [cette page](https://helpx.adobe.com/fr/campaign/kb/campaign-privacy-overview.html#whatisgdpr).

<!--* **GDPR** (General Data Protection Regulation) is the European Union’s (EU) privacy law that harmonizes and modernizes data protection requirements. GDPR applies to Adobe Campaign customers who hold data for Data Subjects residing in the EU.

* **CCPA** (California Consumer Privacy Act) provides California residents new rights in regards to their personal information and imposes data protection responsibilities on certain entities whom conduct business in California.

* **Thailand's PDPA** (Personal Data Protection Act) is the new privacy law that harmonizes and modernizes data protection requirements for Thailand. This regulation applies to Adobe Campaign customers who hold data for Data Subjects residing in this country.

Brazil's Lei Geral de Proteção de Dados (LGPD) will be effective starting Aug, 16 for all companies collecting or processing personal data in Brazil. This regulation also applies to Adobe Campaign customers who hold data for Data Subjects residing in this country.-->

Les demandes **d’accès** et de **suppression** sont présentées sur [cette page](https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html#righttoaccess). Les étapes principales pour créer ces requêtes sont détaillées dans [cette section](https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html#ManagingPrivacyRequests). <!--Tutorials are also available [here](https://docs.adobe.com/content/help/en/campaign-standard-learn/tutorials/privacy/privacy-overview.html).-->

## Fonctionnalités de tracking {#tracking-capabilities}

### Cookies {#cookies}

Grâce à ses fonctionnalités de tracking, Adobe Campaign vous permet de suivre la navigation de vos destinataires de diffusion à l’aide de deux types de cookies :

* Un **cookie de session** (nlid). Il contient l’identifiant de l’email envoyé au contact (broadlogId) et l’identifiant du modèle de message (deliveryId). Il est déposé lorsque le contact clique sur une URL contenue dans un email envoyé par Adobe Campaign et permet de tracker son comportement sur le web. Ce cookie de session est effacé automatiquement à la fermeture du navigateur. Le contact a la possibilité d’en interdire le dépôt en adaptant les paramètres de son navigateur.
* Un **cookie permanent** partagé entre les solutions Adobe Experience Cloud. Il permet d’identifier un internaute qui interagit avec les solutions Experience Cloud lors de ses visites sur un site web. La description de ce cookie est disponible [ici](https://docs.adobe.com/content/help/fr/core-services/interface/ec-cookies/cookies-mc.html).

Les règlements tels que le Règlement général sur la protection des données (RGPD) stipulent que les sociétés doivent demander l’accord des utilisateurs du site web avant l’installation de cookies.

* Ainsi, vous devez informer les utilisateurs de vos sites soumis au tracking web via une zone de demande de consentement (par exemple en surimpression de la page) proposant une case à cocher pour autoriser l’utilisation de cookies, ou afficher une bannière en haut de la première page visitée, etc.
* Les fenêtres de type pop-up sont à éviter car elles sont souvent bloquées par les navigateurs.

### Tracking des messages {#message-tracking}

Adobe Campaign vous permet de suivre les emails envoyés et le comportement de vos destinataires de diffusion : ouverture, clics sur des liens, désinscriptions, etc. Pour plus d’informations à ce sujet, consultez la section [A propos du tracking des messages](../../delivery/using/about-message-tracking.md).

Pour ce faire, ajoutez des [liens suivis](../../delivery/using/how-to-configure-tracked-links.md) à vos messages afin de mesurer l’impact de votre diffusion et le comportement du destinataire dans l’onglet [Tracking](../../delivery/using/monitoring-a-delivery.md#tracking-logs) du tableau de bord de diffusion. Les données de suivi sont interprétées dans le rapport des [indicateurs de tracking](../../reporting/using/delivery-reports.md#tracking-indicators).

### Tracking web {#web-tracking}

Adobe Campaign vous permet également de contrôler la manière dont les destinataires naviguent sur votre site web : insérez des balises de tracking pour collecter des informations et mesurer les visites sur les pages d’applications web. Pour plus d’informations à ce sujet, consultez la section [Tracking d’une application web](../../web/using/tracking-a-web-application.md).

Le paramétrage du tracking web est présenté dans [cette section](../../configuration/using/about-web-tracking.md).

Pour mieux gérer le tracking, Adobe Campaign vous permet d’afficher une bannière d’opt-out afin d’arrêter le tracking des comportements web des utilisateurs finaux qui se sont désinscrits du tracking comportemental. Pour plus d’informations à ce sujet, consultez la section [Désinscription (opt-out) du tracking des applications web](../../web/using/web-application-tracking-opt-out.md).
