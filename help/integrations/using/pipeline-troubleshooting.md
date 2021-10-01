---
product: campaign
title: Configuration de l'intégration
description: Configuration de l'intégration
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: ht
source-wordcount: '694'
ht-degree: 100%

---

# Dépannage du pipeline {#pipeline-troubleshooting}

![](../../assets/common.svg)

**Échec du pipeline avec l&#39;erreur &#39;&#39;Aucune tâche ne correspond au masque pipelined@&lt; instance >&quot;**

Votre version d’Adobe Campaign Classic ne prend pas en charge le pipeline.

1. Vérifiez si l’élément [!DNL pipelined] se trouve dans le fichier de configuration. Si ce n’est pas le cas, cela signifie qu’il n’est pas pris en charge.
1. Effectuez une mise à niveau vers Campaign 20.3 ou la version [!DNL Gold Standard] 11.

**Échec du pipeline avec « aurait dû commencer par `[` ou `{` (iRc=16384) »**

L’option **NmsPipeline_Config** n’est pas définie. Il s’agit en fait d’une erreur d’analyse JSON.
Définissez la configuration JSON dans l’option **NmsPipeline_Config**. Voir « Option de routage » dans cette page.

**Échec du pipeline avec « le sujet doit être une organisation ou un client valide »**

La configuration de l&#39;identifiant de l&#39;organisation n&#39;est pas valide.

1. Vérifiez que l’IMSOrgId est défini dans le fichier serverConf.xml.
1. Recherchez un IMSOrgId vide dans le fichier de configuration de l’instance qui peut remplacer le paramètre par défaut. Si vous en trouvez un, supprimez-le.
1. Vérifiez que l’IMSOrgId correspond à celui du client dans Experience Cloud.

**Échec du pipeline avec « clé non valide »**

Le paramètre @authPrivateKey du fichier de configuration de l’instance est incorrect.

1. Vérifiez qu’authPrivateKey est défini.
1. Vérifiez qu’authPrivateKey commence par @, se termine par = et comporte environ 4 000 caractères.
1. Recherchez la clé d’origine et vérifiez qu’elle est au format RSA, fait 4 096 bits de long, et commence par `-----BEGIN RSA PRIVATE KEY-----`.
   <br> Si nécessaire, recréez la clé et enregistrez-la sur Adobe Analytics.
1. Vérifiez que la clé a été codée dans la même instance que [!DNL pipelined]. <br>Si nécessaire, recommencez le codage à l’aide de l’exemple JavaScript ou de workflow.

**Échec du pipeline avec « impossible de lire le jeton durant l’authentification »**

Le format de la clé privée n’est pas valide.

1. Exécutez les étapes de cryptage de clé sur cette page.
1. Vérifiez que la clé est cryptée sur la même instance.
1. Vérifiez que l’authPrivateKey du fichier de configuration correspond à la clé générée. <br>Veillez à utiliser OpenSSL pour générer la paire de clés. Par exemple, PuttyGen ne génère pas le format approprié.

**Échec du pipeline avec &quot;n&#39;est plus autorisé à récupérer le jeton d&#39;accès&quot;**

Les logs doivent être les suivants :

```
2021-05-31T08:42:18.124Z        66462   66501   1       error   log     Listener: JWT Token is empty. (iRc=16384)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     Unknown authentication mode: 'Bearer realm="Adobe Analytics"'. (iRc=-55)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     BAS-010007 Function not implemented (iRc=-55)
2021-05-31T08:42:48.582Z        66462   66501   1       warning log     Connection seems to have been lost. Attempting to reconnect.
2021-05-31T08:43:09.156Z        66462   66501   1       error   log     INT-150012 The HTTP query returned a 'Forbidden' type error (403) (iRc=-53)
2021-05-31T08:43:09.160Z        66462   66501   1       error   log     Error while authenticating: '{"error":"This client: df73c224e5-triggers-test is no longer allowed to get access token."}' (iRc=16384)
```

Ce message d&#39;erreur signifie que l&#39;authentification est configurée à l&#39;aide de l&#39;ancienne base Omniture OAuth. Consultez la documentation [Configuration d&#39;Adobe I/O pour les Triggers Adobe Experience Cloud](../../integrations/using/configuring-adobe-io.md) pour mettre à niveau votre authentification.

**Aucun déclencheur n’est récupéré**

Lorsque le processus [!DNL pipelined] est en cours d’exécution et qu’aucun déclencheur n’est récupéré :

1. Vérifiez que le déclencheur est actif dans Analytics et qu’il génère des événements.
1. Vérifiez que le processus [!DNL pipelined] est en cours d’exécution.
1. Recherchez des erreurs dans le log [!DNL pipelined].
1. Recherchez des erreurs dans la page d’état [!DNL pipelined]. Le nombre d’indicateurs trigger-discarted, trigger-failures doit être nul.
1. Vérifiez que le nom du déclencheur est configuré dans l’option **[!UICONTROL NmsPipeline_Config]**. En cas de doute, utilisez l’option de caractère générique.
1. Vérifiez qu’Analytics possède un déclencheur actif et qu’il génère des événements. Il peut y avoir un délai de quelques heures après la configuration dans Analytics.

**Les événements ne sont pas liés à un client**

Lorsque certains événements ne sont pas liés à un client :

1. Vérifiez que le workflow de réconciliation est en cours d’exécution, le cas échéant.
1. Vérifiez que l’événement contient un identifiant client.
1. Effectuez une requête sur la table client à l’aide de l’identifiant client.
1. Vérifiez la fréquence de l’import client. Les nouveaux clients sont importés dans Adobe Campaign avec un workflow.

**Latence du traitement des événements**

Lorsque l’horodatage Analytics est beaucoup plus ancien que la date de création de l’événement dans Campaign.

En règle générale, un déclencheur peut prendre 15 à 90 minutes pour lancer une campagne marketing. Ce délai varie en fonction de l’implémentation de la collecte de données, de la charge sur le pipeline, de la configuration personnalisée du déclencheur défini et du workflow dans Adobe Campaign.

1. Vérifiez si le processus [!DNL pipelined] a été exécuté.
1. Recherchez des erreurs dans pipelined.log susceptibles de provoquer des reprises. Corrigez les erreurs, le cas échéant.
1. Vérifiez la taille de la file d’attente dans la page d’état [!DNL pipelined]. Si la taille de la file d’attente est importante, améliorez les performances de JS.
1. Comme le retard semble augmenter avec le volume, configurez les déclencheurs sur Analytics en utilisant moins de messages.

**Mise à niveau des instances d&#39;évaluation de l&#39;authentification héritée vers l&#39;authentification d’Adobe IO**

La modification de l&#39;authentification de l&#39;intégration sur votre instance d&#39;évaluation n&#39;affecte pas la configuration de votre instance de production. Vous pouvez choisir de mettre à niveau votre instance d&#39;évaluation, puis de mettre à jour l&#39;authentification pour Adobe IO et tester vos triggers sur votre instance d&#39;évaluation.

Votre instance de production continuera à utiliser l&#39;authentification héritée et ne sera pas affectée par cette modification.
