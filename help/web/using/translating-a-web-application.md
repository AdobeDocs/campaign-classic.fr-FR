---
title: Traduire une application Web
seo-title: Traduire une application Web
description: Traduire une application Web
seo-description: null
page-status-flag: never-activated
uuid: 7b24a872-d3d1-4473-a6f9-96ba2a0eee8b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 328e5b2f-8596-4eda-8ac5-57cb29bfb691
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Traduire une application Web{#translating-a-web-application}

Vous pouvez traduire des pages d&#39;applications Web créées avec l&#39;éditeur de contenu numérique Adobe Campaign (DCE).

If you select at least one additional language via the **[!UICONTROL Localization]** tab in the **[!UICONTROL Properties]** of a Web application, a new option becomes available when adding an HTML content block in a page edited with DCE.

Cette option vous permet d&#39;indiquer si le contenu du bloc doit être traduit ou non.

Les chaînes à traduire sont collectées de la même manière que les autres chaînes de l&#39;application Web, via l&#39; **[!UICONTROL Translations]** onglet de l&#39;application. Voir à ce propos [cette page](../../web/using/translating-a-web-form.md).

Pour marquer les chaînes à traduire :

1. Ouvrez une page de contenu éditée via le DCE dans une application Web.

   ![](assets/dce_translation_3.png)

1. Sélectionnez un bloc HTML.
1. Dans le bloc de paramètres sur la droite, l’ **[!UICONTROL Localization]** option vous permet d’indiquer le contenu du bloc sélectionné. Par défaut, seul le titre de la page doit être traduit.

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >Les chaînes doivent contenir au maximum 1023 caractères.

   Il existe trois cas spécifiques :

   * Lorsqu&#39;un bloc sélectionné contient plusieurs chaînes/blocs, ce dernier est ajouté sous forme d&#39;une seule chaîne à traduire. La chaîne contient alors le code HTML des éléments que le bloc contient.
   * Lorsque vous souhaitez traduire un bloc contenant plusieurs chaînes dont au moins l&#39;une d&#39;entre-elles est déjà marquée comme à traduire, un message vous en avertit. Vous pouvez alors choisir de retirer la chaîne isolée et d&#39;ajouter le bloc entier.

      ![](assets/dce_translation_4.png)

   * Lorsque vous souhaitez ne pas traduire une chaîne contenue dans un bloc déjà marqué comme à traduire, vous ne pouvez pas modifier l&#39;option de traduction de la chaîne. Vous pouvez toutefois sélectionner le bloc à traduire dont la chaîne fait partie afin de modifier votre choix concernant le bloc entier.

      ![](assets/dce_translation_2.png)

1. Once you have finished flagging the strings, go back to the Web application and select the **[!UICONTROL Translations]** tab.
1.  Sélectionnez **[!UICONTROL Collect the strings to translate]**. Les chaînes marquées dans DCE sont ajoutées aux chaînes de l’application Web.

   >[!NOTE]
   >
   >Une fois les chaînes collectées, elles ne sont pas retirées si vous les marquez à nouveau comme n&#39;étant pas à traduire dans le DCE. Cela permet qu&#39;elles soient conservées dans la mémoire de traduction.

1. Traduisez et validez les chaînes.

   You can then preview the translations by selecting the desired language from the **[!UICONTROL Preview]** tab in the Web application.

