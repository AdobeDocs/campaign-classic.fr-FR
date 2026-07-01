---
product: campaign
title: Traduire une application web
description: Traduire une application web
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Web Apps
exl-id: 82c5c610-8161-4686-aa79-1b690e763765
TQID: https://experienceleague.adobe.com/AVV-TybR3s6d68N7DS0TSKBN46-etor1Ezhlaah-MJs
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a4671286-a59f-47e3-b97b-90627a1977d5
subfeature_v2: id: f391046b-0cf3-4e76-bd3b-97fe06654506id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281id: d7be2b01-dc9c-40f7-aace-a151707504ed
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 384
ht-degree: 100%

---

# Traduire une application web{#translating-a-web-application}



Vous pouvez traduire les pages d’applications Web créées avec l’éditeur Digital Content Editor (DCE) d’Adobe Campaign.

Lorsque vous sélectionnez une ou plusieurs langues supplémentaires via l&#39;onglet **[!UICONTROL Localisation]** des **[!UICONTROL Propriétés]** d&#39;une application Web, une option supplémentaire apparaît lorsque vous vous placez au niveau d&#39;un bloc de contenu HTML d&#39;une page éditée avec le DCE.

Cette option vous permet d&#39;indiquer si le contenu du bloc doit être traduit ou non.

Les chaînes marquées sont collectées pour être traduites, de la même manière que les autres chaînes de l&#39;application web, via l&#39;onglet **[!UICONTROL Traductions]** de l&#39;application. Pour plus d’informations, consultez [cette page](translating-a-web-form.md).

Pour marquer les chaînes à traduire :

1. Ouvrez une page de contenu éditée via le DCE dans une application Web.

   ![](assets/dce_translation_3.png)

1. Sélectionnez un bloc HTML.
1. Dans le bloc de paramètres de droite, l’option **[!UICONTROL Localisation]** vous permet de marquer le contenu du bloc sélectionné.Par défaut, seul le titre de la page est à traduire.

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >Les chaînes doivent contenir au maximum 1023 caractères.

   Trois cas spécifiques sont à noter :

   * Lorsque le bloc sélectionné contient plusieurs chaînes/blocs, il est marqué comme une seule chaîne à traduire.La chaîne contient alors le code HTML des éléments que ce bloc contient.
   * Lorsque vous souhaitez marquer un bloc contenant plusieurs chaînes dont au moins l’une d’entre-elles est déjà marquée, un avertissement s’affiche.Vous pouvez alors choisir de retirer la chaîne isolée et d’ajouter le bloc entier.

     ![](assets/dce_translation_4.png)

   * Lorsque vous souhaitez supprimer l’indicateur d’une chaîne contenue dans un bloc déjà marqué comme à traduire, vous ne pouvez pas modifier directement l’option de traduction de la chaîne.Vous pouvez toutefois accéder au bloc contenant la chaîne afin de la modifier.

     ![](assets/dce_translation_2.png)

1. Une fois les chaînes marquées, revenez à l&#39;application Web et sélectionnez l&#39;onglet **[!UICONTROL Traductions]**.
1. Sélectionnez **[!UICONTROL Collecter les chaînes à traduire]**.Les chaînes marquées dans le DCE viennent s’ajouter à celles de l’application web.

   >[!NOTE]
   >
   >Une fois les chaînes collectées, elles ne seront pas retirées de la liste si vous les marquez à nouveau comme n’étant pas à traduire dans le DCE.Cela permet de les conserver dans la mémoire de traduction.

1. Traduisez et validez les chaînes.

   Vous pouvez ensuite prévisualiser les traductions en sélectionnant la langue de votre choix via l&#39;onglet **[!UICONTROL Prévisualisation]** de l&#39;application Web.
