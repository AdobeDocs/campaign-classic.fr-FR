---
product: campaign
title: Message Center (Execution)
description: Message Center (Execution)
hide: true
hidefromtoc: true
feature: Workflows
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: ht
source-wordcount: '223'
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
     <li> <p><strong>En attente</strong> : l'événement se trouve dans la file d'attente. Aucun modèle de message ne lui a encore été associé.</p> </li> 
     <li> <p><strong>En attente de diffusion</strong> : l'événement est dans la file d'attente, un modèle de message lui a été associé et il est en cours de traitement par la diffusion.</p> </li> 
     <li> <p><strong>Envoyé</strong> : ce statut est copié depuis les logs de diffusion. Il signifie que la diffusion a été envoyée.</p> </li> 
     <li> <p><strong>Ignoré par la diffusion</strong> : ce statut est copié depuis les logs de diffusion. Il signifie que la diffusion a été ignorée.</p> </li> 
     <li> <p><strong>Erreur de diffusion</strong> : ce statut est copié depuis les logs de diffusion. Il signifie que la diffusion a échoué.</p> </li> 
     <li> <p><strong>Evénement non pris en charge</strong> : l'association de l'événement à un modèle de message a échoué. L'événement ne sera pas retraité.</p> </li> 
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

