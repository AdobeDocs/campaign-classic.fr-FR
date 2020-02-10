---
title: Lignes de commande
seo-title: Lignes de commande
description: Lignes de commande
seo-description: null
page-status-flag: never-activated
uuid: fa897d6a-0326-4922-8936-2471af2f213c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: 3621d4ec-8839-40c3-a574-486c408f79ba
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Lignes de commande{#command-lines}

Les lignes de commande suivantes requièrent la possibilité d&#39;accéder au serveur applicatif. Pour les déploiements hébergés par Adobe, ces commandes ne peuvent être exécutées que par Adobe.

## Création d&#39;une instance {#creating-an-instance}

La création d&#39;une instance peut être exécutée en ligne de commande avec la syntaxe :

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(where **eng** and **fra** are possible values for the `[lang]` parameter)

La commande **nlserver config -addinstance:instance1/demo*/fra** permet de créer une instance de nom **instance1** de langue française avec le masque DNS demo*.

## Déclaration de la base {#declaring-a-database}

Vous pouvez associer une base de données existante à une instance. Pour cela, la ligne de commande est la suivante :

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

The following values are possible for the **`[rdbms]`** parameter:

* **postgresql** : pour le moteur PostgreSQL,
* **oracle** : pour le moteur Oracle,
* **mssql** : pour Microsoft SQL Server,
* **DB2** : pour le moteur DB2.

La commande suivante paramètre l&#39;instance **demo** avec la base de type SQL Server nommée **base6**, associée au compte **campaign** et son mot de passe **password** sur le serveur **dbsrv**.

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

