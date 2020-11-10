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
ht-degree: 1%

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
>Si vous devez demander les privilèges d&#39;administrateur système de l&#39;organisation IMS, suivez la procédure détaillée [dans cette page](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html) pour fournir cet accès à tous les Profils de produits.


## Étape 1 : Créer/mettre à jour un projet d&#39;E/S d&#39;Adobe {#creating-adobe-io-project}

1. Accédez aux E/S d&#39;Adobe et connectez-vous avec le droit Administrateur système pour IMSorg.

   >[!NOTE]
   >
   > Assurez-vous d’être connecté au portail IMSorg approprié.

1. Extrayez l’ID client d’intégration existant du fichier de configuration de l’instance ims/authIMSTAClientId. Un attribut non existant ou vide indique que l’ID client n’est pas configuré.

   >[!NOTE]
   >
   >Si votre ID client est vide, vous pouvez directement **[!UICONTROL créer un nouveau projet]** dans les E/S d&#39;Adobe.

1. Identifiez le projet existant à l’aide de l’ID client extrait. Recherchez des projets existants avec le même ID client que celui extrait à l’étape précédente.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Sélectionnez **[!UICONTROL + Ajouter au projet]** et choisissez **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. Dans la fenêtre **[!UICONTROL Ajouter une API]** , sélectionnez **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Sélectionnez **[!UICONTROL Service Account (JWT)]** comme type d’authentification.

   ![](assets/do-not-localize/adobe_io_3.png)

1. Si votre ID client était vide, sélectionnez **[!UICONTROL Générer une paire]** de clés pour créer une paire de clés publique et privée.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Téléchargez votre clé publique et cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. Sélectionnez le profil de produit appelé **Analytics-&lt; Nom de l’entreprise >** et cliquez sur **[!UICONTROL Enregistrer l’API]** configurée.

   ![](assets/do-not-localize/adobe_io_6.png)

1. Dans votre projet, sélectionnez Compte **[!UICONTROL de service (JWT)]** et copiez les informations suivantes :
   * **[!UICONTROL Identifiant du client]**
   * **[!UICONTROL Secret client]**
   * **[!UICONTROL ID de compte technique]**
   * **[!UICONTROL Identifiant de l&#39;organisation]**

   ![](assets/do-not-localize/adobe_io_7.png)

## Étape 2 : Ajouter les informations d’identification du projet dans Adobe Campaign {#add-credentials-campaign}

Pour ajouter les informations d’identification du projet en Adobe Campaign, exécutez la commande suivante en tant qu’utilisateur néolane sur tous les conteneurs de l’instance Adobe Campaign pour insérer les informations d’identification du compte **** technique dans le fichier de configuration de l’instance.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Vous devez coder la clé privée au format base64 UTF-8. N&#39;oubliez pas de supprimer la nouvelle ligne de la clé avant de la coder, à l&#39;exception de la clé privée. La clé privée doit être la même que celle utilisée pour créer l’intégration.

## Étape 3 : Mise à jour de la balise en pipeline {#update-pipelined-tag}

Pour mettre à jour [!DNL pipelined] la balise, vous devez mettre à jour le type d’authentification vers le projet d’E/S d’Adobe dans le fichier de configuration **config-&lt; nom-instance >.xml** comme suit :

```
<pipelined ... authType="imsJwtToken"  ... />
```
