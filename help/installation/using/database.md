---
product: campaign
title: Recommandations à propos de la base de données Campaign Classic
description: Recommandations à propos de la base de données
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
badge-v7-prem: label="On-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 100%

---

# Base de données{#database}



Le serveur de base de données peut fonctionner sur n&#39;importe quel système d&#39;exploitation, sans tenir compte du système utilisé par le ou les serveurs applicatifs, sous réserve de connectivité réseau entre eux.

Quel que soit le système d&#39;exploitation sur lequel le moteur de base de données est installé, la connectivité doit être disponible sur les machines qui exécutent des composants d&#39;Adobe Campaign.

Voir également la section [Couches d’accès à la base de données](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers).

## Microsoft SQL Server {#microsoft-sql-server}

Le client natif doit être installé sur les serveurs applicatifs Adobe Campaign.

Vous pouvez rechercher le client natif sur le serveur via le panneau de configuration du pilote ODBC, sous **SQL Server Native Client 11.0**.

La DLL d&#39;accès suivante doit être présente : **sqlncli11.dll**.

Les DLL d&#39;accès sont disponibles sur le site de Microsoft.

>[!NOTE]
>
>L&#39;accès à Microsoft SQL Server depuis un serveur applicatif sous Linux n&#39;est pas supporté.

## Oracle {#oracle}

>[!NOTE]
>
>Les noms de colonne avec des caractères multi-octets ne sont pas pris en charge.

Les paramètres **NLS_NCHAR_CHARACTERSET** et **NLS_CHARACTERSET** doivent avoir été correctement configurés pour un bon fonctionnement de la base en Unicode ou en ANSI.

Adobe Campaign utilise les encodages par défaut d&#39;Oracle. Si vous en utilisez d&#39;autres, il peut se produire une incompatibilité. Dans ce cas, contactez le support technique.

Pour connaître votre encodage, vous pouvez utiliser la commande **sqlplus** suivante :

```
SELECT * FROM nls_database_parameters ;
```

* Pour une installation en Unicode, les encodages supportés sont :

  ```
  NLS_NCHAR_CHARACTERSET         AL16UTF16
  NLS_CHARACTERSET         AL32UTF8
  ```

* Pour une installation en ANSI (non Unicode), le seul encodage supporté est le suivant :

```
  NLS_CHARACTERSET WE8MSWIN1252
```

Pour vous connecter à **sqlplus**, utilisez le profil utilisateur Oracle :

```
su - oracle 
sqlplus 
[login] [password]
```

Voir également la section [Client Oracle sous Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

Nous vous recommandons d&#39;installer le support UTF-8 lors de l&#39;installation du moteur de base, afin de pouvoir créer des bases Unicode.

**Rubrique connexe**

* [Option non enregistrée dans les tables Adobe Campaign Classic](https://helpx.adobe.com/fr/campaign/kb/unlogged-tables-classic.html)
