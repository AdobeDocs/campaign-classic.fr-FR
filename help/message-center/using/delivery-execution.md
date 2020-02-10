---
title: Exécution de la diffusion
seo-title: Exécution de la diffusion
description: Exécution de la diffusion
seo-description: null
page-status-flag: never-activated
uuid: d4f4cea7-783b-45d3-b004-297104f0a906
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: afb375de-2de3-47ad-8b37-664cc04864e8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 211556bbf023731ffeab2e90692410a852ab3555

---


# Exécution de la diffusion{#delivery-execution}

>[!NOTE]
>
>Le MTA donne la priorité au traitement des messages transactionnels par rapport à toute autre diffusion.

Sur l’instance d’exécution, une fois les étapes d’enrichissement terminées et un modèle de remise lié à l’événement, la remise est envoyée. Toutes les livraisons sont regroupées dans le **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** dossier.

![](assets/messagecenter_deliveries_execinstances_001.png)

Par défaut, elles sont classées dans un sous-dossier correspondant au mois d&#39;envoi.

Ce classement peut être modifié dans les propriétés du modèle de message comme illustré ci-dessous.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Pour les installations hébergées ou hybrides, si vous avez effectué la mise à niveau vers la MTA améliorée, tous les messages transactionnels peuvent également être envoyés avec la MTA améliorée d’Adobe Campaign pour une meilleure délivrabilité, un meilleur débit et une meilleure gestion des retours. Tous les impacts sont identiques aux messages marketing standard et sont détaillés dans le document MTA [amélioré d’](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html) Adobe Campaign.