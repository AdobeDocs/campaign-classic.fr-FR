---
product: campaign
title: Web Analytics
description: En savoir plus sur le package Web Analytics
feature: Workflows, Analytics Integration
source-git-commit: a1dbef3e1feca1e3347de013db8bd7809d315016
workflow-type: tm+mt
source-wordcount: '178'
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
   <td> Ce workflow permet d'envoyer les indicateurs des campagnes par e-mail d'Adobe Campaign à Adobe Experience Cloud Suite via le connecteur Adobe® Analytics. Les indicateurs concernés sont les suivants : <strong>Envoyés</strong> (iSent), <strong>Nombre total d'ouvertures</strong> (iTotalRecipientOpen), <strong>Nombre total de destinataires ayant cliqué</strong> (iTotalRecipientClick), <strong>Erreurs</strong> (iError), <strong>Opt-Out</strong> (opt-out) (iOptOut).<br /> </td> 
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

