---
product: campaign
title: À propos des intégrations de Campaign
description: Utilisez d'autres solutions Adobe et combinez leurs différentes fonctionnalités avec Campaign.
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: ht
source-wordcount: '762'
ht-degree: 100%

---

# Prise en main des intégrations Adobe Campaign {#about-campaign-integrations}



Adobe Experience Cloud constitue un ensemble exhaustif de solutions intégrées haut de gamme accessibles sur une plateforme de données commune, avec un ensemble commun de puissants core services.

Découvrez les intégrations fonctionnelles disponibles entre Adobe Campaign et les [solutions Adobe Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/marketing-cloud-integrations.html?lang=fr) et les [core services](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=fr). Vous pouvez ensuite moderniser vos implémentations de solution et mettre en œuvre Experience Cloud pour utiliser des fonctionnalités comme les audiences et les attributs client.

![](assets/ExCloud-solutions.png)

Découvrez la liste complète des solutions et core services Adobe pouvant être intégrés avec Adobe Campaign, ainsi que la documentation associée, à [cette page](#experience-cloud-integrations).

>[!CAUTION]
>
>La plupart de ces intégrations nécessitent la mise en œuvre d’Adobe IDentity Management System (IMS), pour se connecter via un Adobe ID. [En savoir plus dans cette page](../../integrations/using/about-adobe-id.md).

## Liaison des solutions {#working-with-experience-cloud-solutions}

Plusieurs solutions peuvent être liées à Adobe Experience Cloud. L’**organisation** est l’entité client qui permet à un administrateur de configurer des groupes et des utilisateurs, et de contrôler l’authentification unique dans Adobe Experience Cloud. L’organisation joue le rôle d’une société de connexion qui couvre tous les produits et solutions Experience Cloud. L&#39;organisation correspond le plus souvent au nom de votre société. Toutefois, une société peut détenir plusieurs organisations.

La gestion des organisations et la liaison de comptes à Adobe Experience Cloud sont détaillées sur le [portail d&#39;aide Adobe Marketing Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=fr).

## Gestion des identités et des cookies {#id-and-cookies}

Lors de l’installation d’Adobe Campaign ou de l’intégration d’une installation existante avec Adobe Experience Cloud, le [Service d’identités d’Adobe Experience Cloud](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=fr) est activé. Ce service remplace le cookie permanent utilisé en premier lieu par Adobe Campaign pour ses fonctionnalités de tracking.

Le Service d&#39;identités d’Adobe Experience Cloud fournit un identifiant universel et permanent qui identifie vos visiteurs dans toutes les solutions Experience Cloud.

Un ID de visiteur unique sera attribué aux logs de tracking qui génèrent des destinataires. Cet identifiant sera enregistré dans le champ UUID du **[!UICONTROL Requester UUID (@sourceID)]** de la table **[!UICONTROL nms:trackingLogRcp]**. **Les données de tracking des destinataires qui existaient avant la mise en œuvre du service d’identification des visiteurs ne seront donc plus utilisables**.

L&#39;identifiant sera ensuite reconnu par les autres solutions Adobe Experience Cloud partageant le même CNAME. [En savoir plus](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/cname.html?lang=fr)

## Intégrations Experience Cloud {#experience-cloud-integrations}

Le tableau suivant donne accès à la documentation disponible sur les intégrations Experience Cloud.

<table> 
 <thead> 
  <tr> 
   <th> Solution et Core services<br /> </th> 
   <th> Cas pratiques<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Plateforme de données clientes Adobe en temps réel (RTCDP)</strong><br /> </td> 
   <td> L’intégration entre Adobe Campaign et la plateforme de données clientes en temps réel d’Adobe (RTCDP) vous permet de partager des données de segments et d’importer des audiences dans Adobe Campaign.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">En savoir plus</a> sur l'intégration de Campaign et d'Adobe Real-time Customer Data Platform.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe IDentity Management System (IMS) - Adobe ID</strong><br /> </td> 
   <td> Permet de se connecter à Adobe Campaign avec le même Adobe ID que pour les autres solutions d'Adobe Experience Cloud.<br /> La connexion avec un Adobe ID est nécessaire pour pouvoir utiliser certaines fonctionnalités liées aux intégrations Adobe Experience Cloud, notamment les Core Services.<br /> <p><a href="../../integrations/using/about-adobe-id.md">En savoir plus</a> sur l'implémentation d'Adobe ID avec Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Permet de créer des contenus d'email ou des formulaires mappés à la base Adobe Campaign directement dans <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">En savoir plus</a> sur l'intégration Adobe Campaign - Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Permet d’insérer des images calculées dynamiquement par <strong>Adobe Target</strong> au moment de l'ouverture d'un email créé et envoyé via Adobe Campaign.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">En savoir plus</a> sur l'intégration Adobe Campaign - Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>People core service</strong><br /> <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Permet de partager des audiences avec les solutions Adobe Experience Cloud et les core services que vous utilisez.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">En savoir plus</a> sur les intégrations Adobe Campaign - People core service et Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Assets core service</strong><br /> </td> 
   <td> Permet d'insérer des ressources de votre bibliothèque Adobe Experience Cloud dans les emails et les landing pages créés dans Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">En savoir plus</a> sur l'intégration Adobe Campaign - Assets core service.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Permet d'insérer des ressources de votre bibliothèque <strong>AEM Assets</strong> dans les emails et les landing pages créées dans Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">En savoir plus</a> sur l'intégration Adobe Campaign - AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Triggers Experience Cloud</strong><br /> </td> 
   <td> L’intégration entre <strong>Triggers core service</strong> et Adobe Campaign permet d’envoyer des emails personnalisés à vos clients en réaction à des comportements spécifiques trackés sur votre site web par Adobe Analytics.<br /> <p><a href="https://helpx.adobe.com/fr/campaign/kb/triggers-and-campaign.html">En savoir plus</a> sur l'intégration Adobe Campaign - Triggers Experience Cloud.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Connecteur Adobe Analytics</strong><br /> </td> 
   <td> <strong>Connecteur Adobe Analytics</strong> permet à Adobe Campaign et à Adobe Analytics d’interagir par le biais de segments portant sur le comportement des utilisateurs suite à une campagne par e-mail. Réciproquement, elle envoie des indicateurs et des attributs de campagnes par e-mail diffusées par Adobe Campaign à Adobe Analytics.<br /> <p><a href="../../platform/using/adobe-analytics-connector.md">En savoir plus</a> sur l'intégration Adobe Campaign - Analytics Connector.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
