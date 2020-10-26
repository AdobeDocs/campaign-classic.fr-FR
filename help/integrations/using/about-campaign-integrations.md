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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '777'
ht-degree: 100%

---


# A propos des intégrations de Campaign {#about-campaign-integrations}

Adobe Experience Cloud constitue un ensemble exhaustif de solutions intégrées haut de gamme accessibles sur une plateforme de données commune, avec un ensemble commun de puissants core services.

Découvrez les intégrations fonctionnelles disponibles entre Adobe Campaign et les [solutions Adobe Experience Cloud](https://docs.adobe.com/content/help/fr-FR/core-services/interface/marketing-cloud-integrations.html) et les [core services](https://docs.adobe.com/content/help/fr-FR/core-services/interface/about-core-services/core-services.html). Vous pouvez ensuite moderniser vos implémentations de solution et mettre en œuvre Experience Cloud pour utiliser des fonctionnalités comme les audiences et les attributs client.

Découvrez la liste complète des solutions et core services Adobe pouvant être intégrés avec Adobe Campaign, ainsi que la documentation associée, à [cette page](#experience-cloud-integrations).

![](assets/ExCloud-solutions.png)


>[!CAUTION]
>
>La plupart de ces intégrations requiert une connexion via un Adobe ID (IMS). Pour plus d&#39;informations sur cette implémentation, consultez [cette page](../../integrations/using/about-adobe-id.md).
>
>Notez que la mise en œuvre d’IMS est un processus complexe, potentiellement fastidieux. Il est strictement réservé aux administrateurs techniques d’Adobe.

## Liaison des solutions {#working-with-experience-cloud-solutions}

En fonction de votre environnement, plusieurs solutions peuvent être liées à Adobe Experience Cloud. Elles sont liées sous la forme d&#39;organisations. Une **organisation** est l&#39;entité qui permet à un administrateur de configurer des groupes et des utilisateurs et de contrôler l&#39;authentification unique dans Experience Cloud. L&#39;organisation fonctionne comme une société de connexion qui couvre tous les produits et solutions Experience Cloud. L&#39;organisation correspond le plus souvent au nom de votre société. Toutefois, une société peut détenir plusieurs organisations.

La gestion des organisations et la liaison de comptes à Adobe Experience Cloud sont détaillées sur le [portail d&#39;aide Adobe Marketing Cloud](https://docs.adobe.com/content/help/fr-FR/core-services/interface/manage-users-and-products/organizations.html).

>[!CAUTION]
>
>Lors d&#39;une nouvelle installation d&#39;Adobe Campaign ou de l&#39;intégration d&#39;une installation existante avec Adobe Experience Cloud, le [Service Experience Cloud ID](https://docs.adobe.com/content/help/fr-FR/id-service/using/home.html) est activé. Ce service remplace le cookie permanent utilisé en premier lieu par Adobe Campaign pour ses fonctionnalités de tracking.
>
>Un identifiant visiteur unique sera alors attribué aux destinataires générant des logs de tracking. Cet identifiant sera enregistré dans le champ **[!UICONTROL UUID du demandeur (@sourceID)]** de la table **[!UICONTROL nms:trackingLogRcp]**. Les données de tracking des destinataires qui existaient avant l&#39;implémentation du service d&#39;identification des visiteurs ne seront donc plus utilisables.
>
>L&#39;identifiant sera ensuite reconnu par les autre solutions Adobe Experience Cloud partageant le même [CNAME](https://docs.adobe.com/content/help/fr-FR/id-service/using/reference/analytics-reference/cname.html).

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
   <td> <strong>Plateforme de données clientes Adobe en temps réel</strong><br /> </td> 
   <td> L’intégration entre Adobe Campaign et la plateforme de données clientes en temps réel d’Adobe vous permet de partager des données de segments et d’importer des audiences dans Adobe Campaign.<br /> <p><a href="https://docs.adobe.com/content/help/fr-FR/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">En savoir plus</a> sur l’intégration de Campaign et de la plateforme de données clientes Adobe en temps réel.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>IMS - Adobe ID</strong><br /> </td> 
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

