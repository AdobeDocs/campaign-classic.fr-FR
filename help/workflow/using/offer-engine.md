---
product: campaign
title: Moteur d'offres
description: Moteur d'offres
feature: Workflows, Interaction
hide: true
hidefromtoc: true
exl-id: 8db4b04f-7754-4a49-ab72-afc916888ebb
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 100%

---

# Moteur d&#39;offres{#offer-engine}



L&#39;activité **[!UICONTROL Moteur d&#39;offres]** vous permet de définir un appel au moteur d&#39;offres en amont d&#39;une diffusion.

Cette activité fonctionne sur le même principe que l’activité d’enrichissement avec un appel au moteur, en enrichissant les données de la population entrante avec une offre calculée par le moteur, avant une diffusion.

![](assets/int_offerengine_activity2.png)

Après avoir paramétré votre requête (voir cette [section](query.md)) :

1. Placez et ouvrez une activité **[!UICONTROL Moteur d&#39;offres]**.
1. Renseignez les différents champs disponibles afin de définir les paramètres d&#39;appel au moteur (emplacement, catégorie ou thème(s), date de contact, nombre d&#39;offres à conserver). Le moteur calculera automatiquement la ou les offres à ajouter en fonction de ces paramètres.

   >[!CAUTION]
   >
   >Si vous utilisez cette activité, seules les propositions utilisées dans la diffusion sont stockées.

   ![](assets/int_offerengine_activity1.png)

1. Paramétrez ensuite une activité de diffusion correspondant au canal de votre choix. Voir à ce sujet la section [Diffusions cross-canal](cross-channel-deliveries.md).
