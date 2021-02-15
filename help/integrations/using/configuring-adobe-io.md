---
solution: Campaign Classic
product: campaign
title: Configuration d’Adobe I/O pour les Triggers Adobe Experience Cloud
description: Découvrez comment configurer Adobe I/O pour les Triggers Adobe Experience Cloud
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c5c881d6919a8715e6588fb39793f562a16873bb
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 98%

---


# Configuration d’Adobe I/O pour les Triggers Adobe Experience Cloud {#configuring-adobe-io}

>[!CAUTION]
>
>Si vous utilisez une ancienne version de l’intégration Triggers par le biais de l’authentification OAuth, **vous devez migrer vers Adobe I/O comme décrit ci-dessous**. L’ancien mode d’authentification OAuth sera abandonné le 30 avril 2021. [En savoir plus](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)
>
>Notez que lors de ce déplacement vers Adobe I/O, certains triggers entrants peuvent être perdus.

## Prérequis {#adobe-io-prerequisites}

Cette intégration ne s&#39;applique qu&#39;à partir des **versions Campaign Classic 20.3, 20.2.4, 19.1.8 et Gold Standard 11**.

Avant de commencer cette mise en œuvre, vérifiez que vous disposez des éléments suivants :

* Un **identifiant d&#39;organisation** valide : l&#39;identifiant de l&#39;organisation Identity Management System (IMS) est l’identifiant unique dans Adobe Experience Cloud, utilisé par exemple pour le service VisitorID et l’authentification unique (SSO) IMS. [En savoir plus](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=fr)
* Un **accès développeur** à votre organisation.  Si vous devez demander les privilèges d’administrateur système de l’organisation IMS, procédez comme décrit [dans cette page](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html) pour accorder cet accès à tous les profils de produit.

## Étape 1 : créer/mettre à jour un projet Adobe I/O {#creating-adobe-io-project}

1. Accédez à Adobe I/O et connectez-vous avec le droit Administrateur système pour I’organisation IMS.

   >[!NOTE]
   >
   > Assurez-vous d&#39;être connecté au portail de l&#39;organisation approprié.

1. Extrayez l&#39;identifiant client (identifiant du client) d&#39;intégration existant du fichier de configuration de l&#39;instance ims/authIMSTAClientId. Un attribut non existant ou vide indique que l’identifiant du client n’est pas configuré.

   >[!NOTE]
   >
   >Si l’identifiant du client est vide, vous pouvez directement **[!UICONTROL créer un nouveau projet]** dans Adobe I/O.

1. Identifiez le projet existant à l’aide de l’identifiant du client extrait. Recherchez des projets existants avec le même identifiant du client que celui extrait à l&#39;étape précédente.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Sélectionnez **[!UICONTROL + Ajouter au projet]** et choisissez **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. Dans la fenêtre **[!UICONTROL Ajouter une API]**, sélectionnez **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Sélectionnez **[!UICONTROL Compte de service (JWT)]** comme type d&#39;authentification.

   ![](assets/do-not-localize/adobe_io_3.png)

1. Si l’identifiant du client était vide, sélectionnez **[!UICONTROL Générer une paire de clés]** pour créer une paire de clés publique et privée.

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

>[!CAUTION]
>
>Le certificat Adobe I/O expire après 12 mois. Vous devez générer une nouvelle paire de clés chaque année.

## Étape 2 : ajouter les informations d&#39;identification du projet dans Adobe Campaign {#add-credentials-campaign}

Pour ajouter les informations d’identification du projet dans Adobe Campaign, exécutez la commande ci-après en tant qu’utilisateur &#39;neolane&#39; sur tous les conteneurs de l’instance Adobe Campaign pour insérer les informations d’identification du **[!UICONTROL compte technique]** dans le fichier de configuration de l’instance.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
```

>[!NOTE]
>
>Vous devez coder la clé privée au format base64 UTF-8. N&#39;oubliez pas de supprimer la nouvelle ligne de la clé avant de la coder, à l&#39;exception de la clé privée. La clé privée doit être la même que celle utilisée pour créer l&#39;intégration. Pour tester l&#39;encodage base64 de la clé privée, vous pouvez utiliser [ce site Web](https://www.base64encode.org/).

## Étape 3 : mettre à jour la balise en pipeline {#update-pipelined-tag}

Pour mettre à jour la balise [!DNL pipelined], vous devez mettre à jour le type d’authentification du projet Adobe I/O dans le fichier de configuration **config-&lt; nom-instance >.xml** comme suit :

```
<pipelined ... authType="imsJwtToken"  ... />
```
