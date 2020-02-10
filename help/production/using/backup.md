---
title: Sauvegarde
seo-title: Sauvegarde
description: Sauvegarde
seo-description: null
page-status-flag: never-activated
uuid: 50134154-a671-4534-b48d-a9e2c42e8f1a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 870ab0f2-1bd7-42e7-8d83-a08a520b6587
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# Sauvegarde{#backup}

La sauvegarde est une opération primordiale afin de ne pas perdre de données en cas de problème (physique ou système) sur une machine.

Les données sont stockées dans deux endroits distincts :

* des fichiers physiques sont stockés dans les répertoires d&#39;Adobe Campaign,
* les autres données sont stockées dans la base de données.

La grande majorité des données se trouve dans la base. Elle représente 99% de l&#39;espace des données sauvegardées.

## Les fichiers physiques {#physical-files}

Ces fichiers sont répartis en plusieurs catégories :

* Les fichiers de configuration situés dans **nl6/conf**

   Ils permettent de reparamétrer Adobe Campaign très rapidement.

* Redirection files ** nl6/var/`<instancename>`/redir**

   Ils se trouvent sur les serveurs de tracking (communément appelés &quot;frontaux&quot;) et contiennent l&#39;ensemble des redirections des campagnes effectuées. Ils sont toujours utilisés par les anciennes campagnes.

* Log files: **nl6/var/`<instancename>`/log**

   Ils peuvent être utilisés afin de tracer des problèmes.

Les répertoires à sauvegarder sont donc :

* nl6/conf

* nl6/var/`<instanceName>`/DI (pour chaque instance)

* nl6/var/`<instanceName>`/log (facultatif)

* nl6/var/`<instanceName>`/relay (facultatif)

>[!CAUTION]
>
>La sauvegarde de la base de données est impérative.

## Base de données {#database}

La base de données contient toutes les informations affichées dans la console cliente riche Adobe Campaign, ainsi que toutes les données métiers.

Cette opération est à la charge de votre hébergeur, et plus particulièrement de leurs administrateurs de bases de données.
