---
product: campaign
title: Inbox rendering dans Campaign
description: Découvrez comment capturer les rendus des e-mails et y accéder dans un rapport dédié
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Inbox Rendering, Monitoring, Email Rendering
role: User
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
TQID: 'https://experienceleague.adobe.com/d0fFXi4Ma-PwY8vsSBOmvbhRD4631kUoagNXlf4Rmek'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: 2317b1ea-6db4-58c7-851f-717a69c0f5c0
    internal-label: Inbox Rendering
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
  - id: aef0b685-fc31-54d4-b831-a87fdb9d69de
    internal-label: Email Rendering
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: cce1f22c34cbd13d063850a7ca636a3b0dfc62f6
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 82%
---
# Rendu de la boîte de réception{#inbox-rendering}

Adobe Campaign tire parti de la solution web de test d&#39;email [Litmus](https://litmus.com/email-testing) pour capturer les rendus d&#39;email et les rendre disponibles dans un rapport dédié.

Dans le cadre de la transition de Campaign v7 vers v8, la documentation de Campaign Classic a été rationalisé et réorganisé. Les fonctionnalités communes sont désormais disponibles exclusivement dans le jeu de documentation de Campaign v8. Pour en savoir plus sur l&#39;inbox rendering, consultez la documentation de [Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/deliverability-management/inbox-rendering){target=_blank}.

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/deliverability-management/inbox-rendering){target=_blank}

## Activation de l&#39;Inbox rendering {#activating-inbox-rendering}

[!BADGE On-premise et hybride]{type=Caution url="https://experienceleague.adobe.com/fr/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"}

Pour les clients hébergés et hybrides, l&#39;Inbox rendering est configuré pour votre instance par l&#39;assistance technique et les consultants d&#39;Adobe. Pour plus d&#39;informations, contactez votre chargé de compte Adobe.

Pour les installations sur site, suivez la procédure ci-dessous pour configurer l&#39;Inbox rendering.

1. Installez le package **[!UICONTROL Inbox rendering (IR)]** via le menu **[!UICONTROL Outils]** >**[!UICONTROL Avancé]** > **[!UICONTROL Import de package]**. Pour plus d&#39;informations, voir la section [Installer des packages standard Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).
1. Configurez un compte externe de type HTTP via le nœud **[!UICONTROL Administration]** > **[!UICONTROL Plateforme]** > **[!UICONTROL Comptes externes]**. Pour plus d&#39;informations, consultez la section [Créer un compte externe](../../installation/using/external-accounts.md#creating-an-external-account).
1. Définissez les paramètres du compte externe comme suit :
   * **[!UICONTROL Libellé]** : informations relatives au serveur de délivrabilité
   * **[!UICONTROL Nom interne]** : deliverabilityInstance
   * **[!UICONTROL Type]** : HTTP
   * **[!UICONTROL Serveur]** : https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Chiffrement]** : Aucun
   * Cochez l&#39;option **[!UICONTROL Activé]**.

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. Accédez au nœud **[!UICONTROL Administration]** > **[!UICONTROL Plateforme]** > **[!UICONTROL Options]**. Recherchez l&#39;option **[!UICONTROL DmRendering_cuid]** et contactez l&#39;assistance technique pour obtenir l&#39;identifiant des rapports de diffusion qui doit être copié dans le champ **[!UICONTROL Valeur (texte)]**.
1. Modifiez le fichier **serverConf.xml** pour autoriser un appel au serveur Litmus. Ajoutez la ligne suivante à la section `<urlPermission>` :

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. Chargez de nouveau la configuration à l&#39;aide de la commande suivante :

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>Vous devrez peut-être vous déconnecter de la console et vous reconnecter pour pouvoir utiliser l&#39;Inbox rendering.
