---
title: Création du contenu du message
seo-title: Création du contenu du message
description: Création du contenu du message
seo-description: null
page-status-flag: never-activated
uuid: 4ee013fc-fba2-4120-b796-dd4008000ea9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 1f420652-c9af-4a49-8d5c-a640e960aced
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2c0d4054fbc15a88ea0370269b62c7d647aea033

---


# Création du contenu du message{#creating-message-content}

La définition du contenu du message transactionnel fonctionne selon les mêmes principes que pour une diffusion classique dans Adobe Campaign. Par exemple, pour une diffusion email, vous pouvez créer un contenu au format HTML ou texte, ajouter des pièces jointes ou personnaliser l&#39;objet de la diffusion. Reportez-vous au chapitre [Diffuser par email](../../delivery/using/about-email-channel.md) pour plus d&#39;informations.

>[!CAUTION]
>
>Les images incluses dans le message doivent être accessibles publiquement. Adobe Campaign ne fournit pas de mécanisme de mise en ligne des images pour les messages transactionnels.\
>Contrairement à JSSP ou webApp, `<%=` il n’y a pas d’échappement par défaut.
>
>Dans ce cas, vous devez enregistrer toutes les données provenant de l’événement correctement. Cette séquence d’échappement dépend de l’utilisation de ce champ. Par exemple, dans une URL, utilisez encodeURIComponent. Pour être affiché dans le code HTML, vous pouvez utiliser escapeXMLString.

Lorsque vous avez défini le contenu de votre message, vous pouvez intégrer les informations de l&#39;événement dans le corps du message et ainsi le personnaliser. Les informations de l&#39;événement sont insérées dans le corps du texte à l&#39;aide des balises de personnalisation.

![](assets/messagecenter_create_content_001.png)

* Tous les champs de personnalisation proviennent de la charge utile.
* Il est possible de référencer un ou plusieurs blocs de personnalisation dans un message transactionnel. Le contenu du bloc sera ajouté au contenu de diffusion pendant la publication dans l’instance d’exécution.

Pour insérer des balises de personnalisation dans le corps d&#39;un message email, procédez comme suit :

1. Dans le modèle de message, cliquez sur l&#39;onglet correspondant au format de l&#39;email (HTML ou texte).
1. Rédigez le corps du message.
1. Dans le corps du texte, insérez la balise à l&#39;aide des menus **[!UICONTROL Evénement temps réel>XML de l&#39;événement]**.

   ![](assets/messagecenter_create_custo_002.png)

1. Complétez la balise selon la syntaxe suivante : .**nom de l&#39;élément**.@**nom de l&#39;attribut** comme illustré ci-dessous.

   ![](assets/messagecenter_create_custo_003.png)

