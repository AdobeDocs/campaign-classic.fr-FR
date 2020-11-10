---
title: Workflows du Règlement sur la protection des données à caractère personnel
description: En savoir plus sur les workflows de réglementation de la protection des données à caractère personnel
page-status-flag: never-activated
uuid: cb5f5d79-52ac-4ce4-abc7-a3a1f0a001cf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 050c804e-87b7-4d68-b787-c396fec329d2
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 86%

---


# Règlement sur la protection des informations personnelles{#general-data-protection-regulation-gdpr}

Les workflows présentés ci-dessous sont installés par défaut avec le module **Règlement sur la protection des informations personnelles**. Voir à ce propos cet [article](https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Libellé</strong><br /> </td> 
   <td> <strong>Nom interne</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Collecter les demandes d’accès à des informations personnelles</span> <br /> </td> 
   <td> <span class="uicontrol">collectPrivacyRequests</span> <br /> </td> 
   <td> Ce workflow génère les données du destinataire stockées dans Adobe Campaign et les met à disposition sur l’écran de la demande d’accès.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Supprimer les données des demandes d’accès à des informations personnelles</span> <br /> </td> 
   <td> <span class="uicontrol">deletePrivacyRequestsData</span> <br /> </td> 
   <td> Ce workflow supprime les données du destinataire stockées dans Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Nettoyage des demandes d’accès à des informations personnelles</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPrivacyRequests</span> <br /> </td> 
   <td> Ce workflow supprime les fichiers de demande d’accès qui ont plus de 90 jours.<br /> </td> 
  </tr> 
 </tbody> 
</table>

