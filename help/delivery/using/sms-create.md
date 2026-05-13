---
product: campaign
title: Créer des SMS avec Campaign
description: Découvrez comment créer des SMS avec Campaign
feature: SMS
role: User
hide: true
exl-id: 94aa4628-d973-433d-b963-b078e2d6672b
TQID: https://experienceleague.adobe.com/ENt9cwc7OjXcMr5tbkg2f3BxpPBNtVytVTw70NQZPyI
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 473
ht-degree: 75%

---

# Créer une diffusion SMS {#creating-a-sms-delivery}

## Choisir le canal de diffusion {#selecting-the-delivery-channel}

Pour créer une diffusion SMS, procédez comme suit :

>[!NOTE]
>
>Les concepts généraux de création d’une diffusion sont présentés dans la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=fr){target="_blank"}.

1. Créez une diffusion, par exemple depuis le tableau de bord des diffusions.
1. Sélectionnez le modèle de diffusion **Envoyé vers mobiles (SMPP)** que vous avez créé précédemment. Pour plus d&#39;informations, consultez la section [Modifier le modèle de diffusion](sms-set-up.md#changing-the-delivery-template).

   ![](assets/s_user_mobile_wizard.png)

1. Identifiez votre diffusion avec un libellé, un code et une description. Pour en savoir plus, consultez cette section dans la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=fr#create-the-delivery){target="_blank"}.
1. Cliquez sur **[!UICONTROL Continuer]** pour valider ces informations et afficher la fenêtre de configuration du message.

## Définition du contenu du SMS {#defining-the-sms-content}

Pour définir le contenu du SMS, procédez comme suit :

1. Saisissez le contenu du message dans la section **[!UICONTROL Contenu texte]** de l’assistant. Les boutons de la barre d’outils permettent d’importer, d’enregistrer ou de rechercher dans un contenu. Le dernier bouton permet d&#39;insérer des champs de personnalisation.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   L’utilisation des champs de personnalisation est présentée dans la section [À propos de la personnalisation](about-personalization.md).

1. Cliquez sur l&#39;onglet **[!UICONTROL Aperçu]** en bas de page afin de visualiser le rendu du message, avec sa personnalisation. Pour lancer la visualisation, vous devez choisir un destinataire à partir du bouton **[!UICONTROL Tester la personnalisation]** situé dans la barre d&#39;outils. Sélectionnez un individu parmi la ou les cibles définies ou choisissez une autre personne.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   Vous pouvez approuver le SMS. Vous pouvez également afficher le contenu du SMS sur l’écran du téléphone mobile affiché à droite de l’éditeur de contenu. Cliquez sur l’écran et utilisez la souris pour faire défiler le contenu.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. Cliquez sur le lien **[!UICONTROL Données chargées]** pour visualiser les informations concernant le destinataire.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >Les SMS sont limités à une longueur de 160 caractères si la page de code Latin-1 (ISO-8859-1) est utilisée. Si le message est écrit en Unicode, il ne doit pas dépasser 70 caractères. Certains caractères spéciaux peuvent affecter la longueur du message. Pour plus d’informations sur la longueur des messages, voir la section [Translittération des caractères SMS](#about-character-transliteration).
   >
   >En présence de champs de personnalisation ou de contenu conditionnel, la taille du message varie d&#39;un destinataire à l&#39;autre. La longueur du message doit être évaluée une fois la personnalisation effectuée.
   >
   >Lorsque vous lancez l&#39;analyse, la longueur des messages est contrôlée et un message d&#39;avertissement est affiché en cas de dépassement.

1. Si vous utilisez le connecteur NetSize ou un connecteur SMPP, il est possible de personnaliser le nom de l&#39;émetteur de la diffusion. Pour plus d&#39;informations, consultez la section [Paramètres avancés](#advanced-parameters).

## Choisir la population cible {#selecting-the-target-population}

Le processus détaillé de sélection de la population cible d’une diffusion est présenté dans [cette section](steps-defining-the-target-population.md).

Pour plus d’informations sur l’utilisation des champs de personnalisation, consultez [cette section](about-personalization.md).

Pour plus d’informations sur l’inclusion d’une liste de contrôle, consultez [cette page](about-seed-addresses.md).
