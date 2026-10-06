---
product: campaign
title: Web Analytics
description: En savoir plus sur le package Web Analytics
hide: true
feature: Workflows, Analytics Integration
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 100%
---

# Web Analytics{#web-analytics}



Les workflows présentés ci-dessous sont installés par défaut avec le module **Connecteurs Web Analytics**. Voir à ce propos [cette section](../../integrations/using/gs-aa.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Libellé</strong><br /> </td> 
   <td> <strong>Nom interne</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Envoi des indicateurs et des attributs de campagne</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span> <br /> </td> 
   <td> Ce workflow permet d'envoyer les indicateurs des campagnes par e-mail d'Adobe Campaign vers Adobe Experience Cloud Suite via le connecteur Adobe® Analytics. Les indicateurs concernés sont les suivants : <strong>Envoyés</strong> (iSent), <strong>Nombre total d'ouvertures</strong> (iTotalRecipientOpen), <strong>Nombre total de destinataires ayant cliqué</strong> (iTotalRecipientClick), <strong>Erreurs</strong> (iError), <strong>Opt-Out</strong> (opt-out) (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identification des contacts convertis</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> Ce workflow répertorie les visiteurs du site ayant concrétisé leur achat après une campagne de remarketing. Les données récupérées par ce workflow sont accessibles dans le <span class="uicontrol">Rapport Efficacité du remarketing</span>. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Purge des événements</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> Ce workflow permet de supprimer de la base tous les événements selon la période paramétrée dans le champ <span class="uicontrol">Durée de vie. </span><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Récupération des événements web</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> Toutes les heures, ce workflow télécharge les segments portant sur le comportement des internautes sur un site donné, les inclut dans la base de données Adobe Campaign et lance le workflow de re-marketing. <br /> </td> 
  </tr> 
 </tbody> 
</table>

