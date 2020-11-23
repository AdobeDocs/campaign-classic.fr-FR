---
solution: Campaign Classic
product: campaign
title: Configuration du pipeline
description: Découvrez comment configurer le pipeline
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 84%

---


# Configuration du pipeline {#configuring-pipeline}

Les paramètres d&#39;authentification tels que l&#39;identifiant client, la clé privée et le point d&#39;entrée de l&#39;authentification sont configurés dans les fichiers de configuration de l&#39;instance.
La liste des déclencheurs à traiter est configurée dans une option au format JSON.
Les déclencheurs sont utilisés pour le ciblage par un workflow de campagne qui envoie des emails. La campagne est configurée de sorte qu&#39;un client qui a les deux événements de déclencheur reçoive un email.

>[!CAUTION]
>
>Dans le cas d&#39;un déploiement hybride, vérifiez que le pipeline est configuré sur une instance mid-sourcing.

## Prérequis {#prerequisites}

Avant de démarrer cette configuration, vérifiez que vous utilisez :

* Version minimale d’Adobe Campaign 20.3
* Version de Adobe Analytics Standard

Vous aurez également besoin de :

* Authentification du projet d&#39;E/S Adobe
* un IMSOrgID valide, l&#39;identifiant du client Experience Cloud avec Adobe Analytics ajouté
* a Accès des développeurs à l&#39;organisation IMS
* configuration des déclencheurs effectuée en Adobe Analytics

## Fichiers d&#39;authentification et de configuration {#authentication-configuration}

L&#39;authentification est requise, car le pipeline est hébergé dans Adobe Experience Cloud.
Une paire de clés publique et privée est utilisée. Ce processus fonctionne de la même manière qu&#39;un nom d&#39;utilisateur/mot de passe, mais il est plus sécurisé.
L&#39;authentification est prise en charge pour le Marketing Cloud via le projet d&#39;E/S d&#39;Adobe.

## Étape 1 : Création/mise à jour d&#39;un projet d&#39;E/S d&#39;Adobe {#creating-adobe-io-project}

Pour les clients hébergés, vous pouvez créer un ticket d&#39;assistance clientèle pour permettre à votre entreprise d&#39;utiliser des jetons de compte technique d&#39;E/S d&#39;Adobe pour l&#39;intégration des déclencheurs.

For On Premise customers, refer to the [Configuring Adobe I/O for Adobe Experience Cloud Triggers](../../integrations/using/configuring-adobe-io.md) page. Note that you need to select **[!UICONTROL Adobe Analytics]** while adding API to the Adobe I/O credential.

## Étape 2 : configuration de l&#39;option de pipeline NmsPipeline_Config {#configuring-nmspipeline}

Une fois l&#39;authentification définie, le pipeline récupère les événements. Il traitera uniquement les déclencheurs configurés dans Adobe Campaign. Le déclencheur doit avoir été généré à partir d&#39;Adobe Analytics et envoyé vers le pipeline qui traitera uniquement les déclencheurs configurés dans Adobe Campaign.
L&#39;option peut également être configurée avec un caractère générique pour capturer tous les déclencheurs, quel que soit leur nom.

1. Dans Adobe Campaign, accédez au menu des options sous **[!UICONTROL Administration]** > **[!UICONTROL Plateforme]** > **[!UICONTROL Options]** dans l&#39;**[!UICONTROL Explorateur.]**

1. Sélectionnez l&#39;option **[!UICONTROL NmsPipeline_Config]**.

1. Dans le champ **[!UICONTROL Valeur (texte long)]**, vous pouvez coller le code JSON suivant, qui spécifie deux déclencheurs. N&#39;oubliez pas de supprimer les commentaires.

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

### Le paramètre Consommateur {#consumer-parameter}

Le pipeline fonctionne comme un modèle &quot;fournisseur et consommateur&quot;. Les messages ne sont consommés que pour un utilisateur individuel : chaque consommateur reçoit sa propre copie des messages.

Le paramètre **Consommateur** identifie l&#39;instance comme l&#39;un de ces consommateurs. L&#39;identité de l&#39;instance appelle le pipeline. Vous pouvez le remplir avec le nom de l&#39;instance qui se trouve sur la page Surveillance de la console cliente.

Le service de pipeline effectue le suivi des messages récupérés par chaque consommateur. L&#39;utilisation de différents consommateurs pour différentes instances vous permet de vous assurer que chaque message est envoyé à chaque instance.

### Recommandations relatives à l&#39;option Pipeline {#pipeline-option-recommendation}

Pour configurer l&#39;option Pipeline, vous devez suivre les recommandations suivantes :

* Ajoutez ou modifiez les déclencheurs sous **[!UICONTROL Déclencheurs]**, sans modifier le reste.
* Assurez-vous que le fichier JSON est valide. Vous pouvez utiliser un programme de validation JSON. Reportez-vous à ce [site Web](http://jsonlint.com/), par exemple.
* &quot;name&quot; correspond à l&#39;ID du déclencheur. Un caractère générique &quot;*&quot; capture tous les déclencheurs.
* &quot;Consommateur&quot; correspond au nom de l&#39;instance ou de l&#39;application appelante.
* Le pipeline prend également en charge la rubrique &quot;alias&quot;.
* Vous devez toujours redémarrer en pipeline après avoir apporté des modifications.

## Étape 3 : Configuration facultative {#step-optional}

Vous pouvez modifier certains paramètres internes en fonction de vos besoins de charge, mais veillez à les tester avant de les mettre en production.

La liste des paramètres facultatifs se trouve ci-dessous :

| Option | Description |
|:-:|:-:|
| appName(Hérité) | AppID de l&#39;application OAuth enregistrée dans l&#39;application Legacy Oath où la clé publique a été chargée. Voir à ce propos [cette page](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md.) |
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

Le processus en pipeline doit être démarré automatiquement.

Pour ce faire, définissez l&#39;élément &lt; pipelined > dans le fichier de configuration sur autostart=&quot;true&quot; :

```
 <pipelined autoStart="true" ... "/>
```

### Redémarrage du processus en pipeline {#pipelined-process-restart}

Un redémarrage est nécessaire pour que les modifications soient prises en compte :

```
nlserver restart pipelined@instance
```

## Étape 4 : validation {#step-validation}

Pour valider la configuration du pipeline pour l&#39;approvisionnement, procédez comme suit :

* Vérifiez que le processus [!DNL pipelined] est en cours d&#39;exécution.
* Recherchez les logs de connexion du pipeline dans le fichier pipeline.log.
* Vérifiez la connexion et si des pings sont reçus. Les clients hébergés peuvent utiliser le Monitoring depuis la console cliente.
