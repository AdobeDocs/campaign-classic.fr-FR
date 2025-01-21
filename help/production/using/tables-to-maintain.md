---
product: campaign
title: Tables à maintenir
description: Tables à maintenir
feature: Monitoring
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
source-git-commit: 517b85f5d7691acc2522bf4541f07c34c60c7fbf
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 100%

---

# Tables à maintenir{#tables-to-maintain}



La liste des tables à maintenir dépend de votre version d’Adobe Campaign, de l’utilisation que vous en faites et de la configuration du modèle de données.

Dans la liste qui suit, ne sont mentionnées que les tables les plus sujettes à la fragmentation. Les impacts sont les suivants :

* une surconsommation de l&#39;espace-disque qui impacte les performances d&#39;accès à la base,
* des index qui n’ont pas été mis à jour depuis longtemps ce qui réduit les performances des requêtes.

## Tables Adobe Campaign {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Nom de la table </strong><br /> </th> 
   <th> <strong>Taille</strong><br /> </th> 
   <th> <strong>Activité principale</strong><br /> </th> 
   <th> <strong>Commentaires</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery<br /> </td> 
   <td> Petit volume<br /> </td> 
   <td> Mises à jour<br /> </td> 
   <td> Il existe un enregistrement par action de diffusion. Un seul enregistrement peut être mis à jour plusieurs fois tout au long du processus de diffusion. Par conséquent, les index de cette table ont tendance à se fragmenter rapidement. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> Volume moyen<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Table de travail dans laquelle les enregistrements sont insérés pendant la préparation de la diffusion, puis mis à jour lors de la diffusion, puis supprimés lorsque la diffusion est terminée.<br /> Cette table a tendance à se fragmenter rapidement, même si sa taille moyenne reste modeste.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> Gros volume<br /> </td> 
   <td> Insertions, suppressions<br /> </td> 
   <td> Cette table contient les informations nécessaires à la génération de pages miroir personnalisées. Elle contient un champ mémo (CLOB) et, par conséquent, a tendance à être très volumineuse. Le volume est directement proportionnel à l'historique des pages miroir conservées. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> Volume moyen<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Cette table contient des statistiques sur le processus de diffusion. Ses enregistrements sont régulièrement mis à jour. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> Volume moyen<br /> </td> 
   <td> Mises à jour, Insertions<br /> </td> 
   <td> Cette table contient des informations sur les adresses e-mail. Elle est fréquemment mise à jour lors du processus de mise en quarantaine ; les enregistrements sont créés lors de la première erreur de diffusion, mis à jour lorsque les compteurs sont modifiés, puis supprimés lorsque la diffusion parvient à destination. <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> Petit volume<br /> </td> 
   <td> Mises à jour<br /> </td> 
   <td> A chaque instance de workflow correspond un enregistrement, soit peu d'enregistrements. Cependant la table est fréquemment mise à jour tout au long du déroulement du workflow et lors de la mise à jour de son statut.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> Petit volume<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> L'exécution d'une activité de workflow crée un enregistrement dans la table. Le système de purge des données les supprime une fois qu'elles sont expirées.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> Petit volume<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Chaque transition activée entre les tâches d’un workflow entraîne la création d’un enregistrement dans cette table. Le mécanisme de purge les supprime une fois qu’ils ont expiré. <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> Très petit volume <br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Cette table est spécifique au moteur de workflow. Elle permet d'envoyer des commandes aux workflows (Démarrer, Arrêter et Mettre en pause, par exemple). Bien qu'elle soit de petite taille, cette table est prise en compte lors du nettoyage des tables transactionnelles liées aux workflows.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> Table la plus volumineuse du système<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Cette table est la plus volumineuse du système. À chaque message envoyé correspond un enregistrement. Ces enregistrements sont insérés dans la table, mis à jour pour assurer un tracking du statut de la diffusion, puis supprimés lorsque l'historique est purgé. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> Gros volume<br /> </td> 
   <td> Insertions, suppressions<br /> </td> 
   <td> Les logs de tracking sont insérés dans la table puis supprimés lorsque l'historique est purgé mais ne sont pas mis à jour. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> Petit volume<br /> </td> 
   <td> Mises à jour<br /> </td> 
   <td> Cette table contient des informations permettant de qualifier les erreurs SMTP. Elle est assez petite, mais sera massivement mise à jour. Les index de cette table ont donc tendance à se fragmenter rapidement. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> Volume moyen<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Cette table contient les agrégats sur les erreurs SMTP, classées par domaine. Elle contient initialement des informations détaillées qui sont agrégées par la tâche de nettoyage une fois qu’elle devient obsolète. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid (sur une instance de mid-sourcing)<br /> </td> 
   <td> Gros volume<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Uniquement lorsque l'instance 5.10 (ou ultérieure) est utilisée comme instance de midsourcing. Il s’agit de l’une des tables les plus volumineuses de la base de données. À chaque message envoyé correspond un enregistrement. Ces enregistrements sont insérés, mis à jour pour suivre le statut de la diffusion et supprimés lorsque l'historique est purgé. Dans le cas d'une architecture midsourcing, il est recommandé de limiter l'historique (généralement moins de deux mois), de telle sorte que cette table garde une taille raisonnable, soit moins de 30 Go pour 60 millions de lignes comprenant les données et les index. Il est cependant très important de la reconstruire de temps à autre. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp (lorsque la table NmsRecipient est utilisée) <br /> </td> 
   <td> Gros volume<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Il s’agit de la table la plus volumineuse du système. À chaque message envoyé correspond un enregistrement. Ces enregistrements sont insérés dans la table, mis à jour pour assurer un tracking du statut de la diffusion, puis supprimés lorsque l'historique est purgé. Dans la version 5.10, cette table est plus petite que la table équivalente en version 4.05 (NmsBroadLog) du fait que le texte du message SMTP est factorisé dans la table NmsBroadLogMsg dans la version 5.10. Il est cependant indispensable de recréer l'index de cette table régulièrement (toutes les deux semaines est une bonne base de départ) et de la reconstruire entièrement de temps à autre (tous les mois environ ou avant que les performances ne soient trop dégradées). <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx (lorsqu'une table de destinataires externe est utilisée)<br /> </td> 
   <td> Gros volume<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Identique à NmsBroadLogRcp, mais avec une table de destinataires externe. Veuillez adapter Yyy et Xxx avec les valeurs de votre mapping de diffusion. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp (lorsque la table NmsRecipient est utilisée) <br /> </td> 
   <td> Gros volume<br /> </td> 
   <td> Insertions, suppressions<br /> </td> 
   <td> Les logs de tracking sont insérés dans la table puis supprimés lorsque l'historique est purgé mais ne sont pas mis à jour. Le volume dépend de la durée de rétention des données. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXxx (lorsqu'une table de destinataires externe est utilisée)<br /> </td> 
   <td> Gros volume<br /> </td> 
   <td> Insertions, suppressions<br /> </td> 
   <td> Identique à NmsTrackingLogRcp, mais avec une table de destinataires externe. Veuillez adapter Yyy et Xxx avec les valeurs utilisées dans votre mapping de diffusion. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent (instance d'exécution Message Center)<br /> </td> 
   <td> Gros volume<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Similaire aux autres tables de broadlogs, mais avec la table NmsRtEvent au lieu de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent (instance d'exécution Message Center)<br /> </td> 
   <td> Gros volume<br /> </td> 
   <td> Insertions, suppressions<br /> </td> 
   <td> Similaire aux autres tables de trackingLog, mais avec la table NmsRtEvent au lieu de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent (instance d'exécution Message Center)<br /> </td> 
   <td> Gros volume<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Table contenant la file d'attente des événements Message Center. Le statut de ces événements est mis à jour par Message Center au fur et à mesure de leur traitement. Les suppressions sont effectuées pendant la purge. Il est conseillé de régulièrement recréer l'index de cette table et la reconstruire.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto (instance de pilotage Message Center)<br /> </td> 
   <td> Gros volume<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Semblable à NmsRtEvent. Cette table archive tous les événements de toutes les instances d'exécution. Elle n'est utilisée par aucun processus temps réel, uniquement par des rapports.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> Très petit volume<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Table contenant les applications mobiles ainsi que leur configuration.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> Gros volume<br /> </td> 
   <td> Insertions, mises à jour<br /> </td> 
   <td> Table contenant les identifiants d'appareils mobiles (adresses) utilisés pour envoyer la notification (similaire à une table de destinataire).<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> Gros volume<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Similaire aux autres tables de broadlogs, mais avec la table NmsappSubscriptionRcp au lieu de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp<br /> </td> 
   <td> Gros volume<br /> </td> 
   <td> Insertions, suppressions<br /> </td> 
   <td> Similaire aux autres tables de trackingLog, mais avec la table NmsappSubscriptionRcp au lieu de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo<br /> </td> 
   <td> Petit volume<br /> </td> 
   <td> Insertions, suppressions<br /> </td> 
   <td> Table contenant les sessions utilisateurs. Le nombre d'insertions et de suppressions est très important.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tables Clients {#customer-tables}

En plus de la liste ci-dessus, les tables créées par les clientes et clients (qui n’existent pas dans le modèle de données Adobe Campaign) lors de la configuration de la plateforme peuvent également être sujettes à la fragmentation, en particulier si elles sont fréquemment mises à jour lors des procédures de synchronisation ou de chargement des données. Ces tables peuvent faire partie du modèle de données d&#39;Adobe Campaign (**NmsRecipient**, par exemple). C&#39;est donc à la personne chargée de l&#39;administration de la plateforme Adobe Campaign qu’il appartient de rechercher ces tables personnalisées dans le modèle de base de données spécifique. Ces tables ne sont pas nécessairement mentionnées explicitement dans nos procédures de maintenance.
