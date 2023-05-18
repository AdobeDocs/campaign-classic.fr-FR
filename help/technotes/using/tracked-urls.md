---
product: campaign
title: Problème de signature des URL trackées
description: Problème de signature des URL trackées
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
hide: true
hidefromtoc: true
exl-id: e7d4331b-7149-4768-8e46-2e2911319074
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Problème de signature des URL trackées {#tracked-urls}



Suite à des modifications récentes, les URL trackées peuvent échouer lorsque la signature d&#39;URL est active dans Campaign. Certaines boîtes de réception peuvent être plus touchées que d&#39;autres, car certaines sociétés disposent d&#39;outils de sécurité spécifiques qui peuvent affecter les liens et modifier le mécanisme de signature d&#39;URL.

Par conséquent, Adobe vous recommande de désactiver le mécanisme de signature pour les liens de tracking. Cette procédure corrige les anciens liens de tracking, à l&#39;exception de ceux qui ont été reçus avec un double échappement.

Veuillez noter que les liens de désinscription peuvent échouer comme tout autre lien, la fréquence est variable d&#39;hôte à hôte, mais inférieure à 1 %.

**Cela vous concerne-t-il ?**

Pour améliorer la sécurité, le mécanisme de signature pour les liens de tracking dans les emails a été introduit dans [Campaign Gold Standard 8](../../rn/using/gold-standard.md#gs8), avril 2020, et est activé par défaut pour tous les clients qui commencent la version 19.1.4 (9032@3a9dc9c) et Campaign 20.2.

Si votre environnement s&#39;exécute sur l&#39;une des versions répertoriées ci-dessous, vous pouvez être affecté :

* Gold Standard 8 à 11. [En savoir plus](../../rn/using/gold-standard.md#gs-8)
* Campaign versions 21.1.1 (build 9277) à 21.1.2 (build 9282). [En savoir plus](../../rn/using/latest-release.md)
* Campaign versions 20.3.1 (build 9228) à 20.3.3 (build 9234). [En savoir plus](../../rn/using/release--2020.md#release-20-3)
* Campaign versions 20.2.1 (build 9178) à 20.2.4 (build 9187). [En savoir plus](../../rn/using/release--2020.md#release-20-2)
* Campaign versions 20.1.1 (build 9122) à 21.1.3 (build 9124). [En savoir plus](../../rn/using/release--2020.md#release-20-1)
* Campaign versions 19.2.2 (build 9080) à 19.2.3 (build 9081). [En savoir plus](../../rn/using/release--2019.md#release-19-2)
* Campaign versions 19.1.5 (build 9033) à 19.1.7 (build 9036). [En savoir plus](../../rn/using/release--2019.md#release-19-1)


Découvrez comment vérifier votre version [dans cette section](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Comment effectuer la mise à jour ?**

En tant que **client hébergé**, Adobe travaillera avec vous pour mettre à jour votre configuration rapidement.

En tant que **client on-premise/hybride**, vous devez mettre à jour votre configuration.

Procédez comme suit :

1. Dans le [fichier de configuration du serveur](../../installation/using/the-server-configuration-file.md) (serverConf.xml), définissez **signEmailLinks** sur **false**.
1. Redémarrez le service **nlserver**.
1. Sur le serveur de tracking, redémarrez le serveur web (apache2 sur Debian, httpd sur CentOS/RedHat, IIS sous Windows).

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>Le fichier **config-`<instance>`.xml** remplace les paramètres **serverConf.xml**. Si **signEmailLinks** est présent dans **config-`<instance>`.xml** (où **instance** est le nom de votre instance), il doit également être défini sur **false**.

**Quel est l&#39;impact ?**

La maintenance nécessite un temps d&#39;inactivité maximal de 25 minutes et pendant cette période, toutes les diffusions, les liens de tracking et les appels d&#39;API ne fonctionneront pas.

Une fois la mise à jour terminée, tous les liens fonctionnent comme prévu.

>[!NOTE]
>
>Pour toute question sur ces modifications, contactez l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
