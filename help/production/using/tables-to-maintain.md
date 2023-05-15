---
product: campaign
title: Tables à maintenir
description: Tables à maintenir
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 100%

---

# Tables à maintenir{#tables-to-maintain}



La liste des tables à maintenir dépend de votre version d&#39;Adobe Campaign, de l&#39;utilisation que vous en faites et de la configuration du modèle de données.

Dans la liste qui suit, ne sont mentionnées que les tables les plus sujettes à la fragmentation. Les impacts sont les suivants :

* une surconsommation de l&#39;espace-disque qui impacte les performances d&#39;accès à la base,
* des index qui n&#39;ont pas été mis à jour depuis longtemps ce qui ralentit le temps de réponse des requêtes.

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
   <td> A chaque action de diffusion correspond un enregistrement. Un seul enregistrement peut être mis à jour plusieurs fois tout au long du processus de diffusion. Par conséquent, les index de cette table se trouvent rapidement fragmentés. <br /> </td> 
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
   <td> Cette table contient les informations nécessaires à la génération de pages miroir personnalisées. Elle contient un champ mémo (CLOB) ce qui a pour conséquence d'augmenter énormément sa taille. Son volume est proportionnel à l'historique des pages miroir qui est conservé. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> Volume moyen<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Cette table contient les statistiques du processus de diffusion. Ses enregistrements sont fréquemment mis à jour. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> Volume moyen<br /> </td> 
   <td> Mises à jour, Insertions<br /> </td> 
   <td> Cette table contient les informations propres aux adresses email. Elle est fréquemment mise à jour lors du processus de mise en quarantaine : les enregistrements sont créés lors de la première erreur de diffusion, mis à jour lorsque les compteurs sont modifiés puis supprimés lorsque la diffusion parvient à l'adresse spécifiée. <br /> </td> 
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
   <td> L'activation d'une transition dans un workflow crée un enregistrement dans la table. Le système de purge des données les supprime une fois qu'elles sont expirées. <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> Très petit volume <br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Cette table est propre au fonctionnement interne du moteur de workflow. Elle sert à envoyer des commandes aux workflows (Démarrer, Arrêter, Pause, par exemple). Bien qu'elle soit de petite taille, cette table est prise en compte lors du nettoyage des tables transactionnelles liées aux workflows.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> Table la plus volumineuse du système<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Cette table est la plus volumineuse du système. A chaque message envoyé correspond un enregistrement. Ces enregistrements sont insérés dans la table, mis à jour régulièrement pour assurer un tracking du statut de la diffusion puis supprimés lorsque l'historique est purgé. <br /> </td> 
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
   <td> Cette table contient des informations permettant de qualifier les erreurs SMTP. Elle est de petite taille mais est amenée à être massivement mise à jour, par conséquent ses index se trouvent rapidement fragmentés. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> Volume moyen<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Cette table contient les agrégats des erreurs SMTP classées par domaine. Au départ elle contient des informations détaillées qui sont agrégées par le workflow de nettoyage lorsqu'elles deviennent obsolètes. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid (sur une instance de mid-sourcing)<br /> </td> 
   <td> Gros volume<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Cette table n'existe que lorsque l'instance mid-sourcing est en version 5.10 et ultérieure. Il s'agit de l'une des tables les plus volumineuses. A chaque message envoyé correspond un enregistrement. Ces enregistrements sont insérés dans la table, mis à jour régulièrement pour assurer un tracking du statut de la diffusion puis supprimés lorsque l'historique est purgé. Dans le cas d'une architecture mid-sourcing, il est recommandé de limiter l'historique (habituellement moins de deux mois). Par conséquent, cette table garde une taille raisonnable, soit moins de 30Go pour 60 millions de lignes comprenant les données et les index. Il est cependant très important de la reconstruire de temps à autre. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp (lorsque la table NmsRecipient est utilisée) <br /> </td> 
   <td> Gros volume<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Cette table est l'une des plus volumineuses. A chaque message envoyé correspond un enregistrement. Ces enregistrements sont insérés dans la table, mis à jour régulièrement pour assurer un tracking du statut de la diffusion puis supprimés lorsque l'historique est purgé. Cette table est plus petite en version 5.10 que la table équivalente en version 4.05 (NmsBroadLog) du fait que le message texte SMTP est factorisé dans la table NmsBroadLogMsg en v5.10. Il est cependant indispensable de recréer l'index de cette table régulièrement (toutes les deux semaines est une bonne base de départ) et la reconstruire entièrement de temps à autre (tous les mois environ ou avant que les performances ne soient trop dégradées). <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx (lorsqu'une table de destinataires externe est utilisée)<br /> </td> 
   <td> Gros volume<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Idem que pour NmsBroadLogRcp mais avec une table de destinataires externe. Remplacer Yyy et Xxx avec les valeurs utilisées dans votre mapping de diffusion. <br /> </td> 
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
   <td> Idem que pour NmsTrackingLogRcp mais avec une table de destinataires externe. Remplacer Yyy et Xxx avec les valeurs utilisées dans votre mapping de diffusion. <br /> </td> 
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
   <td> Table qui contient la file des événements Message Center. Le statut de ces événements est mis à jour par Message Center au fur et à mesure de leur traitement. La suppression est effectuée lors de la purge. Il est conseillé de régulièrement recréer l'index de cette table et la reconstruire.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto (instance de pilotage Message Center)<br /> </td> 
   <td> Gros volume<br /> </td> 
   <td> Insertions, mises à jour, suppressions<br /> </td> 
   <td> Similaire à la table NmsRtEvent. Cette table archive tous les événements de toutes les instances d'exécution. Elle n'est utilisée par aucun processus temps réel, uniquement par des rapports.<br /> </td> 
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

Les tables créées par les clients (qui n&#39;existent pas dans le modèle de données d&#39;Adobe Campaign) lors de la mise en place de la plateforme sont également sujettes à la fragmentation. C&#39;est le cas notamment lorsqu&#39;elles sont fréquemment mises à jour lors de chargements de données ou de procédures de synchronisation. Ces tables peuvent faire partie du modèle de données d&#39;Adobe Campaign (comme **NmsRecipient** par exemple). C&#39;est donc à l&#39;administrateur de la plateforme Adobe Campaign de rechercher l&#39;existence de ces tables spécifiques dans le modèle de données. Il se peut que ces tables ne soient pas explicitement mentionnées dans les procédures de maintenance.
