---
product: campaign
title: Sauvegarde
description: Sauvegarde
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
badge-v7-prem: label="On-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '223'
ht-degree: 100%

---

# Sauvegarde{#backup}

La sauvegarde est une opération primordiale afin de ne pas perdre de données en cas de problème (physique ou système) sur une machine.

Les données sont stockées dans deux endroits distincts :

* des fichiers physiques sont stockés dans les répertoires d&#39;Adobe Campaign,
* les autres données sont stockées dans la base de données.

La grande majorité des données se trouve dans la base. Elle représente 99% de l&#39;espace des données sauvegardées.

## Les fichiers physiques {#physical-files}

Ces fichiers sont répartis en plusieurs catégories :

* Les fichiers de configuration, stockés dans **nl6/conf**, vous permettent de reconfigurer Adobe Campaign très rapidement.

* Les fichiers de redirection, stockés dans **nl6/var/`<instance-name>`/redir**, se trouvent sur les serveurs de tracking (souvent appelés « frontaux ») et incluent toutes les redirections de campagnes précédentes. Ils sont toujours utilisés par les campagnes précédentes.

* Les fichiers journaux, stockés dans **nl6/var/`<instance-name>`/log**, peuvent être utilisés pour effectuer le suivi les problèmes.

Les répertoires à sauvegarder sont donc :

* nl6/conf

* nl6/var/`<instance-name>`/redir (pour chaque instance)

* nl6/var/`<instance-name>`/log (facultatif)

* nl6/var/`<instance-name>`/relay (facultatif)


## Base de données {#database}

>[!IMPORTANT]
>
>La sauvegarde de la base de données est essentielle.


La base de données contient toutes les informations affichées dans la console cliente riche Adobe Campaign, ainsi que toutes les données métiers.

Cette opération est à la charge de votre hébergeur, et plus particulièrement de leurs administrateurs de bases de données.
