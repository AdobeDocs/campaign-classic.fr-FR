---
product: campaign
title: 'Note technique : activation de Microsoft Edge Chromium dans votre environnement Campaign'
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
description: Campaign - Edge Chromium
feature: Technote, Upgrade
exl-id: 22f4cbaf-ca37-47b9-b7dd-1ee73d5b348d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 100%

---

# Comment activer Microsoft Edge Chromium dans votre environnement {#edge-conf}




## Qu’est-ce qui a changé ?

Compte tenu de la fin de vie de Microsoft Internet Explorer 11, le moteur de rendu HTML des tableaux de bord dans la console cliente utilise désormais Edge Chromium, à compter de Campaign Classic v7.3

Outre l’installation du runtime Microsoft Edge Webview 2, qui est désormais [requis pour toute installation de console cliente](../../installation/using/installing-the-client-console.md#webview), Microsoft Edge Chromium doit être activé sur votre ou vos instances.

## Cela vous concerne-t-il ?

Si votre environnement a été mis à niveau vers Campaign Classic v7.3 (ou version ultérieure), cela vous concerne.

## Comment effectuer la mise à jour ?

* En tant que cliente ou client **hébergé(e)**, Adobe a déjà activé Microsoft Edge Chromium sur votre ou vos instances. Aucune action supplémentaire n’est requise.

* En tant que cliente ou client **On-Premise/hybride**, vous devez activer Microsoft Edge Chromium sur votre ou vos instances.

  Lors de la mise à niveau vers Campaign Classic v7.3 (et versions ultérieures), un nouvel attribut `webView2Mode` est disponible dans le fichier de configuration du serveur Campaign `serverConf.xml`. Cet attribut doit être activé.

  Pour ce faire, respectez les étapes suivantes sur tous vos environnements (MKT, MID, RT) :

   1. Modifiez le fichier de configuration du serveur Campaign (`serverConf.xml`).
   1. Dans le module `<web>`, définissez `webView2Mode = "1"`.
   1. Exécutez la commande suivante pour recharger la configuration du serveur :

      ```
      nlserver config -reload
      ```

   1. Exécutez la commande suivant afin de redémarrer le serveur web :

      ```
      nlserver restart web
      ```

   1. Si votre environnement utilise Apache en tant que serveur web, exécutez la commande suivante pour redémarrer Apache :

      ```
      /etc/init.d/apache2 restart
      ```


>[!NOTE]
>
>Pour toute question sur ces modifications, contactez l’[Assistance clientèle d’Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Rubriques connexes

* [Mise à niveau de votre environnement](../../production/using/build-upgrade.md)
* [FAQ sur la mise à niveau des builds](../../platform/using/faq-build-upgrade.md)
* [Installer la console cliente Campaign](../../installation/using/installing-the-client-console.md)
