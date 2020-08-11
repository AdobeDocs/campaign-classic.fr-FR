---
title: Mise à jour de la console
seo-title: Mise à jour de la console
description: Mise à jour de la console
seo-description: null
page-status-flag: never-activated
uuid: d2193d4f-b98c-47b1-88f1-7e5ccf4c453c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 9281808b-1c2f-4095-9051-f181f089f205
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd
workflow-type: ht
source-wordcount: '69'
ht-degree: 100%

---


# Mise à jour de la console{#console-update}

Si vous avez coché l&#39;option **[!UICONTROL Ne pas demander la mise à jour de la console]** et que vous souhaitez réactiver la demande de mise à jour, la procédure est la suivante :

1. Ouvrez l’éditeur de la base de registre via la commande **regedit** depuis le menu **[!UICONTROL Démarrer > Exécuter]** de Windows.

   ![](assets/ncs_console_update_1.png)

1. Dans l’arborescence, affichez les options du nœud **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]**.
1. Supprimez l&#39;entrée **[!UICONTROL confAdvisedUpgrade]** et fermez l&#39;éditeur de base de registre.

   ![](assets/ncs_console_update_2.png)

