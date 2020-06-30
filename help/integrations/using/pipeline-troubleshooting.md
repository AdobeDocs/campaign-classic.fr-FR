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
source-wordcount: '652'
ht-degree: 2%

---


# Dépannage du pipeline {#pipeline-troubleshooting}

**Échec de Pipelin avec l&#39;erreur &quot;Aucune tâche ne correspond au masque pipelin@&quot;**

Votre version d’Adobe Campaign Classic ne prend pas en charge le pipeline.

1. Vérifiez si l’élément en pipeline est présent dans le fichier de configuration. Si ce n&#39;est pas le cas, cela signifie qu&#39;il n&#39;est pas pris en charge.
1. Effectuez la mise à niveau vers la version 6.11 de la version 8705 ou ultérieure.

**Pipelin échoue avec &quot; par &quot;[&#39; ou &#39;{&quot; (iRc=16384)&quot;**

L&#39;option **NmsPipeline_Config** n&#39;est pas définie. C&#39;est en fait une erreur d&#39;analyse JSON.
Définissez la configuration JSON dans l’option **NmsPipeline_Config**. Voir &quot;Option de routage&quot; dans cette page.

**Pipelin échoue avec &quot;le sujet doit être une organisation ou un client valide&quot;**

La configuration IMSOrgid n&#39;est pas valide.

1. Vérifiez que l’IMSOrgId est défini dans le fichier serverConf.xml.
1. Recherchez un IMSOrgId vide dans le fichier de configuration de l’instance qui peut remplacer le paramètre par défaut. Si tel est le cas, supprimez-le.
1. Vérifiez que l’IMSOrgId correspond à celui du client dans l’Experience Cloud.

**Échec de Pipelin avec &quot;key non valide&quot;**

Le paramètre @authPrivateKey du fichier de configuration de l&#39;instance est incorrect.

1. Vérifiez que authPrivateKey est défini.
1. Vérifiez que authPrivateKey : débuts avec @, se termine par = et comporte environ 4 000 caractères.
1. Recherchez la clé d’origine et vérifiez qu’elle est : au format RSA, 4096 bits de long, et débuts avec —BEGIN RSA PRIVATE KEY—.
   <br> Si nécessaire, recréez la clé et enregistrez-la sur Adobe Analytics. Consultez cette [section](../../integrations/using/configuring-pipeline.md#oauth-client-creation).
1. Vérifiez que la clé a été codée au sein de la même instance que la clé en pipeline. <br>Si nécessaire, recommencez le codage à l’aide de l’exemple de code JavaScript ou de flux de travaux.

**Pipelin ne parvient pas à &quot;lire le jeton pendant l&#39;authentification&quot;.**

Le format de la clé privée n&#39;est pas valide.

1. Exécutez les étapes de chiffrement de clé sur cette page.
1. Vérifiez que la clé est chiffrée sur la même instance.
1. Vérifiez que l’authPrivateKey du fichier de configuration correspond à la clé générée. <br>Veillez à utiliser OpenSSL pour générer la paire de clés. Par exemple, PuttyGen ne génère pas le format approprié.

**Aucun déclencheur n&#39;est récupéré**

Lorsque le processus en pipeline est en cours d’exécution et qu’aucun déclencheur n’est récupéré :

1. Assurez-vous que le déclencheur est actif en Analytics et qu’il génère des événements.
1. Assurez-vous que le processus en pipeline est en cours d’exécution.
1. Recherchez des erreurs dans le journal en pipeline.
1. Recherchez des erreurs dans la page d’état de l’oléoduc. trigger-discarted, trigger-failure doit être nul.
1. Vérifiez que le nom du déclencheur est configuré dans l&#39;option **[!UICONTROL NmsPipeline_Config]** . En cas de doute, utilisez l’option générique.
1. Vérifiez que Analytics possède un déclencheur actif et génère des événements. Il peut y avoir un délai de quelques heures après que la configuration a été effectuée en Analytics avant d&#39;être active.

**Les Événements ne sont pas liés à un client**

Lorsque certains événements ne sont pas liés à un client :

1. Vérifiez que le processus de rapprochement est en cours d’exécution, le cas échéant.
1. Vérifiez que le événement contient un ID de client.
1. Effectuez une requête sur la table du client à l’aide de l’ID de client.
1. Vérifiez la fréquence de l&#39;importation du client. Les nouveaux clients sont importés dans l’Adobe Campaign avec un processus.

**Latence du traitement des événements**

Lorsque l’horodatage Analytics est beaucoup plus ancien que la date de création du événement à Campaign.

En règle générale, un déclencheur peut prendre de 15 à 90 minutes pour lancer une campagne marketing. Cela varie en fonction de l’implémentation de la collecte de données, de la charge sur le pipeline, de la configuration personnalisée du déclencheur défini et du processus dans l’Adobe Campaign.

1. Vérifiez si le processus en pipeline est en cours d’exécution.
1. Recherchez des erreurs dans pipeline.log susceptibles de provoquer des Reprises. Corrigez les erreurs, le cas échéant.
1. Vérifiez la taille de la file d&#39;attente dans la page d&#39;état en pipeline. Si la taille de la file d’attente est importante, améliorez les performances de JS.
1. Comme un délai semble augmenter avec le volume, configurez les déclencheurs sur Analytics en utilisant moins de messages.
Annexes

**Utilisation du code JavaScript de chiffrement de clé**

Exécutez un script JavaScript pour chiffrer la clé privée. Elle est requise pour la configuration du pipeline.

Voici un exemple de code que vous pouvez utiliser pour exécuter la fonction cryptString :

```
/*
USAGE:
  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
*/
 
function usage()
{
  return "USAGE:\n" +
    '  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js\n'
}
 
var fn = application.arg;
if( fn == "" )
  logError("Missing key file file\n" + usage());
 
//open the pem file
plaintext = loadFile(fn)
 
if( !plaintext.match(/^-----BEGIN RSA PRIVATE KEY-----/) )
  logError("File should be an rsa private key")
 
logInfo("Encrypted key:\n" + cryptString(plaintext, <xtkSecretKey>))
```

Sur le serveur, exécutez le script Javascript :

```
nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
```

Copiez et collez la clé codée de la sortie vers la console.