---
title: A propos des intégrations de Campaign
description: Utilisez d'autres solutions d'Adobe et combinez leurs différentes fonctionnalités avec Campaign.
page-status-flag: never-activated
uuid: 087abdf0-b4b2-45e6-be21-b03bf85ddf83
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: campaign-integrations
discoiquuid: 0af1fd96-48ef-43c9-a03b-0f9a6e0e02fe
translation-type: tm+mt
source-git-commit: 4b98c23f4120cbea6dd54cd68b61202e74bee3e1
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 71%

---


# Get started with Adobe Campaign integrations {#about-campaign-integrations}

Adobe Experience Cloud constitue un ensemble exhaustif de solutions intégrées haut de gamme accessibles sur une plateforme de données commune, avec un ensemble commun de puissants core services.

Découvrez les intégrations fonctionnelles disponibles entre Adobe Campaign et les [solutions Adobe Experience Cloud](https://docs.adobe.com/content/help/fr-FR/core-services/interface/marketing-cloud-integrations.html) et les [core services](https://docs.adobe.com/content/help/fr-FR/core-services/interface/about-core-services/core-services.html). Vous pouvez ensuite moderniser vos implémentations de solution et mettre en œuvre Experience Cloud pour utiliser des fonctionnalités comme les audiences et les attributs client.

![](assets/ExCloud-solutions.png)

Découvrez la liste complète des solutions et core services Adobe pouvant être intégrés avec Adobe Campaign, ainsi que la documentation associée, à [cette page](#experience-cloud-integrations).

>[!CAUTION]
>
>La plupart de ces intégrations nécessitent la mise en oeuvre d&#39;Adobe Identity Management System (IMS), pour se connecter via un Adobe ID. [En savoir plus dans cette page](../../integrations/using/about-adobe-id.md).


## Liaison des solutions {#working-with-experience-cloud-solutions}

Plusieurs solutions peuvent être liées à Adobe Experience Cloud. The **organization** is the customer entity that enables an administrator to configure groups and users, and to control single sign-on (SSO) in Adobe Experience Cloud. L’organisation agit comme une société de connexion qui englobe tous les produits et solutions Experience Cloud. L&#39;organisation correspond le plus souvent au nom de votre société. Toutefois, une société peut détenir plusieurs organisations.

La gestion des organisations et la liaison de comptes à Adobe Experience Cloud sont détaillées sur le [portail d&#39;aide Adobe Marketing Cloud](https://docs.adobe.com/content/help/fr-FR/core-services/interface/manage-users-and-products/organizations.html).

## Gestion des identités et des cookies {#id-and-cookies}

Lors de l’installation d’Adobe Campaign ou de l’intégration d’une installation existante avec Adobe Experience Cloud, le service [d’identité](https://docs.adobe.com/content/help/fr-FR/id-service/using/home.html) Adobe Experience Cloud est activé. Ce service remplace le cookie permanent utilisé en premier lieu par Adobe Campaign pour ses fonctionnalités de suivi.

Le service d’identification Adobe Experience Cloud (Service d’identification) fournit un identifiant universel et persistant qui identifie vos visiteurs dans toutes les solutions de l’Experience Cloud.

Un identifiant de visiteur unique sera attribué aux logs de tracking générateurs de destinataires. Cet identifiant sera enregistré dans le champ UUID du **[!UICONTROL demandeur (@sourceID)]** de la table **[!UICONTROL nms:trackingLogRcp]** . **Les données de suivi des destinataires qui existaient avant la mise en oeuvre du service d’identification des visiteurs ne seront donc plus utilisables**.

L&#39;identifiant sera ensuite reconnu par les autre solutions Adobe Experience Cloud partageant le même [CNAME](https://docs.adobe.com/content/help/fr-FR/id-service/using/reference/analytics-reference/cname.html).

## Intégrations Experience Cloud {#experience-cloud-integrations}

Le tableau suivant donne accès à la documentation disponible sur les intégrations Experience Cloud.

<table> 
 <thead> 
  <tr> 
   <th> Solution et Core services<br /> </th> 
   <th> Cas pratiques<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Plateforme de données client en temps réel Adobe (RTCDP)</strong><br /> </td> 
   <td> The integration between Adobe Campaign and Adobe Real-time Customer Data Platform (RTCDP) allows you to share segments data and import audiences to Adobe Campaign.<br /> <p><a href="https://docs.adobe.com/content/help/fr-FR/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">En savoir plus</a> sur l’intégration de Campaign et de la plateforme de données clientes Adobe en temps réel.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management System (IMS) - Adobe ID</strong><br /> </td> 
   <td> Permet de se connecter à Adobe Campaign avec le même Adobe ID que pour les autres solutions d'Adobe Experience Cloud.<br /> La connexion avec un Adobe ID est nécessaire pour pouvoir utiliser certaines fonctionnalités liées aux intégrations Adobe Experience Cloud, notamment les Core Services.<br /> <p><a href="../../integrations/using/about-adobe-id.md">En savoir plus</a> sur l'implémentation d'Adobe ID avec Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Permet de créer des contenus d'email ou des formulaires mappés à la base Adobe Campaign directement dans <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">En savoir plus</a> sur l'intégration Adobe Campaign - Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Permet d’insérer des images calculées dynamiquement par <strong>Adobe Target</strong> au moment de l'ouverture d'un email créé et envoyé via Adobe Campaign.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">En savoir plus</a> sur l'intégration Adobe Campaign - Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>People core service</strong><br /> <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Permet de partager des audiences avec les solutions Adobe Experience Cloud et les core services que vous utilisez.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">En savoir plus</a> sur les intégrations Adobe Campaign - People core service et Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Assets core service</strong><br /> </td> 
   <td> Permet d'insérer des ressources de votre bibliothèque Adobe Experience Cloud dans les emails et les landing pages créés dans Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">En savoir plus</a> sur l'intégration Adobe Campaign - Assets core service.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Permet d'insérer des ressources de votre bibliothèque <strong>AEM Assets</strong> dans les emails et les landing pages créées dans Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">En savoir plus</a> sur l'intégration Adobe Campaign - AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Triggers Experience Cloud</strong><br /> </td> 
   <td> L’intégration entre <strong>Triggers core service</strong> et Adobe Campaign permet d’envoyer des emails personnalisés à vos clients en réaction à des comportements spécifiques trackés sur votre site web par Adobe Analytics.<br /> <p><a href="https://helpx.adobe.com/fr/campaign/kb/triggers-and-campaign.html">En savoir plus</a> sur l'intégration Adobe Campaign - Triggers Experience Cloud.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics - Connecteurs de données</strong><br /> </td> 
   <td> Les <strong>connecteurs de données</strong> (anciennement appelés Adobe Genesis) permettent de faire interagir Adobe Campaign et Adobe Analytics par le biais de segments de segments portant sur le comportement des utilisateurs, suite à une campagne email. Inversement, ils envoient les indicateurs et les attributs des campagnes email lancées par Adobe Campaign vers Adobe Analytics - connecteur de données.<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">En savoir plus</a> sur l'intégration Adobe Campaign - Connecteurs de données.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>

