---
product: campaign
title: Sauvegarde
description: Sauvegarde
feature: Monitoring
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
TQID: https://experienceleague.adobe.com/ZCExecNbs9DnWVoQLpvzlrH7k2eGhBNq7pEiybyQdi4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 232
ht-degree: 92%

---

# Sauvegarde{#backup}

La sauvegarde est une opération primordiale afin de ne pas perdre de données en cas de problème (physique ou système) sur une machine.

Les données sont stockées dans deux endroits distincts :

* des fichiers physiques sont stockés dans les répertoires d&#39;Adobe Campaign,
* les autres données sont stockées dans la base de données.

La plupart des données se trouvent dans la base de données. Cela représente 99 % des informations à sauvegarder.

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
