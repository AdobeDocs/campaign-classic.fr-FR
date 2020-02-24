---
title: Paramétrage du multibranding
seo-title: Paramétrage du multibranding
description: Paramétrage du multibranding
seo-description: null
page-status-flag: never-activated
uuid: 61b4235c-da03-4da8-b14b-7ffb12c8d4c8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 907d82c8-9262-4952-b8df-21144dd55824
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d5eac80743d4cc82cdf55aa9287e8bb4fcc84356

---


# Paramétrage du multibranding{#configuring-multibranding}

Cette section présente une solution pour configurer le tracking et les URL de page miroir par marque pour les messages transactionnels dans Adobe Campaign.

## Prérequis {#prerequisites}

* Tous les hôtes doivent être ajoutés au fichier de configuration de l&#39;instance (`config-<instance>.xml`).
* Un sous-domaine doit être affecté à chaque marque.
* Si le tracking web est réalisé sur les pages HTTPS, vous devez disposer d&#39;un certificat HTTPS pour chacune des marques.

## Procédure standard {#typical-process}

Pour paramétrer le multibranding, vous devez configurer les instances d&#39;exécution et l&#39;instance de pilotage. Dans les instances d&#39;exécution, procédez comme suit :

1. Créez un compte externe par marque.

   >[!NOTE]
   >
   >Creating an execution instance type external account is presented in the [Control instance](../../message-center/using/creating-a-shared-connection.md#control-instance) section.

1. Etendez le schéma nms:extAccount pour ajouter l&#39;URL de tracking :

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >L&#39;extension d&#39;un schéma existant est présentée dans la section [Extension d&#39;un schéma](../../configuration/using/extending-a-schema.md).

1. Modifiez le formulaire nms:extAccount :

   ```
   <container label="Message domain branding" type="frame">
        <static type="help"> These parameters are used to override the DNS alias and addresses used during message delivery. When not populated, the values of the 'NmsServer_MirrorPageUrl' and 'NmsEmail_DefaultErrorAddr' options are used.</static>
        <input xpath="@mirrorURL"/>
        <input xpath="@trackingURL"/>
        <input img="nms:sendemail.png" menuId="deliveryMenuBuilder" type="scriptEdit">
               xpath="errorAddress"/>
      </container>
   ```

1. Modifiez les options NmsTracking_OpenFormula et NmsTracking_ClickFormula afin d&#39;utiliser le compte externe au lieu d&#39;une option globale.

   Pour cela, remplacez :

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   par :

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!CAUTION]
   >
   >Ces modifications peuvent entraîner des conflits lors de la mise à niveau. Vous devrez peut-être fusionner manuellement ces formules avec leur nouvelle version.

Sur l&#39;instance de pilotage, vous devez lier les modèles de diffusion et les comptes externes. Pour cela, vous devez effectuer les opérations suivantes :

1. Créez un compte externe par marque avec le même nom interne qu&#39;à l&#39;étape 1.
1. Créez un modèle de diffusion par défaut par marque.
1. Dans les **[!UICONTROL Propriétés]** du modèle de diffusion, définissez le routage sur le compte externe de la marque.

