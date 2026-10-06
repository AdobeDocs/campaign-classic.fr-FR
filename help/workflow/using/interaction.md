---
product: campaign
title: Interaction
description: Interaction
hide: true
feature: Workflows, Interaction, Offers
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 65702805-0026-5ca1-843a-144fa79f0883
    internal-label: Interaction
  - id: ea08db70-4682-59a2-9408-9aedd9548e07
    internal-label: Offers
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 100%
---

# Interaction{#interaction}



Les workflows présentés ci-dessous sont installés par défaut avec le module complémentaire **Moteur d’offres (Interaction)**.

Pour plus d&#39;informations à ce sujet, en fonction de la version de Campaign, reportez-vous aux sections suivantes :

![](assets/do-not-localize/v7.jpeg)[Documentation de Campaign v7](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png)[Documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html?lang=fr)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>Libellé</strong><br /> </td> 
   <td> <strong>Nom interne</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Calcul de l'agrégat full (cube propositionrcp)</span> <br /> </td> 
   <td> <span class="uicontrol">agg_nmspropositionrcp_full</span> <br /> </td> 
   <td> Ce workflow met à jour l’agrégat <strong>Full</strong> du cube <strong>Proposition d’offre</strong>. Par défaut, il se déclenche tous les jours à 6 h 00. Cet agrégat capture les dimensions suivantes : Canal, Diffusion, Offre marketing et Date.<br /> Le cube <strong>Proposition d’offre</strong> est ensuite utilisé pour générer des rapports basés sur les offres. Vous pouvez en savoir plus sur les cubes dans <a href="../../reporting/using/ac-cubes.md">cette section</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Calcul de l'agrégat full (cube propositionrcp) du MessageCenter</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Ce workflow met à jour l’agrégat complet<strong>(Full)</strong> du cube <strong>Message Center</strong>. Il est déclenché tous les jours à 3h du matin par défaut. Cet agrégat capture les dimensions suivantes : Canal, Date, Statut et Type d’événement.<br /> Le cube <strong>Message Center</strong> est ensuite utilisé pour générer des rapports basés sur les événements. Vous pouvez en savoir plus sur les cubes dans <a href="../../reporting/using/ac-cubes.md">cette section</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

