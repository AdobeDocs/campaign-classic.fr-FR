---
solution: Campaign Classic
product: campaign
title: Configuration des tests A/B
description: Découvrez comment configurer les tests A/B en Campaign Classic.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: a341980e9d940857388bb2755e5eaa74824cf6ea
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---


# Configuration des tests A/B {#configuring-a-b-testing}

Cette section décrit comment créer un processus pour effectuer des tests A/B.

1. Créez un nouveau processus, puis configurez une activité [Requête](../../workflow/using/query.md) pour cible de la population souhaitée.

1. Ajouter une activité [fractionnée](../../workflow/using/split.md) pour diviser la population ciblée en plusieurs sous-ensembles.

1. Ouvrez l’activité, puis configurez chaque sous-ensemble en fonction de vos besoins. Pour plus d&#39;informations sur la configuration d&#39;une activité **[!UICONTROL Split]**, consultez [cette section](../../workflow/using/split.md).

   Dans cet exemple, nous voulons tester deux nouveaux sujets pour un bulletin d&#39;information en les présentant à 10 % de la population ciblée.

   ![](assets/ab-testing-split.png)

1. Ajoutez une transition afin d&#39;envoyer au reste de la population le bulletin d&#39;information sur le sujet en cours. Pour ce faire, activez l&#39;option **[!UICONTROL Générer un complément]** à partir de l&#39;onglet **[!UICONTROL Général]**.

   ![](assets/ab-testing-complement.png)

1. Pour chaque sous-ensemble, ajoutez la version de la diffusion à tester.

   ![](assets/ab-testing-delivery.png)

Vous pouvez maintenant début le processus. Une fois les diffusions envoyées, vous pourrez suivre le comportement des trois sous-ensembles dans les logs de diffusion, afin de voir quel sujet a été le plus réussi.

Les workflows vous permettent également d&#39;automatiser vos processus en identifiant automatiquement la variante de diffusion qui a obtenu de meilleurs résultats, puis en l&#39;envoyant à la population restante. Pour plus d&#39;informations à ce sujet, reportez-vous à ce [cas d&#39;utilisation](../../delivery/using/a-b-testing-use-case.md) dédié.
