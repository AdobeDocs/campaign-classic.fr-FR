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
source-git-commit: bc227c2da2e8b1a78714748809ad40bbcefe0458

---


# Exécution de la diffusion{#delivery-execution}

>[!NOTE]
>
>Le MTA donne la priorité au traitement des messages transactionnels par rapport à toute autre diffusion.

Sur le  , une fois l&#39;étape du  terminée et qu&#39;un a été lié à l&#39;, leest envoyé. Tous les  de sont regroupés dans le dossier **[!UICONTROL Administration > Production > Centre de messages > Valeur par défaut >]** .

![](assets/messagecenter_deliveries_execinstances_001.png)

Par défaut, elles sont classées dans un sous-dossier correspondant au mois d&#39;envoi.

Ce classement peut être modifié dans les propriétés du modèle de message comme illustré ci-dessous.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Pour les installations hébergées ou hybrides, si vous avez effectué la mise à niveau vers le MTA amélioré d’Adobe Campaign, tous les messages transactionnels peuvent également être envoyés avec celui-ci pour optimiser la délivrabilité, le débit et la gestion des bounces. Tous les impacts sont identiques à ceux des messages marketing standard et sont présentés dans le document sur le [MTA amélioré d’Adobe Campaign](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html).