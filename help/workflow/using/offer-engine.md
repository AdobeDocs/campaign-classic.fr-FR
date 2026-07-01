---
product: campaign
title: Moteur d'offres
description: Moteur d'offres
feature: Workflows, Interaction
hide: true
exl-id: 8db4b04f-7754-4a49-ab72-afc916888ebb
TQID: https://experienceleague.adobe.com/oAzSAhtWhfJTWcWowjaewtlVucahY839933SaCQZO10
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 141
ht-degree: 100%

---

# Moteur d&#39;offres{#offer-engine}



L&#39;activité **[!UICONTROL Moteur d&#39;offres]** vous permet de définir un appel au moteur d&#39;offres en amont d&#39;une diffusion.

Cette activité fonctionne sur le même principe que l’activité d’enrichissement avec un appel au moteur, en enrichissant les données de la population entrante avec une offre calculée par le moteur, avant une diffusion.

![](assets/int_offerengine_activity2.png)

Après avoir paramétré votre requête (voir cette [section](query.md)) :

1. Placez et ouvrez une activité **[!UICONTROL Moteur d&#39;offres]**.
1. Renseignez les différents champs disponibles afin de définir les paramètres d’appel d’offres au moteur (emplacement, catégorie ou thème(s), date de contact, nombre d’offres à conserver).Le moteur calculera automatiquement la ou les offres à ajouter en fonction de ces paramètres.

   >[!CAUTION]
   >
   >Si vous utilisez cette activité, seules les propositions utilisées dans la diffusion sont stockées.

   ![](assets/int_offerengine_activity1.png)

1. Paramétrez ensuite une activité de diffusion correspondant au canal de votre choix. Pour plus d&#39;informations, consultez la section [Diffusions cross-canal](cross-channel-deliveries.md).
