---
product: campaign
title: Message Center (Pilotage)
description: Message Center (Pilotage)
feature: Workflows
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: ht
source-wordcount: '145'
ht-degree: 100%

---


# Message Center (Pilotage){#message-center-control}



Le workflow présenté ci-dessous est planifié pour s’exécuter toutes les heures. Il est installé par défaut avec le module **Message Center - Pilotage**.


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

