---
product: campaign
title: À propos des intégrations de Campaign
description: Utilisez d'autres solutions Adobe et combinez leurs différentes fonctionnalités avec Campaign.
feature: Overview
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: 597d24fa780a324507c56c55a5309b6ee1cf46eb
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 46%

---

# Prise en main des intégrations Adobe Campaign {#about-campaign-integrations}

Adobe Experience Cloud est un ensemble complet de solutions intégrées haut de gamme, reposant sur une plateforme de données commune avec un ensemble commun de solutions et d’applications puissantes.

En savoir plus sur les intégrations fonctionnelles disponibles entre les solutions Adobe Campaign et Adobe Experience Cloud dans [cette page](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/integrations){_blank}.

La liste complète des solutions et services d’Adobe qui peuvent être intégrés à Adobe Campaign, ainsi que la documentation associée, est disponible dans la section [cette section](#experience-cloud-integrations).

>[!CAUTION]
>
>Ces intégrations nécessitent la mise en oeuvre d’Adobe Identity Management System (IMS) pour se connecter via un Adobe ID. [En savoir plus dans cette page](../../integrations/using/about-adobe-id.md).
>

## Liaison des solutions {#working-with-experience-cloud-solutions}

Plusieurs solutions peuvent être liées à Adobe Experience Cloud. L’**organisation** est l’entité client qui permet à un administrateur de configurer des groupes et des utilisateurs, et de contrôler l’authentification unique dans Adobe Experience Cloud. L’organisation joue le rôle d’une société de connexion qui couvre tous les produits et solutions Experience Cloud. L&#39;organisation correspond le plus souvent au nom de votre société. Toutefois, une société peut détenir plusieurs organisations.

La gestion des organisations et la liaison de comptes Adobe Experience Cloud sont détaillées dans la section [Portail d’aide Adobe Experience Cloud](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations){_blank}.

## Gestion des identités et des cookies {#id-and-cookies}

Lors de l’installation d’Adobe Campaign ou de l’intégration d’une installation existante avec Adobe Experience Cloud, la variable [Service Adobe Experience Cloud Identity](https://experienceleague.adobe.com/en/docs/id-service/using/home){_blank} est activée. Ce service remplace le cookie permanent utilisé en premier lieu par Adobe Campaign pour ses fonctionnalités de tracking.

Le Service d&#39;identités d’Adobe Experience Cloud fournit un identifiant universel et permanent qui identifie vos visiteurs dans toutes les solutions Experience Cloud.

Un ID de visiteur unique sera attribué aux logs de tracking qui génèrent des destinataires. Cet identifiant sera enregistré dans le champ UUID du **[!UICONTROL Requester UUID (@sourceID)]** de la table **[!UICONTROL nms:trackingLogRcp]**. **Les données de tracking des destinataires qui existaient avant la mise en œuvre du service d’identification des visiteurs ne seront donc plus utilisables**.

L&#39;identifiant sera ensuite reconnu par les autres solutions Adobe Experience Cloud partageant le même CNAME. [En savoir plus](https://experienceleague.adobe.com/en/docs/id-service/using/reference/analytics-reference/cname){_blank}.

## Intégrations Experience Cloud {#experience-cloud-integrations}

Le tableau suivant donne accès à la documentation disponible sur les intégrations Experience Cloud.

<table> 
 <thead> 
  <tr> 
   <th> Solutions et applications<br /> </th> 
   <th> Cas pratiques<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Plateforme de données clientes Adobe en temps réel (RTCDP)</strong><br /> </td> 
   <td> Configurez l’intégration entre Adobe Campaign et Adobe Real-time Customer Data Platform (RTCDP) pour partager des données de segments et importer des audiences dans Adobe Campaign.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">En savoir plus</a> sur l'intégration de Campaign et d'Adobe Real-time Customer Data Platform.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe IDentity Management System (IMS) - Adobe ID</strong><br /> </td> 
   <td> Configurez Adobe IMS pour vous connecter à Adobe Campaign avec le même Adobe ID que pour les autres solutions Adobe Experience Cloud.<br /> Une Adobe ID doit être utilisée pour se connecter afin d'utiliser certaines fonctionnalités liées aux intégrations Adobe Experience Cloud.<br /> <p><a href="../../integrations/using/about-adobe-id.md">En savoir plus</a> sur l'implémentation d'Adobe ID avec Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Configurez cette intégration pour créer des contenus d’email ou des formulaires mappés à la base de données Adobe Campaign directement dans <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">En savoir plus</a> sur l'intégration Adobe Campaign - Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Configurez cette intégration pour insérer des images calculées dynamiquement par <strong>Adobe Target</strong> lorsque l'email créé et envoyé par Adobe Campaign est ouvert.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">En savoir plus</a> sur l'intégration Adobe Campaign - Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Configurez cette intégration pour partager des audiences entre les solutions et applications Adobe Experience Cloud que vous utilisez.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">En savoir plus</a> à propos des intégrations Adobe Campaign - Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Ressources</strong><br /> </td> 
   <td> Configurez cette intégration pour insérer des ressources de votre bibliothèque Adobe Experience Cloud dans les emails et les landing pages créés dans Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">En savoir plus</a> À propos de l’intégration Adobe Campaign - Assets</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Configurer cette intégration pour insérer des ressources à partir de <strong>AEM Assets</strong> dans les emails et les landing pages créés dans Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">En savoir plus</a> sur l'intégration Adobe Campaign - AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Triggers Experience Cloud</strong><br /> </td> 
   <td> Configurer l'intégration entre <strong>Adobe Experience Cloud Triggers</strong> et Adobe Campaign pour envoyer des emails personnalisés à vos clients en réaction à des comportements spécifiques trackés sur votre site web par Adobe Analytics.<br /> <p><a href="about-triggers.md">En savoir plus</a> sur l'intégration Adobe Campaign - Triggers Experience Cloud.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Connecteur Adobe Analytics</strong><br /> </td> 
   <td> Configurez cette intégration pour permettre à Adobe Campaign et Adobe Analytics d’interagir par le biais de segments portant sur le comportement des utilisateurs suite à une campagne par e-mail. Réciproquement, elle envoie des indicateurs et des attributs de campagnes par e-mail diffusées par Adobe Campaign à Adobe Analytics.<br /> <p><a href="../../integrations/using/gs-aa.md">En savoir plus</a> sur l'intégration Adobe Campaign - Analytics Connector.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
