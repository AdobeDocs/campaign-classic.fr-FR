---
product: campaign
title: Utiliser une table de personnes destinataires externe
description: Utiliser une table de personnes destinataires externe
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '94'
ht-degree: 100%

---

# Utiliser une table de personnes destinataires externe{#using-an-external-recipient-table}



Si le tableau des diffusions est un tableau externe, vous devrez effectuer des configurations supplémentaires. Le schéma **[!UICONTROL nms:seedmember]** doit être étendu. Un onglet est ajouté aux adresses de contrôle afin de définir les champs adéquats, comme indiqué ci-dessous :

![](assets/s_ncs_user_seedlist_new_tab.png)

Dans ce cas, pour ajouter les adresses de contrôle dans la diffusion, renseignez directement les champs adéquats dans l&#39;onglet correspondant ou importez des modèles d&#39;adresses :

![](assets/s_ncs_user_seedlist_add_new_tab.png)

L&#39;extension du schéma **nms:seedMember** est présentée dans [cette section](../../configuration/using/seed-addresses.md).
