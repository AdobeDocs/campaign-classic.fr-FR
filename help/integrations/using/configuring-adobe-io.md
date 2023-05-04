---
product: campaign
title: Configuration d’Adobe I/O pour les Triggers Adobe Experience Cloud
description: Découvrez comment configurer Adobe I/O pour les Triggers Adobe Experience Cloud
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
source-git-commit: 98a67e5b6e3f8cf8ba596db1fadd61fff821be30
workflow-type: ht
source-wordcount: '765'
ht-degree: 100%

---

# Configuration d’Adobe I/O pour les Triggers Adobe Experience Cloud {#configuring-adobe-io}

![](../../assets/v7-only.svg)

>[!CAUTION]
>
>Si vous utilisez une ancienne version de l’intégration Triggers par le biais de l’authentification OAuth, **vous devez migrer vers Adobe I/O comme décrit ci-dessous**.
>Notez que lors de ce déplacement vers [!DNL Adobe I/O], certains triggers entrants peuvent être perdus.
>
>L’ancien mode d’authentification OAuth avec Campaign a été abandonné le **20 octobre 2021**. Les environnements hébergés bénéficient dʼune extension jusquʼau **25 mai 2022**. En tant que client on-premise ou hybride, contactez lʼassistance clientèle dʼAdobe pour étendre lʼassistance jusquʼen **mai 2022**. Vous devez [fournir l’AppID de l’application OAuth](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) à Adobe.

## Conditions préalables {#adobe-io-prerequisites}

Cette intégration ne s’applique qu’à partir des **versions Campaign Classic 20.2.4 et ultérieures, 19.1.8 et Gold Standard 11**.

Avant de commencer cette implémentation, vérifiez que vous disposez des éléments suivants :

* un **identifiant d’organisation** valide : l’identifiant de l’organisation est l’identifiant unique dans Adobe Experience Cloud. Il est utilisé, entre autres, pour le service VisitorID et l’authentification unique (SSO) de l’IMS. [En savoir plus](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=fr)
* Un **accès développeur** à votre organisation. L’administrateur système de l’organisation doit suivre la procédure **Ajouter des développeurs à un profil de produit unique** présentée [dans cette page](https://helpx.adobe.com/fr/enterprise/using/manage-developers.html) pour fournir aux développeurs l’accès au profil du produit `Analytics - {tenantID}` Adobe Analytics associé aux Triggers.

## Étape 1 : créer/mettre à jour un projet Adobe I/O {#creating-adobe-io-project}

1. Accédez à [!DNL Adobe I/O] et connectez-vous avec l’accès développeur de votre organisation.

   >[!NOTE]
   >
   > Assurez-vous d’être connecté au portail d’organisation approprié.

1. Extrayez l&#39;identifiant client d&#39;intégration existant du fichier de configuration de l&#39;instance ims/authIMSTAClientId. Un attribut non existant ou vide indique que l&#39;identifiant du client n&#39;est pas configuré.

   >[!NOTE]
   >
   >Si l’identifiant du client est vide, vous pouvez directement **[!UICONTROL créer un nouveau projet]** dans Adobe I/O.

1. Identifiez le projet existant à l’aide de l’identifiant du client extrait. Recherchez des projets existants avec le même identifiant du client que celui extrait à l&#39;étape précédente.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Sélectionnez **[!UICONTROL + Ajouter au projet]** et choisissez **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. Dans la fenêtre **[!UICONTROL Ajouter une API]**, sélectionnez **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Sélectionnez **[!UICONTROL Compte de service (JWT)]** comme type d’authentification.

   ![](assets/do-not-localize/adobe_io_3.png)

1. Si l’identifiant du client était vide, sélectionnez **[!UICONTROL Générer une paire de clés]** pour créer une paire de clés publique et privée.

   Les clés seront alors automatiquement téléchargées avec une date d’expiration par défaut de 365 jours. Une fois la date d’expiration atteinte, vous devez générer une nouvelle paire de clés et mettre à jour l’intégration dans le fichier de configuration. L’option 2 vous permet de créer et de télécharger manuellement votre **[!UICONTROL clé publique]** avec une date d’expiration plus longue.

   Pour un guide détaillé sur le remplacement des paires de clé de certificat arrivant à expiration, consultez [cette page](https://developer.adobe.com/developer-console/docs/guides/email-alerts/cert-expiry/#a-step-by-step-guide-to-replacing-expiring-certificate-key-pairs).


   >[!CAUTION]
   >
   >Vous devez enregistrer le fichier config.zip lorsque l&#39;invite de téléchargement s&#39;affiche, car vous ne pourrez plus le télécharger.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. Sélectionnez un **[!UICONTROL profil de produit]** existant ou créez-en un si nécessaire. Aucune autorisation n’est requise pour ce **[!UICONTROL profil de produit]**. Pour plus d’informations sur les **[!UICONTROL profils de produit]** [!DNL Analytics], consultez la [documentation Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=fr#admin-console).

   Cliquez ensuite sur **[!UICONTROL Enregistrer l’API configurée]**.

   ![](assets/do-not-localize/adobe_io_6.png)

1. Dans votre projet, sélectionnez **[!UICONTROL Adobe Analytics]** et copiez les informations suivantes sous **[!UICONTROL Compte Service (JWT)]** :

   * **[!UICONTROL Identifiant du client]**
   * **[!UICONTROL Secret du client]**
   * **[!UICONTROL Identifiant du du compte technique]**
   * **[!UICONTROL Identifiant de l&#39;organisation]**

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
>Le certificat Adobe I/O expire après 12 mois. Vous devez générer une nouvelle paire de clés chaque année.

## Étape 2 : ajouter les informations d&#39;identification du projet dans Adobe Campaign {#add-credentials-campaign}

>[!NOTE]
>
>Cette étape n&#39;est pas requise si l&#39;identifiant du client n&#39;était pas vide à l&#39;[étape 1 : créer/mettre à jour un projet Adobe I/O](#creating-adobe-io-project).

La clé privée doit être encodée au format UTF-8 base64. Pour ce faire :

1. Utilisez la clé privée générée dans la section [Étape 1 : créer/mettre à jour un projet Adobe I/O](#creating-adobe-io-project). La clé privée doit être la même que celle utilisée pour créer l&#39;intégration.

1. Encodez la clé privée à l’aide de la commande suivante : `base64 ./private.key > private.key.base64`. Le contenu base64 sera ainsi enregistré dans un nouveau fichier `private.key.base64`.

   >[!NOTE]
   >
   >Des lignes supplémentaires peuvent parfois être automatiquement ajoutées lors du copier/coller de la clé privée. Pensez à les supprimer avant d’encoder votre clé privée.

1. Copiez le contenu du fichier `private.key.base64`.

1. Connectez-vous via SSH à chaque conteneur où l&#39;instance Adobe Campaign est installée et ajoutez les informations d&#39;identification du projet dans Adobe Campaign en exécutant la commande suivante en tant qu&#39;utilisateur `neolane`. Les informations d&#39;identification du **[!UICONTROL compte technique]** seront alors insérées dans le fichier de configuration de l&#39;instance.

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

## Étape 3 : mettre à jour la balise en pipeline {#update-pipelined-tag}

>[!NOTE]
>
>Cette étape n&#39;est pas requise si l&#39;identifiant du client n&#39;était pas vide à l&#39;[étape 1 : Créer/mettre à jour un projet Adobe I/O](#creating-adobe-io-project).

Pour mettre à jour la balise [!DNL pipelined], vous devez mettre à jour le type d’authentification du projet Adobe I/O dans le fichier de configuration **config-&lt; nom-instance >.xml** comme suit :

```
<pipelined ... authType="imsJwtToken"  ... />
```

Ensuite, exécutez `config -reload` et redémarrez [!DNL pipelined] pour que les modifications soient prises en compte.
