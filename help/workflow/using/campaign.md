---
product: campaign
title: Campagne
description: Campagne
feature: Workflows
hide: true
topic-tags: technical-workflows
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
source-wordcount: '166'
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
   <td> Ce workflow déclenche les diffusions validées et lance les post-traitements du prestataire pour une diffusion externe. Il envoie également des notifications de validation et des rappels.<br /> </td> 
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

