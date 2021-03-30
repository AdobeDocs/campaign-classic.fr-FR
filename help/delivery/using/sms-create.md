---
solution: Campaign Classic
product: campaign
title: Créer un SMS avec Campaign
description: Découvrez comment créer des SMS avec Campaign
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
translation-type: tm+mt
source-git-commit: 5a084ebe5295d19de24cf92c721d4692f0f5deb8
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 84%

---


# Créer une diffusion SMS {#creating-a-sms-delivery}

## Sélectionnez le canal de diffusion {#selecting-the-delivery-channel}

Pour créer une diffusion SMS, procédez comme suit :

>[!NOTE]
>
>Les concepts généraux relatifs à la création d&#39;une diffusion sont présentés dans [cette section](../../delivery/using/steps-about-delivery-creation-steps.md).

1. Créez une diffusion, par exemple depuis le tableau de bord des diffusions.
1. Sélectionnez le modèle de diffusion **Envoyé vers mobiles (SMPP)** que vous avez créé précédemment. Pour en savoir plus sur ce sujet, consultez la section [Modifier le modèle de diffusion](sms-set-up.md#changing-the-delivery-template).

   ![](assets/s_user_mobile_wizard.png)

1. Identifiez la diffusion avec un libellé, un code et une description. Voir à ce propos [cette section](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery).
1. Cliquez sur **[!UICONTROL Continuer]** pour valider ces informations et afficher la fenêtre de configuration du message.

## Définissez le contenu du SMS {#defining-the-sms-content}

Pour définir le contenu du SMS, procédez comme suit :

1. Saisissez le contenu du message dans la section **[!UICONTROL Contenu texte]** de l&#39;assistant. Les boutons de la barre d&#39;outils permettent d&#39;importer, d&#39;enregistrer ou de rechercher dans un contenu. Le dernier bouton permet d&#39;insérer des champs de personnalisation.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   L&#39;utilisation des champs de personnalisation est présentée dans la section [À propos de la personnalisation](../../delivery/using/about-personalization.md).

1. Cliquez sur l&#39;onglet **[!UICONTROL Aperçu]** en bas de page afin de visualiser le rendu du message, avec sa personnalisation. Pour lancer la visualisation, vous devez choisir un destinataire à partir du bouton **[!UICONTROL Tester la personnalisation]** situé dans la barre d&#39;outils. Sélectionnez un individu parmi la ou les cibles définies ou choisissez une autre personne.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   Vous pouvez valider le message SMS. Vous pouvez également visualiser le contenu du SMS sur l&#39;écran du téléphone mobile affiché à la droite de l&#39;éditeur de contenu. Cliquez sur l&#39;écran pour faire défiler le contenu avec la souris.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. Cliquez sur le lien **[!UICONTROL Données chargées]** pour visualiser les informations concernant le destinataire.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >La longueur des messages SMS est limitée à 160 caractères si la page de code Latin-1 (ISO-8859-1) est utilisée. Si le message est rédigé en unicode, il ne peut dépasser 70 caractères. Certains caractères spéciaux peuvent avoir une influence sur la longueur du message. Pour plus d&#39;informations sur la longueur du message, consultez la section [translittération des caractères SMS](#about-character-transliteration).
   >
   >Lors de la présence de champs de personnalisation ou de contenu conditionnel, la taille du message varie d&#39;un destinataire à l&#39;autre. La longueur du message doit être évaluée une fois la personnalisation effectuée.
   >
   >Lorsque vous lancez l&#39;analyse, la longueur des messages est contrôlée et un message d&#39;avertissement est affiché en cas de dépassement.

1. Si vous utilisez le connecteur NetSize ou un connecteur SMPP, il est possible de personnaliser le nom de l&#39;émetteur de la diffusion. Voir à ce propos la section [Paramètres avancés](#advanced-parameters).

## Sélectionner la population de cibles {#selecting-the-target-population}

Le processus détaillé lors de la sélection de la population cible d&#39;une diffusion est présenté dans [cette section](../../delivery/using/steps-defining-the-target-population.md).

Pour plus d&#39;informations sur l&#39;utilisation des champs de personnalisation, consultez [cette section](../../delivery/using/about-personalization.md).

Pour plus d&#39;informations sur l&#39;inclusion d&#39;une liste de semences, consultez [cette page](../../delivery/using/about-seed-addresses.md).

