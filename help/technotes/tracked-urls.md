---
solution: Campaign Classic
product: campaign
title: Note technique
description: Note technique
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: f47b0ecfd3e35d15a78779fd9f38cc93c798d5d2
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 20%

---

# Problème de signature des URL suivies {#tracked-urls}

Suite à des modifications récentes, les URL suivies peuvent échouer lorsque la signature d’URL est principale dans Campaign. Certaines boîtes aux lettres peuvent être plus touchées que d&#39;autres, car certaines sociétés disposent d&#39;outils de sécurité spécifiques qui peuvent affecter les liens et modifier le mécanisme de signature d&#39;URL.

Par conséquent, l’Adobe vous recommande de désactiver le mécanisme de signature pour le suivi des liens. Cette procédure corrige les liens de suivi anciens, à l’exception de ceux qui ont été reçus avec une fuite de doublon.

Notez que les liens de désinscription peuvent échouer comme tout autre lien, la fréquence est variable d’hôte à hôte, mais inférieure à 1 %.

**Cela vous concerne-t-il ?**

Pour améliorer la sécurité, le mécanisme de signature pour le suivi des liens dans les courriels a été introduit dans [Campaign Gold Standard 8](../rn/using/gold-standard.md#gs8) - avril 2020 - et est activé par défaut pour tous les clients qui commencent la version 19.1.4 (9032@3a9dc9c) et Campaign 20.2.

Si votre environnement s’exécute sur l’une des versions répertoriées ci-dessous, vous pouvez être affecté :

* Gold Standard 7 - 11. [En savoir plus](../rn/using/gold-standard.md)
* Versions Campaign 21.1.1 - 21.1.2. [En savoir plus](../rn/using/latest-release.md)
* Versions Campaign 20.3.1 à 20.3.3. [En savoir plus](../rn/using/release--20-3.md)
* Versions Campaign 20.2.1 à 20.2.3. [En savoir plus](../rn/using/release--20-2.md)
* Versions Campaign 20.1.1 - 21.1.3. [En savoir plus](../rn/using/release--20-1.md)
* Campaign versions 19.2.2 - 19.2.3. [En savoir plus](../rn/using/release--19-2.md)
* Campaign versions 19.1.5 à 19.1.7. [En savoir plus](../rn/using/release--19-1.md)

Découvrez comment vérifier votre version [dans cette section](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Comment effectuer la mise à jour ?**

En tant que **client hébergé**, l’Adobe travaillera avec vous pour mettre à jour votre configuration sous peu.

En tant que client **sur site/hybride**, vous devez mettre à jour votre configuration.

Procédez comme suit :

1. Dans le [fichier de configuration du serveur](../installation/using/the-server-configuration-file.md) (serverConf.xml), remplacez **signEmailLinks** par **false**.
1. Redémarrez le service **nlserver**.
1. Sur le serveur de tracking, redémarrez le serveur web (apache2 sur Debian, httpd sur CentOS/RedHat, IIS sous Windows).

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>Le fichier **config-`<instance>`.xml** remplace les paramètres **serverConf.xml**. Si **signEmailLinks** est présent dans **config-`<instance>`.xml** (où **instance** est le nom de votre instance), il doit également être remplacé par **false**.


**Quel est l&#39;impact ?**

La maintenance nécessite un temps d&#39;inactivité maximal de 25 minutes et pendant cette période, toutes les diffusions, les liens de suivi et les appels d&#39;API ne fonctionneront pas.

Une fois la mise à jour terminée, tous les liens fonctionnent comme prévu.

>[!NOTE]
>
>Pour toute question sur ces modifications, contactez l’[Assistance clientèle d’Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

