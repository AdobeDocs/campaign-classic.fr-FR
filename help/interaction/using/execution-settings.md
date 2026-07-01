---
product: campaign
title: Paramètres d'exécution
description: Paramètres d'exécution
feature: Interaction, Offers
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: e2dea4a0-9ed8-47b6-a16b-eeee653d2290
TQID: https://experienceleague.adobe.com/k2-e-laXDXtVyBJnoiyKAdNHKiS3nB-t1X1cEaqeudM
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
subfeature_v2: []
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 171
ht-degree: 100%

---

# Paramètres d’exécution{#execution-settings}



Lors de la création d’une simulation, vous pouvez, si nécessaire, spécifier les paramètres d’exécution.Ces paramètres vous permettent d’exécuter la simulation pendant une période de faible activité selon son niveau de priorité ou d’enregistrer les requêtes SQL dans le log.Cette étape est facultative.

Ces paramètres peuvent être modifiés par la suite depuis l&#39;onglet **[!UICONTROL Général]** de la fenêtre de simulation.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Différer l&#39;exécution vers une plage horaire de faible activité]** : permet de décaler le lancement de la simulation en fonction de la priorité choisie (Basse, Moyenne ou Haute), ceci pour optimiser les performances d&#39;Adobe Campaign.
* **[!UICONTROL Priorité]** : niveau appliqué à la simulation pour différer le déclenchement de la simulation. Lorsque l&#39;option **[!UICONTROL Différer l&#39;exécution vers une plage horaire de faible activité]** est sélectionnée, le workflow de traitement sur les opérations choisit une plage horaire de moindre activité pour lancer l&#39;opération.
* **[!UICONTROL Enregistrer les requêtes SQL dans le journal]** : cette fonctionnalité est réservée aux utilisateurs et utilisatrices experts.Elle vous permet d’ajouter un onglet au log dans lequel les requêtes SQL sont visibles. Cela permet de détecter un éventuel dysfonctionnement si la simulation se termine avec des erreurs.
