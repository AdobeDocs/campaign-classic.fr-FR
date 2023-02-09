---
product: campaign
title: Sélection d’un mapping de ciblage
description: Découvrez comment effectuer un mapping de ciblage
feature: Delivery Templates
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 100%

---

# Sélection d’un mapping de ciblage{#selecting-a-target-mapping}

![](../../assets/common.svg)

Par défaut, les modèles de diffusion ciblent les **[!UICONTROL Destinataires]**. Leur mapping de ciblage utilise donc les champs de la table **nms:recipient**. Adobe Campaign propose d&#39;autres mappings de ciblage pour vos diffusions que vous pouvez utiliser selon vos besoins.

![](assets/delivery_select_mapping.png)

Ces mappings sont les suivants :

| Nom | Utilisation | Schéma standard |
|---|---|---|
| Destinataires | Diffuser aux destinataires de la base Adobe Campaign | nms:recipient |
| Visiteurs | Diffuser aux visiteurs dont les profils ont été collectés par exemple via un parrainage (marketing viral), via les réseaux sociaux (Facebook, Twitter), etc. | mns:visitor |
| Abonnements  | Diffuser aux destinataires abonnés à un service d&#39;information, par exemple une newsletter | nms:subscription |
| Abonnements des visiteurs | Diffuser à des visiteurs abonnés à un service d&#39;information | nms:visitorSub |
| Service | Publier sur un compte Twitter ou une page Facebook | nms:service |
| Les opérateurs | Diffuser aux opérateurs Adobe Campaign | nms:operator |
| Fichier externe | Diffuser depuis un fichier contenant les toutes informations nécessaires à la diffusion | Aucun schéma associé, aucune cible renseignée |

>[!NOTE]
>
>Il est possible de créer dʼautres mappings de ciblage. Cette opération est toutefois réservée à des utilisateurs avancés. Pour plus d’informations, consultez [cette section](../../configuration/using/target-mapping.md).
