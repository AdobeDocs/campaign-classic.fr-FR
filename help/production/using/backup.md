---
product: campaign
title: Sauvegarde
description: Sauvegarde
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 4b13e310fcee9ba24e83b697fca57bc494505642
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 68%

---

# Sauvegarde{#backup}

La sauvegarde est une opération primordiale afin de ne pas perdre de données en cas de problème (physique ou système) sur une machine.

Les données sont stockées dans deux endroits distincts :

* des fichiers physiques sont stockés dans les répertoires d&#39;Adobe Campaign,
* les autres données sont stockées dans la base de données.

La grande majorité des données se trouve dans la base. Elle représente 99% de l&#39;espace des données sauvegardées.

## Les fichiers physiques {#physical-files}

Ces fichiers sont répartis en plusieurs catégories :

* Fichiers de configuration, stockés dans **nl6/conf**, vous permettent de reconfigurer Adobe Campaign très rapidement.

* Fichiers de redirection, stockés dans  **nl6/var/`<instance-name>`/redir**, se trouvent sur les serveurs de suivi (souvent appelés &quot;frontaux&quot;) et incluent toutes les redirections de campagne précédentes. Elles sont toujours utilisées par les campagnes précédentes.

* Fichiers journaux, stockés dans **nl6/var/`<instance-name>`/log**, peut être utilisé pour tracer les problèmes.

Les répertoires à sauvegarder sont donc :

* nl6/conf

* nl6/var/`<instance-name>`/redir (pour chaque instance)

* nl6/var/`<instance-name>`/log (facultatif)

* nl6/var/`<instance-name>`/relay (facultatif)


## Base de données {#database}

>[!IMPORTANT]
>
>Il est impératif de sauvegarder la base de données.


La base de données contient toutes les informations affichées dans la console cliente riche Adobe Campaign, ainsi que toutes les données métiers.

Cette opération est à la charge de votre hébergeur, et plus particulièrement de leurs administrateurs de bases de données.
