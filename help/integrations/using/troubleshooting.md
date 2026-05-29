---
product: campaign
title: Résolution des problèmes
description: Résolution des problèmes
feature: Audiences, People Core Service Integration, Troubleshooting
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
audience: integrations
content-type: reference
topic-tags: audience-sharing
hide: true
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
TQID: https://experienceleague.adobe.com/4de9cxyepP-REa2OTWniBFWInphApeUM79sZuFGcynI
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 147
ht-degree: 78%

---

# Résolution des problèmes{#troubleshooting}



En cas d&#39;erreur, vérifiez que les éléments suivants sont correctement configurés :

* **Comptes externes**

  Dans **[!UICONTROL Administration > Plateforme > Comptes externes]**, vérifiez que les comptes SFTP externes suivants sont correctement configurés. Les serveurs SFTP mentionnés doivent avoir été configurés dans Adobe Experience Cloud par votre consultant.

   * **[!UICONTROL importSharedAudience : compte SFTP dédié à l&#39;import d&#39;audiences.]**
   * **[!UICONTROL exportSharedAudience : compte SFTP dédié à l&#39;export d&#39;audiences.]**

* **AMC Data source**

  Dans **[!UICONTROL Administration > Plateforme > AMC Data sources]**, vérifiez que l&#39;AMC Data source est correctement définie.

Il est possible que certaines données soient manquantes lors du partage d’une audience via Experience Cloud Audience ou lors de l’import d’une audience. Seuls les enregistrements dont l’identifiant (&#39;Visitor ID&#39; ou &#39;Declared ID&#39;) a pu être réconcilié avec la dimension des profils sont transférés. Les identifiants provenant de segments non reconnus par Adobe Campaign ne sont pas importés.
