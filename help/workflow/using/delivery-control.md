---
product: campaign
title: Agir sur une diffusion
description: En savoir plus sur l’activité de workflow de contrôle de diffusion
feature: Workflows
hide: true
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
TQID: https://experienceleague.adobe.com/WVXqtjcGQQOQJfVi58BqtLPqgG7AkgslAzQk4Vjbl9k
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 180
ht-degree: 62%

---

# Agir sur une diffusion{#delivery-control}



Une action de type **Agir sur une diffusion** permet de démarrer, mettre en pause ou arrêter une diffusion.

Il peut s&#39;agir de la diffusion spécifiée par la transition, d&#39;une diffusion explicitement sélectionnée ou bien calculée par un script. Pour plus d&#39;informations, consultez la section [Diffusion](delivery.md).

![](assets/edit_diffusion_act.png)

Si vous sélectionnez **[!UICONTROL Démarrer]**, l&#39;activité effectue toutes les étapes nécessaires pour démarrer la diffusion (calcul de la cible, préparation du contenu, diffusion). Si certaines de ces étapes ont déjà été effectuées par une activité de workflow précédente, elles ne seront pas réexécutées. Par exemple, si l’estimation de la cible a déjà été effectuée par une activité de type **[!UICONTROL Diffusion]** (voir [Diffusion](delivery.md)), l’activité **[!UICONTROL Agir sur la diffusion]** lancera les étapes restantes (préparation et diffusion du contenu).

Les options disponibles sont les suivantes :

* **[!UICONTROL Générer une transition sortante]**

  Crée une transition sortante qui sera activée en fin d&#39;exécution. Vous pouvez choisir de récupérer ou non la cible de la diffusion sortante.

* **[!UICONTROL Traiter les erreurs]**

  Pour plus d&#39;informations, consultez la section [Erreurs de traitement](monitoring-workflow-execution.md#processing-errors).

## Paramètres d&#39;entrée {#input-parameters}

* deliveryId

Identifiant de la diffusion, si l&#39;action sélectionnée est **[!UICONTROL Spécifiée par la transition]**.
