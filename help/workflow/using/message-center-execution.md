---
product: campaign
title: Message Center (Execution)
description: Message Center (Execution)
hide: true
feature: Workflows
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 100%
---

# Message Center (Execution){#message-center-execution}



Les workflows présentés ci-dessous sont installés par défaut avec le module complémentaire **Message Center - Exécution**.

Pour plus d&#39;informations à ce sujet, en fonction de la version de Campaign, reportez-vous aux sections suivantes :

![](assets/do-not-localize/v7.jpeg)[Documentation de Campaign v7](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png)[Documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html?lang=fr)

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Libellé</strong><br /> </td> 
   <td> <strong>Nom interne</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Mise à jour du statut des événements</span> <br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span> <br /> </td> 
   <td> Ce workflow vous permet d'attribuer un statut à un événement. Les statuts des événements sont les suivants :<br /> 
    <ul> 
     <li> <p><strong>En attente</strong> : l’événement se trouve dans une file d’attente. Aucun modèle de message ne lui a encore été associé.</p> </li> 
     <li> <p><strong>En attente de diffusion</strong> : l’événement est dans une file d’attente, un modèle de message lui a été associé et il est en cours de traitement par la diffusion.</p> </li> 
     <li> <p><strong>Envoyé</strong> : ce statut est copié depuis les logs de diffusion. Il signifie que la diffusion a été envoyée.</p> </li> 
     <li> <p><strong>Ignoré par la diffusion</strong> : ce statut est copié depuis les logs de diffusion. Cela signifie que la diffusion a été ignorée.</p> </li> 
     <li> <p><strong>Erreur de diffusion</strong> : ce statut est copié depuis les logs de diffusion. Il signifie que la diffusion a échoué.</p> </li> 
     <li> <p><strong>Événement non pris en charge</strong> : l’association de l’événement à un modèle de message a échoué. L’événement ne sera pas traité à nouveau.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Traitement des événements batch</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> Ce workflow permet de répartir les événements batch dans une file d'attente avant qu'ils ne soient associés à un modèle de message. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Traitement des événements en temps réel</span> <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span> <br /> </td> 
   <td> Ce workflow permet de répartir les événements temps réel dans une file d'attente avant qu'ils ne soient associés à un modèle de message. <br /> </td> 
  </tr> 
 </tbody> 
</table>

