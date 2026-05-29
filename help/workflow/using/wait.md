---
product: campaign
title: Attente
description: En savoir plus sur l’activité de workflow d’attente
feature: Workflows
hide: true
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
TQID: https://experienceleague.adobe.com/sQ3GwMFQnhy6eOmFSfMUwT8Z3UE0p4cHLAjr8CjS2FM
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 193
ht-degree: 59%

---

# Attente{#wait}



Une activité **Attente** active sa transition après un délai compris entre quelques secondes et plusieurs mois. Une tâche d’attente ne bloque pas l’exécution des autres tâches ; le workflow peut exécuter des tâches en parallèle alors que cette tâche est en attente.

L&#39;éditeur permet de saisir le libellé et la durée d&#39;attente, comme dans l&#39;exemple ci-dessous :

![](assets/edit_wait.png)

Dans le champ **[!UICONTROL Durée]**, la valeur peut être exprimée dans l’unité de votre choix (en fonction des paramètres régionaux définis pour l’opérateur ou l’opératrice) :

* Si les paramètres régionaux ne sont pas spécifiés : **s** pour les secondes, **m** pour les minutes, **h** pour les heures, **j** pour les jours, **y** pour les années. Lors de la validation, la valeur est automatiquement convertie dans l’unité la plus lisible.

  L&#39;unité par défaut est le jour (**j**).

* Tandis que si, par exemple, les paramètres régionaux sont définis sur &#39;Français&#39; : **s** pour les secondes, **mn** pour les minutes, **h** pour les heures, **j** pour les jours, **m** pour les mois, **a** pour les années. Lors de la validation, la valeur est automatiquement traduite dans l&#39;unité la plus lisible, comme dans l&#39;exemple ci-dessus : **90s** a été traduit en **1mn 30s**.

  L&#39;unité par défaut est le jour (**j**).
