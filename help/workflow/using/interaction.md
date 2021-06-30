---
product: campaign
title: Interaction
description: Interaction
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: ht
source-wordcount: '153'
ht-degree: 100%

---


# Interaction{#interaction}

Les workflows présentés ci-dessous sont installés par défaut avec le module **Moteur d’offres (Interaction)**. Voir à ce propos [cette section](../../interaction/using/interaction-and-offer-management.md).

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
   <td> Ce workflow met à jour l'agrégat <strong>Complet (full)</strong> du cube <strong>Proposition d'offre</strong>. Par défaut, il se déclenche tous les jours à 6H00. Cet agrégat capture les dimensions suivantes : Canal, Diffusion, Offre marketing et Date.<br /> Le cube <strong>Proposition d'offre</strong> est ensuite utilisé pour générer des rapports basés sur les offres. Pour plus d'informations sur les cubes, consultez <a href="../../reporting/using/about-cubes.md">cette section</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Calcul de l'agrégat full (cube propositionrcp) du MessageCenter</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Ce workflow met à jour l’agrégat complet<strong>(Full)</strong> du cube <strong>Message Center</strong>. Il est déclenché tous les jours à 3h du matin par défaut. Cet agrégat capture les dimensions suivantes : Canal, Date, Statut et Type d'événement.<br /> Le cube <strong>Message center</strong> est ensuite utilisé pour générer des rapports basés sur des événements. Vous pouvez en savoir plus sur les cubes dans <a href="../../reporting/using/about-cubes.md">cette section</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

