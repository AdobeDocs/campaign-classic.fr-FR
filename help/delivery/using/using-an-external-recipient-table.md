---
product: campaign
title: Utiliser une table de personnes destinataires externe
description: Utiliser une table de personnes destinataires externe
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
TQID: https://experienceleague.adobe.com/Uq5yqNYkyDrFVtueUlkIOEC9XEUaYtBArNy8-t1rKAw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 92
ht-degree: 92%

---

# Utiliser une table de personnes destinataires externe{#using-an-external-recipient-table}



Si le tableau des diffusions est un tableau externe, vous devrez effectuer des configurations supplémentaires. Le schéma **[!UICONTROL nms:seedmember]** doit être étendu. Un onglet est ajouté aux adresses de contrôle afin de définir les champs adéquats, comme indiqué ci-dessous :

![](assets/s_ncs_user_seedlist_new_tab.png)

Dans ce cas, pour ajouter les adresses de contrôle dans la diffusion, renseignez directement les champs adéquats dans l&#39;onglet correspondant ou importez des modèles d&#39;adresses :

![](assets/s_ncs_user_seedlist_add_new_tab.png)

L’extension de schéma **nms:seedMember** est [cette section](../../configuration/using/seed-addresses.md).
