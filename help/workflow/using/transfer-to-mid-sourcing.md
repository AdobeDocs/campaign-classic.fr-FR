---
product: campaign
title: Emission vers Mid-sourcing
description: En savoir plus sur les workflows d’émission vers Mid-sourcing
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
feature: Workflows
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 85%

---


# Émission vers Mid-sourcing{#transfer-to-mid-sourcing}



Les workflows présentés ci-dessous sont installés par défaut avec le module **Émission vers Mid-sourcing**. Pour en savoir plus à ce sujet consultez le [ Guide d&#39;installation de Campaign Classic v7](../../installation/using/mid-sourcing-deployment.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Libellé</strong><br /> </td> 
   <td> <strong>Nom interne</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Mid-sourcing (compteurs des diffusions)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingDlv</span> <br /> </td> 
   <td> <p>Ce workflow collecte les informations de comptage des diffusions sur le serveur de midsourcing. Les informations de comptage comprennent les indicateurs généraux de diffusion tels que le nombre de diffusions envoyées, etc.</p> <p>Les informations de tracking comme les ouvertures ne sont pas incluses.</p> <p>Par défaut, il se déclenche toutes les dix minutes.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Mid-sourcing (logs de diffusion)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span> <br /> </td> 
   <td> Ce workflow collecte les logs de diffusion sur le serveur de mid-sourcing. Par défaut, il se déclenche toutes les heures.<br /> </td> 
  </tr> 
 </tbody> 
</table>

