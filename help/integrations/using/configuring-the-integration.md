---
title: Configuration de l'intégration
seo-title: Configuration de l'intégration
description: Configuration de l'intégration
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Configuration de l&#39;intégration{#configuring-the-integration}

## Configuration dans Adobe Campaign {#configuring-in-adobe-campaign}

Afin de pouvoir utiliser conjointement ces deux solutions, vous devez les paramétrer pour les connecter l&#39;une à l&#39;autre.

Suivez les étapes ci-dessous pour commencer la configuration dans Adobe Campaign :

1. [Installation du package d&#39;intégration AEM dans Adobe Campaign](#install-the-aem-integration-package-in-adobe-campaign)
1. [Configuration du compte externe](#configure-the-external-account)
1. [Configuration du filtrage des ressources AEM](#configure-aem-resources-filtering)

Pour les configurations avancées telles que la gestion des blocs et des champs de personnalisation, consultez la [documentation](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html) d&#39;Adobe Experience Manager.

### Installation du package d&#39;intégration AEM dans Adobe Campaign {#install-the-aem-integration-package-in-adobe-campaign}

You first need to install the **[!UICONTROL AEM integration]** package.

1. From your Adobe Campaign instance, select **[!UICONTROL Tools]** from the upper toolbar.
1. Sélectionner **[!UICONTROL Tools > Advanced > Import package...]**.

   ![](assets/aem_config_1.png)

1. Sélectionner **[!UICONTROL Install a standard package]**.
1. Cochez **[!UICONTROL AEM integration]** puis cliquez sur le **[!UICONTROL Next]** bouton.

   ![](assets/aem_config_2.png)

1. Dans la fenêtre suivante, cliquez sur le **[!UICONTROL Start]** bouton pour lancer l&#39;installation de votre pack. Fermez la fenêtre une fois l’installation terminée.

### Configuration de la zone de sécurité pour l&#39;opérateur AEM {#configure-the-security-zone-for-aem-operator}

Le **[!UICONTROL AEM integration]** package définit l’ **[!UICONTROL aemserver]** opérateur dans Campaign. Cet opérateur sera utilisé pour connecter le serveur Adobe Experience Manager à Adobe Campaign.

Vous devez configurer une zone de sécurité pour que cet opérateur puisse se connecter à Adobe Campaign par le biais d&#39;Adobe Experience Manager.

>[!CAUTION]
>
>Il est vivement recommandé de créer une zone de sécurité dédiée à AEM afin d&#39;éviter tout problème de sécurité. Voir à ce propos le [guide](../../installation/using/configuring-campaign-server.md#defining-security-zones) d&#39;installation.

Si votre instance de Campaign est hébergée par Adobe, contactez l&#39;équipe d&#39;assistance Adobe. Si vous utilisez Campaign on-premise, procédez comme suit :

1. Ouvrez le fichier de configuration **serverConf.xml**.
1. Accédez à l&#39;attribut **allowUserPassword** de la zone de sécurité sélectionnée et définissez-le sur **true**.

   AEM peut ainsi se connecter à Adobe Campaign par le biais d&#39;un identifiant/mot de passe.

### Configuration du compte externe {#configure-the-external-account}

Le **[!UICONTROL AEM integration]** pack a créé le compte externe pour Adobe Experience Cloud. Vous devez maintenant le configurer pour vous connecter à votre instance Adobe Experience Manager.

Pour configurer le compte externe AEM, procédez comme suit :

1. Cliquez sur le **[!UICONTROL Explorer]** bouton.

   ![](assets/aem_config_3.png)

1. Sélectionner **[!UICONTROL Administration > Platform > External accounts]**.
1. Dans la **[!UICONTROL External account]** liste, sélectionnez **[!UICONTROL AEM instance]**.
1. Renseignez les paramètres de votre instance de création AEM :

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**
   >[!NOTE]
   >
   >Make sure that your **[!UICONTROL Server]** address does not end with a a trailing slash.

   ![](assets/aem_config_4.png)

1. Cochez la **[!UICONTROL Enabled]** case.
1. Cliquez sur le **[!UICONTROL Save]** bouton.

### Configuration du filtrage des ressources AEM {#configure-aem-resources-filtering}

L’option **AEMResourceTypeFilter **permet de filtrer les types de ressources Experience Manager pouvant être utilisés dans Adobe Campaign. Cela permet à Adobe Campaign de récupérer le contenu d’Experience Manager spécifiquement conçu pour être utilisé dans Adobe Campaign uniquement.

Pour vérifier si l&#39;option **[!UICONTROL AEMResourceTypeFilter]** est configurée :

1. Cliquez sur le **[!UICONTROL Explorer]** bouton.
1. Sélectionner **[!UICONTROL Administration > Platform > Options]**.
1. Dans la **[!UICONTROL Options]** liste, sélectionnez **[!UICONTROL AEMResourceTypeFilter]**.
1. In the **[!UICONTROL Value (text)]** field, the path should be as follows:

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   Ou, dans certains cas :

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## Configuration dans Adobe Experience Manager {#configuring-in-adobe-experience-manager}

Suivez les étapes ci-dessous pour commencer la configuration dans Adobe Experience Manager :

1. Configurez la **réplication** entre les instances Adobe Experience Manager de création et de publication.

   Pour découvrir comment configurer la réplication, consultez la [documentation](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/replication.html) d&#39;Adobe Experience Manager.

1. Uniquement pour AEM versions 5.6.1 et 6.0 : installez le package de fonctionnalités (**FeaturePack**) dédié à l&#39;intégration sur votre instance de création, puis répliquez l&#39;installation sur votre instance de publication.

   Pour découvrir comment installer le package de fonctionnalités (FeaturePack), consultez la [documentation](https://helpx.adobe.com/experience-manager/aem-previous-versions.html) d&#39;Adobe Experience Manager.

1. Connectez Adobe Experience Manager à Adobe Campaign en configurant un **Cloud Service dédié**.

   Pour découvrir comment connecter les deux solutions via les Cloud Services, consultez la [documentation](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) d&#39;Adobe Experience Manager .

1. Configurez le **service d&#39;externalisation**.

   Pour découvrir comment le configurer, consultez la [documentation](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/externalizer.html) d&#39;Adobe Experience Manager.

