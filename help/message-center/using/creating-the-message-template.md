---
solution: Campaign Classic
product: campaign
title: Concevoir des modèles de messages transactionnels
description: Découvrez comment créer et concevoir un modèle de message transactionnel dans Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: a52bc140-072e-4f81-b6da-f1b38662bce5
source-git-commit: a9054fb8e10bef37675922b2f81c7615cd04c1bb
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 74%

---

# Concevoir des modèles de messages transactionnels {#creating-the-message-template}

Pour que chaque événement puisse être transformé en message personnalisé, vous devez créer un modèle de message correspondant à chaque type d’événement.

>[!IMPORTANT]
>
>Les types d’événement doivent être créés au préalable. Voir à ce sujet la section [Création des types d&#39;événement](../../message-center/using/creating-event-types.md).

Les modèles de messages transactionnels contiennent les informations nécessaires pour personnaliser le message transactionnel. Vous pouvez également utiliser des modèles pour tester la prévisualisation des messages et envoyer des BAT à l’aide d’adresses de contrôle avant de les diffuser à la cible finale. Voir à ce propos la section [Test des modèles de messages transactionnels](../../message-center/using/testing-message-templates.md).

## Création du modèle de message {#creating-message-template}

1. Positionnez-vous au niveau du dossier **[!UICONTROL Message Center > Modèles de messages transactionnels]** dans l&#39;arborescence Adobe Campaign.

1. Dans la liste des modèles de messages transactionnels, cliquez avec le bouton droit de la souris et sélectionnez **[!UICONTROL Nouveau]** dans le menu contextuel ou cliquez sur le bouton **[!UICONTROL Nouveau]** situé au-dessus de la liste des modèles de messages transactionnels.

   ![](assets/messagecenter_create_model_001.png)

1. Dans la fenêtre de diffusion, sélectionnez le modèle de diffusion propre au canal que vous souhaitez utiliser.

   ![](assets/messagecenter_create_model_002.png)

1. Modifiez le libellé si nécessaire.

1. Sélectionnez le type d&#39;événement correspondant au message que vous souhaitez envoyer.

   ![](assets/messagecenter_create_model_003.png)

   Les types d&#39;événements doivent être créés au préalable dans la console. Voir à ce sujet la section [Création des types d&#39;événement](../../message-center/using/creating-event-types.md).

   >[!IMPORTANT]
   >
   >Un type d’événement ne peut pas être lié à plusieurs modèles.

1. Saisissez une nature et une description, puis cliquez sur **[!UICONTROL Continuer]** pour créer le corps du message (voir [Création du contenu du message](#creating-message-content)).

   ![](assets/messagecenter_create_model_004.png)

## Création du contenu du message {#creating-message-content}

La définition du contenu du message transactionnel fonctionne selon les mêmes principes que pour une diffusion classique dans Adobe Campaign. Par exemple, pour une diffusion email, vous pouvez créer un contenu au format HTML ou texte, ajouter des pièces jointes ou personnaliser l&#39;objet de la diffusion. Reportez-vous au chapitre [Diffuser par email](../../delivery/using/about-email-channel.md) pour plus d&#39;informations.

>[!IMPORTANT]
>
>Les images incluses dans le message doivent être accessibles publiquement. Adobe Campaign ne fournit pas de mécanisme de mise en ligne des images pour les messages transactionnels.\
>Contrairement à JSSP ou webApp, `<%=` n’a pas de séquence d’échappement par défaut.
>
>Dans ce cas, vous devez appliquer une séquence d’échappement correcte à toutes les données provenant de l’événement. Cette séquence d’échappement dépend de l’utilisation de ce champ. Par exemple, dans une URL, utilisez encodeURIComponent. Pour un affichage dans le code HTML, vous pouvez utiliser escapeXMLString.

Lorsque vous avez défini le contenu de votre message, vous pouvez intégrer les informations de l&#39;événement dans le corps du message et ainsi le personnaliser. Les informations de l&#39;événement sont insérées dans le corps du texte à l&#39;aide des balises de personnalisation.

![](assets/messagecenter_create_content_001.png)

* Tous les champs de personnalisation proviennent de la payload.
* Il est possible de référencer un ou plusieurs blocs de personnalisation dans un message transactionnel. Le contenu du bloc est ajouté au contenu de la diffusion au cours de la publication dans l’instance d’exécution.

Pour insérer des balises de personnalisation dans le corps d&#39;un message email, procédez comme suit :

1. Dans le modèle de message, cliquez sur l&#39;onglet correspondant au format de l&#39;email (HTML ou texte).

1. Rédigez le corps du message.

1. Dans le corps du texte, insérez la balise à l’aide du menu **[!UICONTROL Evénements temps réel > XML de l’événement]** .

   ![](assets/messagecenter_create_custo_002.png)

1. Complétez la balise selon la syntaxe suivante : .**nom de l&#39;élément**.@**nom de l&#39;attribut** comme illustré ci-dessous.

   ![](assets/messagecenter_create_custo_003.png)

1. Enregistrez votre contenu.

Votre message est maintenant prêt à être [testé](../../message-center/using/testing-message-templates.md).
