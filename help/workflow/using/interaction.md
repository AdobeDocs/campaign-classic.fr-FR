---
product: campaign
title: Interaction
description: Interaction
feature: Workflows, Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 96%

---


# Interaction{#interaction}



Les workflows présentés ci-dessous sont installés par défaut avec le module complémentaire **Moteur d’offres (Interaction)**.

Pour plus d&#39;informations à ce sujet, en fonction de la version de Campaign, reportez-vous aux sections suivantes :

![](assets/do-not-localize/v7.jpeg)[Documentation Campaign v7](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png)[Documentation Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html?lang=fr)


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
   <td> Ce workflow met à jour l'agrégat <strong>Complet (full)</strong> du cube <strong>Proposition d'offre</strong>. Par défaut, il se déclenche tous les jours à 6H00. Cet agrégat capture les dimensions suivantes : Canal, Diffusion, Offre marketing et Date.<br /> Le cube <strong>Proposition d'offre</strong> est ensuite utilisé pour générer des rapports basés sur les offres. Pour plus d'informations sur les cubes, consultez <a href="../../reporting/using/ac-cubes.md">cette section</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Calcul de l'agrégat full (cube propositionrcp) du MessageCenter</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Ce workflow met à jour l’agrégat complet<strong>(Full)</strong> du cube <strong>Message Center</strong>. Il est déclenché tous les jours à 3h du matin par défaut. Cet agrégat capture les dimensions suivantes : Canal, Date, Statut et Type d'événement.<br /> Le cube <strong>Message center</strong> est ensuite utilisé pour générer des rapports basés sur des événements. Vous pouvez en savoir plus sur les cubes dans <a href="../../reporting/using/ac-cubes.md">cette section</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

