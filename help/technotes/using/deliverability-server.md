---
product: campaign
title: Migration vers le nouveau serveur de délivrabilité
description: Découvrez comment implémenter le serveur de délivrabilité de Campaign
hide: true
hidefromtoc: true
source-git-commit: a2590a6d8df1e73d77bbdef7b8cf3b2d6efe207f
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 40%

---

# Serveur de délivrabilité de Campaign {#acc-deliverability}

Depuis la version v7 21.1 de Campaign Classic, Adobe Campaign propose un nouveau serveur de délivrabilité qui assure une haute disponibilité et résout les problèmes de conformité en matière de sécurité. Campaign Classic synchronise désormais les règles de délivrabilité, les broadlogs et l’adresse de suppression depuis et vers le nouveau serveur de délivrabilité.

En tant que client Campaign Classic, vous devez implémenter le nouveau serveur de délivrabilité.

>[!NOTE]
>
>Pour toute question sur ces modifications, consultez le [FAQ](#faq-aa). Pour plus d&#39;informations, contactez l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Qu&#39;est-ce qui a changé ?{#acc-deliverability-changes}

Adobe désactive les anciens centres de données pour des raisons de conformité à la sécurité. Les clients Adobe Campaign Classic doivent migrer vers le nouveau service de délivrabilité, hébergé sur Amazon Web Service (AWS).

Ce nouveau serveur garantit une haute disponibilité (9.9) &#x200B; et fournit des points de terminaison sécurisés et authentifiés permettant aux serveurs de campagne de récupérer les données requises : plutôt que de se connecter à la base de données pour chaque demande, le nouveau serveur de délivrabilité met en cache les données afin de répondre aux demandes, dans la mesure du possible. Ce mécanisme améliore le temps de réponse. &#x200B;


## Cela vous concerne-t-il ?{#acc-deliverability-impacts}

Si vous utilisez le serveur de délivrabilité Adobe Campaign existant et que votre environnement a été implémenté sur une version inférieure à Campaign 21.1.1, cela vous impacte. Vous devez effectuer la mise à niveau vers Campaign 21.1 (ou version ultérieure).

Découvrez comment vérifier votre version [dans cette section](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Comment effectuer la mise à jour ?{#acc-deliverability-update}

En tant que client hébergé, Adobe collaborera avec vous afin de mettre à niveau votre ou vos instance(s) vers la nouvelle version.

En tant que client on-premise/hybride, vous devez effectuer une mise à niveau vers l’une des versions les plus récentes pour bénéficier du nouveau serveur de délivrabilité .
Une fois toutes les instances mises à niveau, vous pourrez [mettre en oeuvre la nouvelle intégration ;](#implementation-steps) pour Adobe du serveur de délivrabilité et assurer une transition transparente.

## Étapes de mise en oeuvre (clients hybrides et on-premise) {#implementation-steps}

>[!IMPORTANT]
>
>Ces étapes ne doivent être effectuées que par des implémentations hybrides et on-premise.
>
>Pour les implémentations hébergées, contactez [Assistance clientèle Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

### Conditions préalables{#prerequisites}

Dans le cadre de la nouvelle intégration du serveur de délivrabilité, Campaign doit communiquer avec Adobe Shared Services via une authentification basée sur Identity Management Service (IMS). La méthode recommandée consiste à utiliser le jeton de passerelle basé sur Adobe Developer (également appelé Jeton de compte technique ou JWT d’Adobe IO).

### Étape 1 : Créer/mettre à jour votre projet Adobe Developer {#adobe-io-project}

1. Accès [Console Adobe Developer](https://developer.adobe.com/console/home) et connectez-vous avec l’accès Développeur de votre organisation.

   >[!NOTE]
   >
   > Assurez-vous d’être connecté au portail d’organisation approprié.

1. Sélectionnez **[!UICONTROL + Ajouter au projet]** et choisissez **[!UICONTROL API]**.
1. Dans le **[!UICONTROL Ajout d’une API]** fenêtre, sélectionnez **[!UICONTROL Adobe Campaign]**.
1. Sélectionnez **[!UICONTROL Compte de service (JWT)]** comme type d&#39;authentification.
1. Si l’identifiant du client était vide, sélectionnez **[!UICONTROL Générer une paire de clés]** pour créer une paire de clés publique et privée.

   Les clés seront alors automatiquement téléchargées avec une date d’expiration par défaut de 365 jours. Une fois la date d’expiration atteinte, vous devez générer une nouvelle paire de clés et mettre à jour l’intégration dans le fichier de configuration. L’option 2 vous permet de créer et de télécharger manuellement votre **[!UICONTROL clé publique]** avec une date d’expiration plus longue.

   >[!CAUTION]
   >
   >Vous devez enregistrer le fichier config.zip lorsque l&#39;invite de téléchargement s&#39;affiche, car vous ne pourrez plus le télécharger.

1. Cliquez sur **[!UICONTROL Suivant]**.
1. Sélectionnez un **[!UICONTROL profil de produit]** existant ou créez-en un si nécessaire. Aucune autorisation n’est requise pour ce **[!UICONTROL profil de produit]**. Pour plus d’informations sur [!DNL Analytics] **[!UICONTROL Profils de produit]**, voir [cette page](https://helpx.adobe.com/fr/enterprise/using/manage-developers.html).

   Cliquez ensuite sur **[!UICONTROL Enregistrer l’API configurée]**.

1. Dans votre projet, sélectionnez **[!UICONTROL Adobe Campaign]** et copiez les informations suivantes sous **[!UICONTROL Compte de service (JWT)]**:

   * **[!UICONTROL Identifiant du client]**
   * **[!UICONTROL Secret du client]**
   * **[!UICONTROL Identifiant du du compte technique]**
   * **[!UICONTROL Identifiant de l&#39;organisation]**

>[!CAUTION]
>
>Le certificat Adobe Developer expire après 12 mois. Vous devez générer une nouvelle paire de clés chaque année.

### Étape 2 : ajouter les informations d&#39;identification du projet dans Adobe Campaign {#add-credentials-campaign}

La clé privée doit être encodée au format UTF-8 base64.

Pour ce faire :

1. Utilisez la clé privée générée dans les étapes ci-dessus.
1. Encodez la clé privée à l’aide de la commande suivante : `base64 ./private.key > private.key.base64`. Le contenu base64 sera ainsi enregistré dans un nouveau fichier `private.key.base64`.

   >[!NOTE]
   >
   >Des lignes supplémentaires peuvent parfois être automatiquement ajoutées lors du copier/coller de la clé privée. Pensez à les supprimer avant d’encoder votre clé privée.

1. Copiez le contenu du fichier `private.key.base64`.
1. Connectez-vous via SSH à chaque conteneur où l&#39;instance Adobe Campaign est installée et ajoutez les informations d&#39;identification du projet dans Adobe Campaign en exécutant la commande suivante en tant qu&#39;utilisateur `neolane`. Les informations d&#39;identification du **[!UICONTROL compte technique]** seront alors insérées dans le fichier de configuration de l&#39;instance.

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

1. Vous devez arrêter et redémarrer le serveur pour que cette modification soit prise en compte. Vous pouvez également exécuter une `config -reload` .

### Étape 3 : Vérifier votre configuration

Une fois les paramètres définis, vous pouvez vérifier la configuration de votre instance. Procédez comme suit :

1. Ouvrez la console cliente et connectez-vous à Adobe Campaign en tant qu’administrateur.
1. Accédez à **Administration > Plateforme > Options**.
1. Vérifiez les `DmRendering_cuid` La valeur de l’option est renseignée. Il doit être renseigné sur toutes vos instances Campaign (MKT, MID, RT, EXEC). Si elle n’est pas renseignée, vous devez renseigner la valeur. Si aucune valeur n’est renseignée, contactez [Assistance clientèle Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) pour obtenir votre CUID.

### Étape 4 : Activer le nouveau serveur de délivrabilité

Vous pouvez maintenant activer le nouveau serveur de délivrabilité. Pour ce faire :

1. Ouvrez la console cliente et connectez-vous à Adobe Campaign en tant qu’administrateur.
1. Accédez à **Administration > Plateforme > Options**.
1. Accédez au `NewDeliverabilityServer_FeatureFlag` et définissez la valeur sur `1`. Cette configuration doit être effectuée sur toutes vos instances Campaign (MKT, MID, RT, EXEC).


### Étape 5 : Validation de votre configuration

Pour vérifier que l’intégration est réussie, procédez comme suit :


1. Ouvrez la console cliente et connectez-vous à Adobe Campaign.
1. Accédez à **Administration > Exploitation > Workflows techniques**.
1. Redémarrez le **Mise à jour pour la délivrabilité** Workflow (deliverabilityUpdate). Cela doit être effectué sur toutes vos instances Campaign (MKT, MID, RT, EXEC).
1. Vérifier les logs : le workflow doit s’exécuter sans erreur.

## FAQ{#faq-aa}

Q : A :

Q : A :



Pour d&#39;autres conseils, contactez l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
