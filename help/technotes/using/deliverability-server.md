---
product: campaign
title: Effectuer une migration vers le nouveau serveur de délivrabilité
description: Découvrez comment implémenter le serveur de délivrabilité de Campaign.
hide: true
hidefromtoc: true
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: c3b1ffcb580c7510a64115e0abbf16cb766146c5
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 64%

---

# Serveur de délivrabilité de Campaign {#acc-deliverability}

Depuis la version 7 21.1 de Campaign Classic, Adobe Campaign propose un nouveau serveur de délivrabilité qui assure une haute disponibilité et résout les problèmes de conformité en matière de sécurité. Campaign Classic synchronise désormais les règles de délivrabilité, les broadlogs, ainsi que l’adresse de suppression depuis et vers le nouveau serveur de délivrabilité.

En tant que client Campaign Classic, vous devez implémenter le nouveau serveur de délivrabilité. **avant le 31 août 2022**.

>[!NOTE]
>
>Pour toute question concernant ces modifications, reportez-vous à la section [FAQ](#faq)ou contactez [Assistance clientèle Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Qu’est-ce qui a changé ?{#acc-deliverability-changes}

Adobe désactive les anciens centres de données pour des raisons de conformité en matière de sécurité. Les clients Adobe Campaign Classic doivent effectuer une migration vers le nouveau serveur de délivrabilité, hébergé sur Amazon Web Service (AWS).

Ce nouveau serveur garantit une haute disponibilité (99,9) et fournit des points d’entrée sécurisés et authentifiés permettant aux serveurs de campagne de récupérer les données requises. Ainsi, plutôt que de se connecter à la base de données pour chaque demande, le nouveau serveur de délivrabilité met en cache les données afin de répondre aux demandes, dans la mesure du possible. Ce mécanisme améliore le temps de réponse.

## Cela vous concerne-t-il ?{#acc-deliverability-impacts}

Si votre environnement a été implémenté sur une version inférieure à [Campaign v7.2.1](../../rn/using/latest-release.md#release-7-2-2), vous êtes affecté. Vous devez effectuer la mise à niveau vers Campaign v7.2.1 (ou version ultérieure).

Découvrez comment vérifier votre version [dans cette section](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Comment effectuer la mise à jour ?{#acc-deliverability-update}

Comme **client hébergé**, Adobe collaborera avec vous pour mettre à niveau votre ou vos instances vers la version la plus récente et créer le projet dans la console Adobe Developer.

En tant que **client on-premise/hybride**, vous devez effectuer la mise à niveau vers l’une des versions les plus récentes pour bénéficier du nouveau serveur de délivrabilité. Une fois toutes les instances mises à niveau, vous pouvez [implémenter la nouvelle intégration](#implementation-steps) vers le serveur de délivrabilité d’Adobe, et assurer ainsi une transition transparente.

## Étapes dʼimplémentation {#implementation-steps}

Dans le cadre de la nouvelle intégration du serveur de délivrabilité, Campaign doit communiquer avec les services partagés d’Adobe via une authentification basée sur Identity Management Service (IMS). La méthode recommandée consiste à utiliser le jeton de passerelle basé sur Adobe Developer (également appelé Jeton de compte technique ou JWT d’Adobe IO).


>[!WARNING]
>
>Ces étapes ne doivent être effectuées que par des implémentations hybrides et On-premise.

### Conditions préalables{#prerequisites}

Avant de commencer l’implémentation, vérifiez la configuration de votre instance.

1. Ouvrez la console cliente Campaign et connectez-vous à Adobe Campaign en tant qu&#39;administrateur.
1. Accédez à **Administration > Plateforme > Options**.
1. Vérifiez que la valeur de l’option `DmRendering_cuid` est renseignée.

   * Si cette option est remplie, vous pouvez lancer la mise en oeuvre.
   * Si aucune valeur n’est renseignée, contactez l’[Assistance clientèle d’Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) pour obtenir votre CUID.

      Cette option doit être renseignée sur toutes vos instances Campaign (MKT, MID, RT, EXEC) avec la même valeur.

### Étape 1 : Créer/mettre à jour votre projet Adobe Developer {#adobe-io-project}

1. Accédez à [Adobe Developer Console](https://developer.adobe.com/console/home) et connectez-vous avec l’accès développeur de votre organisation.

   >[!NOTE]
   >
   > Assurez-vous d’être connecté au portail d’organisation approprié.

1. Sélectionner **[!UICONTROL Créer un projet]**.
   ![](assets/New-Project.png)


   >[!CAUTION]
   >
   >Si vous utilisez déjà la fonctionnalité d’authentification JWT d’Adobe IO pour une autre intégration, telle qu’Analytics Connector ou Adobe Triggers, vous devez mettre à jour votre projet en ajoutant **API Campaign** à ce projet.

1. Choisir **[!UICONTROL Ajout d’une API]**.
   ![](assets/Add-API.png)
1. Dans la fenêtre **[!UICONTROL Ajouter une API]**, sélectionnez **[!UICONTROL Adobe Campaign]**.
   ![](assets/AC-API.png)
1. Si l’identifiant du client était vide, sélectionnez **[!UICONTROL Générer une paire de clés]** pour créer une paire de clés publique et privée.
   ![](assets/Generate-a-key-pair.png)

   Les clés seront alors automatiquement téléchargées avec une date d’expiration par défaut de 365 jours. Une fois la date d’expiration atteinte, vous devez générer une nouvelle paire de clés et mettre à jour l’intégration dans le fichier de configuration. L’option 2 vous permet de créer et de télécharger manuellement votre **[!UICONTROL clé publique]** avec une date d’expiration plus longue.
   ![](assets/New-key-pair.png)

   >[!CAUTION]
   >
   >Vous devez enregistrer la variable `config.zip` lorsque l’invite de téléchargement apparaît, car vous ne pourrez plus le télécharger.

1. Cliquez sur **[!UICONTROL Suivant]**.
1. Sélectionnez un **[!UICONTROL profil de produit]** existant ou créez-en un si nécessaire. Aucune autorisation n’est requise pour ce **[!UICONTROL profil de produit]**. Pour en savoir plus sur les Profils de produit ****, consultez [cette page](https://helpx.adobe.com/fr/enterprise/using/manage-developers.html).
   ![](assets/Product-Profile-API.png)

   Cliquez ensuite sur **[!UICONTROL Enregistrer l’API configurée]**.

1. Dans votre projet, sélectionnez **[!UICONTROL Adobe Campaign]** et copiez les informations suivantes sous **[!UICONTROL Compte de service (JWT)]**

   ![](assets/Config-API.png)

   * **[!UICONTROL Identifiant du client]**
   * **[!UICONTROL Secret du client]**
   * **[!UICONTROL Identifiant du du compte technique]**
   * **[!UICONTROL Identifiant de l&#39;organisation]**

>[!CAUTION]
>
>Le certificat Adobe Developer expire au bout de 12 mois. Vous devez générer une nouvelle paire de clés chaque année.

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

1. Vous devez arrêter et redémarrer le serveur pour que cette modification soit prise en compte. Vous pouvez également exécuter une commande `config -reload`.

### Étape 3 : activer le nouveau serveur de délivrabilité

Vous pouvez maintenant activer le nouveau serveur de délivrabilité. Procédez comme suit :

1. Ouvrez la console cliente et connectez-vous à Adobe Campaign en tant qu’administrateur.
1. Accédez à **Administration > Plateforme > Options**.
1. Accédez à l’option `NewDeliverabilityServer_FeatureFlag` et définissez la valeur sur `1`. Cette configuration doit être effectuée sur toutes vos instances Campaign (MKT, MID, RT, EXEC).

### Étape 4 : valider votre configuration

Pour vérifier que l’intégration est réussie, procédez comme suit :


1. Ouvrez la console cliente et connectez-vous à Adobe Campaign.
1. Accédez à **Administration > Production > Workflows techniques**.
1. Redémarrez le workflow **Mise à jour pour la délivrabilité** (deliverabilityUpdate). Cette opération doit être réalisée sur toutes vos instances Campaign (MKT, MID, RT, EXEC).
1. Vérifier les logs : le workflow doit s’exécuter sans erreur.


## Forum aux questions {#faq}

### Que se passe-t-il si je ne mets pas à niveau mon environnement ?

Toute instance de Campaign non mise à niveau d&#39;ici le 31 août ne pourra plus se connecter au serveur de délivrabilité de Campaign. Par conséquent, la **Mise à jour pour la délivrabilité** Le workflow (deliverabilityUpdate) échouera. Ce workflow gère la mise à jour quotidienne des règles MX et des règles d&#39;inbounces.

Si vous ne mettez pas à niveau votre environnement, les paramètres d’email cesseront d’être synchronisés (règles de gestion MX, règles de mail entrant, règles de gestion des domaines et règles de qualification des bounces). Cela peut avoir une incidence sur votre délivrabilité au fil du temps. Si une modification importante est apportée à ces règles, celles-ci doivent être appliquées manuellement à partir de ce point.

Pour les instances MKT uniquement [Liste de suppression globale](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules) est affectée.

### Je ne peux pas effectuer la mise à niveau maintenant. Quel est le conseil ?

Si vous ne pouvez pas mettre à niveau votre instance avant le 31 août, vous devez désactiver temporairement la variable **Mise à jour pour la délivrabilité** (deliverabilityUpdate) jusqu&#39;à la fin de la mise à niveau afin de ne pas tenter de se synchroniser avec l&#39;ancien serveur de délivrabilité.



Pour d’autres conseils, contactez l’[Assistance clientèle d’Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
