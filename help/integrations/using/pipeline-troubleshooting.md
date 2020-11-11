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
translation-type: ht
source-git-commit: 3e73d7c91fbe7cff7e1e31bdd788acece5806e61
workflow-type: ht
source-wordcount: '587'
ht-degree: 100%

---


# Dépannage du pipeline {#pipeline-troubleshooting}

**Échec du pipeline avec l&#39;erreur &#39;&#39;Aucune tâche ne correspond au masque pipelined@&lt; instance >&quot;**

Votre version d’Adobe Campaign Classic ne prend pas en charge le pipeline.

1. Vérifiez si l’élément [!DNL pipelined] se trouve dans le fichier de configuration. Si ce n’est pas le cas, cela signifie qu’il n’est pas pris en charge.
1. Effectuez la mise à niveau vers la version 6.11 build 8705 ou ultérieure.

**Échec du pipeline avec « aurait dû commencer par `[` ou `{` (iRc=16384) »**

L’option **NmsPipeline_Config** n’est pas définie. Il s’agit en fait d’une erreur d’analyse JSON.
Définissez la configuration JSON dans l’option **NmsPipeline_Config**. Voir « Option de routage » dans cette page.

**Échec du pipeline avec « le sujet doit être une organisation ou un client valide »**

La configuration IMSOrgid n’est pas valide.

1. Vérifiez que l’IMSOrgId est défini dans le fichier serverConf.xml.
1. Recherchez un IMSOrgId vide dans le fichier de configuration de l’instance qui peut remplacer le paramètre par défaut. Si vous en trouvez un, supprimez-le.
1. Vérifiez que l’IMSOrgId correspond à celui du client dans Experience Cloud.

**Échec du pipeline avec « clé non valide »**

Le paramètre @authPrivateKey du fichier de configuration de l’instance est incorrect.

1. Vérifiez qu’authPrivateKey est défini.
1. Vérifiez qu’authPrivateKey commence par @, se termine par = et comporte environ 4 000 caractères.
1. Recherchez la clé d’origine et vérifiez qu’elle est au format RSA, fait 4 096 bits de long, et commence par -----BEGIN RSA PRIVATE KEY-----.
   <br> Si nécessaire, recréez la clé et enregistrez-la sur Adobe Analytics.
1. Vérifiez que la clé a été codée dans la même instance que [!DNL pipelined]. <br>Si nécessaire, recommencez le codage à l’aide de l’exemple JavaScript ou de workflow.

**Échec du pipeline avec « impossible de lire le jeton durant l’authentification »**

Le format de la clé privée n’est pas valide.

1. Exécutez les étapes de cryptage de clé sur cette page.
1. Vérifiez que la clé est cryptée sur la même instance.
1. Vérifiez que l’authPrivateKey du fichier de configuration correspond à la clé générée. <br>Veillez à utiliser OpenSSL pour générer la paire de clés. Par exemple, PuttyGen ne génère pas le format approprié.

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
Annexes
