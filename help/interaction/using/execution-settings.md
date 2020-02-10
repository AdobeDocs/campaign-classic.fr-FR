---
title: Paramètres d'exécution
seo-title: Paramètres d'exécution
description: Paramètres d'exécution
seo-description: null
page-status-flag: never-activated
uuid: a6549091-0c33-4fe1-adde-de3b285dd456
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: simulating-offers
discoiquuid: 52b5d5a9-10dc-4601-8fe4-962a2334322b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Paramètres d&#39;exécution{#execution-settings}

Lors de la création d&#39;une simulation, vous pouvez, si besoin est, spécifier les paramètres d&#39;exécution. Ces paramètres permettent d&#39;exécuter la simulation pendant une plage horaire de moindre activité selon son niveau de priorité ou d&#39;enregistrer les requêtes SQL dans le journal. Cette étape est optionnelle.

These settings can be changed later in the **[!UICONTROL General]** tab of the simulation window.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** : vous permet de planifier la simulation en fonction de la priorité choisie (Faible, Moyenne ou Elevée) afin d’optimiser les performances d’Adobe Campaign.
* **[!UICONTROL Priority]** : il s’agit du niveau appliqué à la simulation pour la planifier. Lorsque l’ **[!UICONTROL Schedule execution for a time of low activity]** option est cochée, le processus de traitement de la campagne sélectionne un moment de faible activité pour lancer la campagne.
* **[!UICONTROL Log SQL queries in the journal]** : cette fonctionnalité est réservée aux utilisateurs experts. Il vous permet d&#39;ajouter un onglet au journal affichant des requêtes SQL afin de détecter d&#39;éventuels dysfonctionnements si la simulation se termine par des erreurs.

