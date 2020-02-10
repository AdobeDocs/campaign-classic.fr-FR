---
title: Modules et problèmes courants
seo-title: Modules et problèmes courants
description: Modules et problèmes courants
seo-description: null
page-status-flag: never-activated
uuid: d53324ce-b6e2-40d7-932d-36ce4a6f5cf8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: a44f5e71-3f9b-4d02-8b7a-a9782bb6bdd8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Modules et problèmes courants{#modules-and-frequent-issues}

Voici une liste des modules concernés par des problèmes courants :

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
   <td> Si certains journaux sont manquants dans les fichiers journaux, vérifiez que le module utilise le port 6666. Reportez-vous à <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">Liste des ports</a>ouverts.<br /> </td> 
  </tr> 
  <tr> 
   <td> tracking </td> 
   <td> Consolidation et récupération des logs de tracking<br /> </td> 
   <td> Vérifier ce module lorsque les logs de tracking ne remontent plus.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> Serveur d'écriture et de purge des logs de tracking<br /> </td> 
   <td> Vérifiez ce module si les journaux de suivi ne sont plus transférés et qu’il n’y a aucune trace de journaux dans les fichiers du serveur. Reportez-vous à la section <a href="../../production/using/tracking-logs-issues.md" target="_blank">Suivi des problèmes</a>de journaux.<br /> </td> 
  </tr> 
  <tr> 
   <td> watchdog </td> 
   <td> Module de démarrage et suivi<br /> </td> 
   <td> Vérifier ce module si aucun processus ne démarre.<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> Serveur applicatif (HTTP et SOAP)<br /> </td> 
   <td> Vérifier ce module si les connexions console et web ne marchent pas et provoquent une erreur de type <strong> xtk:session.</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Contrôle l'exécution des instances de workflows<br /> </td> 
   <td> Si vous rencontrez des problèmes, redémarrez ce module. Si nécessaire, appliquez la procédure pour accroître la précision des journaux décrits dans la section <a href="../../production/using/log-precision.md" target="_blank">Précision</a> du journal.<br /> </td> 
  </tr> 
 </tbody> 
</table>

