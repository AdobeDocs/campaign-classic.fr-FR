---
product: campaign
title: Mise à jour vers le nouveau serveur de délivrabilité
description: Découvrez comment mettre à jour le nouveau serveur de délivrabilité de Campaign
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: 8b8935b181b615c0a243799b14d01f778b84b715
workflow-type: tm+mt
source-wordcount: '1186'
ht-degree: 96%

---

# Mise à jour vers le nouveau serveur de délivrabilité {#acc-deliverability}

Depuis la [version 7.2.1](../../rn/using/latest-release.md#release-7-2-2), Adobe Campaign s’appuie sur un nouveau serveur de délivrabilité qui assure une haute disponibilité et résout les problèmes de conformité en matière de sécurité. Campaign Classic synchronise désormais les règles de délivrabilité, les broadlogs, ainsi que l’adresse de suppression depuis et vers le nouveau serveur de délivrabilité. L’ancien serveur de délivrabilité sera désactivé le 31 août 2022.

En tant que client Campaign Classic, vous devez implémenter le nouveau serveur de délivrabilité **avant le 31 août 2022**.

>[!NOTE]
>
>Pour plus d’informations sur ces modifications, reportez-vous à la section [FAQ](#faq) ou contactez [l’Assistance clientèle d’Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}.

## Qu’est-ce qui a changé ?{#acc-deliverability-changes}

Adobe désactive les anciens centres de données pour des raisons de conformité en matière de sécurité. Les clients Adobe Campaign Classic doivent effectuer une migration vers le nouveau serveur de délivrabilité, hébergé sur Amazon Web Service (AWS).

Ce nouveau serveur garantit une haute disponibilité (99,9) et fournit des points d’entrée sécurisés et authentifiés permettant aux serveurs de campagne de récupérer les données requises. Ainsi, plutôt que de se connecter à la base de données pour chaque demande, le nouveau serveur de délivrabilité met en cache les données afin de répondre aux demandes, dans la mesure du possible. Ce mécanisme améliore le temps de réponse.

## Cela vous concerne-t-il ?{#acc-deliverability-impacts}

Tous les clients sont affectés et doivent effectuer la mise à niveau vers [la version 7.2.1 de Campaign](../../rn/using/latest-release.md#release-7-2-2) (ou une version ultérieure) et implémenter leur environnement pour bénéficier du nouveau serveur de délivrabilité.

## Comment effectuer la mise à jour ?{#acc-deliverability-update}

En tant que **client hébergé**, Adobe collaborera avec vous pour mettre à niveau votre ou vos instances vers la version la plus récente et créer le projet dans la console Adobe Developer.

En tant que **client on-premise/hybride**, vous devez effectuer la mise à niveau vers [la version 7.2.1 de Campaign](../../rn/using/latest-release.md#release-7-2-2) (ou une version ultérieure) pour bénéficier du nouveau serveur de délivrabilité. Une fois toutes les instances mises à niveau, vous devez [implémenter la nouvelle intégration](#implementation-steps) vers le serveur de délivrabilité d’Adobe, et assurer ainsi une transition transparente.

## Étapes dʼimplémentation {#implementation-steps}

Dans le cadre de la nouvelle intégration du serveur de délivrabilité, Campaign doit communiquer avec les services partagés d’Adobe via une authentification basée sur Identity Management Service (IMS). Il est préférable d’utiliser le jeton de passerelle basé sur Adobe Developer (également appelé Jeton de compte technique ou JWT Adobe IO).


>[!WARNING]
>
>Ces étapes ne doivent être effectuées que pour les implémentations hybrides et On-premise.

### Conditions préalables{#prerequisites}

Avant de commencer l’implémentation, vérifiez la configuration de votre instance.

1. Ouvrez la console cliente Campaign et connectez-vous à Adobe Campaign en tant qu’administrateur.
1. Accédez à **Administration > Plateforme > Options**.
1. Vérifiez que la valeur de l’option `DmRendering_cuid` est renseignée.

   * Si vous avez renseigné cette option, vous pouvez lancer l’implémentation.
   * Si aucune valeur n’est renseignée, contactez l’[Assistance clientèle d’Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} pour obtenir votre CUID.

   Cette option doit être renseignée sur toutes vos instances Campaign (MKT, MID, RT, EXEC) avec la valeur correcte. En tant que client hybride, contactez Adobe pour que l’option soit définie sur vos instances MID, RT et EXEC.

>[!CAUTION]
>
>En tant que client on-premise, si un pare-feu est implémenté sur votre côté, vous devez ajouter cette URL. `https://deliverability-service.adobe.io` à votre liste autorisée. [En savoir plus](../../installation/using/url-permissions.md).

### Étape 1 : Créer/mettre à jour votre projet Adobe Developer {#adobe-io-project}

1. Accédez à [Adobe Developer Console](https://developer.adobe.com/console/home) et connectez-vous avec l’accès développeur de votre organisation. Assurez-vous d’être connecté au portail d’organisation approprié.

1. Sélectionnez **[!UICONTROL Créer un projet]**.
   ![](assets/New-Project.png)


   >[!CAUTION]
   >
   >Si vous utilisez déjà la fonctionnalité d’authentification JWT d’Adobe IO pour une autre intégration, telle qu’Analytics Connector ou Adobe Triggers, vous devez mettre à jour votre projet en ajoutant **API Campaign** à ce projet.

1. Choisissez **[!UICONTROL Ajouter une API]**.
   ![](assets/Add-API.png)
1. Dans la fenêtre **[!UICONTROL Ajouter une API]**, sélectionnez **[!UICONTROL Adobe Campaign]**.
   ![](assets/AC-API.png)
1. Si l’identifiant du client était vide, sélectionnez **[!UICONTROL Générer une paire de clés]** pour créer une paire de clés publique et privée.
   ![](assets/Generate-a-key-pair.png)

   Les clés seront alors automatiquement téléchargées avec une date d’expiration par défaut de 365 jours. Une fois la date d’expiration atteinte, vous devez générer une nouvelle paire de clés et mettre à jour l’intégration dans le fichier de configuration. L’option 2 vous permet de créer et de télécharger manuellement votre **[!UICONTROL clé publique]** avec une date d’expiration plus longue.
   ![](assets/New-key-pair.png)

   >[!CAUTION]
   >
   >Vous devez enregistrer le fichier `config.zip` lorsque l’invite de téléchargement s’affiche, car vous ne pourrez plus le télécharger.

1. Cliquez sur **[!UICONTROL Suivant]**.
1. Sélectionnez un **[!UICONTROL profil de produit]** existant ou créez-en un si nécessaire. Aucune autorisation n’est requise pour ce **[!UICONTROL profil de produit]**. Pour plus d’informations sur les **[!UICONTROL Profils de produit]**, consultez [cette page](https://helpx.adobe.com/fr/enterprise/using/manage-developers.html){_blank}.
   ![](assets/Product-Profile-API.png)

   Cliquez ensuite sur **[!UICONTROL Enregistrer l’API configurée]**.

1. Dans votre projet, sélectionnez **[!UICONTROL Adobe Campaign]** et copiez les informations suivantes sous **[!UICONTROL Compte Service (JWT)]**.

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
1. Accédez à l’option `NewDeliverabilityServer_FeatureFlag` et définissez la valeur sur `1`. Cette configuration doit être effectuée sur toutes vos instances Campaign (MKT, MID, RT, EXEC). En tant que client hybride, contactez Adobe pour que l’option soit définie sur vos instances MID, RT et EXEC.

### Étape 4 : valider votre configuration

Pour vérifier que l’intégration est réussie, procédez comme suit :


1. Ouvrez la console cliente et connectez-vous à Adobe Campaign.
1. Accédez à **Administration > Production > Workflows techniques**.
1. Redémarrez le workflow **Actualiser la délivrabilité** (deliverabilityUpdate). Cette opération doit être réalisée sur toutes vos instances Campaign (MKT, MID, RT, EXEC). En tant que client hybride, contactez Adobe pour redémarrer le workflow sur vos instances MID, RT et EXEC.
1. Vérifier les logs : le workflow doit s’exécuter sans erreur.


## Forum aux questions {#faq}

### Quelle est le planning de la mise à jour ?

La transition vers le nouveau serveur de délivrabilité, permettant l’ajout de ces fonctionnalités améliorées et le renforcement de la sécurité, commencera le 22 juillet pour les clients hébergés (Campaign Managed Services). Tous les clients hébergés seront mis à jour avant la fin du mois d’août.

Les clients on-premise et hybrides doivent effectuer une transition à la même période.

### Que se passe-t-il si je ne mets pas à niveau mon environnement ?

Toute instance de Campaign non mise à niveau d’ici le 31 août ne pourra plus se connecter au serveur de délivrabilité de Campaign. Par conséquent, le workflow **Actualiser la délivrabilité** (deliverabilityUpdate) échouera, ce qui affectera votre délivrabilité.

Si vous ne mettez pas à niveau votre environnement, les paramètres d’e-mail ne seront plus synchronisés (règles de gestion MX, règles relatives aux e-mails entrants, règles de gestion des domaines et règles de qualification des rebonds). Cela peut affecter votre délivrabilité au fil du temps. Si une modification importante est apportée à ces règles, celles-ci doivent être appliquées manuellement à partir de ce point.

Pour les instances MKT, seule la [Liste de suppression globale](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules) est affectée.

