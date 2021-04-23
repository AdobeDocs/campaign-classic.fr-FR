---
solution: Campaign Classic
product: campaign
title: Architecture générale
description: Architecture générale
audience: production
content-type: reference
topic-tags: introduction
exl-id: 3bfb5448-6996-4080-bf9a-434f1207637e
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '181'
ht-degree: 100%

---

# Architecture générale{#general-architecture}

## Architecture minimale {#minimum-architecture}

Dans une configuration minimale, Adobe Campaign fonctionne avec :

* le serveur applicatif Adobe Campaign,
* la base de données.

   ![](assets/formation_exploitation.png)

Ce schéma montre que les seuls flux utilisés dans le cadre d&#39;une architecture minimale sont :

1. du protocole HTTP vers le serveur Adobe Campaign depuis Internet,
1. du protocole SMTP de et vers le serveur Adobe Campaign depuis Internet.

## Architecture répartie {#distributed-architecture}

Adobe Campaign est composé de multiples modules qui peuvent être répartis entre plusieurs machines. Ce mode de fonctionnement présente plusieurs intérêts :

* répartition de la charge,
* mise en place de la redondance de modules,
* construction d&#39;une architecture répartie sur plusieurs prestataires (segmentation des services fournis).

![](assets/architecturerepartie.png)

La répartition des modules sur plusieurs machines offre une grande souplesse d&#39;utilisation et une meilleure adaptabilité.

>[!NOTE]
>
>Pour plus d’informations sur les différentes architectures, reportez-vous à [cette section](../../installation/using/general-architecture.md).

## Liste des ports ouverts {#list-of-open-ports}

| Numéro de port | Module Adobe Campaign ou application concerné | Paramétrable |
|---|---|---|
| 443/tcp ou 80/tcp | Serveurs Web (Apache/IIS) | OUI |
| 6666/udp (local) | Adobe Campaign : Syslogd | OUI |
| 8005/tcp (local) | Adobe Campaign : module web | OUI |
| 8080/tcp | Adobe Campaign : module web (tomcat) | OUI |
| 7777 | Serveur de statistiques (stat server) | OUI |
