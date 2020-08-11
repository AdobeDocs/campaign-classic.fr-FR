---
title: Configuration de l'intégration
seo-title: Configuration de l'intégration
description: Configuration de l'intégration
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 0112d5bd052ad66169225073276d1da4f3c245d8
workflow-type: ht
source-wordcount: '937'
ht-degree: 100%

---


# Configuration du pipeline {#configuring-pipeline}

Les paramètres d’authentification tels que l’identifiant client, la clé privée et le point d’entrée de l’authentification sont configurés dans les fichiers de configuration de l’instance.
La liste des déclencheurs à traiter est configurée dans une option. Celle-ci est au format JSON.
Le déclencheur est traité immédiatement à l’aide du code JavaScript. Il est enregistré dans une table de base de données sans autre traitement en temps réel.
Les déclencheurs sont utilisés pour le ciblage par un workflow de campagne qui envoie des emails. La campagne est configurée de sorte qu’un client qui a les deux événements de déclencheur reçoive un email.

## Prérequis {#prerequisites}

L’utilisation de [!DNL Experience Cloud Triggers] dans Campaign requiert :

* Adobe Campaign version 6.11 build 8705 ou ultérieure.
* Adobe Analytics Ultimate, Premium, Foundation, OD, Select, Prime, Mobile Apps, Select ou Standard.

Les configurations préalables requises sont les suivantes :

* Création d’un fichier de clé privée puis création de l’application oAuth enregistrée avec cette clé
* Configuration des déclencheurs dans Adobe Analytics

La configuration d’Adobe Analytics n’entre pas dans le cadre de ce document.

Adobe Campaign nécessite les informations suivantes d’Adobe Analytics :

* le nom de l’application oAuth,
* l’IMSOrgId, c’est-à-dire l’identifiant du client Experience Cloud,
* les noms des déclencheurs configurés dans Analytics,
* le nom et le format des champs de données à réconcilier avec la base de données Marketing.

Une partie de cette configuration est un travail de développement personnalisé qui requiert les connaissances suivantes :

* connaissances opérationnelles de l’analyse JSON, XML et Javascript dans Adobe Campaign,
* connaissances opérationnelles des API QueryDef et Writer,
* notions de cryptage et d&#39;authentification à l’aide de clés privées.

>[!NOTE]
>
>Étant donné que la modification du code JS nécessite des compétences techniques, ne le modifiez pas si vous ne le maîtrisez pas. <br>Les déclencheurs sont enregistrés dans une table de base de données. Les données de déclenchement peuvent donc être utilisées en toute sécurité par les opérateurs marketing dans les workflows de ciblage.

## Fichiers d’authentification et de configuration {#authentication-configuration}

L’authentification est requise, car Pipeline est hébergé dans Adobe Experience Cloud.
Si le serveur Marketing est hébergé on-premise, il doit s’authentifier lorsqu’il se connecte à Pipeline pour que la connexion soit sécurisée.
Une paire de clés publique et privée est utilisée. Ce processus fonctionne de la même manière qu’un nom d’utilisateur/mot de passe, mais il est plus sécurisé.

### IMSOrgId {#imsorgid}

L’IMSOrgId est l’identifiant du client sur Adobe Experience Cloud.
Définissez-le dans le fichier serverConf.xml de l’instance, sous l’attribut IMSOrgId.
Exemple :

```
<redirection IMSOrgId="C5E715(…)98A4@AdobeOrg" (…)
```

### Génération de clés {#key-generation}

La clé est une paire de fichiers. Elle est au format RSA et fait 4 096 octets. Elle peut être générée avec un outil open source tel qu&#39;OpenSSL. Chaque fois que l’outil est exécuté, une nouvelle clé est générée de manière aléatoire.
Par souci de commodité, les étapes sont répertoriées ci-dessous :

* ```openssl genrsa -out <private_key.pem> 4096```

* ```openssl rsa -pubout -in <private_key.pem> -out <public_key.pem>```

Exemple de fichier private_key.pem :

```
----BEGIN RSA PRIVATE KEY----
MIIEowIBAAKCAQEAtqcYzt5WGGABxUJSfe1Xy8sAALrfVuDYURpdgbBEmS3bQMDb
(…)
64+YQDOSNFTKLNbDd+bdAA+JoYwUCkhFyvrILlgvlSBvwAByQ2Lx
----END RSA PRIVATE KEY----
```

Exemple de fichier public_key.pem :

```
----BEGIN PUBLIC KEY----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAtqcYzt5WGGABxUJSfe1X
(…)
EwIDAQAB
----END PUBLIC KEY----
```

>[!NOTE]
>
>Les clés ne doivent pas être générées par PuttyGen. OpenSSL est la meilleure solution.

### Création d’un client oAuth dans Adobe Experience Cloud {#oauth-client-creation}

Une application de type JWT doit être créée en se connectant à Adobe Analytics dans le compte d’organisation approprié (**[!UICONTROL Admin]** > **[!UICONTROL User Management]** > **[!UICONTROL Application Oath héritée]**).

Procédez comme suit :

1. Sélectionnez le **[!UICONTROL Compte de service (assertion JWT)]**.
1. Saisissez le **[!UICONTROL Nom de l’application]**.
1. Enregistrez la **[!UICONTROL Clé publique]**.
1. Sélectionnez les **[!UICONTROL Portées]** du déclencheur.

   ![](assets/triggers_5.png)

1. Cliquez sur **[!UICONTROL Créer]** et vérifiez l’**[!UICONTROL ID de l’application]** et la **[!UICONTROL Clé secrète]** créés.

   ![](assets/triggers_6.png)

### Enregistrement du nom de l’application dans Adobe Campaign Classic {#application-name-registration}

L’ID de l’application du client oAuth créé doit être configuré dans Adobe Campaign. Pour ce faire, modifiez le fichier de configuration de l’instance dans l’élément [!DNL pipelined], en particulier l’attribut appName.

Exemple :

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Cryptage de la clé {#key-encription}

Pour être utilisée par [!DNL pipelined], la clé privée doit être cryptée. Le cryptage est effectué à l’aide de la fonction JavaScript cryptString et doit être réalisé sur la même instance que [!DNL pipelined].

Un exemple de cryptage de clé privée avec JavaScript est disponible dans cette [page](../../integrations/using/pipeline-troubleshooting.md).

La clé privée cryptée doit être enregistrée dans Adobe Campaign. Pour cela, modifiez le fichier de configuration de l’instance dans l’élément [!DNL pipelined], en particulier l’attribut authPrivateKey.

Exemple :

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Démarrage automatique du processus en pipeline {#pipelined-auto-start}

Le processus [!DNL pipelined] doit être démarré automatiquement.
Pour cela, définissez l’élément du fichier de configuration sur autostart=&quot;true&quot; :

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Redémarrage du processus en pipeline {#pipelined-restart}

Il peut également être démarré manuellement à l’aide de la ligne de commande :

```
nlserver start pipelined@instance
```

Un redémarrage est nécessaire pour que les modifications soient prises en compte :

```
nlserver restart pipelined@instance
```

En cas de problème, recherchez les erreurs dans la sortie standard (si vous avez démarré manuellement) ou dans le log [!DNL pipelined]. Consultez la section Résolution des problèmes de ce document pour plus d’informations sur la résolution des problèmes.

### Options de configuration en pipeline {#pipelined-configuration-options}

| Option | Description |
|:-:|:-:|
| appName | ID de l’application OAuth (ID de l’application) enregistré dans Adobe Analytics (où la clé publique a été téléchargée) : Admin > User Management > Application Oath héritée. Consultez cette [section](../../integrations/using/configuring-pipeline.md#oauth-client-creation). |
| authGatewayEndpoint | URL permettant d’obtenir des « jetons de passerelle ». <br> Par défaut : https://api.omniture.com |
| authPrivateKey | Clé privée (partie publique téléchargée dans Adobe Analytics (voir cette section). Cryptage AES avec l’option XtkSecretKey : xtk.session.EncryptPassword(&quot;PRIVATE_KEY&quot;); |
| disableAuth | Désactivation de l’authentification (la connexion sans jetons de passerelle n’est acceptée que par certains points d’entrée du pipeline de développement) |
| discoverPipelineEndpoint | URL permettant de découvrir le point d’entrée de Pipeline Services à utiliser pour ce tenant. Par défaut : https://producer-pipeline-pnw.adobe.net |
| dumpStatePeriodSec | Période comprise entre 2 sauvegardes de l’état interne du processus dans var/INSTANCE/pipelined.json L’état interne est également accessible sur demande à l’adresse http://INSTANCE/pipelined/status (port 7781). |
| forcedPipelineEndpoint | Désactivation de la découverte de PipelineServicesEndpoint et la forcer |
| monitorServerPort | Le processus [!DNL pipelined] écoute sur ce port pour fournir l’état interne du processus à l’adresse http://INSTANCE/pipelined/status (port 7781). |
| pointerFlushMessageCount | Lorsque ce nombre de messages est traité, les décalages sont enregistrés dans la base de données. La valeur par défaut est de 1 000 |
| pointerFlushPeriodSec | Après cette période, les décalages seront enregistrés dans la base de données. La valeur par défaut est de 5 (secondes) |
| processingJSThreads | Nombre de messages de traitement de threads dédiés avec des connecteurs JS personnalisés. La valeur par défaut est de 4 |
| processingThreads | Nombre de messages de traitement de threads dédiés avec code natif. La valeur par défaut est de 4 |
| retryPeriodSec | Délai entre les reprises (en cas d’erreurs de traitement). La valeur par défaut est de 30 (secondes) |
| retryValiditySec | Ignorer le message s’il n’est pas traité correctement après cette période (trop de reprises). La valeur par défaut est de 300 (secondes) |
