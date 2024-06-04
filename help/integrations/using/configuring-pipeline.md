---
product: campaign
title: Configuration du pipeline
description: Découvrez comment configurer le pipeline pour l'intégration Campaign - Triggers
feature: Triggers
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
audience: integrations
content-type: reference
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: 271e0f9fde0cbfb016e201c8390b26673d8fc696
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 63%

---

# Configuration du pipeline {#configuring-pipeline}

Les paramètres d’authentification tels que l’ID de client, la clé privée et le point de terminaison de l’authentification sont configurés dans les fichiers de configuration de l’instance.

La liste des déclencheurs à traiter est configurée dans une option au format JSON.

Les déclencheurs sont utilisés pour le ciblage par un workflow de campagne qui envoie des emails. La campagne est configurée de sorte qu&#39;un client qui a les deux événements de déclencheur reçoive un email.

## Conditions préalables {#prerequisites}

Avant de commencer cette configuration, vérifiez que vous disposez des éléments suivants :

* Un projet Adobe Developer
* Un ID d’organisation valide - Pour trouver votre ID d’organisation, reportez-vous à la section [cette page](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255){_blank}
* Un accès développeur à votre organisation
* Configuration de déclencheurs valide dans Adobe Analytics

## Fichiers d&#39;authentification et de configuration {#authentication-configuration}

L’authentification est requise, car le pipeline est hébergé dans Adobe Experience Cloud. Une paire de clés publique et privée est utilisée. Ce processus a la même fonction qu’un utilisateur/mot de passe, mais il est plus sécurisé. L’authentification est prise en charge pour le Marketing Cloud via Adobe Developer Project.

## Étape 1 : Créer/mettre à jour votre projet Adobe Developer {#creating-adobe-io-project}

Pour les clients hébergés, travaillez avec votre représentant d’Adobe/l’assistance clientèle pour activer votre organisation avec des jetons de compte Adobe Developer pour l’intégration des Triggers.

Pour les clients On-premise/hybrides, reportez-vous au [Configuration de l’Adobe I/O pour Adobe Experience Cloud Triggers](../../integrations/using/configuring-adobe-io.md) page. Notez que vous devez sélectionner **[!UICONTROL Adobe Analytics]** lors de l’ajout d’une API aux informations d’identification Adobe Developer.

## Étape 2 : configuration de l’option de pipeline {#configuring-nmspipeline}

Une fois l&#39;authentification définie, le pipeline récupère les événements. Il traitera uniquement les déclencheurs configurés dans Adobe Campaign. Le déclencheur doit avoir été généré à partir d’Adobe Analytics et envoyé vers le pipeline qui traitera uniquement les déclencheurs configurés dans Adobe Campaign.

L&#39;option peut également être configurée avec un caractère générique pour capturer tous les déclencheurs, quel que soit leur nom.

1. Dans Adobe Campaign, accédez au menu des options sous **[!UICONTROL Administration]** > **[!UICONTROL Plateforme]** > **[!UICONTROL Options]** dans l&#39;**[!UICONTROL Explorateur.]**

1. Sélectionnez l&#39;option **[!UICONTROL NmsPipeline_Config]**.

1. Dans le champ **[!UICONTROL Valeur (texte long)]**, vous pouvez coller le code JSON suivant, qui spécifie deux déclencheurs. N&#39;oubliez pas de supprimer les commentaires.

   ```json
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

   ```json
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

### Définition du paramètre Consommateur {#consumer-parameter}

Le pipeline fonctionne comme un modèle &quot;fournisseur et consommateur&quot;. Les messages ne sont consommés que pour un utilisateur individuel : chaque consommateur reçoit sa propre copie des messages.

Le paramètre **Consommateur** identifie l&#39;instance comme l&#39;un de ces consommateurs. L&#39;identité de l&#39;instance appelle le pipeline. Vous pouvez le remplir avec le nom de l&#39;instance qui se trouve sur la page Surveillance de la console cliente.

Le service de pipeline effectue le suivi des messages récupérés par chaque consommateur. L&#39;utilisation de différents consommateurs pour différentes instances vous permet de vous assurer que chaque message est envoyé à chaque instance.

### Recommandations relatives à l&#39;option Pipeline {#pipeline-option-recommendation}

Pour configurer l&#39;option Pipeline, vous devez suivre les recommandations suivantes :

* Ajoutez ou modifiez des déclencheurs sous **[!UICONTROL Triggers]**.
* Assurez-vous que le fichier JSON est valide.
* La variable **Nom** correspond à l’identifiant du déclencheur. Un caractère générique &quot;*&quot; capture tous les déclencheurs.
* La variable **Consommation** correspond au nom de l’instance ou de l’application appelante.
* la valeur `pipelined`Le processus prend également en charge la rubrique &quot;alias&quot;.
* Vous devez toujours redémarrer `pipelined`après avoir apporté des modifications.

## Étape 3 : Configuration facultative {#step-optional}

Vous pouvez modifier certains paramètres internes en fonction de vos besoins de charge, mais veillez à les tester avant de les appliquer à votre environnement de production.

La liste des paramètres facultatifs est la suivante :

| Option | Description |
|:-:|:-:|
| appName (hérité) | AppID de l&#39;application OAuth enregistrée dans l&#39;application Legacy Oath où la clé publique a été chargée. Voir à ce propos [cette page](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md) |
| authGatewayEndpoint(hérité) | URL permettant d&#39;obtenir des jetons de passerelle. Par défaut: ```https://api.omniture.com``` |
| authPrivateKey(hérité) | La clé privée, la partie publique téléchargée dans l&#39;application Legacy Oath, AES chiffré avec l&#39;option XtkKey : ```cryptString("PRIVATE_KEY")``` |
| disableAuth(hérité) | La désactivation de l&#39;authentification, la connexion sans jetons de passerelle n&#39;est acceptée que par certains points d’entrée du pipeline de développement. |
| discoverPipelineEndpoint | URL permettant de trouver le point d’entrée de Pipeline Services à utiliser pour ce tenant. Par défaut: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | La période entre deux vidages du processus d&#39;état interne dans ```var/INSTANCE/pipelined.json.``` <br> L&#39;état interne est également accessible à la demande ici : ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | Désactiver la détection de PipelineServicesEndpoint et la forcer |
| monitorServerPort | Le processus en pipeline écoutera sur ce port pour fournir le processus d&#39;état interne ici : ```http://INSTANCE:PORT/pipelined/status```. <br>La valeur par défaut est de 7781 |
| pointerFlushMessageCount | Lorsque ce nombre de messages est traité, les décalages seront enregistrés dans la base de données. <br> La valeur par défaut est de 1000 |
| pointerFlushPeriodSec | Après cette période, les décalages seront enregistrés dans la base de données. <br>La valeur par défaut est de 5 (secondes) |
| processingJSThreads | Nombre de messages de traitement de threads dédiés avec des connecteurs JS personnalisés. <br> La valeur par défaut est de 4 |
| processingThreads | Nombre de messages de traitement de threads dédiés avec code natif. <br>La valeur par défaut est de 4 |
| retryPeriodSec | Délai entre les reprises en cas d&#39;erreurs de traitement. <br>La valeur par défaut est de 30 (secondes) |
| retryValiditySec | Ignorer le message s&#39;il n&#39;est pas traité correctement après cette période (trop de reprises). <br>La valeur par défaut est de 300 (secondes) |

### Démarrage automatique du processus en pipeline {#pipelined-process-autostart}

La variable `pipelined` Le processus doit être démarré automatiquement.

Pour ce faire, définissez la variable `<`pipelined`>` élément dans le fichier de configuration à autostart=&quot;true&quot; :

```sql
 <pipelined autoStart="true" ... "/>
```

### Redémarrage du processus en pipeline {#pipelined-process-restart}

Un redémarrage est nécessaire pour que les modifications soient prises en compte :

```sql
nlserver restart pipelined@instance
```

## Étape 4 : validation {#step-validation}

Pour valider la configuration du pipeline pour l&#39;approvisionnement, procédez comme suit :

* Vérifiez que le processus `pipelined` est en cours d&#39;exécution.
* Vérifiez les `pipelined.log` pour les journaux de connexion de pipeline.
* Vérifiez la connexion et si des pings sont reçus. Les clients hébergés peuvent utiliser le Monitoring depuis la console cliente.
