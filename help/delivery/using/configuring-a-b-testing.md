---
product: campaign
title: Configurer les tests AB
description: Découvrez comment configurer les tests AB dans Campaign
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: ht
source-wordcount: '215'
ht-degree: 100%

---

# Configurer les tests AB {#configuring-a-b-testing}



Cette section décrit comment créer un workflow pour effectuer des tests A/B.

1. Créez un nouveau workflow, puis configurez une activité [Requête](../../workflow/using/query.md) pour cibler la population souhaitée.

1. Ajoutez une activité [Partage](../../workflow/using/split.md) pour diviser la population ciblée en plusieurs sous-ensembles.

1. Ouvrez l&#39;activité, puis configurez chaque sous-ensemble en fonction de vos besoins. Pour plus d&#39;informations sur le paramétrage d&#39;une activité **[!UICONTROL Partage]**, consultez [cette section](../../workflow/using/split.md).

   Dans cet exemple, nous voulons tester deux nouveaux sujets pour une newsletter en les présentant à 10 % de la population ciblée.

   ![](assets/ab-testing-split.png)

1. Ajoutez une transition afin d&#39;envoyer au reste de la population la newsletter avec le sujet actuel. Pour ce faire, activez l&#39;option **[!UICONTROL Générer le complémentaire]** à partir de l&#39;onglet **[!UICONTROL Général]**.

   ![](assets/ab-testing-complement.png)

1. Pour chaque sous-ensemble, ajoutez la version de la diffusion à tester.

   ![](assets/ab-testing-delivery.png)

Vous pouvez maintenant démarrer le workflow. Une fois les diffusions envoyées, vous pourrez suivre le comportement des trois sous-ensembles dans les logs de diffusion, afin de déterminer quel sujet a rencontré le plus de succès.

Les workflows vous permettent également d&#39;automatiser vos processus en identifiant automatiquement la variante de diffusion qui a obtenu de meilleurs résultats, puis en l&#39;envoyant à la population restante. Voir à ce propos le [cas pratique](a-b-testing-use-case.md) dédié.
