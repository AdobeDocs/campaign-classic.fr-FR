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
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '197'
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

* Les fichiers de configuration situés dans **nl6/conf**

   Ils permettent de reparamétrer Adobe Campaign très rapidement.

* Les fichiers de redirection ** nl6/var/`<instancename>`/redir**

   Ils se trouvent sur les serveurs de tracking (communément appelés &quot;frontaux&quot;) et contiennent l&#39;ensemble des redirections des campagnes effectuées. Ils sont toujours utilisés par les anciennes campagnes.

* Les fichiers de logs : **nl6/var/`<instancename>`/log**

   Ils peuvent être utilisés afin de tracer des problèmes.

Les répertoires à sauvegarder sont donc :

* nl6/conf

* nl6/var/`<instanceName>`/redir (pour chaque instance)

* nl6/var/`<instanceName>`/log (facultatif)

* nl6/var/`<instanceName>`/relay (facultatif)

>[!IMPORTANT]
>
>La sauvegarde de la base de données est impérative.

## Base de données {#database}

La base de données contient toutes les informations affichées dans la console cliente riche Adobe Campaign, ainsi que toutes les données métiers.

Cette opération est à la charge de votre hébergeur, et plus particulièrement de leurs administrateurs de bases de données.
