---
product: campaign
title: Lignes de commande
description: Lignes de commande
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
TQID: 'https://experienceleague.adobe.com/e85vFL0iZ586ICGGH1CP6fgqGU717W1aPDWqmj40-3s'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: ht
source-wordcount: '144'
ht-degree: 100%
---
# Lignes de commande{#command-lines}



Les lignes de commande suivantes requièrent la possibilité d’accéder au serveur d’applications. Pour les déploiements hébergés par Adobe, ces commandes ne peuvent être exécutées que par Adobe.

## Création d’une instance {#creating-an-instance}

La création d&#39;une instance peut être exécutée en ligne de commande avec la syntaxe :

```sql
nlserver config -addinstance:instance/masques DNS[/lang]
```

(où **eng** et **fra** correspondent aux valeurs possibles du paramètre `[lang]`)

La commande **nlserver config -addinstance:instance1/demo&#42;/eng** vous permet de créer une instance appelée **instance1** en anglais avec le masque DNS demo&#42;.

## Déclaration d’une base de données {#declaring-a-database}

Vous pouvez associer une base de données existante à une instance. Pour cela, la ligne de commande est la suivante :

```sql
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Les valeurs possibles pour le paramètre **`[rdbms]`** sont les suivantes :

* **postgresql** : pour le moteur PostgreSQL,
* **oracle** : pour le moteur Oracle,
* **mssql** : pour Microsoft SQL Server,

La commande suivante paramètre l’instance **demo** avec la base de type SQL Server nommée **base6**, associée au compte **campaign** et son mot de passe **password** sur le serveur **dbsrv**.

```sql
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
