---
title: Workflow technique d'Inbox rendering dans Adobe Campaign Classic
description: Cette section décrit le workflow technique installé avec le package Inbox rendering dans Adobe Campaign Classic.
page-status-flag: never-activated
uuid: f60a09f0-47a0-4fc0-b0ac-47178af6ad55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: da0779dc-b734-483b-81e9-ff4706a2b6de
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: e1bd878c45576932e085b579f91eb72f5d36d6fd
workflow-type: ht
source-wordcount: '81'
ht-degree: 100%

---


# Inbox rendering (IR){#inbox-rendering}

Le workflow détaillé ci-dessous est installé par défaut avec le module **Inbox rendering (IR)**. Voir à ce propos [cette section](../../delivery/using/inbox-rendering.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Libellé</strong><br /> </td> 
   <td> <strong>Nom interne</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Mettre à jour le réseau de contrôle pour Inbox Rendering</strong><br /> </td> 
   <td> <span class="uicontrol">updateRenderingSeeds</span> <br /> </td> 
   <td> Ce workflow met à jour les adresses email utilisées pour l'Inbox rendering et ne fonctionne que si le port HTTPS est ouvert pour <strong>deliverability.neolane.net</strong><br />. </td> 
  </tr> 
 </tbody> 
</table>

