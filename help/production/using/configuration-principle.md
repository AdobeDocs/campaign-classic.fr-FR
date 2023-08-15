---
product: campaign
title: Principe de configuration
description: Principe de configuration
feature: Monitoring, Configuration
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
badge-v7-prem: label="On-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 100%

---

# Principe de configuration{#configuration-principle}



La plateforme Adobe Campaign repose sur le concept d&#39;instance semblable à la notion d&#39;hôte virtuel comme c&#39;est le cas par exemple sous Apache. Ce mode de fonctionnement permet de mutualiser un serveur en y affectant plusieurs instances. Chaque instance est totalement découplée des autres et fonctionne avec sa propre base et son propre fichier de configuration.

Sur un même serveur, deux éléments sont communs à l&#39;ensemble des instances Adobe Campaign :

* Le mot de passe **internal** : il s&#39;agit du mot de passe administrateur général. Il est commun à toutes les instances d&#39;un même serveur applicatif.

  >[!IMPORTANT]
  >
  >Pour vous connecter avec l’identifiant **Internal**, vous devez impérativement avoir défini un mot de passe. Voir à ce sujet [cette section](../../installation/using/configuring-campaign-server.md#internal-identifier).

* De nombreux paramétrages techniques du serveur : ces paramétrages peuvent tous être surchargés dans la configuration spécifique d&#39;une instance.

Les fichiers de configuration sont enregistrés dans le répertoire **conf** du répertoire d’installation. La configuration est divisée en trois fichiers :

* **serverConf.xml** : configuration générale pour toutes les instances.
* **Config-.xml **`<instance>`**.xml** (où **`<instance>`** est le nom de l&#39;instance) : configuration spécifique d’une instance.
* **serverConf.xml.diff** : delta entre la configuration initiale et la configuration actuelle. Ce fichier est géré automatiquement par l&#39;application et ne doit pas être modifié manuellement. Il permet de propager automatiquement les modifications utilisateur lors d&#39;une mise à jour de build.

Le chargement de la configuration d&#39;une instance est réalisé de la manière suivante :

* Le module charge le fichier **serverConf.xml** pour obtenir les paramètres communs à toutes les instances.
* Il charge ensuite le fichier **config-**`<instance>`**.xml**. Les valeurs trouvées dans ce fichier ont priorité sur les valeurs contenues dans **serverConf.xml**.

  Ces deux fichiers ont le même format. Toute valeur du fichier **serverConf.xml** peut être surchargée pour une instance donnée dans le fichier **config-`<instance>`.xml**.

Ce principe de fonctionnement permet une très grande souplesse dans les paramétrages.
