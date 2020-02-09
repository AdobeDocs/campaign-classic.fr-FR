---
title: Valider
seo-title: Valider
description: Valider
seo-description: null
page-status-flag: never-activated
uuid: e3cd96ef-4f5d-4e17-9fec-5eaa4d835cb1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
discoiquuid: c363a7cf-81a5-4c02-a021-b822eeeadd03
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 70f51ba3937d0f20d9a488c61b52b7ec4396fa5e

---


# Valider{#validating}

Les concepts globaux de validation d’une diffusion sont présentés dans [cette section](../../delivery/using/steps-validating-the-delivery.md).

Le fichier de sortie d’une remise de courrier direct est généré pendant l’analyse de la remise. Le contenu du fichier dépend des colonnes de sortie sélectionnées (voir Fichier [d’](../../delivery/using/defining-the-direct-mail-content.md#extraction-file)extraction).

>[!NOTE]
>
>La phase d’analyse est détaillée dans [Analyse de la diffusion](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

Pendant la phase d&#39;analyse, le fichier est généré mais aucune information concernant les destinataires (à savoir les logs de diffusion) n&#39;est mise à jour. Vous pouvez donc annuler cette opération sans aucun risque.

Check the result of the analysis and the content of the output file before clicking **[!UICONTROL Confirm delivery]**. A confirmation message lets you launch the delivery.

La confirmation de l&#39;envoi lance l&#39;extraction des données dans le fichier spécifié.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

You can then close the wizard and look at the delivery logs via the **[!UICONTROL Delivery]** tab, accessible via the delivery details.

You can configure the delivery logs retrieval mode from the **[!UICONTROL Analysis]** tab of the delivery properties.

Deux modes sont proposés :

* **[!UICONTROL Messages are considered sent after validation]** (mode par défaut) : dans ce mode de fonction, tous les journaux de diffusion sont mis à jour lorsque l’opérateur confirme l’envoi (son état passe de &quot;Livraison en attente&quot; à &quot;Envoyé&quot;) et la diffusion est automatiquement définie sur **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** : ce mode vous permet de mettre à jour les journaux de diffusion via un fichier externe envoyé par le fournisseur de services. Dans ce cas, un processus de traitement de ces informations doit être utilisé pour mettre à jour l’état du journal large.

   >[!NOTE]
   >
   >In this case, the delivery&#39;s status also needs to be changed to **[!UICONTROL Finished]** by the user as soon as the broadlogs are updated.
