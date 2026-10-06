---
product: campaign
title: Canal LINE
description: Canal LINE
hide: true
feature: Workflows
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 100%
---

# Canal LINE{#line-channel}



Les workflows présentés ci-dessous sont installés par défaut avec le module **canal LINE**. Voir à ce propos [cette section](../../delivery/using/line-channel.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Libellé</strong><br /> </td> 
   <td> <strong>Nom interne</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Mise à jour du jeton d’accès LINE V2</span> <br /> </td> 
   <td> <span class="uicontrol">updateLineV2AccessToken</span> <br /> </td> 
   <td> Ce workflow actualise le jeton d’accès à la version LINE V2.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Nettoyage des utilisateurs LINE bloqués</span> <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> Ce workflow assure la suppression des données des utilisateurs LINE V2 s’ils ont bloqué le compte officiel LINE pendant 180 jours.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Migration du MID vers l’identifiant utilisateur Line</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigration</span> <br /> </td> 
   <td> Ce workflow génère les ID des utilisateurs LINE V2 pour la migration de LINE V1 vers LINE V2.<br /> </td> 
  </tr> 
 </tbody> 
</table>

