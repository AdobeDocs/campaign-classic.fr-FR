---
product: campaign
title: Offres par cellule
description: Offres par cellule
feature: Workflows, Targeting Activity, Interaction
exl-id: 72b17b48-093a-4eb9-a848-3c1570e49b61
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Offres par cellule{#offers-by-cell}

![](../../assets/v7-only.svg)

L&#39;activité **[!UICONTROL Offres par cellules]** vous permet de répartir la population entrante (par exemple issue d&#39;une requête) en plusieurs segments, et de définir une offre à proposer pour chacun de ces segments.

Cette activité ne peut être utilisée qu&#39;avec **Interaction**. Pour plus d&#39;informations, consultez cette [section](../../interaction/using/about-outbound-channels.md).

Pour cela :

1. Placez l&#39;activité **[!UICONTROL Offres par cellules]** après avoir défini la population cible, puis ouvrez-là.
1. Dans l&#39;onglet **[!UICONTROL Général]**, sélectionnez l&#39;emplacement sur lequel vous souhaitez proposer les offres.
1. Dans l&#39;onglet **[!UICONTROL Cellules]**, définissez les différents sous-ensembles via le bouton **[!UICONTROL Ajouter]** :

   * Définissez la population du sous-ensemble grâce aux règles de filtrage et de limitation disponibles.
   * Sélectionnez ensuite l&#39;offre que vous souhaitez proposer au sous-ensemble. Les offres disponibles sont celles éligibles sur l&#39;emplacement sélectionné à l&#39;étape précédente.

      ![](assets/int_offer_per_cell1.png)

1. Paramétrez ensuite une activité de diffusion correspondant au canal de votre choix. Voir à ce sujet la section [Diffusions cross-canal](cross-channel-deliveries.md).
