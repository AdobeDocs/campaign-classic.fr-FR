---
title: Principe de configuration
seo-title: Principe de configuration
description: Principe de configuration
seo-description: null
page-status-flag: never-activated
uuid: 6315d526-b820-46ab-96c7-e64e101c6a7d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: d08ff769-da93-4f86-8802-f0fb5b051ece
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 34cd6e6cf5652c9e2163848c2b1ef32f53ee6ca4

---


# Principe de configuration{#configuration-principle}

La plateforme Adobe Campaign repose sur le concept d&#39;instance semblable à la notion d&#39;hôte virtuel comme c&#39;est le cas par exemple sous Apache. Ce mode de fonctionnement permet de mutualiser un serveur en y affectant plusieurs instances. Chaque instance est totalement découplée des autres et fonctionne avec sa propre base et son propre fichier de configuration.

Sur un même serveur, deux éléments sont communs à l&#39;ensemble des instances Adobe Campaign :

* Le mot de passe **internal** : il s&#39;agit du mot de passe administrateur général. Il est commun à toutes les instances d&#39;un même serveur applicatif.

   >[!CAUTION]
   >
   >Pour vous connecter avec l’identifiant **Internal**, vous devez impérativement avoir défini un mot de passe. Voir à ce sujet [cette section](../../installation/using/campaign-server-configuration.md#internal-identifier).

* De nombreux paramétrages techniques du serveur : ces paramétrages peuvent tous être surchargés dans la configuration spécifique d&#39;une instance.

Les fichiers de configuration sont enregistrés dans le répertoire **conf** du répertoire d’installation. La configuration est divisée en trois fichiers :

* **serverConf.xml** : configuration générale pour toutes les instances.
* **config-**`<instance>`**.xml** (où **`<instance>`** est le nom de l’instance) : configuration spécifique d’une instance.
* **serverConf.xml.diff** : delta entre la configuration initiale et la configuration actuelle. Ce fichier est géré automatiquement par l&#39;application et ne doit pas être modifié manuellement. Il permet de propager automatiquement les modifications utilisateur lors d&#39;une mise à jour de build.

Le chargement de la configuration d&#39;une instance est réalisé de la manière suivante :

* The module loads the **serverConf.xml** file to obtain the parameters shared by all instances.
* Il charge ensuite le fichier **config-**`<instance>`**.xml** . Les valeurs trouvées dans ce fichier ont priorité sur les valeurs contenues dans **serverConf.xml**.

   Ces deux fichiers ont le même format. Toute valeur du fichier **serverConf.xml** peut être surchargée pour une instance donnée dans le fichier **config-`<instance>`.xml** .

Ce principe de fonctionnement permet une très grande souplesse dans les paramétrages.
