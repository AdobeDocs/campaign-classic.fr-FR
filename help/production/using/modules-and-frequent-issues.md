---
product: campaign
title: Modules et problèmes courants
description: Modules et problèmes courants
feature: Monitoring, Troubleshooting
badge-v7-prem: label="On-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 88%

---

# Modules et problèmes courants{#modules-and-frequent-issues}



Voici une liste des modules concernés par des problèmes courants :

<table> 
 <thead> 
  <tr> 
   <th> Module </th> 
   <th> Périmètre d'exécution </th> 
   <th> Résolution des problèmes </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> export </td> 
   <td> Exécution d'un traitement d'export<br /> </td> 
   <td> L'opérateur qui a programmé cet export doit le relancer. delta ou relance complète.<br /> </td> 
  </tr> 
  <tr> 
   <td> import </td> 
   <td> Exécution d'un traitement d'import<br /> </td> 
   <td> L'opérateur qui a programmé cet export doit le relancer. Recherchez des doublons dans la base de données.<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> Lecture de la boîte de mails rebonds<br /> </td> 
   <td> Vérifier ce module lorsque les mails rebonds ne remontent plus.<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> Effectue les envois d'email<br /> </td> 
   <td> Vérifier ce module lorsque les mails ne partent plus.<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> Maintient les statistiques des connexions des MTA<br /> </td> 
   <td> Vérifier ce module lorsque les mails ne partent plus.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> Ecriture des logs<br /> </td> 
   <td> En cas d’absence de logs dans les fichiers de log : vérifier si le module utilise bien le port 6666. Voir <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">Liste des ports ouverts</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> tracking </td> 
   <td> Consolidation et récupération des logs de tracking<br /> </td> 
   <td> Vérifier ce module lorsque les logs de tracking ne remontent plus.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> Serveur d'écriture et de purge des logs de tracking<br /> </td> 
   <td> Vérifier ce module lorsque les logs de tracking ne remontent plus et qu’il n’y a aucune trace de logs dans les fichiers sur le serveur. Voir <a href="../../production/using/tracking-logs-issues.md" target="_blank">Problèmes relatifs aux logs de tracking</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> watchdog </td> 
   <td> Module de démarrage et suivi<br /> </td> 
   <td> Vérifier ce module si aucun processus ne démarre.<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> Serveur applicatif (HTTP et SOAP)<br /> </td> 
   <td> Vérifier ce module si les connexions console et web ne fonctionnent pas et provoquent une erreur de type <strong>xtk:session.</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Contrôle l'exécution des instances de workflows<br /> </td> 
   <td> Si vous rencontrez des problèmes, redémarrez ce module. Si nécessaire, appliquez la procédure pour accroître la précision des logs décrite dans la section <a href="../../production/using/log-precision.md" target="_blank">Précision des logs</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>
