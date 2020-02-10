---
title: Joindre des fichiers
seo-title: Joindre des fichiers
description: Joindre des fichiers
seo-description: null
page-status-flag: never-activated
uuid: a4dc1908-a6ef-4bc8-a310-605fc80c34ca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: f3666c12-5e6f-452e-b1d6-b69a7e9f6f6e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 06f2106c7c37fd5f115d15f3530997571f1f8e70

---


# Joindre des fichiers{#attaching-files}

## A propos des pièces jointes à un email {#about-email-attachments}

Vous pouvez attacher un ou plusieurs fichiers à une diffusion par email. Deux cas sont possibles :

* Sélectionner un fichier et le joindre tel quel à la diffusion.
* Personalize the content of the attachment for each recipient. In this case, you need to create a **calculated attachment**: the name of the attachment is computed at the time of delivery for each message depending on the recipient. The content can also be personalized and converted into PDF format at the time of delivery, if you have the **Variable Digital Printing** option.

>[!NOTE]
>
>Ce type de configuration est généralement effectué dans les modèles de remise. For more on this, refer to [About templates](../../delivery/using/about-templates.md).

## Joindre un fichier local {#attaching-a-local-file}

Pour joindre un fichier local à une remise, procédez comme suit.

>[!NOTE]
>
>Vous pouvez joindre plusieurs fichiers à une remise. Les pièces jointes peuvent être dans n’importe quel format, format compressé inclus.

1. Cliquez sur le **[!UICONTROL Attachments]** lien.
1. Cliquez sur le **[!UICONTROL Add]** bouton, puis sur **[!UICONTROL File...]** pour sélectionner le fichier à joindre à la remise.

![](assets/s_ncs_user_wizard_email_attachement.png)

Vous pouvez également faire glisser et déposer directement le fichier dans le champ de remise **[!UICONTROL Attachments]** ou utiliser l’icône **[!UICONTROL Attach]** de la barre d’outils de l’assistant de remise,

![](assets/s_ncs_user_wizard_add_file_ico.png)

1. Une fois le fichier sélectionné, il est immédiatement téléchargé sur le serveur pour être disponible au moment de la remise. Il est répertorié dans le **[!UICONTROL Attachments]** champ.

![](assets/s_ncs_user_wizard_email_attachement_e.png)

## Créer un attachement calculé {#creating-a-calculated-attachment}

Lorsque vous créez un attachement calculé, le nom de la pièce jointe peut être calculé au moment de l&#39;analyse ou de l&#39;envoi pour chaque message et dépendre du destinataire. Il peut également être personnalisé et converti en PDF.

![](assets/s_ncs_user_wizard_attachment.png)

Pour créer une pièce jointe personnalisée, procédez comme suit :

1. Cliquez sur le **[!UICONTROL Attachments]** lien.
1. Cliquez sur le **[!UICONTROL Add]** bouton, puis sélectionnez **[!UICONTROL Calculated attachment]**.
1. Sélectionnez le de calcul dans la liste déroulante **[!UICONTROL Type]** Type :

![](assets/s_ncs_user_wizard_email01_136.png)

Les options disponibles sont les suivantes :

* **Le nom de fichier est renseigné lors de la création du modèle de diffusion**
* **Le contenu du fichier est personnalisé et converti en PDF au moment de l&#39;envoi pour chaque message**
* **Le nom de fichier est calculé lors de l&#39;analyse de la diffusion (il ne peut pas dépendre du destinataire)**
* **Le nom de fichier est calculé au moment de l&#39;envoi pour chaque destinataire (il peut dépendre du destinataire)**

### Joindre un fichier local {#attach-a-local-file}

Si la pièce jointe est un fichier local, sélectionnez l’option : **[!UICONTROL File name is specified when creating the delivery template]**. Le fichier est sélectionné localement et téléchargé sur le serveur. Suivez les étapes ci-dessous :

1. Select the file to upload in the **[!UICONTROL Local file]** field.
1. Précisez le libellé si nécessaire. Le libellé remplace le nom du fichier lorsqu&#39;il est visualisé dans les systèmes de messagerie. Si rien n&#39;est spécifié, le nom du fichier est utilisé par défaut.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_02.png)

1. Si nécessaire, sélectionnez **[!UICONTROL Upload file on the server]**, puis cliquez **[!UICONTROL Update on server]** pour lancer le transfert.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_01.png)

   Le fichier est alors disponible sur le serveur pour être joint aux diffusions créées à partir de ce modèle.

### Ajout d’un message personnalisé {#attach-a-personalized-message}

Cette option **[!UICONTROL The file content is personalized and converted into PDF format at the time of delivery for each message]** vous permet de sélectionner une amende avec des champs de personnalisation, tels que le nom et le prénom du destinataire.

![](assets/s_ncs_user_wizard_email_calc_attachement_06.png)

Pour ce type d&#39;attachement, les étapes de paramétrage sont les suivantes :

1. Sélectionnez le fichier à télécharger.

   >[!NOTE]
   >
   >Le fichier source doit être créé sous LibreOffice. La configuration de l&#39;instance doit respecter les prérequis décrits dans [cette section](../../installation/using/before-starting.md).

1. Précisez le libellé si nécessaire.
1. Sélectionnez **[!UICONTROL Upload file on the server]**, puis cliquez sur **[!UICONTROL Update on server]** pour lancer le transfert.
1. Vous pouvez afficher une prévisualisation : pour cela, sélectionnez un destinataire.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_07.png)

1. Analysez votre diffusion puis démarrez-la.

   Chaque destinataire reçoit un PDF personnalisé en attachement de la diffusion.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_08.png)

### Ajout d’un fichier calculé {#attach-a-calculated-file}

Vous pouvez calculer le nom de la pièce jointe pendant la préparation de la remise. Pour ce faire, sélectionnez l’option **[!UICONTROL The file name is calculated during delivery analysis (it cannot depend on the recipient)]**.

>[!NOTE]
>
>Cette option n&#39;est utilisée que lorsque la diffusion est envoyée par un procédé externe ou par un workflow.

1. Précisez le libellé que vous souhaitez appliquer à la pièce jointe.
1. Indiquez le chemin d&#39;accès au fichier et son nom exact dans la fenêtre de définition.

   >[!CAUTION]
   >
   >Le fichier doit être présent sur le serveur.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_04.png)

1. Analysez puis démarrez votre diffusion.

   Le calcul du nom du fichier est visible dans le journal de l&#39;analyse.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_05.png)

### Ajout d’un fichier personnalisé {#attach-a-personalized-file}

Lorsque vous sélectionnez la pièce jointe, vous pouvez choisir l’option **[!UICONTROL The file name is calculated during delivery for each recipient (it can depend on the recipient)]**. Vous pouvez ensuite mapper les données de personnalisation du destinataire avec le nom du fichier à envoyer.

>[!NOTE]
>
>Cette option n&#39;est utilisée que lorsque la diffusion est envoyée par un procédé externe ou par un workflow.

1. Précisez le libellé que vous souhaitez appliquer à la pièce jointe.
1. Indiquez le chemin d&#39;accès du fichier, ainsi que son nom exact dans la fenêtre de définition. Si le nom du fichier est personnalisé, vous pouvez utiliser les champs de personnalisation pour les valeurs correspondantes.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_010.png)

   >[!CAUTION]
   >
   >Le fichier doit être présent sur le serveur.

1. Analysez puis démarrez votre diffusion.

   Dans l&#39;exemple ci-dessous, le fichier attaché a été choisi en fonction de son nom tel qu&#39;il a été défini à l&#39;aide des champs de fusion.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_011.png)

### Paramètres des fichiers attachés {#attachment-settings}

Pour les deux premières options, vous pouvez choisir **[!UICONTROL Upload file on the server]** en sélectionnant l’option appropriée. Le **[!UICONTROL Update the file on the server]** lien vous permet de commencer à télécharger.

![](assets/s_ncs_user_wizard_email01_137.png)

Un message vous indique que le fichier a bien été téléchargé sur le serveur :

![](assets/s_ncs_user_wizard_email01_1371.png)

En cas de changement de fichier, un message d&#39;avertissement est affiché :

![](assets/s_ncs_user_wizard_email01_1372.png)

The **[!UICONTROL Advanced]** tab lets you define advanced options on attached files:

* Vous pouvez définir des options de filtre pour éviter d’envoyer le fichier joint à tous les destinataires. L’option **[!UICONTROL Enable filtering of recipients who will receive the attachment]** active un champ de saisie utilisé pour définir un script de sélection de destinataire, qui doit être entré dans JavaScript.
* Vous pouvez scripter le nom du fichier afin de le personnaliser.

   Entrez votre texte dans la fenêtre et utilisez les champs de personnalisation disponibles dans la liste déroulante. Dans l&#39;exemple ci-dessous, le nom du fichier est personnalisé pour contenir la date du jour et le nom du destinataire.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_09.png)
