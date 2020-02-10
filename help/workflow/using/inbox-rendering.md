---
title: Flux technique de rendu de boîte de réception dans Adobe Campaign Classic
description: Cette section décrit le processus technique installé avec le package de rendu Boîte de réception dans Adobe Campaign Classic.
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
translation-type: tm+mt
source-git-commit: e1bd878c45576932e085b579f91eb72f5d36d6fd

---


# Rendu de la boîte de réception (IR){#inbox-rendering}

Le flux de travail détaillé ci-dessous est installé par défaut avec le module de rendu de la **boîte de réception (IR)** . For more on Inbox rendering, refer to this [section](../../delivery/using/inbox-rendering.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Libellé</strong><br /> </td> 
   <td> <strong>Nom interne</strong><br /> </td> 
   <td> <strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Mise à jour du réseau de base pour le rendu de boîte de réception</strong><br /> </td> 
   <td> <span class="uicontrol">updateRenderingSeeds</span><br /> </td> 
   <td> This workflow updates email addresses used for Inbox rendering and only works if the HTTPS port is open for <strong>deliverability.neolane.net</strong>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

