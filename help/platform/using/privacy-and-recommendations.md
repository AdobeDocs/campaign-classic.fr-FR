---
product: campaign
title: Confidentialité et consentement
description: En savoir plus sur la confidentialité et le consentement
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: d2451b62-bddf-4dee-8789-35aaae8348e1
source-git-commit: a119378e4285d3258a9b4f1f68c0b625264e5d37
workflow-type: tm+mt
source-wordcount: '2025'
ht-degree: 100%

---

# Confidentialité et consentement{#privacy-and-recommendations}



## Recommandations générales {#general-recommendations}

Adobe Campaign est un puissant outil servant à collecter et à traiter de très grands volumes de données, notamment des informations personnelles et des données sensibles. La confidentialité doit donc être gérée avec soin.

* Utilisez toujours les informations personnelles de manière responsable et éthique.

* Évitez d&#39;envoyer des emails, des notifications push et des messages SMS non sollicités (« spam »). Adobe est fermement attachée aux principes du consentement (autorisation marketing) pour fidéliser le client et offrir une valeur ajoutée tout au long de sa durée de vie. L’utilisation d’Adobe Campaign pour l’envoi de messages non sollicités est donc strictement interdite.

Prenez le temps de consulter la [liste de contrôle de sécurité et de confidentialité](../../installation/using/get-started-security-privacy.md) afin de connaître les principaux éléments à vérifier en termes de sécurité et de confidentialité.

### Règlements relatifs à la confidentialité {#privacy-regulations}

Pour gérer correctement la confidentialité et les données personnelles, travaillez dans le cadre des législations applicables aux zones géographiques où vous intervenez. Ces règlements comprennent :
* [RGPD](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_fr) (Règlement général européen sur la protection des données)
* [DPA](https://www.gov.uk/data-protection) (mise en œuvre du RGPD au Royaume-Uni)
* [Directive européenne sur la protection de la vie privée et les communications électroniques](https://eur-lex.europa.eu/legal-content/FR/TXT/?uri=CELEX:02002L0058-20091219)
* [CAN-SPAM Act](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business) (loi des États-Unis fixant les règles et les exigences relatives aux emails commerciaux)
* [CCPA](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5.&amp;part=4.&amp;chapter=&amp;article=) (California Consumer Privacy Act)
* [PDPA](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/) (loi thaïlandaise sur la protection des données personnelles)
* [LGPD](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf) (loi générale brésilienne sur la protection des données)

>[!NOTE]
>
>Pour plus d’informations sur la façon dont le RGPD, le CCPA, la PDPA et la LGPD s’appliquent à Adobe Campaign, consultez [cette page](../../platform/using/privacy-management.md#privacy-management-regulations).

### Confidentialité d&#39;Adobe Experience Cloud {#experience-cloud-privacy}

Adobe Campaign fait partie des solutions Adobe Experience Cloud. La façon dont la confidentialité est gérée dans Campaign obéit aux principes généraux d’Experience Cloud, tels que :

* **Informations collectées lors de l&#39;utilisation d&#39;Adobe Experience Cloud**

  En tant que société utilisant les solutions Adobe Experience Cloud, vous choisissez les informations à collecter et à envoyer à votre compte Adobe Experience Cloud. Parmi les types d&#39;informations pouvant être collectées, citons les activités de navigation sur le Web, les adresses IP, les informations de localisation des appareils mobiles, les taux de succès des campagnes, les articles achetés ou placés dans un panier, etc.

  >[!NOTE]
  >
  >Comme pour tous les produits Adobe, Campaign collecte des informations relatives aux utilisateurs d&#39;applications et de sites web. Pour plus d’informations, consultez la [Politique de confidentialité d&#39;Adobe](https://www.adobe.com/fr/privacy/policy.html).

* **Modalités de collecte des informations dans Adobe Experience Cloud**

   * Les solutions Adobe Experience Cloud utilisent des cookies et des technologies similaires, telles que les balises web (également appelées pixels), pour vous permettre de collecter des informations. Pour plus d’informations sur les cookies et les fonctionnalités de tracking avec Adobe Campaign, consultez [cette section](#tracking-capabilities).
   * Vous pouvez également utiliser les technologies Adobe Experience Cloud dans vos applications mobiles. Pour plus d&#39;informations sur l&#39;envoi de diffusions mobiles avec Campaign, reportez-vous à la page [canal SMS](../../delivery/using/sms-channel.md) et [canal d&#39;application mobile](../../delivery/using/about-mobile-app-channel.md).

* **Choix de confidentialité de vos utilisateurs concernant votre utilisation d&#39;Adobe Experience Cloud**

  Adobe vous demande de fournir à vos clients des politiques de confidentialité décrivant :

   * Vos pratiques de confidentialité en rapport avec Adobe Experience Cloud
   * La manière dont les utilisateurs peuvent définir leurs préférences pour la collecte ou l&#39;utilisation de leurs informations en rapport avec Adobe Experience Cloud

  >[!NOTE]
  >
  >Pour tous les produits Adobe, les utilisateurs de Campaign peuvent s&#39;opposer (opt-out) au partage des informations collectées à leur sujet par le biais d&#39;applications et de sites web. Pour plus d’informations, consultez le [FAQ sur les informations d’utilisation d’Adobe Experience Cloud](https://www.adobe.com/fr/privacy/experience-cloud-usage-info-faq.html).

Pour plus d’informations sur la confidentialité dans Adobe Experience Cloud, consultez [cette page](https://www.adobe.com/fr/privacy/marketing-cloud.html).

## Données personnelles et personnes concernées {#personal-data}

Pour la gestion des informations personnelles, il est important de définir les données à traiter avec soin et par qui.
* **Les données personnelles** sont des informations qui permettent d&#39;identifier directement ou indirectement un individu vivant.
* **Les données personnelles sensibles** sont des informations relatives à l&#39;origine, aux points de vue politiques, aux croyances religieuses, aux antécédents criminels, aux renseignements génétiques, aux données sur la santé, aux préférences sexuelles, aux renseignements biométriques ainsi qu&#39;à l&#39;appartenance syndicale.

Lors de l&#39;intégration de Campaign à d&#39;autres solutions Experience Cloud dans lesquelles des audiences peuvent être transférées d&#39;un système à un autre, comme [Adobe Analytics](../../platform/using/adobe-analytics-connector.md), [Audience Manager ou People core service](../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md), [Campaign Standard](../../integrations/using/synchronizing-audiences.md), ou avec d&#39;autres solutions par l&#39;intermédiaire de [connecteurs CRM](../../platform/using/crm-connectors.md), vous devez veiller à la protection des données personnelles.

Les [principaux règlements](#privacy-regulations) se réfèrent de la manière suivante aux différentes entités chargées des données :
* Un **contrôleur de données** est l&#39;autorité qui détermine les moyens et les objectifs de la collecte, de l&#39;utilisation et du partage des données personnelles.
* Un **responsable du traitement des données** est un individu ou une partie qui collecte, utilise ou partage des données personnelles selon les instructions du contrôleur de données.
* Un **titulaire de données** est une personne vivante dont les données à caractère personnel sont collectées, utilisées ou partagées et qui peut être identifiée, directement ou indirectement, par référence à ces données à caractère personnel.

Ainsi, en tant qu’entreprise qui collecte et partage des données personnelles, vous êtes le contrôleur de données, vos clients sont les titulaires de données et Adobe Campaign agit comme un responsable du traitement des données lors du traitement des données personnelles des clients selon vos instructions. Notez qu’en tant que contrôleur de données, il vous appartient de gérer les relations avec les titulaires de données, par exemple lors de la gestion des [demandes d’accès à des informations personnelles](#privacy-requests). 

### Scénario d’utilisation {#use-case-scenario}

Pour illustrer l’interaction entre les différentes personnes, voici un exemple général de cas d’utilisation d’expérience client de RGPD de haut niveau.

Dans cet exemple, une compagnie aérienne est le client Adobe Campaign. Cette société est le **contrôleur de données** et tous les clients de la compagnie aérienne sont **titulaires de données**. Dans ce cas particulier, Laura est une cliente de la compagnie aérienne.

Voici les différentes personnes utilisées dans cet exemple :

* **Laura** est la **titulaire de données**. Elle reçoit les messages de la compagnie aérienne. Laura voyage peut-être fréquemment, mais elle peut décider à un moment donné de ne pas recevoir de publicité personnalisée ou de messages marketing de la part de la compagnie aérienne. Elle demandera à la compagnie aérienne (selon leur processus) de supprimer son numéro de vol fréquent.

* **Anne** est le **contrôleur de données** de la compagnie aérienne. Elle reçoit la demande de Laura, récupère les identifiants utiles requis pour identifier le titulaire de données et soumet la demande dans Adobe Campaign.

* **Adobe Campaign** est le **responsable du traitement des données**.

![](assets/privacy-gdpr-flow.png)

Voici le flux général de ce cas pratique :

1. La **titulaire de données** (Laura) envoie une demande RGPD au **contrôleur de données**, par le biais d’un e-mail, de l’assistance clientèle ou d’un portail web.

1. Le **contrôleur de données** (Anne) transmet la demande RGPD à Campaign via l’interface ou à l’aide d’une API.

1. Une fois que le **responsable du traitement des données** (Adobe Campaign) reçoit la demande, il la traite et envoie une réponse ou une confirmation au **contrôleur de données** (Anne).

1. Le **contrôleur de données** (Anne) examine ensuite les informations et les renvoie au **titulaire de données** (Laura).

## Acquisition de données {#data-acquisition}

Adobe Campaign vous permet de collecter des données, y compris des informations personnelles et sensibles. Il est donc essentiel de recevoir et surveiller le consentement de vos destinataires.

* Demandez toujours aux destinataires d&#39;accepter de recevoir des communications. Pour ce faire, continuez à honorer les demandes d&#39;opt-out le plus rapidement possible et vérifiez le consentement par le biais d&#39;un processus de double opt-in. Pour plus d&#39;informations à ce sujet, voir [Créer un formulaire d&#39;abonnement avec double opt-in](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).
* N&#39;importez pas de listes frauduleuses et utilisez des adresses de contrôle pour vérifier que votre fichier client n&#39;est pas utilisé de façon frauduleuse. Pour plus d’informations à ce sujet, voir [À propos des adresses de contrôle](../../delivery/using/about-seed-addresses.md).
* Grâce à la gestion des droits et du consentement, vous pouvez tracker les préférences de vos destinataires et gérer les données correspondantes et les utilisateurs de votre organisation qui peuvent y accéder. Pour plus d’informations, consultez [cette section](#consent).
* Faciliter et gérer les demandes d&#39;accès à des informations personnelles de vos destinataires. Pour plus d’informations, consultez [cette section](#privacy-requests).

## Gestion de la confidentialité {#privacy-management}

La gestion de la confidentialité se rapporte à tous les processus et outils qui peuvent vous aider à vous conformer aux règlements relatifs à la confidentialité (RGPD, CCPA, etc.). Pour une présentation de la gestion de la confidentialité, consultez [cette page](privacy-and-recommendations.md).

Adobe Campaign vous propose divers ensembles de fonctionnalités dédiées à la gestion de la confidentialité :
* Gestion du consentement, conservation des données et rôles utilisateur. Voir [cette section](#consent).
* Demandes d&#39;accès à des informations personnelles (droit d&#39;accès et droit à l&#39;oubli). Voir [cette section](#privacy-requests).
* Droit d&#39;opposition (opt-out) à la vente des informations personnelles (spécifique au règlement CCPA). Voir [cette section](../../platform/using/privacy-requests.md#sale-of-personal-information-ccpa).

Les principales fonctionnalités de confidentialité relatives à Campaign et un exemple des acteurs impliqués sont présentés dans [cette section](https://helpx.adobe.com/fr/campaign/kb/campaign-privacy-more.html#gdprpersonasandflow).

### Consentement, conservation des données et rôles {#consent}

Depuis l’origine, Adobe Campaign dispose de fonctions importantes, essentielles pour la confidentialité :

* **Gestion du consentement** : grâce au processus de gestion des abonnements, vous pouvez gérer vos préférences de destinataires et déterminer quels destinataires ont choisi quel type d&#39;abonnement. Pour plus d’informations, consultez la section [À propos des abonnements](../../delivery/using/about-services-and-subscriptions.md).
* **Conservation des données** : toutes les tables de journalisation standard natives comportent des périodes de rétention prédéfinies, limitant généralement le stockage de leurs données à 6 mois maximum. Il est possible de définir des périodes de conservation supplémentaires à l&#39;aide de workflows. Pour en savoir plus, contactez les consultants Adobe ou les administrateurs techniques.
* **Gestion des droits** : Adobe Campaign permet de gérer les droits affectés aux divers opérateurs Campaign par l’intermédiaire de différents rôles préconfigurés ou personnalisés. Vous pouvez ainsi gérer qui, dans votre entreprise, peut accéder à différents types de données, les modifier ou les exporter. Pour plus d’informations à ce sujet, consultez la section [À propos de la gestion des accès](../../platform/using/access-management.md).

Pour plus d’informations sur ces fonctionnalités et leur gestion dans Adobe Campaign, consultez [cette section](../../platform/using/privacy-management.md#consent-retention-roles).

### Demandes d&#39;accès à des informations personnelles {#privacy-requests}

Adobe Campaign dispose de fonctionnalités supplémentaires pour vous aider à vous préparer, en tant que contrôleur de données, à certaines demandes d’accès à des informations personnelles :

* Le **droit d’accès** permet au titulaire de données de demander au contrôleur de données si les données personnelles le concernant sont traitées ou non, et lorsqu’elles le sont, où et à quelles fins.

* Le **Droit à l’oubli** (demande de suppression) autorise le titulaire de données à demander au contrôleur de données d’effacer ses données personnelles.

Les demandes d&#39;**accès** et de **suppression** sont présentées dans [cette section](../../platform/using/privacy-management.md#right-access-forgotten).

La procédure de création de ces demandes est pour sa part détaillée sur [cette page](../../platform/using/privacy-requests.md).

## Fonctionnalités de tracking {#tracking-capabilities}

### Cookies {#cookies}

Grâce à ses fonctionnalités de suivi, Adobe Campaign vous permet de suivre la navigation de vos destinataires de diffusion en utilisant trois types de cookies : un cookie de session et deux cookies permanents.

* Un cookie de **session** : le cookie **nlid** contient l&#39;identifiant de l&#39;email envoyé au contact (**broadlogId**) et l&#39;identifiant du modèle de message (**deliveryId**). Il est déposé lorsque le contact clique sur une URL contenue dans un email envoyé par Adobe Campaign et permet de tracker son comportement sur le web. Ce cookie de session est effacé automatiquement à la fermeture du navigateur. Le contact a la possibilité d&#39;en interdire le dépôt en adaptant les paramètres de son navigateur.

* Deux cookies **permanents** :
   * Le cookie **UUID** (Universal Unique IDentifier) est partagé entre les solutions Adobe Experience Cloud. Il est défini une fois jusqu’à ce qu’il disparaisse du navigateur client lorsqu’une nouvelle valeur est générée. Il permet d&#39;identifier un internaute qui interagit avec les solutions Experience Cloud lors de ses visites sur un site web. Il peut être déposé par une landing page (pour associer des activités de clients inconnues à un destinataire) ou par une diffusion. La description de ce cookie est disponible dans [cette page](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-mc.html?lang=fr#ec-cookies).
   * Le cookie **nllastdelid** (introduit dans Campaign Classic 20.3) est un cookie permanent qui contient l&#39;identifiant **deliveryId** de la dernière diffusion d&#39;où l&#39;utilisateur a cliqué sur le lien. Ce cookie est utilisé - lorsque le cookie de session est manquant - pour identifier la table de tracking qui sera utilisée.

Des règlements, tels que le Règlement général sur la protection des données (RGPD), imposent aux entreprises d’obtenir l’accord des utilisateurs du site web avant d’installer des cookies.

* Ainsi, vous devez informer les utilisateurs de vos sites soumis au tracking web via une zone de demande de consentement (par exemple en surimpression de la page) proposant une case à cocher pour autoriser l&#39;utilisation de cookies, ou afficher une bannière en haut de la première page visitée, etc.
* Les fenêtres de type pop-up sont à éviter car elles sont souvent bloquées par les navigateurs.

### Tracking des messages {#message-tracking}

Adobe Campaign vous permet de suivre les emails envoyés et le comportement de vos destinataires de diffusion : ouverture, clics sur des liens, désinscriptions, etc. Pour plus d’informations à ce sujet, consultez la section [À propos du tracking des messages](../../delivery/using/about-message-tracking.md).

Pour ce faire, ajoutez des [liens suivis](../../delivery/using/how-to-configure-tracked-links.md) à vos messages afin de mesurer l&#39;impact de votre diffusion et le comportement du destinataire dans l&#39;onglet [Tracking](../../delivery/using/delivery-dashboard.md#tracking-logs) du tableau de bord de diffusion. Les données de suivi sont interprétées dans le rapport des [indicateurs de tracking](../../reporting/using/delivery-reports.md#tracking-indicators).

### Tracking web {#web-tracking}

Adobe Campaign vous permet également de contrôler la manière dont les destinataires naviguent sur votre site web : insérez des balises de tracking pour collecter des informations et mesurer les visites sur les pages d’applications web. Pour plus d’informations, consultez la section [Tracking d&#39;une application web](../../web/using/tracking-a-web-application.md).

Le paramétrage du tracking web est présenté dans [cette section](../../configuration/using/about-web-tracking.md).

Pour mieux gérer le tracking, Adobe Campaign vous permet d’afficher une bannière d’opt-out afin d’arrêter le tracking des comportements web des utilisateurs finaux qui se sont désinscrits du tracking comportemental. Pour plus d’informations, consultez la section [Désinscription (opt-out) du tracking des applications web](../../web/using/web-application-tracking-opt-out.md).
