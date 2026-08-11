---
product: campaign
title: Migration vers l’API Adobe Analytics 2.0
description: Campaign Classic - Guide de migration de l’API Adobe Analytics 2.0
feature: Technote, Analytics Integration
hide: true
source-git-commit: 64460d51b002a7821bba9c2998d9ccccab3046ad
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 2%

---

# Migration vers l’API Adobe Analytics 2.0 {#analytics-2-migration}

Les API d’Adobe Analytics 1.4 [en fin de vie](https://developer.adobe.com/analytics-apis/docs/1.4/guides/eol){target="_blank"}. Le [connecteur Web Analytics](../../integrations/using/gs-aa.md) qui relie votre instance Campaign à Adobe Analytics repose sur ces API. Vous devez donc effectuer une mise à niveau vers une version qui utilise les nouvelles API Analytics 2.0 pour que l’intégration reste en cours d’exécution.

>[!CAUTION]
>
>La mise à niveau réimporte les deux workflows techniques intégrés qui alimentent le connecteur, [!UICONTROL webAnalyticsSendMetrics] et [!UICONTROL webAnalyticsGetWebEvents] (voir la [référence des workflows Web Analytics](../../workflow/using/web-analytics.md) pour savoir ce que chacun fait). Toute personnalisation effectuée en plus de ces workflows est remplacée par la réimportation. Évitez de modifier directement ces workflows intégrés : créez plutôt votre personnalisation dans un workflow personnalisé distinct, de sorte que les futures mises à niveau ne la remplacent pas. La mise à niveau met également à jour les fichiers Analytics JavaScript intégrés : si l’un de vos workflows personnalisés fait référence à ces fichiers, ils seront rompus et devront être adaptés au nouveau code.

## Cela vous concerne-t-il ? {#are-you-impacted}

Cela vous concerne si votre instance utilise le compte externe [!UICONTROL Web Analytics] pour l’un des éléments suivants :

* Envoi des indicateurs et des attributs des campagnes par e-mail à Adobe Analytics en tant que mesures.
* Envoi de données de classification à Adobe Analytics.
* Flux de remarketing (identification des contacts convertis après une campagne).
* Compte externe [!UICONTROL Web Analytics] que vous prévoyez de configurer pour la première fois.

Vous ne savez pas laquelle de ces propositions s’applique à vous ? Vérifiez quels workflows techniques ci-dessus sont actifs sur votre instance et passez en revue la configuration de votre compte externe [!UICONTROL Web Analytics] dans [!UICONTROL Administration > Plateforme > Comptes externes] (voir [Compte externe Web Analytics](../../installation/using/external-accounts.md#web-analytics-external-account)).

## Comment migrer {#how-to-migrate}

Si vous vous trouvez sur une instance **hébergée par**, Adobe gère l’approvisionnement SFTP, la liste autorisée d’adresses IP et la configuration des clés pour vous dans le cadre de la mise à niveau. Vous ne devez valider vos cas d’utilisation qu’une fois la nouvelle version activée.

Si vous utilisez un déploiement **On-Premise ou hybride**, procédez comme suit.

1. [Mettez à niveau votre environnement Campaign](../../production/using/build-upgrade.md) vers une version qui inclut les modifications d’Adobe Analytics 2.0. Vous pouvez confirmer la version que vous exécutez à partir de [!UICONTROL Aide > À propos...] (voir [Comment vérifier votre version de Campaign](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)).
1. Vérifiez lequel des cas d’utilisation ci-dessus s’applique à votre instance, puisque l’étape suivante en dépend.
1. Si vous utilisez le flux de remarketing, le workflow [!UICONTROL webAnalyticsFindConverted] nécessite un canal SFTP dédié pour échanger des données avec Adobe Analytics 2.0. Configurez-le comme suit ; sinon, passez à l’étape suivante.
   1. Fournissez un serveur SFTP pour l’instance à l’aide de l’authentification par clé, en suivant les mêmes [bonnes pratiques d’utilisation du serveur SFTP](../../platform/using/sftp-server-usage.md) que celles que vous appliquez à toute autre intégration SFTP externe. Adobe fournit un [exemple de script de configuration SFTP](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html?package=/content/software-distribution/en/details.html/content/dam/campaign/public/setup_sftp.zip){target="_blank"} pour vous aider à commencer.
   1. Enregistrez les détails de connexion de ce serveur dans Adobe Analytics en exécutant le script fourni avec la nouvelle build :

      ```
      nlserver javascript -instance:<instance_name> -arg:host=<sftp_host_url>#user=<sftp_user> -file <path_to_the_file>/aaremarketingLocation.js
      ```

      Exemple:

      ```
      nlserver javascript -instance:test_mkt_stage2 -arg:host=test-mkt-stage1.campaign.adobe.com#user=test -file ./nl6/datakit/nms/eng/js/aaremarketingLocation.js
      ```

   1. Ajout d’Adobe Analytics sur la liste autorisée de votre serveur SFTP, car les exportations de remarketing ne sont jamais lancées qu’à partir d’un ensemble fixe de plages d’adresses IP Adobe :
      * [Recherchez les adresses IP actuelles de la collecte de données Adobe Analytics](https://experienceleague.adobe.com/en/docs/core-services/interface/data-collection/ip-addresses){target="_blank"} et ajoutez-les à la liste autorisée de données de votre serveur SFTP. Les exportations d’Analytics basées sur FTP (y compris les flux de données) proviennent uniquement des adresses IPv4 des régions de Londres, de l’Oregon et de Singapour.
      * [Récupérez la clé publique Adobe Analytics](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-18141){target="_blank"} et ajoutez-la au fichier `authorized_keys` sur votre serveur SFTP afin qu’Analytics puisse s’authentifier.
1. Activez l&#39;indicateur de fonctionnalité `FEATUREFLAG_USE_ANALYTICS_20_API` sur votre instance en créant ou en définissant la `longvalue` de l&#39;option sur `1` dans [!UICONTROL xtkOption], sous **[!UICONTROL Administration] > [!UICONTROL Plateforme] > [!UICONTROL Options]** dans l&#39;arborescence de l&#39;explorateur Campaign. Cette étape est requise quel que soit le cas d’utilisation ci-dessus qui vous concerne.
1. Validez la migration en réalisant chaque cas d’utilisation qui s’applique à votre instance (envoyez une campagne de test, vérifiez que les indicateurs arrivent dans Analytics et confirmez les données de remarketing, le cas échéant) avant de mettre hors service toute ancienne connectivité.

## Configuration d’un nouveau compte externe Web Analytics {#setting-up-a-new-web-analytics-external-account}

Les éléments suivants s’appliquent que votre instance soit hébergée par Adobe ou on-premise/hybride.

Si vous configurez le compte externe [!UICONTROL Web Analytics] pour la première fois, plutôt que de migrer un compte existant, suivez les [étapes de configuration du compte externe](../../installation/using/external-accounts.md#web-analytics-external-account) et le guide de prise en main du connecteur [&#128279;](../../integrations/using/gs-aa.md).

Dans la mesure où Analytics 2.0 introduit une nouvelle gestion des classifications, vous devez également créer un ensemble de classifications dans Adobe Analytics avant que votre compte externe puisse récupérer les données de classification de votre suite de rapports. Il s’agit d’une nouvelle étape : créez-la après la configuration de vos variables de conversion et événements de succès, et avant la configuration du compte externe dans Campaign.

Pour créer votre ensemble de classifications :

1. Dans la barre de menus supérieure [!DNL Adobe Analytics], sélectionnez **[!UICONTROL Composants]** > **[!UICONTROL Ensembles de classifications]**, puis cliquez sur **[!UICONTROL Nouveau]**.

   ![](assets/analytics-classification-set-menu.png)

1. Dans la boîte de dialogue **[!UICONTROL Ajouter un nouvel ensemble de classifications]** :

   ![](assets/analytics-classification-set-dialog.png)

   * Saisissez un **[!UICONTROL Nom]** pour l’ensemble de classifications.
   * Définissez le **[!UICONTROL Type]** sur **[!UICONTROL Principal]**.
   * Dans **[!UICONTROL Notifications de tâche]**, choisissez les personnes à avertir de la réussite ou de l’échec des tâches de l’ensemble de classifications et indiquez les adresses e-mail correspondantes.
   * Dans **[!UICONTROL Abonnements]**, sélectionnez votre suite de rapports et la variable de conversion que vous avez créée pour le nom de la campagne interne à l’étape précédente.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

Cet ensemble de classifications sera automatiquement découvert par Campaign lorsque vous configurerez votre compte externe à l’étape suivante. Pour plus d’informations sur les ensembles de classifications, consultez la documentation d’[&#128279;](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/create-set){target="_blank"}.

## Vous avez besoin d’aide ? {#need-help}

Si vous rencontrez des problèmes lors de la migration, contactez l’[Assistance clientèle &#x200B;](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}.
