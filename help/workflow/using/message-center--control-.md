---
title: Message Center (Pilotage)
seo-title: Message Center (Pilotage)
description: Message Center (Pilotage)
seo-description: null
page-status-flag: never-activated
uuid: bdb3610b-a893-4e60-a9f7-f21d90b66919
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 69e3e99f-d392-4316-926c-3c3c675415ad
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Message Center (Pilotage){#message-center-control}

Le workflow présenté ci-dessous est planifié pour s’exécuter toutes les heures. Il est installé par défaut avec le module **Message Center - Pilotage**. Pour plus d’informations sur ce module, consultez cette [section](../../message-center/using/about-transactional-messaging.md).

Pour en savoir plus sur la configuration des workflows techniques associés au module Message Center, consultez [cette page](../../message-center/using/technical-workflows.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Libellé</strong><br /> </td> 
   <td> <strong>Nom interne</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Message Center &lt;external_account_name&gt;<br /> </td> 
   <td> mcSynch_&lt;external_account_name&gt;<br /> </td> 
   <td> Ce workflow :<br /> 
    <ul> 
     <li> <p>récupère la liste des événements traités par la ou les opérations,</p> </li> 
     <li> <p>se synchronise avec la table NmsBroadLogMsg afin de récupérer les qualifications des messages de diffusion,</p> </li> 
     <li> <p>récupère les logs de diffusion d'événements dès que la synchronisation avec la table NmsBroadLogMsg est terminée,</p> </li> 
     <li> <p>se synchronise avec la table NmsTrackingUrl afin de récupérer le tracking des URL de diffusion,</p> </li> 
     <li> <p>récupère les URL de tracking des événements dès que la synchronisation avec la table NmsTrackingUrl est terminée,</p> </li> 
     <li> <p>permet de récupérer toutes les adresses email mises en quarantaine toutes les trois heures après l'envoi d'une diffusion.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

