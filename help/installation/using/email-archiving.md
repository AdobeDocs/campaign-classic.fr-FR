---
title: Archivage des emails
seo-title: Archivage des emails
description: Archivage des emails
seo-description: null
page-status-flag: never-activated
uuid: a5ed0659-be61-4d73-98e7-db3da24d92f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: d6467875-949b-4b47-940f-620efd4db5e0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5b9c57b3cba0e8c24300396c2abac613f6e1193a

---


# Archivage des emails{#email-archiving}

Vous pouvez paramétrer Adobe Campaign pour conserver une copie des emails envoyés depuis votre plateforme.

Toutefois, Adobe Campaign ne gère pas lui-même les fichiers archivés : il vous permet d&#39;envoyer les messages de votre choix à une adresse dédiée, depuis laquelle ils peuvent être traités et archivés dans un système externe.

Pour ce faire, les fichiers .eml correspondant aux emails envoyés sont transférés vers un serveur distant, comme un serveur de messagerie SMTP. La destination de l&#39;archivage est une adresse email en Cci (invisible aux destinataires de la diffusion) que vous devez spécifier.

## Recommandations et limitations  {#recommendations-and-limitations}

* Cette fonctionnalité d&#39;archivage des emails est en option. Vérifiez votre contrat de licence.
* Pour les architectures **** hébergées et hybrides, contactez le gestionnaire de compte pour l’activer. L’adresse CC de votre choix doit être fournie à l’équipe Adobe qui la configurera pour vous.
* Pour les installations **** sur site, suivez les instructions ci-dessous pour les activer - reportez-vous aux sections [Activation de l’archivage des e-mails (sur site)](#activating-email-archiving--on-premise-) et [Configuration de l’adresse e-mail BCC (sur site)](#configuring-the-bcc-email-address--on-premise-) .
* Vous ne pouvez utiliser qu&#39;une seule adresse email en Cci.
* Une fois la fonctionnalité email en Cci paramétrée, vérifiez qu’elle est activée dans le modèle de diffusion ou la diffusion par le biais de l’option **[!UICONTROL Archiver les emails]**. Voir à ce sujet [cette section](../../delivery/using/sending-messages.md#archiving-emails).
* Seuls les emails envoyés sont pris en compte, les retours ne le sont pas.
* Le système d’archivage des e-mails a été modifié avec Adobe Campaign 17.2 (version 8795). Si vous utilisiez déjà l’archivage des e-mails, vous devez effectuer une mise à niveau manuelle vers le nouveau système d’archivage des e-mails (BCC). Pour plus d’informations, voir la section [Mise à jour du système d’archivage des e-mails (BCC)](#updated-email-archiving-system--bcc-) .

## Activer l&#39;archivage des emails (on-premise) {#activating-email-archiving--on-premise-}

Pour activer l’archivage des emails en Cci lorsqu’Adobe Campaign est installé on-premise, suivez les étapes ci-dessous.

### Dossier local {#local-folder}

Pour activer le transfert des emails envoyés à une adresse email en Cci, les copies brutes exactes des emails envoyés doivent être enregistrées en tant que fichiers .eml dans un dossier local.

The path for the local folder must be specified in the **config-`<instance>`.xml** file, from the configuration. Par exemple :

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>Les équipes en charge de l&#39;implémentation doivent s&#39;assurer que les conditions de sécurité permettent l&#39;accès au dossier défini via les paramètres **dataLogPath**.

The full path is as follows: **`<datalogpath>  YYYY-MM-DDHHh`**. The date and time are set according to the MTA server&#39;s clock (UTC). Par exemple :

```
C:\emails\2018-12-02\13h
```

Le nom du fichier d’archive est **`<deliveryid>-<broadlogid>.eml`** défini lorsque l’état des courriers électroniques n’est pas **[!UICONTROL Envoyé]**. Une fois que l’état est **[!UICONTROL Envoyé]**, le nom du fichier devient **`<deliveryid>-<broadlogid>-sent.eml`**. Par exemple :

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>Dans une instance mid-sourcing, le dossier des emails archivés se trouve sur le serveur de mid-sourcing.
>
>Les deliveryID et broadlogID sont ceux du serveur de mid-sourcing lorsque le statut des emails n&#39;est pas envoyé. Une fois le statut changé en **[!UICONTROL Envoyé]**, ces ID sont ceux du serveur marketing.

### Paramètres {#parameters}

Une fois le chemin d’accès au dossier local défini, ajoutez et modifiez les éléments suivants selon vos besoins dans le fichier **config-`<instance name>.xml`**. Vous trouverez ci-dessous les valeurs par défaut :

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat** : format utilisé lors de la compression des fichiers .eml. Les valeurs possibles sont les suivantes :

   **0 **: pas de compression (valeur par défaut)

   **1 : compression (au format .zip)**

* **compressBatchSize** : nombre de fichiers .eml ajoutés à une archive (fichier .zip).
* **archivingType** : stratégie d&#39;archivage à utiliser. Les valeurs possibles sont les suivantes :

   **0**: les copies brutes des courriers électroniques envoyés sont enregistrées au format .eml dans le dossier **dataLogPath** (valeur par défaut). Une copie d’archivage du **`<deliveryid>-<broadlogid>-sent.eml`** fichier est enregistrée dans le dossier **dataLogPath/archives** . Le chemin du fichier de courrier électronique envoyé devient **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.

   **1**: les copies brutes des courriers électroniques envoyés sont enregistrées au format .eml dans le dossier **dataLogPath** et sont envoyées à l’adresse de messagerie BCC via SMTP. Une fois les copies de courrier électronique envoyées à l’adresse BCC, le nom du fichier d’archive devient **`<deliveryid>-<broadlogid>-sent-archived.eml`** et le fichier est déplacé dans le dossier **dataLogPath/archives** . Le chemin d’accès au fichier de courrier électronique archivé BCC et envoyé est alors **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

* **expirationDelay** : nombre de jours pendant lesquels les fichiers .eml sont conservés pour archivage. Après ce délai, ils sont automatiquement déplacés vers le dossier **dataLogPath/archives** pour compression. Par défaut, les fichiers .eml expirent au bout de deux jours.
* **purgeArchivesDelay**: nombre de jours pendant lesquels les archives sont conservées dans le dossier **dataLogPath/`<archives>`**. Après cette période, ils sont définitivement supprimés. La purge commence lorsque la MTA est lancée. Par défaut, elle est exécutée tous les sept jours.
* **pollDelay**: fréquence de vérification (en secondes) pour les nouveaux courriers électroniques envoyés au dossier **dataLogPath** . Par exemple, si ce paramètre est défini sur 60, cela signifie que chaque minute, le processus d’archivage passe par les fichiers .eml dans les dossiers **dataLogPath/`<date and time>`**, applique une purge si nécessaire et envoie des copies de courrier électronique à l’adresse BCC et/ou compresse les fichiers archivés au besoin.
* **acquireLimit **: nombre de fichiers .eml traités à la fois avant que le processus d&#39;archivage ne soit réappliqué selon le paramètre **pollDelay**. Par exemple, si vous définissez le paramètre **acquireLimit** sur 100 alors que le paramètre **pollDelay** est défini sur 60, 100 fichiers .eml seront traités par minute.
* **smtpNbConnection** : nombre de connexions SMTP à l&#39;adresse email en Cci.

Veillez à ajuster ces paramètres en fonction du débit d&#39;envoi des emails. Par exemple, dans une configuration où le MTA envoie 30 000 emails par heure, vous pouvez définir le paramètre **pollDelay** sur 600, le paramètre **acquireLimit** sur 5 000 et le paramètre **smtpNbConnection** sur 2. Cela signifie qu&#39;en utilisant 2 connexions SMTP, 5 000 emails seront envoyés à l&#39;adresse en Cci toutes les 10 minutes.

## Configuration de l&#39;adresse email en Cci (on-premise) {#configuring-the-bcc-email-address--on-premise-}

>[!CAUTION]
>
>Pour des raisons de confidentialité, les emails en Cci doivent être traités dans un système d&#39;archivage capable de stocker en toute sécurité les informations d&#39;identification personnelles (PII).

In the **config-`<instance name>.xml`**file, use the following parameters to define the SMTP email server to which the stored files will be transferred:

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress** : destination de la cible d&#39;archivage
* **smtpEnableTLS** : utilisation d&#39;une connexion SMTP sécurisée (protocole TLS/SSL)
* **smtpRelayAddress** : adresse relais à utiliser
* **smtpRelayPort** : port relais à utiliser

>[!NOTE]
>
>Si vous utilisez un relais SMTP, les modifications apportées aux emails par le relais ne sont pas prises en compte dans le processus d&#39;archivage.
>
>En outre, le relais affecte le statut **[!UICONTROL Envoyé]** à tous les emails, y compris ceux qui ne sont pas envoyés. Tous les messages sont donc archivés.

## Système d&#39;archivage des emails mis à jour (Cci) {#updated-email-archiving-system--bcc-}

>[!CAUTION]
>
>Le système d&#39;archivage des emails (Cci) a été modifié avec Adobe Campaign 17.2 (build 8795). Si vous effectuez une mise à niveau à partir d&#39;un build antérieur et que vous utilisiez déjà les fonctionnalités d&#39;archivage des emails, vous devez effectuer une mise à niveau manuelle vers le nouveau système d&#39;archivage des emails (Cci).

Pour ce faire, apportez les modifications suivantes au **`config-<instance>.xml`** fichier :

1. Remove the **zipPath** parameter from the **`<archiving>`** node.
1. Définissez le paramètre **compressionFormat** sur **1** si nécessaire.
1. Définissez le paramètre **archivingType** sur **1**.

Une fois la fonctionnalité email en Cci paramétrée, veillez à sélectionner l&#39;option **[!UICONTROL Archiver les emails]** dans le modèle de diffusion ou la diffusion. Voir à ce sujet [cette section](../../delivery/using/sending-messages.md#archiving-emails).

## Bonnes pratiques {#best-practices}

* **Boîte aux lettres d&#39;adresses en Cci** : vérifiez qu&#39;elle dispose de suffisamment de capacité pour archiver tous les emails envoyés par le MTA.
* **Mutualisation de MTA **: la fonctionnalité d&#39;archivage Cci fonctionne au niveau MTA. Elle vous permet de dupliquer tous les emails envoyés par le MTA. Etant donné que le MTA peut être mutualisé dans plusieurs instances (dev, test ou prod, par exemple) voire même sur plusieurs clients (dans un environnement de mid-sourcing), le paramétrage de cette fonctionnalité influe sur la sécurité :

   * Si vous partagez un MTA avec plusieurs clients et que l&#39;un d&#39;eux active cette option, il aura accès à la totalité des emails provenant des autres clients utilisant le même MTA. Afin d&#39;éviter une telle situation, utilisez un MTA différent pour chaque client.
   * Si vous utilisez le même MTA entre plusieurs instances (développement, test, production) d&#39;un même client, les messages envoyés depuis ces trois instances combinées seront dupliqués par l&#39;option dataLogPath.

* **Emails par connexion **: l’archivage des emails en Cci fonctionne en ouvrant une connexion et en essayant d’envoyer tous les emails via cette connexion. Adobe recommande de vérifier avec votre contact technique le nombre d’emails acceptés sur une connexion donnée. L’augmentation de ce nombre peut avoir un grand impact sur le débit Cci.
* **IP envoyant en Cci** : actuellement, les emails en Cci ne sont pas envoyés par les proxys MTA normaux. Au lieu de cela, une connexion directe est ouverte à partir du serveur MTA vers le serveur d’email de destination. Cela signifie que vous devrez peut-être mettre en whiteliste d’autres IP sur votre réseau, en fonction du paramétrage de votre serveur d’emails.

