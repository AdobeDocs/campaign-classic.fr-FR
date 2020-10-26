---
title: Message Center (Execution)
seo-title: Message Center (Execution)
description: Message Center (Execution)
seo-description: null
page-status-flag: never-activated
uuid: 8dfb09d1-da00-43fb-9df4-243bb915cbde
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: dc3d8998-9493-4d71-b3e2-6f9531cb9bac
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '234'
ht-degree: 100%

---


# Message Center (Execution){#message-center-execution}

Les workflows présentés ci-dessous sont installés par défaut avec le module **Message Center - Exécution**. Pour plus d’informations sur ce module, consultez cette [section](../../message-center/using/about-transactional-messaging.md).

Pour en savoir plus sur la configuration des workflows techniques associés au module Message Center, consultez [cette page](../../message-center/using/technical-workflows.md).

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
   <td> Ce workflow permet d'attribuer un statut à l'événement. Les statuts d'un événement sont les suivants :<br /> 
    <ul> 
     <li> <p><strong>En attente</strong> : l'événement se trouve dans la file d'attente. Aucun modèle de message ne lui a encore été associé.</p> </li> 
     <li> <p><strong>En attente de diffusion</strong> : l'événement est dans la file d'attente, un modèle de message lui a été associé et il est en cours de traitement par la diffusion.</p> </li> 
     <li> <p><strong>Envoyé</strong> : ce statut est copié depuis les logs de diffusion. Il signifie que la diffusion a été envoyée.</p> </li> 
     <li> <p><strong>Ignoré par la diffusion</strong> : ce statut est copié depuis les logs de diffusion. Il signifie que la diffusion a été ignorée.</p> </li> 
     <li> <p><strong>Erreur de diffusion</strong> : ce statut est copié depuis les logs de diffusion. Il signifie que la diffusion a échoué.</p> </li> 
     <li> <p><strong>Evénement non pris en charge</strong> : l'association de l'événement à un modèle de message a échoué. L'événement ne sera pas retraité.</p> </li> 
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

