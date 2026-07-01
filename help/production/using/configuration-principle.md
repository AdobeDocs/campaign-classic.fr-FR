---
product: campaign
title: Principe de configuration
description: Principe de configuration
feature: Monitoring, Configuration
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
TQID: https://experienceleague.adobe.com/qh8T4QUwIzRfwYj0j0ZUOJp0V78fiw4ADrSzzMfAsZg
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 311
ht-degree: 100%

---

# Principe de configuration{#configuration-principle}



La plateforme Adobe Campaign repose sur le concept d’instances, similaires à celles des hôtes virtuels utilisés par Apache.Ce mode de fonctionnement vous permet de partager un serveur en lui associant plusieurs instances.Les instances sont complètement séparées les unes des autres et fonctionnent avec leur propre base de données et leur propre fichier de configuration.

Sur un même serveur, deux éléments sont communs à l&#39;ensemble des instances Adobe Campaign :

* Le mot de passe **internal** : il s’agit du mot de passe général d’administration.Il est commun à toutes les instances d’un même serveur d’applications.

  >[!IMPORTANT]
  >
  >Pour vous connecter avec l’identifiant **Internal**, vous devez impérativement avoir défini un mot de passe. Pour plus d’informations, consultez [cette section](../../installation/using/configuring-campaign-server.md#internal-identifier).

* De nombreux paramétrages techniques du serveur : ces paramétrages peuvent tous être surchargés dans la configuration spécifique d&#39;une instance.

Les fichiers de configuration sont enregistrés dans le répertoire **conf** du répertoire d’installation. La configuration est divisée en trois fichiers :

* **serverConf.xml** : configuration générale pour toutes les instances.
* **Config-.xml **`<instance>`**.xml** (où **`<instance>`** est le nom de l&#39;instance) : configuration spécifique d’une instance.
* **serverConf.xml.diff** : delta entre la configuration initiale et la configuration actuelle.Ce fichier est généré automatiquement par l’application et ne doit pas être modifié manuellement.Il est utilisé pour propager automatiquement les modifications des utilisateurs et utilisatrices lors de la mise à jour d’une version de build.

Le chargement de la configuration d&#39;une instance est réalisé de la manière suivante :

* Le module charge le fichier **serverConf.xml** pour obtenir les paramètres communs à toutes les instances.
* Il charge ensuite le fichier **config-**`<instance>`**.xml**. Les valeurs trouvées dans ce fichier ont priorité sur les valeurs contenues dans **serverConf.xml**.

  Ces deux fichiers ont le même format. Toute valeur du fichier **serverConf.xml** peut être surchargée pour une instance donnée dans le fichier **config-`<instance>`.xml**.

Ce principe de fonctionnement permet une très grande souplesse dans les paramétrages.
