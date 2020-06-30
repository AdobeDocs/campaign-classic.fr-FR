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
translation-type: tm+mt
source-git-commit: 39d6da007d69f81da959660b24b56ba2558a97ba
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 4%

---


# Configuration du pipeline {#configuring-pipeline}

Les paramètres d’authentification tels que l’ID client, la clé privée et le point de terminaison de l’authentification sont configurés dans les fichiers de configuration de l’instance.
La liste des déclencheurs à traiter est configurée dans une option. Il est au format JSON.
Le déclencheur est traité immédiatement à l’aide du code JavaScript. Il est enregistré dans une table de base de données sans autre traitement en temps réel.
Les déclencheurs sont utilisés pour le ciblage par un processus de campagne qui envoie des courriers électroniques. La campagne est configurée de sorte qu’un client qui a les deux événements déclencheurs reçoive un courrier électronique.

## Prérequis {#prerequisites}

L’utilisation [!DNL Experience Cloud Triggers] de Campaign requiert :

* Adobe Campaign version 6.11 build 8705 ou ultérieure.
* Adobe Analytics Ultimate, Premium, Foundation, OD, Select, Prime, Mobile Apps, Select ou Standard.

Les configurations préalables sont les suivantes :

* Création d&#39;un fichier de clé privée puis création de l&#39;application Auth enregistrée avec cette clé.
* Configuration des déclencheurs dans Adobe Analytics.

La configuration Adobe Analytics n&#39;est pas du ressort de ce document.

L&#39;Adobe Campaign nécessite les informations suivantes de Adobe Analytics :

* Nom de l’application Auth.
* IMSOrgId, identifiant du client Experience Cloud.
* Noms des déclencheurs configurés en Analytics.
* Nom et format des champs de données à rapprocher de la base de données Marketing.

Une partie de cette configuration est un développement personnalisé et requiert les éléments suivants :

* Connaissance de l’analyse JSON, XML et Javascript dans l’Adobe Campaign.
* Connaissance opérationnelle des API QueryDef et Writer.
* Des notions de fonctionnement de cryptage et d&#39;authentification utilisant des clés privées.

>[!NOTE]
>
>Etant donné que la modification du code JS nécessite des compétences techniques, ne la tentez pas sans la bonne compréhension. <br>Les déclencheurs sont enregistrés dans une table de base de données. Les données de déclenchement peuvent donc être utilisées en toute sécurité par les opérateurs marketing dans les workflows de ciblage.

## Fichiers d’authentification et de configuration {#authentication-configuration}

L’authentification est requise, car Pipeline est hébergé dans Adobe Experience Cloud.
Si le serveur Marketing est hébergé sur site, lorsqu’il se connecte à Pipeline, il doit s’authentifier pour disposer d’une connexion sécurisée.
Il utilise une paire de clés publiques et privées. Ce processus fonctionne de la même manière qu’un utilisateur/mot de passe, mais est plus sécurisé.

### IMSOrgId {#imsorgid}

IMSOrgId est l’identifiant du client sur Adobe Experience Cloud.
Définissez-la dans le fichier d’instance serverConf.xml, sous l’attribut IMSOrgId.
Exemple :

```
<redirection IMSOrgId="C5E715(…)98A4@AdobeOrg" (…)
```

### Génération de clés {#key-generation}

La clé est une paire de fichiers. Il est au format RSA et fait 4 096 octets. Il peut être généré avec un outil open source tel qu&#39;OpenSSL. Chaque fois que l’outil est exécuté, une nouvelle clé est générée de manière aléatoire.
Par souci de commodité, les étapes sont énumérées ci-dessous :

* ```openssl genrsa -out <private_key.pem> 4096```

* ```openssl rsa -pubout -in <private_key.pem> -out <public_key.pem>```

Exemple de fichier private_key.pem :

```
----BEGIN RSA PRIVATE KEY----
MIIEowIBAAKCAQEAtqcYzt5WGGABxUJSfe1Xy8sAALrfVuDYURpdgbBEmS3bQMDb
(…)
64+YQDOSNFTKLNbDd+bdAA+JoYwUCkhFyvrILlgvlSBvwAByQ2Lx
----END RSA PRIVATE KEY----
```

Exemple de fichier public_key.pem :

```
----BEGIN PUBLIC KEY----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAtqcYzt5WGGABxUJSfe1X
(…)
EwIDAQAB
----END PUBLIC KEY----
```

>[!NOTE]
>
>Les clés ne doivent pas être générées par PuttyGen, OpenSSL est le meilleur choix.

### Auteur de la création de clients dans Adobe Experience Cloud {#oauth-client-creation}

Une application de type JWT doit être créée en se connectant à Adobe Analytics dans le compte d’organisation approprié sous **[!UICONTROL Admin]** > Gestion **** utilisateur > Application **[!UICONTROL de serment]** héritée.

Procédez comme suit :

1. Sélectionnez le compte **[!UICONTROL de service (assertion JWT)]**.
1. Saisissez le nom **[!UICONTROL de l’]** application.
1. Enregistrez la clé **** publique.
1. Sélectionnez les **[!UICONTROL étendues]** du déclencheur.

   ![](assets/triggers_5.png)

1. Cliquez sur **[!UICONTROL Créer]** et vérifiez le **[!UICONTROL ID de l&#39;application]** et la **[!UICONTROL Clé secrète]** créés.

   ![](assets/triggers_6.png)

### Enregistrement du nom de l’application dans Adobe Campaign Classic {#application-name-registration}

Le ID de l&#39;application du client Auth créé doit être configuré dans Adobe Campaign. Pour ce faire, modifiez le fichier de configuration d’instance dans l’élément en pipeline, en particulier l’attribut appName.

Exemple :

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Chiffrement de clé {#key-encription}

Pour être utilisée par pipelin, la clé privée doit être chiffrée. Le chiffrement est effectué à l’aide de la fonction JavaScript cryptString et doit être exécuté sur la même instance que pipelin.

Un exemple de chiffrement de clé privée avec JavaScript est disponible dans cette [page](../../integrations/using/pipeline-troubleshooting.md).

La clé privée chiffrée doit être enregistrée dans l&#39;Adobe Campaign. Pour ce faire, modifiez le fichier de configuration d’instance dans l’élément en pipeline, en particulier l’attribut authPrivateKey.

Exemple :

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### début automatique du processus en pipelines {#pipelined-auto-start}

Le processus en pipeline doit être démarré automatiquement.
Pour ce faire, définissez l’élément du fichier de configuration sur autostart=&quot;true&quot; :

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Redémarrage du processus en pipeline {#pipelined-restart}

Il peut également être démarré manuellement à l’aide de la ligne de commande :

```
nlserver start pipelined@instance
```

Un redémarrage est nécessaire pour que les modifications prennent effet :

```
nlserver restart pipelined@instance
```

En cas d’erreur, recherchez des erreurs sur la sortie standard (si vous avez démarré manuellement) ou dans le fichier journal en pipeline. Consultez la section Résolution des problèmes de ce document pour plus d&#39;informations sur la résolution des problèmes.

### Options de configuration des pipelines {#pipelined-configuration-options}

| Option | Description |
|:-:|:-:|
| appName | ID de l&#39;application OAuth (ID de l&#39;application) enregistrée dans Adobe Analytics (où la clé publique a été téléchargée) : Admin > Gestion utilisateur > Application de serment héritée. Refer to this [section](../../integrations/using/configuring-pipeline.md#oauth-client-creation). |
| authGatewayEndpoint | URL permettant d’obtenir des &quot;jetons de passerelle&quot;. <br> Par défaut : https://api.omniture.com |
| authPrivateKey | Clé privée (partie publique téléchargée dans Adobe Analytics (voir cette section). AES crypté avec l&#39;option XtkSecretKey : xtk.session.EncryptPassword(&quot;PRIVATE_KEY&quot;); |
| disableAuth | Désactiver l&#39;authentification (la connexion sans jetons de passerelle n&#39;est acceptée que par certains points de terminaison du pipeline de développement) |
| discoverPipelineEndpoint | URL permettant de découvrir le point de terminaison Pipeline Services à utiliser pour ce client. Par défaut : https://producer-pipeline-pnw.adobe.net |
| dumpStatePeriodSec | Période comprise entre 2 vidages de l’état interne du processus dans var/INSTANCE/pipelined.json L’état interne est également accessible à la demande à l’adresse http://INSTANCE/pipelined/status (port 7781). |
| forcedPipelineEndpoint | Désactiver la découverte du point de terminaison PipelineServices et la forcer |
| monitorServerPort | Le processus en pipeline écoute sur ce port pour fournir l’état interne du processus à l’adresse http://INSTANCE/pipelined/status (port 7781). |
| pointerFlushMessageCount | Lorsque ce nombre de messages est traité, les décalages sont enregistrés dans la base de données. La valeur par défaut est 1 000 |
| pointerFlushPeriodSec | Après cette période, les décalages seront enregistrés dans la base de données. La valeur par défaut est 5 (secondes) |
| processingJSThreads | Nombre de messages de traitement de threads dédiés avec des connecteurs JS personnalisés. Par défaut : 4 |
| processingThreads | Nombre de messages de traitement de threads dédiés avec du code intégré. Par défaut : 4 |
| retryPeriodSec | Délai entre les Reprises (en cas d’erreurs de traitement). La valeur par défaut est 30 (s) |
| retryValiditySec | Ignorer le message s’il n’est pas traité correctement après cette période (trop de Reprises). La valeur par défaut est 300 (s) |
