---
product: campaign
title: Modules et problèmes courants
description: Modules et problèmes courants
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 100%

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
   <td> L'opérateur qui a programmé cet export doit le relancer. Possibilité de delta ou relance complète.<br /> </td> 
  </tr> 
  <tr> 
   <td> import </td> 
   <td> Exécution d'un traitement d'import<br /> </td> 
   <td> L'opérateur qui a programmé cet import doit le relancer. Vérification de non insertion de doublon dans la base de données.<br /> </td> 
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
