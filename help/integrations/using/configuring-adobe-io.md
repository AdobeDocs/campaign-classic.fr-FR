---
title: Configuration des E/S d'Adobe pour les déclencheurs Adobe Experience Cloud
description: Découvrez comment configurer les E/S d'Adobe pour les déclencheurs Adobe Experience Cloud
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
source-git-commit: 160af30e13bb6a81672477f4f801dbd5cc3c767c
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 34%

---


# Configuring Adobe I/O for Adobe Experience Cloud Triggers {#configuring-adobe-io}

>[!CAUTION]
>
>Si vous utilisez une ancienne version de l’intégration Triggers par le biais de l’authentification Auth, **vous devez passer à l’E/S d’Adobe comme décrit ci-dessous**. Le mode d’authentification Auth hérité sera abandonné le 30 avril 2021. [En savoir plus](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)

## Prérequis {#adobe-io-prerequisites}

Cette intégration s’applique uniquement à partir de la version **de** Campaign Classic 20.3.

Avant de commencer cette mise en oeuvre, vérifiez que vous disposez des éléments suivants :

* un IMSOrgID valide : l’identifiant d’organisation IMS (Identity Management System) est l’identifiant unique au sein du Adobe Experience Cloud, utilisé par exemple pour le service d’identification des visiteurs et l’authentification unique (SSO) IMS,
* a Accès des développeurs à l&#39;organisation IMS.

>[!NOTE]
>
>If you need to request the System Administrator privileges of the IMS Org, follow the procedure detailed [in this page](https://helpx.adobe.com/fr/enterprise/admin-guide.html/fr/enterprise/using/manage-developers.ug.html) to provide this access for the all Product Profiles.


## Étape 1 : Créer/mettre à jour un projet d&#39;E/S d&#39;Adobe {#creating-adobe-io-project}

1. Accédez aux E/S d&#39;Adobe et connectez-vous avec le droit Administrateur système pour IMSorg.

   >[!NOTE]
   >
   > Assurez-vous d&#39;être connecté au portail de l&#39;organisation IMS approprié.

1. Extrayez l&#39;identifiant du client d&#39;intégration existant du fichier de configuration de l&#39;instance ims/authIMSTAClientId. Un attribut non existant ou vide indique que l’ID client n’est pas configuré.

   >[!NOTE]
   >
   >If your Client ID is empty, you can directly **[!UICONTROL Create a New project]** in Adobe I/O.

1. Identifiez le projet existant à l’aide de l’ID client extrait. Recherchez des projets existants avec le même identifiant du client que celui extrait à l&#39;étape précédente.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Sélectionnez **[!UICONTROL + Ajouter au projet]** et choisissez **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. In the **[!UICONTROL Add an API]** window, select **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Sélectionnez **[!UICONTROL Compte de service (JWT)]** comme type d&#39;authentification.

   ![](assets/do-not-localize/adobe_io_3.png)

1. If your Client ID was empty, select **[!UICONTROL Generate a key pair]** to create a Public and Private keypair.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Téléchargez votre clé publique et cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. Sélectionnez le profil de produit appelé **Analytics-&lt; Nom de l&#39;entreprise >** et cliquez sur **[!UICONTROL Enregistrer l&#39;API configurée]**.

   ![](assets/do-not-localize/adobe_io_6.png)

1. Dans votre projet, sélectionnez **[!UICONTROL Compte de service (JWT)]** et copiez les informations suivantes :
   * **[!UICONTROL Identifiant du client]**
   * **[!UICONTROL Secret du client]**
   * **[!UICONTROL Identifiant du du compte technique]**
   * **[!UICONTROL Identifiant de l&#39;organisation]**

   ![](assets/do-not-localize/adobe_io_7.png)

## Étape 2 : ajouter les informations d&#39;identification du projet dans Adobe Campaign {#add-credentials-campaign}

To add the project credentials in Adobe Campaign, run the following command as &#39;neolane&#39; user on all the containers of the Adobe Campaign instance to insert the **[!UICONTROL Technical Account]** credentials in the instance configuration file.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Vous devez coder la clé privée au format base64 UTF-8. N&#39;oubliez pas de supprimer la nouvelle ligne de la clé avant de la coder, à l&#39;exception de la clé privée. La clé privée doit être la même que celle utilisée pour créer l&#39;intégration.

## Étape 3 : mettre à jour la balise en pipeline {#update-pipelined-tag}

To update [!DNL pipelined] tag, you need to update the authentication type to Adobe I/O project in the configuration file **config-&lt; instance-name >.xml** as follows:

```
<pipelined ... authType="imsJwtToken"  ... />
```
