---
product: campaign
title: Agir sur une diffusion
description: En savoir plus sur l’activité de workflow de contrôle de diffusion
feature: Workflows
hide: true
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
TQID: https://experienceleague.adobe.com/WVXqtjcGQQOQJfVi58BqtLPqgG7AkgslAzQk4Vjbl9k
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 180
ht-degree: 100%

---

# Agir sur une diffusion{#delivery-control}



Une action de type **Agir sur une diffusion** permet de démarrer, mettre en pause ou arrêter une diffusion.

Il peut s&#39;agir de la diffusion spécifiée par la transition, d&#39;une diffusion explicitement sélectionnée ou bien calculée par un script. Pour plus d&#39;informations, consultez la section [Diffusion](delivery.md).

![](assets/edit_diffusion_act.png)

Si vous sélectionnez **[!UICONTROL Démarrer]**, l’activité effectue toutes les étapes requises pour démarrer la diffusion (calcul de la cible, préparation du contenu, diffusion).Si certaines de ces étapes ont déjà été effectuées par une activité de workflow précédente, elles ne seront plus exécutées.Par exemple, si l’estimation de la cible a déjà été effectuée par une activité de type **[!UICONTROL Diffusion]** (voir [Diffusion](delivery.md)), l’activité **[!UICONTROL Agir sur la diffusion]** lancera les étapes restantes (préparation et diffusion du contenu).

Les options disponibles sont les suivantes :

* **[!UICONTROL Générer une transition sortante]**

  Crée une transition sortante qui sera activée à la fin de l’exécution.Vous pouvez choisir de récupérer la cible de la diffusion sortante ou non.

* **[!UICONTROL Traiter les erreurs]**

  Pour plus d&#39;informations, consultez la section [Erreurs de traitement](monitoring-workflow-execution.md#processing-errors).

## Paramètres d&#39;entrée {#input-parameters}

* deliveryId

Identifiant de la diffusion, si l&#39;action sélectionnée est **[!UICONTROL Spécifiée par la transition]**.
