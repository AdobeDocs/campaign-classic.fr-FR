---
product: campaign
title: Note technique - Activation de Microsoft Edge Chromium dans votre environnement Campaign
description: Campaign - Edge Chromium
hide: true
hidefromtoc: true
source-git-commit: d9f57d4e5b6f880907040344ece40546456a2321
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 17%

---


# Comment activer Microsoft Edge Chromium dans votre environnement {#edge-conf}

![](../../assets/v7-only.svg)


## Qu’est-ce qui a changé ?

Après la fin de vie de Microsoft Internet Explorer 11, le moteur de rendu de HTML pour Adobe Services (page de connexion) dans la console cliente utilise désormais Microsoft Edge Chromium, à partir de Campaign Classic v7.3.

Outre l’installation du runtime Microsoft Edge Webview 2, qui est désormais [requis pour toute installation de console cliente](../../installation/using/installing-the-client-console.md#webview), Microsoft Edge Chromium doit être activé sur votre ou vos instances.

## Cela vous concerne-t-il ?

Si votre environnement a été mis à niveau vers Campaign Classic v7.3 (ou version ultérieure), vous êtes affecté.

## Comment effectuer la mise à jour ?

* Comme **hébergé** client, Adobe a déjà activé Microsoft Edge Chromium sur vos instances.

* En tant que **on-premise/hybride** client, vous devez activer Microsoft Edge Chromium sur vos instances.

   Lors de la mise à niveau vers Campaign Classic v7.3 (et versions ultérieures), une nouvelle `webView2Mode` est disponible dans le fichier de configuration du serveur Campaign. `serverConf.xml`. Cet attribut doit être activé.

   Pour ce faire, respectez les étapes suivantes sur tous vos environnements (MKT, MID, RT) :

   1. Editez le fichier de configuration du serveur Campaign (`serverConf.xml`)
   1. Dans le `<web>` module, définir `webView2Mode = "1"`
   1. Recharger la configuration du serveur

      ```
      nlserver config -reload
      ```

   1. Redémarrer le serveur Web

      ```
      nlserver restart web
      ```

   1. Si votre environnement s’exécute sur Apache, redémarrez Apache.

      ```
      /etc/init.d/apache2 restart
      ```


>[!NOTE]
>
>Pour toute question sur ces modifications, contactez l’[Assistance clientèle d’Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Rubriques connexes

* [Mise à niveau de votre environnement](../../production/using/build-upgrade.md)
* [FAQ sur la mise à niveau des builds](../../platform/using/faq-build-upgrade.md)
* [Installation de la console cliente Campaign](../../installation/using/installing-the-client-console.md)

