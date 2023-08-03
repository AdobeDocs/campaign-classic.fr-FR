---
product: campaign
title: Archivage des emails
description: Archivage des emails
feature: Installation, Instance Settings, Email
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '1374'
ht-degree: 100%

---

# Configuration du Cci d’email {#email-archiving}



Vous pouvez paramétrer Adobe Campaign pour conserver une copie des emails envoyés depuis votre plateforme.

Toutefois, Adobe Campaign ne gère pas lui-même les fichiers archivés : il vous permet d&#39;envoyer les messages de votre choix à une adresse dédiée, depuis laquelle ils peuvent être traités et archivés dans un système externe.

Pour ce faire, les fichiers .eml correspondant aux emails envoyés sont transférés vers un serveur distant, comme un serveur de messagerie SMTP. La destination de l&#39;archivage est une adresse email en Cci (invisible aux destinataires de la diffusion) que vous devez spécifier.

## Recommandations et limitations    {#recommendations-and-limitations}

* La fonctionnalité E-mail Cci est facultative. Veuillez vérifier votre accord de licence.
* Pour les **architectures hybrides et hébergées**, contactez votre chargé de compte Adobe afin de l&#39;activer. L&#39;adresse email en Cci de votre choix doit être fournie à l&#39;équipe Adobe qui la configurera pour vous.
* Pour les **installations On-premise**, suivez les instructions d&#39;activation ci-dessous : voir les sections [Activer les emails Cci (On-premise)](#activating-email-archiving--on-premise-) et [Configuration de l&#39;adresse email en Cci (on-premise)](#configuring-the-bcc-email-address--on-premise-).
* Vous ne pouvez utiliser qu&#39;une seule adresse email en Cci.
* Une fois que la fonctionnalité Email Cci est configurée, assurez-vous qu&#39;elle est activée dans le modèle de diffusion ou dans la diffusion via l&#39;option **[!UICONTROL Email Cci]**. Voir à ce propos [cette section](../../delivery/using/sending-messages.md#archiving-emails).
* Seuls les emails envoyés sont pris en compte, les retours ne le sont pas.
* Le système d&#39;archivage des emails a été modifié avec Adobe Campaign 17.2 (build 8795). Si vous utilisiez déjà l&#39;archivage des emails, vous devez effectuer une mise à niveau manuelle vers le nouveau système d&#39;Email Cci. Pour plus d’informations, consultez la section [Déplacement vers le nouvel Email Cci](#updated-email-archiving-system--bcc-).

## Activer Email Cci (On-premise) {#activating-email-archiving--on-premise-}

[!BADGE On-premise et hybride]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"}


Pour activer l’archivage des emails en Cci lorsqu’Adobe Campaign est installé on-premise, suivez les étapes ci-dessous.

### Dossier local {#local-folder}

Pour activer le transfert des emails envoyés à une adresse email en Cci, les copies brutes exactes des emails envoyés doivent être enregistrées en tant que fichiers .eml dans un dossier local.

Le chemin du dossier local doit être spécifié dans le fichier **config-`<instance>`.xml**, à partir de la configuration. Par exemple :

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>Les équipes en charge de l&#39;implémentation doivent s&#39;assurer que les conditions de sécurité permettent l&#39;accès au dossier défini via les paramètres **dataLogPath**.

Le chemin complet est comme suit : **`<datalogpath>  YYYY-MM-DDHHh`**. La date et l&#39;heure sont paramétrées par rapport à l&#39;heure locale du serveur qui lance le MTA. Par exemple :

```
C:\emails\2018-12-02\13h
```

Le nom du fichier d’archive est **`<deliveryid>-<broadlogid>.eml`** lorsque l’état des emails n’est pas **[!UICONTROL Envoyé]**. Une fois que l’état change pour **[!UICONTROL Envoyé]**, le nom du fichier devient **`<deliveryid>-<broadlogid>-sent.eml`**. Par exemple :

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>Dans une instance mid-sourcing, le dossier des emails en Cci se trouve sur le serveur de mid-sourcing.
>
>Les deliveryID et broadlogID sont ceux du serveur de mid-sourcing lorsque le statut des emails n&#39;est pas envoyé. Une fois le statut changé en **[!UICONTROL Envoyé]**, ces ID sont ceux du serveur marketing.

### Paramètres {#parameters}

Une fois le chemin d’accès au dossier local défini, ajoutez et modifiez les éléments suivants selon vos besoins dans le fichier **config-`<instance name>.xml`**. Vous trouverez ci-dessous les valeurs par défaut :

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat** : format utilisé lors de la compression des fichiers .eml. Les valeurs possibles sont les suivantes :

  **0** : pas de compression (valeur par défaut)

  **1 : compression (au format .zip)**

* **compressBatchSize** : nombre de fichiers .eml ajoutés à une archive (fichier .zip).
* **archivingType** : stratégie d&#39;archivage à utiliser. Les valeurs possibles sont les suivantes :

  **0** : les copies brutes des emails envoyés sont enregistrées au format .eml dans le dossier **dataLogPath** (valeur par défaut). Une copie d’archivage du fichier **`<deliveryid>-<broadlogid>-sent.eml`** est enregistrée dans le dossier **dataLogPath/archives**. Le chemin d’accès au fichier de l’email envoyé devient **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.

  **1** : les copies brutes des emails sont enregistrées au format .eml dans le dossier **dataLogPath** et sont envoyées à l’adresse email Cci via SMTP. Une fois que les copies d’email sont envoyées à l’adresse Cci, le nom du fichier d’archive devient **`<deliveryid>-<broadlogid>-sent-archived.eml`** et le fichier est déplacé dans le dossier **dataLogPath/archives**. Le chemin d’accès au fichier de l’email envoyé et archivé Cci est alors **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

* **expirationDelay** : nombre de jours pendant lesquels les fichiers .eml sont conservés pour archivage. Après ce délai, ils sont automatiquement déplacés vers le dossier **dataLogPath/archives** pour compression. Par défaut, les fichiers .eml expirent au bout de deux jours.
* **purgeArchivesDelay** : nombre de jours pendant lesquels les archives sont conservées dans le dossier **dataLogPath/`<archives>`**. Après cette période, ils sont définitivement supprimés. La purge commence lorsque le MTA est lancé. Par défaut, elle est exécutée tous les sept jours.
* **pollDelay** : fréquence de vérification (en secondes) des nouveaux emails envoyés entrant dans le dossier **dataLogPath**. Par exemple, si ce paramètre est défini sur 60, cela signifie que chaque minute, le processus d’archivage passe par les fichiers .eml dans les dossiers **dataLogPath/`<date and time>`** , applique une purge si nécessaire et envoie des copies d’emails à l’adresse Cci et/ou compresse les fichiers archivés au besoin.
* **acquireLimit** : nombre de fichiers .eml traités à la fois avant que le processus d&#39;archivage ne soit réappliqué selon le paramètre **pollDelay**. Par exemple, si vous définissez le paramètre **acquireLimit** sur 100 alors que le paramètre **pollDelay** est défini sur 60, 100 fichiers .eml seront traités par minute.
* **smtpNbConnection** : nombre de connexions SMTP à l&#39;adresse email en Cci.

Veillez à ajuster ces paramètres en fonction du débit d&#39;envoi des emails. Par exemple, dans une configuration où le MTA envoie 30 000 emails par heure, vous pouvez définir le paramètre **pollDelay** sur 600, le paramètre **acquireLimit** sur 5 000 et le paramètre **smtpNbConnection** sur 2. Cela signifie qu&#39;en utilisant 2 connexions SMTP, 5 000 emails seront envoyés à l&#39;adresse en Cci toutes les 10 minutes.

## Configuration de l&#39;adresse email en Cci (on-premise) {#configuring-the-bcc-email-address--on-premise-}

[!BADGE On-premise et hybride]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"}


>[!IMPORTANT]
>
>Pour des raisons de confidentialité, les emails en Cci doivent être traités dans un système d&#39;archivage capable de stocker en toute sécurité les informations d&#39;identification personnelles (PII).

Dans le fichier **config-`<instance name>.xml`**, utilisez les paramètres suivants pour définir le serveur email SMTP vers lequel les fichiers stockés seront transférés :

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

## Passage au nouvel Email Cci {#updated-email-archiving-system--bcc-}

[!BADGE On-premise et hybride]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"}



>[!IMPORTANT]
>
>Le système d&#39;archivage des emails (Cci) a été modifié avec Adobe Campaign 17.2 (build 8795). Si vous effectuez une mise à niveau à partir d&#39;un build antérieur et que vous utilisiez déjà les fonctionnalités d&#39;archivage des emails, vous devez effectuer une mise à niveau manuelle vers le nouveau système d&#39;archivage des emails (Cci).

Pour ce faire, apportez les modifications suivantes au fichier **`config-<instance>.xml`** :

1. Retirez le paramètre **zipPath** du nœud **`<archiving>`**.
1. Définissez le paramètre **compressionFormat** sur **1** si nécessaire.
1. Définissez le paramètre **archivingType** sur **1**.

Une fois que l&#39;email Cci est configuré, veillez à sélectionner l&#39;option **[!UICONTROL Email Cci]** dans le modèle de diffusion ou la diffusion. Voir à ce propos [cette section](../../delivery/using/sending-messages.md#archiving-emails).

## Bonnes pratiques en matière d&#39;Email Cci {#best-practices}

* **Boîte aux lettres d’adresses en Cci** : vérifiez qu’elle dispose de suffisamment de capacité pour archiver tous les e-mails envoyés par le MTA.
* **Mise en pool du MTA** : la fonctionnalité d’archivage en Cci fonctionne au niveau du MTA. Elle permet de dupliquer chaque e-mail envoyé par le MTA. Le MTA pouvant être mis en pool à travers plusieurs instances (par exemple de développement, de test ou de production), voire entre plusieurs clients (dans un environnement mid-sourcing), l’utilisation de cette fonctionnalité a une incidence sur la sécurité :

   * Si vous partagez un MTA avec plusieurs clients et que l&#39;un d&#39;eux active cette option, il aura accès à la totalité des emails provenant des autres clients utilisant le même MTA. Afin d&#39;éviter une telle situation, utilisez un MTA différent pour chaque client.
   * Si vous utilisez le même MTA entre plusieurs instances (développement, test, production) d&#39;un même client, les messages envoyés depuis ces trois instances combinées seront dupliqués par l&#39;option dataLogPath.

* **Emails par connexion** : l’archivage des emails en Cci fonctionne en ouvrant une connexion et en essayant d’envoyer tous les emails via cette connexion. Adobe recommande de vérifier avec votre contact technique le nombre d’emails acceptés sur une connexion donnée. L’augmentation de ce nombre peut avoir un grand impact sur le débit Cci.
* **IP d’envoi en Cci** : actuellement, les emails en Cci ne sont pas envoyés par les proxys MTA normaux. En revanche, une connexion directe est ouverte du serveur MTA au serveur de messagerie de destination. Cela signifie que vous devrez peut-être ajouter des adresses IP supplémentaires à la liste autorisée de votre réseau, en fonction de la configuration de votre serveur de messagerie.

<!--## Email BCC with Enhanced MTA {#email-bcc-with-enhanced-mta}

For **hosted and hybrid architectures**, if you have the latest instance of Adobe Campaign, or if you have upgraded to the Enhanced MTA and using Adobe Campaign 19.2 or later, you can use Email BCC with Enhanced MTA, which is more reliable, efficient, and has lower latency.

### Activating Email BCC with Enhanced MTA

To activate this feature, you must contact your account executive to communicate the BCC email address to be used for archiving.

>[!NOTE]
>
>If you were already using BCC email archiving, you can provide the same address as you were using before or use a new one. If you keep the same, you still have to contact your account executive to set it up for you.

### Specificities and recommendations

Email BCC with Enhanced MTA is not activated at the delivery level: once this feature is enabled, **all sent deliveries** are sent to the BCC email address. There is no need to select the **[!UICONTROL Email BCC]** option in the delivery template or in the delivery.

If you were already using BCC and if you keep the same address, you could see a significant increase in the volumes sent to the BCC address.

Consequently, make sure:
* The BCC address has enough reception capacity to archive all the emails that are sent.
* You have the required MTA infrastructure capacity to receive 100% of your email volume delivered to a single address.

### Limitations

* Email BCC with Enhanced MTA delivers to the BCC email address before delivering to the recipients, which can result in BCC messages being sent even though the original deliveries may have bounced. For more on bounces, see [Understanding delivery failures](../../delivery/using/understanding-delivery-failures.md).

* There is no reporting available on the delivery status of the emails sent to the BCC email address.-->