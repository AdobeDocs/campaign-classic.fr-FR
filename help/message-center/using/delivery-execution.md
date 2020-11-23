---
solution: Campaign Classic
product: campaign
title: Exécution de la diffusion
description: Exécution de la diffusion
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 100%

---


# Exécution de la diffusion{#delivery-execution}

>[!NOTE]
>
>Le MTA donne la priorité au traitement des messages transactionnels par rapport à toute autre diffusion.

Concernant l’instance d’exécution, une fois que l’étape d’enrichissement a été effectuée et qu’un modèle de diffusion a été lié à l’événement, la diffusion est envoyée. Toutes les diffusions sont regroupées dans le dossier **[!UICONTROL Administration > Exploitation > Message Center > Défaut > Diffusions]**.

![](assets/messagecenter_deliveries_execinstances_001.png)

Par défaut, elles sont classées dans un sous-dossier correspondant au mois d&#39;envoi.

Ce classement peut être modifié dans les propriétés du modèle de message comme illustré ci-dessous.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Pour les installations hébergées ou hybrides, si vous avez effectué la mise à niveau vers le MTA amélioré d’Adobe Campaign, tous les messages transactionnels peuvent également être envoyés avec celui-ci pour optimiser la délivrabilité, le débit et la gestion des bounces. Tous les impacts sont identiques à ceux des messages marketing standard et sont présentés dans le document sur le [MTA amélioré d’Adobe Campaign](https://helpx.adobe.com/fr/campaign/kb/acc-campaign-enhanced-mta.html).