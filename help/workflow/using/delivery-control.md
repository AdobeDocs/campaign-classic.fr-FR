---
title: Agir sur une diffusion
seo-title: Agir sur une diffusion
description: Agir sur une diffusion
seo-description: null
page-status-flag: never-activated
uuid: f9cef2d9-a6a5-45bd-8c7a-fabc11879628
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 0b5ee05c-4b96-425a-ab0f-60b930de21bd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# Agir sur une diffusion{#delivery-control}

Une activité de type **Agir sur une diffusion** permet de démarrer, mettre en pause ou arrêter une diffusion.

Il peut s&#39;agir de la diffusion spécifiée par la transition, d&#39;une diffusion explicitement sélectionnée ou bien calculée par un script. Voir à ce propos la section [Diffusion](../../workflow/using/delivery.md).

![](assets/edit_diffusion_act.png)

Si vous sélectionnez **[!UICONTROL Démarrer]**, l’activité effectue toutes les étapes requises pour démarrer la diffusion (calcul de la cible, préparation du contenu, diffusion). Si certaines de ces étapes ont déjà été effectuées par une activité de workflow précédente, elles ne seront plus exécutées. Par exemple, si l’estimation de la cible a déjà été effectuée par une activité de type **[!UICONTROL Diffusion]** (voir [Diffusion](../../workflow/using/delivery.md)), l’activité **[!UICONTROL Agir sur la diffusion]** lancera les étapes restantes (préparation et diffusion du contenu).

Les options disponibles sont les suivantes :

* **[!UICONTROL Générer une transition sortante]**

   Crée une transition sortante qui sera activée à la fin de l&#39;exécution. Vous pouvez choisir de récupérer la cible de l&#39;action de diffusion en sortie, ou non.

* **[!UICONTROL Traiter les erreurs]**

   Voir la section [Erreurs de traitement](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Paramètres d&#39;entrée {#input-parameters}

* deliveryId

Identifiant de la diffusion, si l&#39;action sélectionnée est **[!UICONTROL Spécifiée par la transition]**.
