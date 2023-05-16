---
product: campaign
title: Création d'une newsletter Experience Manager
description: Création d'une newsletter Experience Manager
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
exl-id: 9fa3ce08-3007-4c65-9841-bad339428b7c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 100%

---

# Création d&#39;une newsletter Experience Manager{#creating-an-experience-manager-newsletter}



Cette intégration peut être utilisée, par exemple, pour créer une newsletter dans Adobe Experience Manager, qui sera ensuite utilisée dans le cadre d’une campagne e-mail dans Adobe Campaign.

**Depuis Adobe Experience Manager :**

1. Depuis votre instance de création AEM, cliquez sur le logo **Adobe Experience** en haut à gauche de la page, puis sélectionnez **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. Sélectionnez **[!UICONTROL Campagnes > Nom de votre marque (We.Retail, dans le cas présent) > Zone principale > Campagnes par e-mail]**.
1. Cliquez sur le bouton **[!UICONTROL Créer]** en haut à droite de la page, puis sélectionnez **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. Sélectionnez le modèle **[!UICONTROL Adobe Campaign Email (AC 6.1)]** et attribuez un nom à votre newsletter.
1. Une fois votre page créée, accédez au menu **[!UICONTROL Informations sur la page]**, puis cliquez sur **[!UICONTROL Ouvrir les propriétés]**.

   ![](assets/aem_uc_3.png)

1. Dans l&#39;onglet **[!UICONTROL Services Cloud]**, sélectionnez **[!UICONTROL Adobe Campaign]** en tant que **[!UICONTROL Configurations du service Cloud]** et votre instance Adobe Campaign dans la seconde liste déroulante.

   ![](assets/aem_uc_4.png)

1. Editez le contenu de votre email en ajoutant des composants, par exemple des champs de personnalisation depuis Adobe Campaign.
1. Lorsque votre email est prêt, accédez au menu **[!UICONTROL Informations sur la page]**, puis cliquez sur **[!UICONTROL Démarrer le flux de travail]**.

   ![](assets/aem_uc_5.png)

1. Dans la première liste déroulante, sélectionnez **[!UICONTROL Publier dans Adobe Campaign]** en tant que modèle de workflow, puis cliquez sur **[!UICONTROL Démarrer le flux de travail]**.

   ![](assets/aem_uc_6.png)

1. Comme à l&#39;étape précédente, lancez ensuite le workflow **[!UICONTROL Approuver pour Adobe Campaign]**.
1. Une clause d&#39;exclusion de responsabilité apparaît en haut de la page. Cliquez sur **[!UICONTROL Terminé]** pour confirmer la consultation, puis cliquez sur **[!UICONTROL OK]**.

   ![](assets/aem_uc_7.png)

1. Cliquez à nouveau sur **[!UICONTROL Terminé]**, puis sélectionnez **[!UICONTROL Approbation de la newsletter]** dans la liste déroulante **[!UICONTROL Étape suivante]**.

   ![](assets/aem_uc_8.png)

Votre newsletter est maintenant prête et synchronisée dans Adobe Campaign.

**Depuis Adobe Campaign :**

1. Dans l&#39;onglet **[!UICONTROL Campagnes]**, cliquez sur **[!UICONTROL Diffusions]** et sur **[!UICONTROL Créer]**.

   ![](assets/aem_uc_9.png)

1. Dans la liste déroulante **[!UICONTROL Modèle de diffusion]**, sélectionnez le modèle **[!UICONTROL Diffusion par email avec contenu AEM (mailAEMContent)]**.

   ![](assets/aem_uc_10.png)

1. Ajoutez un **[!UICONTROL Libellé]** à votre diffusion, puis cliquez sur **[!UICONTROL Continuer]**.
1. Cliquez sur le bouton **[!UICONTROL Synchroniser]**.

   Si ce bouton ne s&#39;affiche pas dans votre interface, cliquez sur le bouton **[!UICONTROL Propriétés]** et sélectionnez l&#39;onglet **[!UICONTROL Avancé]**. Le champ **[!UICONTROL Mode d&#39;édition du contenu]** doit être défini sur **[!UICONTROL AEM]** avec votre instance AEM dans le champ **[!UICONTROL Compte AEM]**.

   ![](assets/aem_uc_11.png)

1. Sélectionnez la diffusion ayant été précédemment créée dans Adobe Experience Manager, puis cliquez sur **[!UICONTROL OK]**.
1. Cliquez sur le bouton **[!UICONTROL Rafraîchir le contenu]** dès que des modifications sont apportées à votre diffusion AEM.

   ![](assets/aem_uc_12.png)

Votre email est maintenant prêt à être envoyé à votre audience.
