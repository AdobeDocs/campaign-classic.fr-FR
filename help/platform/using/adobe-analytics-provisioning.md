---
product: campaign
title: Approvisionnement du connecteur Adobe Analytics
description: En savoir plus sur l'approvisionnement du connecteur Adobe Analytics.
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
badge-v7-prem: label="On-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
source-git-commit: 26d1b0bc9886988ff636d322c781a23f95a9bcd0
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Approvisionnement du connecteur Adobe Analytics {#adobe-analytics-connector-provisioning}

>[!CAUTION]
>
> Ces étapes ne doivent être effectuées que par des implémentations hybrides et On-Premise.
>
>Pour les mises en oeuvre de Managed Services hébergées et de Campaign, veuillez contacter [Adobe de l’assistance clientèle](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) l&#39;équipe.

L’intégration entre l’authentification Adobe Campaign Classic et Adobe Analytics prend en charge Adobe Identity Management Service (IMS) :

* Si vous gérez un compte externe migré, vous devez mettre en œuvre Adobe IMS et vous connecter à Adobe Campaign via un Adobe ID. L’utilisateur connecté via Adobe ID IMS doit être le propriétaire du compte **Connecteur de données** dans Adobe Analytics et disposer d’un ensemble d’autorisations pour le **Profil de produit** mentionné ci-dessous.

* Si vous implémentez un nouveau connecteur, la mise en œuvre d’Adobe IMS est facultative. En l’absence d&#39;un utilisateur Adobe ID, Adobe Campaign utilisera un utilisateur technique pour se synchroniser avec Adobe Analytics.

Pour que cette intégration fonctionne, vous devez créer un profil produit Adobe Analytics qui sera utilisé exclusivement pour le connecteur Analytics. Vous devez ensuite créer un projet Adobe I/O.

>[!AVAILABILITY]
>
> JWT (JSON Web Tokens) est actuellement en cours d’obsolescence et est remplacé par OAuth. La transition sera progressivement effectuée dans les prochaines versions de Campaign et la documentation sera mise à jour pour refléter ces mises à jour.

## Création d’un profil produit Adobe Analytics {#analytics-product-profile}

Le profil produit détermine le niveau d’accès d’un utilisateur à vos différents composants Analytics.

Si vous disposez déjà d’un profil produit Analytics, vous devez tout de même créer un profil produit Adobe Analytics qui sera utilisé exclusivement pour le connecteur Analytics. Cela permet de s’assurer que votre profil produit est défini avec les autorisations appropriées pour cette intégration.

Pour en savoir plus sur les profils produit, consultez la [documentation relative à Admin Console](https://helpx.adobe.com/fr/enterprise/admin-guide.html).

1. Dans [Admin Console](https://adminconsole.adobe.com/), sélectionnez votre **[!UICONTROL Produit]** Adobe Analytics.

   ![](assets/do-not-localize/triggers_1.png)

1. Cliquez sur **[!UICONTROL Nouveau profil]**.

   ![](assets/do-not-localize/triggers_2.png)

1. Ajoutez un **[!UICONTROL Nom de profil produit]**. Nous vous suggérons d’utiliser la syntaxe suivante : `reserved_campaign_classic_<Company Name>`. Cliquez ensuite sur **[!UICONTROL Suivant]**.

   Ce **[!UICONTROL Profil produit]** doit être utilisé exclusivement pour le connecteur Analytics, ceci afin d’éviter les erreurs de configuration incorrecte.

1. Ouvrez le **[!UICONTROL Profil produit]** que vous venez de créer et sélectionnez l’onglet **[!UICONTROL Autorisations]**.

   ![](assets/do-not-localize/triggers_3.png)

1. Configurez les différentes fonctionnalités en cliquant sur **[!UICONTROL Modifier]**, puis sélectionnez les autorisations à attribuer à votre **[!UICONTROL Profil produit]** en cliquant sur l’icône représentant un plus (+).

   Pour en savoir plus sur la gestion des autorisations, consultez la [documentation relative à Admin Console](https://helpx.adobe.com/fr/enterprise/using/manage-permissions-and-roles.html).

1. Pour la fonctionnalité **[!UICONTROL Suites de rapports]**, ajoutez les **[!UICONTROL Suites de rapports]** dont vous aurez besoin ultérieurement.

   Si vous ne disposez d’aucune suite de rapports, vous pouvez en créer une en suivant [cette procédure](../../platform/using/adobe-analytics-connector.md#report-suite-analytics).

   ![](assets/do-not-localize/triggers_4.png)

1. Pour la fonctionnalité **[!UICONTROL Mesures]**, ajoutez les **[!UICONTROL Mesures]** que vous devrez configurer ultérieurement.

   Si nécessaire, vous pouvez activer l’option Inclusion automatique, qui ajoute chaque élément d’autorisation dans la liste incluse et ajoute automatiquement de nouveaux éléments d’autorisation.

   ![](assets/do-not-localize/triggers_13.png)

1. Pour le **[!UICONTROL Dimensions]** , ajoutez la fonction **[!UICONTROL Dimensions]** nécessaire pour une configuration ultérieure.

   Assurez-vous que les Dimensions sélectionnées correspondent à celles à configurer dans la variable [Compte externe](adobe-analytics-connector.md#external-account-classic) et s’aligner sur le nombre d’eVars correspondant de [Adobe Analytics](adobe-analytics-connector.md#configure-conversion-success).

1. Pour la fonctionnalité **[!UICONTROL Outils de suites de rapports]**, ajoutez les autorisations suivantes :

   * **[!UICONTROL Gestion des suites de rapports]**
   * **[!UICONTROL Variables de conversion]**
   * **[!UICONTROL Événements de succès]**
   * **[!UICONTROL Rapport Data Warehouse personnalisé]**
   * **[!UICONTROL Gestionnaire des sources de données]**
   * **[!UICONTROL Classifications]**

1. Pour la fonctionnalité **[!UICONTROL Outils Analytics]**, ajoutez les autorisations suivantes :

   * **[!UICONTROL Gestionnaire de code - Services web]**
   * **[!UICONTROL Logs - Services web]**
   * **[!UICONTROL Services web]**
   * **[!UICONTROL Accès aux services web]**
   * **[!UICONTROL Création de mesure calculée]**
   * **[!UICONTROL Création de segment]**

Votre profil produit est désormais configuré. Vous devez ensuite créer le projet Adobe I/O.

## Création de projet Adobe I/O {#create-adobe-io}

1. Accédez à Adobe I/O et connectez-vous en tant qu’**Administrateur système** de votre organisation.

   Pour plus d’informations sur les rôles d’administrateur, reportez-vous à cette [page](https://helpx.adobe.com/fr/enterprise/using/admin-roles.html).

1. Cliquez sur **[!UICONTROL Créer un projet]**.

   ![](assets/do-not-localize/triggers_5.png)

1. Cliquez sur **[!UICONTROL Ajouter au projet]** et sélectionnez **[!UICONTROL API]**.

   ![](assets/do-not-localize/triggers_6.png)

1. Sélectionnez [!DNL Adobe Analytics] et cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/do-not-localize/triggers_7.png)

1. Choisissez **[!UICONTROL Compte Service (JWT)]** comme type d’authentification et cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/do-not-localize/triggers_8.png)

1. Sélectionnez l’**[!UICONTROL Option 1 : générer une paire de clés]** et cliquez sur **[!UICONTROL Générer une paire de clés]**.

   Le fichier config.zip est alors automatiquement téléchargé.

   ![](assets/do-not-localize/triggers_9.png)

1. Cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/do-not-localize/triggers_10.png)

1. Sélectionnez le **[!UICONTROL Profil produit]** créé lors des étapes précédentes détaillées dans cette [section](#analytics-product-profile).

1. Cliquez ensuite sur **[!UICONTROL Enregistrer l’API configurée]**.

   ![](assets/do-not-localize/triggers_11.png)

1. Dans votre projet, sélectionnez [!DNL Adobe Analytics] et copiez les informations suivantes sous **[!UICONTROL Compte Service (JWT)]** :

   * **[!UICONTROL Identifiant du client]**
   * **[!UICONTROL Secret du client]**
   * **[!UICONTROL Identifiant du du compte technique]**
   * **[!UICONTROL Identifiant de l&#39;organisation]**

   ![](assets/do-not-localize/triggers_12.png)

1. Utilisez la clé privée générée à l’étape 6.

   Si vous avez déjà configuré des Triggers à l’aide de ces informations d’identification, votre clé privée doit être la même pour cette configuration du connecteur.

1. Encodez la clé privée à l’aide de la commande suivante : `base64 ./private.key > private.key.base64`. Le contenu base64 sera ainsi enregistré dans un nouveau fichier `private.key.base64`.

   >[!NOTE]
   >
   >Des lignes supplémentaires peuvent parfois être automatiquement ajoutées lors du copier/coller de la clé privée. Pensez à les supprimer avant d’encoder votre clé privée.

1. Copiez le contenu du fichier `private.key.base64`.

1. Connectez-vous via SSH à chaque conteneur où l&#39;instance Adobe Campaign est installée et ajoutez les informations d&#39;identification du projet dans Adobe Campaign en exécutant la commande suivante en tant qu&#39;utilisateur `neolane`. Les informations d&#39;identification du **[!UICONTROL compte technique]** seront alors insérées dans le fichier de configuration de l&#39;instance.

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

Vous pouvez maintenant commencer à utiliser le connecteur Analytics et suivre les comportements de vos clients.
