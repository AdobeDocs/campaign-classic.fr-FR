---
title: Création d'une newsletter Experience Manager
seo-title: Création d'une newsletter Experience Manager
description: Création d'une newsletter Experience Manager
seo-description: null
page-status-flag: never-activated
uuid: 75cf4891-06a6-42d2-9b22-b4d93e0dc64a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 627ade78-96b3-4a6e-9ace-74610a3c8d1a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Création d&#39;une newsletter Experience Manager{#creating-an-experience-manager-newsletter}

Cette intégration peut être utilisée, par exemple, pour créer une newsletter dans Adobe Experience Manager, qui sera ensuite utilisée dans le cadre d&#39;une campagne email dans Adobe Campaign.

Pour obtenir un exemple plus détaillé de l&#39;utilisation de cette intégration, consultez ce [guide pas à pas](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/aem.html).

**Depuis Adobe Experience Manager :**

1. Depuis votre instance de création AEM, cliquez sur le logo **Adobe Experience** en haut à gauche de la page, puis sélectionnez **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. Sélectionner **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Master Area > Email campaigns]**.
1. Click the **[!UICONTROL Create]** button in the upper right side of the page then select **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. Select the **[!UICONTROL Adobe Campaign Email (AC 6.1)]** template and name your newsletter.
1. Une fois votre page créée, accédez au **[!UICONTROL Page information]** menu et cliquez sur **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. Dans l’ **[!UICONTROL Cloud Services]** onglet, sélectionnez **[!UICONTROL Adobe Campaign]** et votre instance Adobe Campaign **[!UICONTROL Cloud service configuration]** dans la deuxième liste déroulante.

   ![](assets/aem_uc_4.png)

1. Editez le contenu de votre email en ajoutant des composants, par exemple des champs de personnalisation depuis Adobe Campaign.
1. Lorsque votre adresse électronique est prête, accédez au **[!UICONTROL Page information]** menu et cliquez sur **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. Dans la première liste déroulante, sélectionnez **[!UICONTROL Publish to Adobe Campaign]** comme modèle de flux de travail et cliquez sur **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. Ensuite, comme l’étape précédente, lancez le **[!UICONTROL Approve for Campaign]** flux de travaux.
1. Une clause de rejet de responsabilité s’affiche en haut de votre page. Cliquez sur **[!UICONTROL Complete]** pour confirmer la révision, puis sur **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. Cliquez de nouveau **[!UICONTROL Complete]** et sélectionnez **[!UICONTROL Newsletter approval]** dans la **[!UICONTROL Next Step]** liste déroulante.

   ![](assets/aem_uc_8.png)

Votre newsletter est maintenant prête et synchronisée dans Adobe Campaign.

**Depuis Adobe Campaign :**

1. Dans l’ **[!UICONTROL Campaigns]** onglet, cliquez **[!UICONTROL Deliveries]** puis **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. Dans la **[!UICONTROL Delivery template]** liste déroulante, sélectionnez le **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** modèle.

   ![](assets/aem_uc_10.png)

1. Add a **[!UICONTROL Label]** to your delivery and click **[!UICONTROL Continue]**.
1. Cliquez sur le **[!UICONTROL Synchronize]** bouton.

   Si ce bouton n’apparaît pas dans votre interface, cliquez sur le **[!UICONTROL Properties]** bouton et sélectionnez l’ **[!UICONTROL Advanced]** onglet. Le **[!UICONTROL Content editing mode]** champ doit être défini sur **[!UICONTROL AEM]** avec votre instance AEM dans le **[!UICONTROL AEM account]** champ.

   ![](assets/aem_uc_11.png)

1. Sélectionnez la diffusion ayant été précédemment créée dans Adobe Experience Manager, puis cliquez sur **[!UICONTROL Ok]**.
1. Click the **[!UICONTROL Refresh content]** button as soon as some changes are made to your AEM delivery.

   ![](assets/aem_uc_12.png)

Votre email est maintenant prêt à être envoyé à votre audience.
