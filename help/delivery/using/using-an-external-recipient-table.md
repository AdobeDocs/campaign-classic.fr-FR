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
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 92
ht-degree: 100%

---

# Utiliser une table de personnes destinataires externe{#using-an-external-recipient-table}



Si le tableau des diffusions est un tableau externe, vous devrez effectuer des configurations supplémentaires. Le schéma **[!UICONTROL nms:seedmember]** doit être étendu. Un onglet est ajouté aux adresses de contrôle afin de définir les champs adéquats, comme indiqué ci-dessous :

![](assets/s_ncs_user_seedlist_new_tab.png)

Dans ce cas, pour ajouter les adresses de contrôle dans la diffusion, renseignez directement les champs adéquats dans l&#39;onglet correspondant ou importez des modèles d&#39;adresses :

![](assets/s_ncs_user_seedlist_add_new_tab.png)

L’extension de schéma **nms:seedMember** est présentée dans [cette section](../../configuration/using/seed-addresses.md).
