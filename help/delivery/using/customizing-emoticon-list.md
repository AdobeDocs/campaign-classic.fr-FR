---
title: Personnalisation de la liste émotionnelle
description: Découvrez comment personnaliser la liste émotionnelle lors de l’utilisation d’Adobe Campaign Classic.
page-status-flag: never-activated
uuid: ddcc2e3b-e251-4a7a-a22a-28701522839f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 2ea2747f-957f-41a9-a03f-20c03fa99116
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3beb62d0264cfcb03486c291ce79cc7ff582e9c7
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 2%

---


# Personnalisation de la liste émotionnelle {#customize-emoticons}

La liste émotionnelle affichée dans la fenêtre contextuelle est régie par une énumération qui vous permet d’afficher des valeurs dans une liste afin de limiter les choix de l’utilisateur pour un champ donné.
L&#39;ordre de liste émoticônes peut être personnalisé, vous pouvez également ajouter d&#39;autres émoticônes à votre liste.
Des émoticônes sont disponibles pour les courriels et les notifications Push pour plus d&#39;informations sur cette [page](../../delivery/using/defining-the-email-content.md#inserting-emoticons).

## Ajouter une nouvelle émoticône {#add-new-emoticon}

>[!CAUTION]
>
>La liste émotionnelle ne peut pas afficher plus de 81 entrées.

1. Sélectionnez votre nouvelle émoticône à ajouter à partir de cette [page](https://unicode.org/emoji/charts/full-emoji-list.html). Notez qu’il doit être compatible avec les différentes plates-formes, telles que le navigateur et le système d’exploitation.

1. Dans l’ **[!UICONTROL Explorateur]**, sélectionnez **[!UICONTROL Administration]** > **[!UICONTROL Plateforme]** > **[!UICONTROL Énumérations et cliquez sur la liste Émoticonénumération prête à l’emploi.]******

   >[!NOTE]
   >
   >Les énumérations prêtes à l&#39;emploi ne peuvent être gérées que par un administrateur de votre console Adobe Campaign Classic.

   ![](assets/emoticon_1.png)

1. Cliquez sur **[!UICONTROL Ajouter]**.

1. Renseignez les champs suivants :

   * **[!UICONTROL U+]**: Code de votre nouvelle émoticône. Vous trouverez la liste des codes des émoticônes dans cette [page](https://unicode.org/emoji/charts/full-emoji-list.html).
Pour éviter les problèmes de compatibilité, nous vous conseillons de choisir des émoticônes qui sont prises en charge sur les navigateurs et sur chaque système d&#39;exploitation.

   * **[!UICONTROL Libellé]**: Étiquette de votre nouvelle émoticône.

   ![](assets/emoticon_5.png)

1. Cliquez sur **[!UICONTROL Ok]** , puis **[!UICONTROL Enregistrer]** lorsque votre configuration est terminée.
Votre nouvelle émoticône sera automatiquement placée dans le magasin.

1. Pour l’afficher dans la fenêtre **[!UICONTROL Insérer une émoticône]** de vos diffusions, sélectionnez votre émoticône nouvellement créée en cliquant sur celle-ci par doublon.

1. Choisissez dans la liste déroulante Ordre **** d’affichage l’ordre dans lequel votre nouvelle émoticône s’affichera. Notez qu&#39;en sélectionnant un ordre d&#39;affichage déjà affecté, l&#39;émoticône existante sera automatiquement déplacée vers la boutique.

   <br>Dans cet exemple, nous avons choisi le numéro de commande d&#39;affichage 61, ce qui signifie que si une entrée avait déjà cette commande, elle sera automatiquement déplacée dans le magasin et notre nouvelle entrée prendra sa place dans la liste de énumération.

   ![](assets/emoticon_2.png)

1. Votre nouvelle émoticône a été ajoutée à la énumération **[!UICONTROL Insérer une liste]** émotionnelle prête à l&#39;emploi. Vous pouvez modifier son ordre **[!UICONTROL d’]** affichage à tout moment ou le déplacer vers la boutique si vous n’en avez plus besoin.

1. Pour que vos modifications soient prises en compte, déconnectez-vous puis reconnectez-vous d’Adobe Campaign Classic. Si votre nouvelle émoticône n’apparaît toujours pas dans la fenêtre contextuelle **[!UICONTROL Insérer une émoticône]** , vous devrez peut-être vider votre cache. Voir à ce propos cette [section](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).

1. Votre nouvelle émoticône se trouve maintenant dans vos diffusions dans la fenêtre contextuelle **[!UICONTROL Insérer une émoticône]** à la 61e position, comme configuré dans les étapes précédentes. Pour plus d&#39;informations sur l&#39;utilisation des émoticônes dans vos diffusions, consultez cette [page](../../delivery/using/defining-the-email-content.md#inserting-emoticons).

   ![](assets/emoticon_4.png)

1. Si les émoticônes suivantes apparaissent dans la fenêtre contextuelle **[!UICONTROL Insérer une émoticône]** , cela signifie qu’elles n’ont pas été correctement configurées. Vérifiez si votre code **[!UICONTROL U+]** ou votre ordre **[!UICONTROL d’]** affichage est correct dans la liste ****&#x200B;Émoticon.

   ![](assets/emoticon_6.png)
