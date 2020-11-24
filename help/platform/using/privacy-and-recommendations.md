---
solution: Campaign Classic
product: campaign
title: Confidentialité et consentement
description: En savoir plus sur la confidentialité et le consentement
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1815'
ht-degree: 100%

---


# Confidentialité et consentement{#privacy-and-recommendations}

## Recommandations générales {#general-recommendations}

Adobe Campaign est un outil puissant pour collecter et traiter de très grands volumes de données, notamment des informations personnelles et des données sensibles. La confidentialité doit donc être gérée avec soin.

* Utilisez toujours les informations personnelles de manière responsable et éthique.

* Évitez d&#39;envoyer des emails, des notifications push et des messages SMS non sollicités (« spam »). Adobe croit fermement aux principes du consentement (permission marketing) pour fidéliser le client et offrir une valeur ajoutée tout au long de sa durée de vie et interdit donc strictement l&#39;utilisation d&#39;Adobe Campaign pour l&#39;envoi de messages non sollicités.

Prenez le temps de consulter la [liste de contrôle de sécurité et de confidentialité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html) afin de connaître les principaux éléments à vérifier en termes de sécurité et de confidentialité.

### Règlements relatifs à la confidentialité {#privacy-regulations}

Pour gérer correctement la confidentialité et les données personnelles, travaillez dans le cadre des législations applicables aux zones géographiques où vous intervenez. Ces règlements comprennent :
* [RGPD](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_fr) (Règlement général européen sur la protection des données)
* [DPA](https://www.gov.uk/data-protection) (mise en œuvre du RGPD au Royaume-Uni)
* [Directive européenne sur la protection de la vie privée et les communications électroniques](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02002L0058-20091219)
* [CAN-SPAM Act](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business) (loi des États-Unis fixant les règles et les exigences relatives aux emails commerciaux)
* [CCPA](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5.&amp;part=4.&amp;chapter=&amp;article=) (California Consumer Privacy Act)
* [PDPA](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/) (loi thaïlandaise sur la protection des données personnelles)
* [LGPD](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf) (loi brésilienne générale sur la protection des données) - entrera en vigueur le 16 août 2020

>[!NOTE]
>
>Pour plus d&#39;informations sur la façon dont le RGPD, le CCPA, la PDPA et la LGPD s&#39;appliquent à Adobe Campaign, consultez [cette page](../../platform/using/privacy-management.md#privacy-management-regulations).

### Confidentialité d&#39;Adobe Experience Cloud {#experience-cloud-privacy}

Adobe Campaign fait partie des solutions Adobe Experience Cloud. La façon dont la confidentialité est gérée dans Campaign obéit aux principes généraux d&#39;Experience Cloud, tels que :

* **Informations collectées lors de l&#39;utilisation d&#39;Adobe Experience Cloud**

   En tant que société utilisant les solutions Adobe Experience Cloud, vous choisissez les informations à collecter et à envoyer à votre compte Adobe Experience Cloud. Parmi les types d&#39;informations pouvant être collectées, citons les activités de navigation sur le Web, les adresses IP, les informations de localisation des appareils mobiles, les taux de succès des campagnes, les articles achetés ou placés dans un panier, etc.

   >[!NOTE]
   >
   >Comme pour tous les produits Adobe, Campaign collecte des informations relatives aux utilisateurs d&#39;applications et de sites web. Pour plus d&#39;informations à ce sujet, consultez la [Politique de confidentialité d&#39;Adobe](https://www.adobe.com/fr/privacy/policy.html).

* **Modalités de collecte des informations dans Adobe Experience Cloud**

   * Les solutions Adobe Experience Cloud utilisent des cookies et des technologies similaires, telles que les balises web (également appelées pixels), pour vous permettre de collecter des informations. Pour plus d&#39;informations sur les cookies et les fonctionnalités de tracking avec Adobe Campaign, consultez [cette section](#tracking-capabilities).
   * Vous pouvez également utiliser les technologies Adobe Experience Cloud dans vos applications mobiles. Pour plus d&#39;informations sur l&#39;envoi de diffusions mobiles avec Campaign, reportez-vous à la page [canal SMS](../../delivery/using/sms-channel.md) et [canal d&#39;application mobile](../../delivery/using/about-mobile-app-channel.md).

* **Choix de confidentialité de vos utilisateurs concernant votre utilisation d&#39;Adobe Experience Cloud**

   Adobe vous demande de fournir à vos clients des politiques de confidentialité décrivant :

   * Vos pratiques de confidentialité en rapport avec Adobe Experience Cloud
   * La manière dont les utilisateurs peuvent définir leurs préférences pour la collecte ou l&#39;utilisation de leurs informations en rapport avec Adobe Experience Cloud

   >[!NOTE]
   >
   >Pour tous les produits Adobe, les utilisateurs de Campaign peuvent s&#39;opposer (opt-out) au partage des informations collectées à leur sujet par le biais d&#39;applications et de sites web. Pour en savoir plus à ce sujet, consultez le [FAQ sur les informations d&#39;utilisation d&#39;Adobe Experience Cloud](https://www.adobe.com/fr/privacy/experience-cloud-usage-info-faq.html).

Pour plus d&#39;informations sur la confidentialité dans Adobe Experience Cloud, voir [cette page](https://www.adobe.com/fr/privacy/marketing-cloud.html).

## Données personnelles et acteurs impliqués {#personal-data}

Pour la gestion des informations personnelles, il est important de définir les données à traiter avec soin et par qui.
* **Les données personnelles** sont des informations qui permettent d&#39;identifier directement ou indirectement un individu vivant.
* **Les données personnelles sensibles** sont des informations relatives à l&#39;origine, aux points de vue politiques, aux croyances religieuses, aux antécédents criminels, aux renseignements génétiques, aux données sur la santé, aux préférences sexuelles, aux renseignements biométriques ainsi qu&#39;à l&#39;appartenance syndicale.

Les [principaux règlements](#privacy-regulations) se réfèrent de la manière suivante aux différentes entités chargées des données :
* Un **contrôleur de données** est l&#39;autorité qui détermine les moyens et les objectifs de la collecte, de l&#39;utilisation et du partage des données personnelles.
* Un **responsable du traitement des données** est un individu ou une partie qui collecte, utilise ou partage des données personnelles selon les instructions du contrôleur de données.
* Un **titulaire de données** est une personne vivante dont les données à caractère personnel sont collectées, utilisées ou partagées et qui peut être identifiée, directement ou indirectement, par référence à ces données à caractère personnel.

Ainsi, en tant qu&#39;entreprise qui collecte et partage des données personnelles, vous êtes le contrôleur de données, vos clients sont les titulaires de données et Adobe Campaign agit comme un responsable du traitement des données lors du traitement des données personnelles des clients selon vos instructions. Notez qu&#39;en tant que contrôleur de données, il vous appartient de gérer les relations avec les titulaires de données, par exemple lors de la gestion des [demandes d&#39;accès à des informations personnelles](#privacy-requests).

Lors de l&#39;intégration de Campaign à d&#39;autres solutions Experience Cloud dans lesquelles des audiences peuvent être transférées d&#39;un système à un autre, comme [Adobe Analytics](../../platform/using/adobe-analytics-data-connector.md), [Audience Manager ou People core service](../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md), [Campaign Standard](../../integrations/using/synchronizing-audiences.md), ou avec d&#39;autres solutions par l&#39;intermédiaire de [connecteurs CRM](../../platform/using/crm-connectors.md), vous devez veiller à la protection des données personnelles.

## Acquisition de données {#data-acquisition}

Adobe Campaign vous permet de collecter des données, y compris des informations personnelles et sensibles. Il est donc essentiel de recevoir et surveiller le consentement de vos destinataires.

* Demandez toujours aux destinataires d&#39;accepter de recevoir des communications. Pour ce faire, continuez à honorer les demandes d&#39;exclusion le plus rapidement possible et vérifiez le consentement par le biais d&#39;un processus de double opt-in. Pour plus d&#39;informations à ce sujet, voir [Créer un formulaire d&#39;abonnement avec double opt-in](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).
* N&#39;importez pas de listes frauduleuses et utilisez des adresses de contrôle pour vérifier que votre fichier client n&#39;est pas utilisé de façon frauduleuse. Pour plus d&#39;informations à ce sujet, voir [A propos des adresses de contrôle](../../delivery/using/about-seed-addresses.md).
* Grâce à la gestion du consentement et des droits, vous pouvez suivre les préférences de vos destinataires et gérer les personnes qui, au sein de votre organisation, peuvent accéder aux différentes données. Voir à ce propos [cette section](#consent).
* Faciliter et gérer les demandes d&#39;accès à des informations personnelles de vos destinataires. Voir à ce propos [cette section](#privacy-requests).

## Gestion de la confidentialité {#privacy-management}

La gestion de la confidentialité se rapporte à tous les processus et outils qui peuvent vous aider à vous conformer aux règlements relatifs à la confidentialité (RGPD, CCPA, etc.). Pour une présentation de la gestion de la confidentialité, voir [cette page](https://helpx.adobe.com/fr/campaign/kb/campaign-privacy-overview.html).

Adobe Campaign vous propose divers ensembles de fonctionnalités dédiées à la gestion de la confidentialité :
* Gestion du consentement, conservation des données et rôles utilisateur. Reportez-vous à [cette section](#consent).
* Demandes d&#39;accès à des informations personnelles (droit d&#39;accès et droit à l&#39;oubli). Reportez-vous à [cette section](#privacy-requests).
* Droit d&#39;opposition (opt-out) à la vente des informations personnelles (spécifique au règlement CCPA). Reportez-vous à [cette section](../../platform/using/privacy-requests.md#sale-of-personal-information-ccpa).

Les principales fonctionnalités de confidentialité relatives à Campaign et un exemple des acteurs impliqués sont présentés dans [cette section](https://helpx.adobe.com/fr/campaign/kb/campaign-privacy-more.html#gdprpersonasandflow).

### Consentement, conservation des données et rôles {#consent}

Depuis l&#39;origine, Adobe Campaign dispose de fonctions importantes, essentielles pour la confidentialité :

* **Gestion du consentement** : grâce au processus de gestion des abonnements, vous pouvez gérer vos préférences de destinataires et déterminer quels destinataires ont choisi quel type d&#39;abonnement. Pour plus d&#39;informations à ce sujet, consultez la section [A propos des abonnements](../../delivery/using/about-services-and-subscriptions.md).
* **Conservation des données** : toutes les tables de journalisation standard natives comportent des périodes de rétention prédéfinies, limitant généralement le stockage de leurs données à 6 mois maximum. Il est possible de définir des périodes de conservation supplémentaires à l&#39;aide de workflows. Pour en savoir plus, contactez les consultants Adobe ou les administrateurs techniques.
* **Gestion des droits** : Adobe Campaign permet de gérer les droits affectés aux divers opérateurs Campaign par l&#39;intermédiaire de différents rôles préconfigurés ou personnalisés. Vous pouvez ainsi gérer qui, dans votre entreprise, peut accéder à différents types de données, les modifier ou les exporter. Voir à ce sujet la section [Gestion des accès](../../platform/using/access-management.md).

Pour plus d’informations sur ces fonctionnalités et leur gestion dans Adobe Campaign, consultez [cette section](../../platform/using/privacy-management.md#consent-retention-roles).

### Demandes d&#39;accès à des informations personnelles {#privacy-requests}

Adobe Campaign dispose de fonctionnalités supplémentaires pour vous aider à vous préparer, en tant que contrôleur de données, à certaines demandes d&#39;accès à des informations personnelles :

* Le **droit d&#39;accès** est le droit pour le titulaire de données d&#39;obtenir du contrôleur de données la confirmation que les données personnelles le concernant sont ou non traitées, et lorsqu&#39;elles le sont, où et à quelles fins.

* Le **droit à l&#39;oubli** (demande de suppression) autorise le titulaire de données à effacer ses données personnelles.

>[!NOTE]
>
>Cet ensemble d&#39;outils vous aide à respecter les exigences relatives à la confidentialité énoncées par le RGPD, le CCPA, la PDPA et la LGPD. Pour plus d&#39;informations sur ces différentes réglementations, consultez [cette page](../../platform/using/privacy-management.md#privacy-management-regulations).

<!--* **GDPR** (General Data Protection Regulation) is the European Union’s (EU) privacy law that harmonizes and modernizes data protection requirements. GDPR applies to Adobe Campaign customers who hold data for Data Subjects residing in the EU.

* **CCPA** (California Consumer Privacy Act) provides California residents new rights in regards to their personal information and imposes data protection responsibilities on certain entities whom conduct business in California.

* **Thailand's PDPA** (Personal Data Protection Act) is the new privacy law that harmonizes and modernizes data protection requirements for Thailand. This regulation applies to Adobe Campaign customers who hold data for Data Subjects residing in this country.

Brazil's Lei Geral de Proteção de Dados (LGPD) will be effective starting Aug, 16 for all companies collecting or processing personal data in Brazil. This regulation also applies to Adobe Campaign customers who hold data for Data Subjects residing in this country.-->

Les demandes **d&#39;accès** et de **suppression** sont présentées sur [cette page](../../platform/using/privacy-management.md#right-access-forgotten). Les étapes principales pour créer ces requêtes sont détaillées dans [cette section](../../platform/using/privacy-requests.md). <!--Tutorials are also available [here](https://docs.adobe.com/content/help/en/campaign-standard-learn/tutorials/privacy/privacy-overview.html).-->

## Fonctionnalités de tracking {#tracking-capabilities}

### Cookies {#cookies}

Grâce à ses fonctionnalités de suivi, Adobe Campaign vous permet de suivre la navigation de vos destinataires de diffusion en utilisant trois types de cookies : un cookie de session et deux cookies permanents.

* Un cookie de **session** : le cookie **nlid** contient l&#39;identifiant de l&#39;email envoyé au contact (**broadlogId**) et l&#39;identifiant du modèle de message (**deliveryId**). Il est déposé lorsque le contact clique sur une URL contenue dans un email envoyé par Adobe Campaign et permet de tracker son comportement sur le web. Ce cookie de session est effacé automatiquement à la fermeture du navigateur. Le contact a la possibilité d&#39;en interdire le dépôt en adaptant les paramètres de son navigateur.

* Deux cookies **permanents** :
   * Le cookie **UUID** (Universal Unique IDentifier) est partagé entre les solutions Adobe Experience Cloud. Il est défini une fois jusqu’à ce qu’il disparaisse du navigateur client lorsqu’une nouvelle valeur est générée. Il permet d&#39;identifier un internaute qui interagit avec les solutions Experience Cloud lors de ses visites sur un site web. Il peut être déposé par une landing page (pour associer des activités de clients inconnues à un destinataire) ou par une diffusion. La description de ce cookie est disponible dans [cette page](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-mc.html?lang=fr#ec-cookies).
   * Le cookie **nllastdelid** (introduit dans Campaign Classic 20.3) est un cookie permanent qui contient l&#39;identifiant **deliveryId** de la dernière diffusion d&#39;où l&#39;utilisateur a cliqué sur le lien. Ce cookie est utilisé - lorsque le cookie de session est manquant - pour identifier la table de tracking qui sera utilisée.

Les règlements tels que le Règlement général sur la protection des données (RGPD) stipulent que les sociétés doivent demander l&#39;accord des utilisateurs du site web avant l&#39;installation de cookies.

* Ainsi, vous devez informer les utilisateurs de vos sites soumis au tracking web via une zone de demande de consentement (par exemple en surimpression de la page) proposant une case à cocher pour autoriser l&#39;utilisation de cookies, ou afficher une bannière en haut de la première page visitée, etc.
* Les fenêtres de type pop-up sont à éviter car elles sont souvent bloquées par les navigateurs.

### Tracking des messages {#message-tracking}

Adobe Campaign vous permet de suivre les emails envoyés et le comportement de vos destinataires de diffusion : ouverture, clics sur des liens, désinscriptions, etc. Pour plus d&#39;informations à ce sujet, consultez la section [A propos du tracking des messages](../../delivery/using/about-message-tracking.md).

Pour ce faire, ajoutez des [liens suivis](../../delivery/using/how-to-configure-tracked-links.md) à vos messages afin de mesurer l&#39;impact de votre diffusion et le comportement du destinataire dans l&#39;onglet [Tracking](../../delivery/using/monitoring-a-delivery.md#tracking-logs) du tableau de bord de diffusion. Les données de suivi sont interprétées dans le rapport des [indicateurs de tracking](../../reporting/using/delivery-reports.md#tracking-indicators).

### Tracking web {#web-tracking}

Adobe Campaign vous permet également de contrôler la manière dont les destinataires naviguent sur votre site web : insérez des balises de tracking pour collecter des informations et mesurer les visites sur les pages d&#39;applications web. Pour plus d&#39;informations à ce sujet, consultez la section [Tracking d&#39;une application web](../../web/using/tracking-a-web-application.md).

Le paramétrage du tracking web est présenté dans [cette section](../../configuration/using/about-web-tracking.md).

Pour mieux gérer le tracking, Adobe Campaign vous permet d&#39;afficher une bannière d&#39;opt-out afin d&#39;arrêter le tracking des comportements web des utilisateurs finaux qui se sont désinscrits du tracking comportemental. Pour plus d&#39;informations à ce sujet, consultez la section [Désinscription (opt-out) du tracking des applications web](../../web/using/web-application-tracking-opt-out.md).
