---
product: campaign
title: Joindre des fichiers
description: Joindre des fichiers
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Email
role: User
exl-id: db65e83e-276f-4163-98c3-3658a48acffc
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: ht
source-wordcount: '1082'
ht-degree: 100%

---

# Joindre des fichiers à un email {#attaching-files}

## À propos des pièces jointes à un email {#about-email-attachments}

Vous pouvez joindre un ou plusieurs fichiers à une diffusion d’email.

>[!NOTE]
>
>Pour éviter tout problème de performances, il est recommandé de ne pas inclure plusieurs pièces jointes par email. Le seuil recommandé peut être configuré à partir de la [liste des options de Campaign Classic](../../installation/using/configuring-campaign-options.md#delivery).

Deux cas se présentent :

* Sélectionner un fichier et le joindre tel quel à la diffusion.
* Personnaliser le contenu de la pièce jointe pour chaque destinataire. Dans ce cas, vous devez créer un **attachement calculé** : le nom de la pièce jointe est calculé au moment de l&#39;envoi pour chaque message et peut ainsi dépendre du destinataire. Le contenu peut également être personnalisé et converti en PDF au moment de l&#39;envoi, si vous avez souscrit à l&#39;option **Variable Digital Printing**.

>[!NOTE]
>
>Ce type de configuration est généralement réalisé dans les modèles de diffusion. Voir à ce sujet la section [À propos des modèles](about-templates.md).

## Mécanismes de sécurisation {#attachments-guardrails}

Pour éviter des problèmes de performances, les images incluses dans les e-mails ne doivent pas dépasser 100 Ko. Cette limite, définie par défaut, peut être modifiée à partir de l’option `NmsDelivery_MaxDownloadedImageSize`. Cependant, Adobe recommande vivement d’éviter les images volumineuses dans vos diffusions e-mail.

Adobe recommande également de limiter la taille et le nombre de fichiers joints. Par défaut, vous ne pouvez ajouter qu’un seul fichier en tant que pièce jointe à un e-mail. Ce seuil peut être configuré à partir de l’option `NmsDelivery_MaxRecommendedAttachments`.

En savoir plus dans [la liste des options de Campaign Classic](../../installation/using/configuring-campaign-options.md#delivery).

## Joindre un fichier local {#attaching-a-local-file}

Pour joindre un fichier local à une diffusion, procédez comme suit.

>[!NOTE]
>
>Vous pouvez joindre plusieurs fichiers à une diffusion. Les pièces jointes peuvent être dans n’importe quel format, format compressé inclus.

1. Cliquez sur le lien **[!UICONTROL Pièces jointes]**.
1. Cliquez sur le bouton **[!UICONTROL Ajouter]**.
1. Cliquez sur **[!UICONTROL Fichier...]** pour sélectionner le fichier à joindre à la diffusion.

   ![](assets/s_ncs_user_wizard_email_attachement.png)

Vous pouvez également faire glisser et déposer directement le fichier dans le champ de diffusion **[!UICONTROL Pièces jointes]** ou utiliser l’icône **[!UICONTROL Joindre]** de la barre d’outils de l’assistant de diffusion.

![](assets/s_ncs_user_wizard_add_file_ico.png)

Une fois le fichier sélectionné, il est immédiatement téléchargé sur le serveur afin d&#39;être disponible au moment de la diffusion. Il est répertorié dans le champ **[!UICONTROL Pièces jointes]**.

![](assets/s_ncs_user_wizard_email_attachement_e.png)

## Créer une pièce jointe calculée {#creating-a-calculated-attachment}

Lorsque vous créez un attachement calculé, le nom de la pièce jointe peut être calculé au moment de l&#39;analyse ou de l&#39;envoi pour chaque message et dépendre du destinataire. Il peut également être personnalisé et converti en PDF.

![](assets/s_ncs_user_wizard_attachment.png)

Pour créer une pièce jointe personnalisée, procédez comme suit :

1. Cliquez sur le lien **[!UICONTROL Pièces jointes]**.
1. Cliquez sur le bouton **[!UICONTROL Ajouter]**, puis sélectionnez **[!UICONTROL Pièce jointe calculée]**.
1. Sélectionnez le type de calcul dans la liste déroulante **[!UICONTROL Type]** :

![](assets/s_ncs_user_wizard_email01_136.png)

Les options disponibles sont les suivantes :

* **Le nom de fichier est renseigné lors de la création du modèle de diffusion**
* **Le contenu du fichier est personnalisé et converti en PDF au moment de l&#39;envoi pour chaque message**
* **Le nom de fichier est calculé lors de l&#39;analyse de la diffusion (il ne peut pas dépendre du destinataire)**
* **Le nom de fichier est calculé au moment de l&#39;envoi pour chaque destinataire (il peut dépendre du destinataire)**

### Joindre un fichier local {#attach-a-local-file}

Si la pièce jointe est un fichier local, sélectionnez l’option : **[!UICONTROL Le nom de fichier est renseigné lors de la création du modèle de diffusion]**. Le fichier est sélectionné en local et téléchargé sur le serveur. Suivez les étapes ci-dessous :

1. Sélectionnez le fichier à télécharger dans le champ **[!UICONTROL Fichier local]**.
1. Précisez le libellé si nécessaire. Le libellé remplace le nom du fichier lorsqu&#39;il est visualisé dans les systèmes de messagerie. Si rien n&#39;est spécifié, le nom du fichier est utilisé par défaut.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_02.png)

1. Au besoin, sélectionnez l&#39;option **[!UICONTROL Télécharger le fichier sur le serveur]**, puis cliquez sur le lien **[!UICONTROL Mettre à jour sur le serveur]** pour lancer le transfert.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_01.png)

Le fichier est alors disponible sur le serveur pour être joint aux diffusions créées à partir de ce modèle.

### Ajout d’un message personnalisé {#attach-a-personalized-message}

L’option **[!UICONTROL Le contenu du fichier est personnalisé et converti en PDF au moment de l’envoi pour chaque message]** permet de sélectionner un fichier avec des champs de personnalisation tels que le nom et le prénom du destinataire visé.

![](assets/s_ncs_user_wizard_email_calc_attachement_06.png)

Pour ce type de pièce jointe, les étapes de configuration sont les suivantes :

1. Sélectionnez le fichier à télécharger.
1. Précisez le libellé si nécessaire.
1. Sélectionnez l&#39;option **[!UICONTROL Télécharger le fichier sur le serveur]**, puis cliquez sur le lien **[!UICONTROL Mettre à jour sur le serveur]** pour lancer le transfert.
1. Vous pouvez afficher une prévisualisation : pour cela, sélectionnez un destinataire.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_07.png)

1. Analysez votre diffusion puis démarrez-la.

   Chaque destinataire reçoit un PDF personnalisé en attachement de la diffusion.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_08.png)



### Joindre un fichier calculé {#attach-a-calculated-file}

Vous pouvez calculer le nom d’une pièce jointe pendant la préparation de la diffusion. Pour cela, sélectionnez l’option **[!UICONTROL Le nom de fichier est calculé lors de l’analyse de la diffusion (il ne peut pas dépendre du destinataire)]**.

>[!NOTE]
>
>Cette option n&#39;est utilisée que lorsque la diffusion est envoyée par un procédé externe ou par un workflow.

1. Précisez le libellé que vous souhaitez appliquer à la pièce jointe.
1. Indiquez le chemin d&#39;accès au fichier et son nom exact dans la fenêtre de définition.

   >[!IMPORTANT]
   >
   >Le fichier doit être présent sur le serveur.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_04.png)

1. Analysez puis démarrez votre diffusion.

   Le calcul du nom du fichier est visible dans le journal de l&#39;analyse.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_05.png)

### Joindre un fichier personnalisé {#attach-a-personalized-file}

Lorsque vous sélectionnez la pièce jointe, vous pouvez choisir l’option **[!UICONTROL Le nom de fichier est calculé au moment de l’envoi pour chaque destinataire (il peut dépendre du destinataire)]**. Vous pouvez ensuite associer les données de personnalisation des destinataires au nom du fichier à envoyer.

>[!NOTE]
>
>Cette option n&#39;est utilisée que lorsque la diffusion est envoyée par un procédé externe ou par un workflow.

1. Précisez le libellé que vous souhaitez appliquer à la pièce jointe.
1. Indiquez le chemin d&#39;accès du fichier, ainsi que son nom exact dans la fenêtre de définition. Si le nom du fichier est personnalisé, vous pouvez utiliser les champs de personnalisation pour les valeurs correspondantes.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_010.png)

   >[!IMPORTANT]
   >
   >Le fichier doit être présent sur le serveur.

1. Analysez puis démarrez votre diffusion.

   Dans l&#39;exemple ci-dessous, le fichier attaché a été choisi en fonction de son nom tel qu&#39;il a été défini à l&#39;aide des champs de fusion.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_011.png)

### Paramètres des pièces jointes {#attachment-settings}

Pour les deux premières options, vous pouvez choisir de **[!UICONTROL Télécharger le fichier sur le serveur]**, en cochant l&#39;option correspondante. Le lien **[!UICONTROL Mettre à jour sur le serveur]** permet de lancer le téléchargement.

![](assets/s_ncs_user_wizard_email01_137.png)

Un message vous indique que le fichier a bien été téléchargé sur le serveur :

![](assets/s_ncs_user_wizard_email01_1371.png)

En cas de changement de fichier, un message d&#39;avertissement est affiché :

![](assets/s_ncs_user_wizard_email01_1372.png)

L&#39;onglet **[!UICONTROL Avancé]** permet de définir des options avancées sur les fichiers joints :

* Vous pouvez définir des options de filtrage afin de ne pas transmettre le fichier joint à l’ensemble des destinataires. L&#39;option **[!UICONTROL Activer le filtrage des destinataires qui recevront la pièce jointe]** active une zone de saisie utilisée pour définir un script de sélection des destinataires. Ce script doit être saisi en JavaScript.
* Vous pouvez scripter le nom du fichier afin de le personnaliser.

  Entrez votre texte dans la fenêtre et utilisez les champs de personnalisation disponibles dans la liste déroulante. Dans l&#39;exemple ci-dessous, le nom du fichier est personnalisé pour contenir la date du jour et le nom du destinataire.

  ![](assets/s_ncs_user_wizard_email_calc_attachement_09.png)
