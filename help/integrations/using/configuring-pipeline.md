---
title: Configuration du pipeline
description: Découvrez comment configurer le pipeline
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: tm+mt
source-git-commit: f3caef21a269cf57624a07bfe1b4bf1e241061a6
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 21%

---


# Configuration du pipeline {#configuring-pipeline}

Les paramètres d’authentification tels que l’identifiant client, la clé privée et le point d’entrée de l’authentification sont configurés dans les fichiers de configuration de l’instance.
La liste des déclencheurs à traiter est configurée dans une option au format JSON.
Les déclencheurs sont utilisés pour le ciblage par un workflow de campagne qui envoie des emails. La campagne est configurée de sorte qu’un client qui a les deux événements de déclencheur reçoive un email.

>[!CAUTION]
>
>Dans le cas d’un déploiement hybride, assurez-vous que le pipeline est configuré sur une instance intermédiaire.

## Prérequis {#prerequisites}

Avant de démarrer cette configuration, vérifiez que vous disposez des éléments suivants :

* une version récente de Adobe Campaign : versions 19.1.8 ou 20.2.1 et ultérieures,
* Version de Adobe Analytics Standard

Vous aurez également besoin de :

* Authentification du projet d&#39;E/S Adobe
* un IMSOrgID valide, l&#39;identifiant du client Experience Cloud avec Adobe Analytics ajouté
* a Accès des développeurs à l&#39;organisation IMS
* configuration des déclencheurs effectuée en Adobe Analytics

## Fichiers d’authentification et de configuration {#authentication-configuration}

L’authentification est requise car le pipeline est hébergé dans le Adobe Experience Cloud.
Une paire de clés publique et privée est utilisée. Ce processus a la même fonction qu’un utilisateur/mot de passe mais est plus sécurisé.
L&#39;authentification est prise en charge pour le Marketing Cloud via le projet d&#39;E/S d&#39;Adobe.

## Étape 1 : Création/mise à jour d&#39;un projet d&#39;E/S d&#39;Adobe {#creating-adobe-io-project}

Pour les clients hébergés, vous pouvez créer un ticket d&#39;assistance clientèle pour permettre à votre entreprise d&#39;utiliser des jetons de compte technique d&#39;E/S d&#39;Adobe pour l&#39;intégration des déclencheurs.

Pour les clients sur site, reportez-vous à la page [Configuration des E/S d’Adobe pour les déclencheurs](../../integrations/using/configuring-adobe-io.md) Adobe Experience Cloud. Notez que vous devez sélectionner **[!UICONTROL Adobe Analytics]** lors de l’ajout d’API aux informations d’identification d’E/S de l’Adobe.

## Étape 2 : Configuration de l&#39;option de pipeline NmsPipeline_Config {#configuring-nmspipeline}

Une fois l&#39;authentification définie, le pipeline récupère les événements. Il traitera uniquement les déclencheurs configurés dans Adobe Campaign. Le déclencheur doit avoir été généré à partir d’Adobe Analytics et envoyé vers le pipeline qui traitera uniquement les déclencheurs configurés dans Adobe Campaign.
L’option peut également être configurée avec un caractère générique afin d’attraper tous les déclencheurs, quel que soit le nom.

1. Dans Adobe Campaign, accédez au menu d’options sous **[!UICONTROL Administration]** > **[!UICONTROL Plateforme]** > **[!UICONTROL Options]** dans l’ **[!UICONTROL Explorateur.]**

1. Sélectionnez l&#39;option **[!UICONTROL NmsPipeline_Config]** .

1. Dans le champ **[!UICONTROL Valeur (texte long)]** , vous pouvez coller le code JSON suivant, qui spécifie deux déclencheurs. Vous devez vous assurer de supprimer les commentaires.

   ```
   {
   "topics": [ // list of "topics" that the pipelined is listening to.
      {
           "name": "triggers", // Name of the first topic: triggers.
           "consumer": "customer_dev", // Name of the instance that listens.  This value can be found on the monitoring page of Adobe Campaign.
           "triggers": [ // Array of triggers.
               {
                   "name": "3e8a2ba7-fccc-49bb-bdac-33ee33cf02bf", // TriggerType ID from Analytics 
                   "jsConnector": "cus:triggers.js" // Javascript library holding the processing function.
               }, {
                   "name": "2da3fdff-13af-4c51-8ed0-05802a572e94", // Second TriggerType ID 
                   "jsConnector": "cus:triggers.js" // Can use the same JS for all.
               },
           ]
       }
   ]
   }
   ```

1. Vous pouvez également choisir de coller le code JSON suivant qui capture tous les déclencheurs.

   ```
   {
   "topics": [
     {
       "name": "triggers",
       "consumer":  "customer_dev",
       "triggers": [
         {
           "name": "*",
           "jsConnector": "cus:pipeline.js"
         }
       ]
     }
   ]
   }
   ```

### The Consumer parameter {#consumer-parameter}

Le pipeline fonctionne comme un modèle fournisseur et consommateur. Les messages ne sont consommés que pour un seul utilisateur : chaque consommateur reçoit sa propre copie des messages.

The **Consumer** parameter identifies the instance as one of these consumers. L&#39;identité de l&#39;instance appelle le pipeline. Vous pouvez le remplir avec le nom d&#39;instance qui se trouve sur la page Surveillance de la console client.

Le service de pipeline effectue le suivi des messages récupérés par chaque consommateur. L’utilisation de différents consommateurs pour différentes instances vous permet de vous assurer que chaque message est envoyé à chaque instance.

### Recommandations relatives à l’option Pipeline {#pipeline-option-recommendation}

Pour configurer l&#39;option Pipeline, vous devez suivre les recommandations suivantes :

* Ajoutez ou modifiez les déclencheurs sous **[!UICONTROL Déclencheurs]**, vous ne devez pas modifier le reste.
* Assurez-vous que le fichier JSON est valide. Vous pouvez utiliser un validateur JSON, reportez-vous à ce [site Web](http://jsonlint.com/) , par exemple.
* &quot;name&quot; correspond à l’ID du déclencheur. Un caractère générique &quot;*&quot; capture tous les déclencheurs.
* &quot;Consommateur&quot; correspond au nom de l’instance ou de l’application appelante.
* Le pipeline prend également en charge la rubrique &quot;alias&quot;.
* Vous devez toujours redémarrer l’oléoduc après avoir apporté des modifications.

## Étape 3 : Configuration facultative {#step-optional}

Vous pouvez modifier certains paramètres internes en fonction de vos besoins de charge, mais veillez à les tester avant de les mettre en production.

La liste des paramètres facultatifs se trouve ci-dessous :

| Option | Description |
|:-:|:-:|
| appName(Hérité) | AppID de l&#39;application OAuth enregistrée dans l&#39;application Hérité Oath où la clé publique a été chargée. Voir à ce propos [cette page](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md.) |
| authGatewayEndpoint(hérité) | URL permettant d’obtenir les jetons de passerelle. Par défaut: ```https://api.omniture.com``` |
| authPrivateKey(hérité) | La clé privée, la partie publique téléchargée dans l’application Hérité serment, AES chiffrée avec l’option XtkKey : ```cryptString("PRIVATE_KEY")``` |
| disableAuth(hérité) | Désactivez l&#39;authentification, la connexion sans jetons de passerelle ne sera acceptée que par certains points de terminaison du pipeline de développement. |
| discoverPipelineEndpoint | URL permettant de trouver le point de terminaison Pipeline Services à utiliser pour ce client. Par défaut: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | La période entre deux vidages du processus d&#39;état interne en état ```var/INSTANCE/pipelined.json.```<br> interne est également accessible à la demande ici : ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | Désactiver la détection du PipelineServicesEndpoint pour le forcer |
| monitorServerPort | Le processus pipeliné écoutera sur ce port pour fournir le processus d&#39;état interne ici : ```http://INSTANCE:PORT/pipelined/status```. <br>La valeur par défaut est de 7781 |
| pointerFlushMessageCount | Lorsque ce nombre de messages est traité, les décalages sont enregistrés dans la base de données. <br> La valeur par défaut est de 1000 |
| pointerFlushPeriodSec | Après cette période, les décalages seront enregistrés dans la base de données. <br>La valeur par défaut est de 5 (secondes) |
| processingJSThreads | Nombre de messages de traitement de threads dédiés avec des connecteurs JS personnalisés. <br> La valeur par défaut est de 4 |
| processingThreads | Nombre de messages de traitement de threads dédiés avec code natif. <br>La valeur par défaut est de 4 |
| retryPeriodSec | Délai entre les Reprises en cas d’erreurs de traitement. <br>La valeur par défaut est de 30 (secondes) |
| retryValiditySec | Ignorer le message s’il n’est pas traité correctement après cette période (trop de reprises). <br>La valeur par défaut est de 300 (secondes) |

### Démarrage automatique du processus en pipeline {#pipelined-process-autostart}

Le processus en pipeline doit être démarré automatiquement.

Pour ce faire, définissez l’élément &lt; pipelin > dans le fichier de configuration sur autostart=&quot;true&quot; :

```
 <pipelined autoStart="true" ... "/>
```

### Redémarrage du processus en pipeline {#pipelined-process-restart}

Un redémarrage est nécessaire pour que les modifications soient prises en compte :

```
nlserver restart pipelined@instance
```

## Étape 4 : Validation {#step-validation}

Pour valider la configuration du pipeline pour la mise en service, procédez comme suit :

* Make sure the [!DNL pipelined] process is running.
* Recherchez les journaux de connexion de pipeline dans le fichier pipeline.log.
* Vérifiez la connexion et si des pings sont reçus. Les clients hébergés peuvent utiliser le contrôle depuis la console client.
