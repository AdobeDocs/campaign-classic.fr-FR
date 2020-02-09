---
title: Base de données
seo-title: Base de données
description: Base de données
seo-description: null
page-status-flag: never-activated
uuid: b318365c-8846-4c1d-b5f7-ece55fb8c4af
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1dcf01af-c2f3-4975-ba05-628d52952064
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 28614a6b0c45deef17d9b3275a16e65bdff4538b

---


# Base de données{#database}

Le serveur de base de données peut fonctionner sur n&#39;importe quel système d&#39;exploitation, sans tenir compte du système utilisé par le ou les serveurs applicatifs, sous réserve de connectivité réseau entre eux.

Quel que soit le système d&#39;exploitation sur lequel le moteur de base de données est installé, la connectivité doit être disponible sur les machines qui exécutent des composants d&#39;Adobe Campaign.

Vérifiez également la section des couches [d&#39;accès à la](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) base de données.

## Microsoft SQL Server {#microsoft-sql-server}

Le client natif doit être installé sur les serveurs applicatifs Adobe Campaign.

Vous pouvez vérifier la présence du client natif sur le serveur via le panneau de configuration des pilotes ODBC, sous les libellés **SQL Native Client** (pour un client Microsoft SQL Server 2005), **SQL Server Native Client 10.0** (pour les clients Microsoft SQL Server 2008 et 2008 R2) ou **SQL Server Native Client 11.0** (pour un client Microsoft SQL Server 2012).

Les DLL d&#39;accès suivantes doivent donc être présentes :

* **sqlncli.dll** pour le client Microsoft SQL Server 2005,
* **sqlncli10.dll** pour les clients Microsoft SQL Server 2008 et 2008 R2,
* **sqlncli11.dll** pour le client Microsoft SQL Server 2012.

   Les DLL d&#39;accès sont disponibles sur le site de Microsoft.

>[!NOTE]
>
>L&#39;accès à Microsoft SQL Server depuis un serveur applicatif sous Linux n&#39;est pas supporté.

## Oracle {#oracle}

>[!NOTE]
>
>Les noms de colonne avec des caractères multi-octets ne sont pas pris en charge.

Les paramètres **NLS_NCHAR_CHARACTERSET** et **NLS_CHARACTERSET** doivent avoir été correctement configurés pour un bon fonctionnement de la base en Unicode ou en ANSI.

Adobe Campaign utilise les encodages par défaut d&#39;Oracle. Si vous en utilisez d&#39;autres, il peut se produire une incompatibilité. Dans ce cas, contactez le support technique.

Pour connaître votre encodage, vous pouvez utiliser la commande **sqlplus** suivante :

```
SELECT * FROM nls_database_parameters ;
```

* Pour une installation en Unicode, les encodages supportés sont :

   ```
   NLS_NCHAR_CHARACTERSET         AL16UTF16
   NLS_CHARACTERSET         AL32UTF8
   ```

* Pour une installation en ANSI (non Unicode), le seul encodage supporté est le suivant :

```
  NLS_CHARACTERSET WE8MSWIN1252
```

Pour vous connecter à **sqlplus**, utilisez le profil utilisateur Oracle :

```
su - oracle 
sqlplus 
[login] [password]
```

Vous pouvez également vous référer au client [Oracle sous Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

Nous vous recommandons d&#39;installer le support UTF-8 lors de l&#39;installation du moteur de base, afin de pouvoir créer des bases Unicode.

**Rubrique connexe**

* [Option non enregistrée dans les tableaux Adobe Campaign Classic](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)