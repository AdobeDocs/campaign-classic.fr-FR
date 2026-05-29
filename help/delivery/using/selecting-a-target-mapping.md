---
product: campaign
title: Sélection d’un mapping de ciblage
description: Découvrez comment effectuer un mapping de ciblage
feature: Delivery Templates
hide: true
role: User
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
TQID: https://experienceleague.adobe.com/VpmfQdFoJ2Lfzetqx-s5MAdFdTTEsHxz2ISL15wNXIo
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
source-wordcount: 178
ht-degree: 92%

---

# Sélectionner un mapping de ciblage{#selecting-a-target-mapping}

Par défaut, les modèles de diffusion ciblent les **[!UICONTROL Destinataires]**. Leur mapping de ciblage utilise donc les champs de la table **nms:recipient**. Adobe Campaign propose d&#39;autres mappings de ciblage pour vos diffusions que vous pouvez utiliser selon vos besoins.

![](assets/delivery_select_mapping.png)

Ces mappings sont les suivants :

| Nom | Utilisation | Schéma standard |
|---|---|---|
| Destinataires | Diffuser aux destinataires de la base Adobe Campaign | nms:recipient |
| Visiteurs et visiteuses | Diffuser aux visiteurs et visiteuses dont les profils ont été collectés, par exemple via un parrainage (marketing viral), via les réseaux sociaux (Facebook, X, anciennement Twitter), etc. | mns:visitor |
| Abonnements | Diffuser aux destinataires abonnés à un service d&#39;information, par exemple une newsletter | nms:subscription |
| Abonnements des visiteurs et visiteuses | Diffuser à des visiteurs abonnés à un service d&#39;information | nms:visitorSub |
| Service | Publier sur un compte X ou une page Facebook | nms:service |
| Les opérateurs | Diffuser aux opérateurs Adobe Campaign | nms:operator |
| Fichier externe | Diffuser depuis un fichier contenant les toutes informations nécessaires à la diffusion | Aucun schéma associé, aucune cible renseignée |

>[!NOTE]
>
>Vous pouvez également créer de nouveaux mappings de ciblage. Cette opération est réservée à des utilisateurs experts. Pour plus d’informations, consultez [cette section](../../configuration/using/target-mapping.md).
