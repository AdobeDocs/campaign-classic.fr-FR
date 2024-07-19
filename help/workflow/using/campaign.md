---
product: campaign
title: Campagne
description: Campagne
feature: Workflows
topic-tags: technical-workflows
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 100%

---


# Campagne{#campaign}



Les workflows présentés ci-dessous sont installés par défaut avec le module **Campaign**. Voir à ce propos [cette section](../../campaign/using/designing-marketing-campaigns.md).

>[!CAUTION]
>
>Ces workflows doivent IMPERATIVEMENT être démarrés pour que les processus de campagne soient exécutés au niveau des opérations.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Libellé</strong><br /> </td> 
   <td> <strong>Nom interne</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Calcul des coûts</span> <br /> </td> 
   <td> <span class="uicontrol">budgetMgt</span> <br /> </td> 
   <td> Ce workflow lance le calcul des lignes de dépenses et des coûts sur les budgets, les plans, programmes, opérations, diffusions et tâches.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Stock : commandes et alertes</span> <br /> </td> 
   <td> <span class="uicontrol">stockMgt</span> <br /> </td> 
   <td> Ce workflow lance le calcul des stocks sur les lignes de commande et gère les seuils d'alerte.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Traitements sur les diffusions dans les opérations</span> <br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span> <br /> </td> 
   <td> Ce workflow démarre les diffusions validées et lance les post-traitements du prestataire pour une diffusion externe. Il envoie également des notifications de validation et des rappels.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Traitements sur les opérations</span> <br /> </td> 
   <td> <span class="uicontrol">operationMgt</span> <br /> </td> 
   <td> Ce workflow gère les traitements sur les opérations marketing (démarrage du ciblage, extraction des fichiers, etc.). Il crée également les workflows relatifs aux opérations récurrentes et périodiques.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Traitements sur les prestataires</span> <br /> </td> 
   <td> <span class="uicontrol">supplierMgt</span> <br /> </td> 
   <td> Ce workflow démarre les traitements du prestataire (email au routeur et post-traitement) une fois que les diffusions ont été validées. <br /> </td> 
  </tr> 
 </tbody> 
</table>

