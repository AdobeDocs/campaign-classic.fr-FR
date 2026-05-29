---
product: campaign
title: Configurer les tests AB
description: Découvrez comment configurer les tests AB dans Campaign
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: A/B Testing
role: User
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
TQID: https://experienceleague.adobe.com/PHIsuJZ-o5mBRAPggyVYdzS7PBXL9GYCBc6Fr56ur5Q
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 264
ht-degree: 100%

---

# Configurer les tests AB {#configuring-a-b-testing}

Cette section décrit comment créer un workflow pour effectuer des tests A/B.

1. Créez un workflow, puis configurez une activité Requête pour cibler la population souhaitée. Consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html?lang=fr){target="_blank"}.

1. Ajoutez une activité Partage pour diviser la population ciblée en plusieurs sous-ensembles. Consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html?lang=fr){target="_blank"}.

1. Ouvrez l&#39;activité, puis configurez chaque sous-ensemble en fonction de vos besoins. Pour plus d&#39;informations sur le paramétrage d&#39;une activité **[!UICONTROL Partage]**, consultez [cette section](../../workflow/using/split.md).

   Dans cet exemple, nous voulons tester deux nouveaux objets pour une newsletter en les présentant à 10 % de la population ciblée.

   ![](assets/ab-testing-split.png)

1. Ajoutez une transition afin d’envoyer au reste de la population la newsletter avec l’objet actuel. Pour ce faire, activez l&#39;option **[!UICONTROL Générer le complémentaire]** à partir de l&#39;onglet **[!UICONTROL Général]**.

   ![](assets/ab-testing-complement.png)

1. Pour chaque sous-ensemble, ajoutez la version de la diffusion à tester.

   ![](assets/ab-testing-delivery.png)

Vous pouvez maintenant démarrer le workflow. Une fois les diffusions envoyées, vous pourrez suivre le comportement des trois sous-ensembles dans les logs de diffusion, afin de déterminer quel objet a rencontré le plus de succès.

Les workflows vous permettent également d&#39;automatiser vos processus en identifiant automatiquement la variante de diffusion qui a obtenu de meilleurs résultats, puis en l&#39;envoyant à la population restante. Voir à ce propos le [cas pratique](a-b-testing-use-case.md) dédié.
