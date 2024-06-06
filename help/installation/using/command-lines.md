---
product: campaign
title: Lignes de commande
description: Lignes de commande
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: b7dedddc080d1ea8db700fabc9ee03238b3706cc
workflow-type: ht
source-wordcount: '150'
ht-degree: 100%

---

# Lignes de commande{#command-lines}



Les lignes de commande suivantes requièrent la possibilité d&#39;accéder au serveur applicatif. Pour les déploiements hébergés par Adobe, ces commandes ne peuvent être exécutées que par Adobe.

## Création d’une instance {#creating-an-instance}

La création d&#39;une instance peut être exécutée en ligne de commande avec la syntaxe :

```sql
nlserver config -addinstance:instance/masques DNS[/lang]
```

(où **eng** et **fra** correspondent aux valeurs possibles du paramètre `[lang]`)

La commande **nlserver config -addinstance:instance1/demo&#42;/eng** vous permet de créer une instance appelée **instance1** en anglais avec la démo du masque DNS&#42;.

## Déclaration d’une base de données {#declaring-a-database}

Vous pouvez associer une base de données existante à une instance. Pour cela, la ligne de commande est la suivante :

```sql
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Les valeurs possibles pour le paramètre **`[rdbms]`** sont les suivantes :

* **postgresql** : pour le moteur PostgreSQL,
* **oracle** : pour le moteur Oracle,
* **mssql** : pour Microsoft SQL Server,
* **DB2** : pour le moteur DB2.

La commande suivante paramètre l&#39;instance **demo** avec la base de type SQL Server nommée **base6**, associée au compte **campaign** et son mot de passe **password** sur le serveur **dbsrv**.

```sql
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
