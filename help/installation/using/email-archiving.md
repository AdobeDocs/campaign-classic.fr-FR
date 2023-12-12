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
source-git-commit: e808e71ccf949bdaf735cdb2895389f03638bd71
workflow-type: ht
source-wordcount: '1224'
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
* Seuls les e-mails envoyés sont pris en compte, les rebonds ne le sont pas.
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
>Les équipes en charge de l’implémentation doivent s’assurer que les conditions de sécurité permettent l’accès au dossier défini via les paramètres **dataLogPath**.

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
>Les deliveryID et broadlogID sont ceux du serveur de midsourcing lorsque le statut des e-mails n’est pas envoyé. Une fois que le statut a été remplacé par **[!UICONTROL Envoyé]**, ces identifiants proviennent du serveur marketing.

### Paramètres {#parameters}

Une fois le chemin d’accès au dossier local défini, ajoutez et modifiez les éléments suivants selon vos besoins dans le fichier **config-`<instance name>.xml`**. Vous trouverez ci-dessous les valeurs par défaut :

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="1" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat** : format utilisé lors de la compression des fichiers .eml. Les valeurs possibles sont les suivantes :

  **0** : pas de compression (valeur par défaut)

  **1 : compression (au format .zip)**

* **compressBatchSize** : nombre de fichiers .eml ajoutés à une archive (fichier .zip).


* **archivingType** : stratégie d’archivage à utiliser. La seule valeur possible est **1**. Les copies brutes des e-mails sont enregistrées au format .eml dans le dossier **dataLogPath** et sont envoyées à l’adresse e-mail Cci via SMTP. Une fois que les copies d’e-mail sont envoyées à l’adresse Cci, le nom du fichier d’archive devient **`<deliveryid>-<broadlogid>-sent-archived.eml`** et le fichier est déplacé dans le dossier **dataLogPath/archives**. Le chemin d’accès au fichier de l’email envoyé et archivé Cci est alors **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

  <!--
  **0**: raw copies of sent emails are saved in .eml format to the **dataLogPath** folder (default value). An archiving copy of the **`<deliveryid>-<broadlogid>-sent.eml`** file is saved to the **dataLogPath/archives** folder. The sent email file path becomes **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.-->

* **expirationDelay** : nombre de jours pendant lesquels les fichiers .eml sont conservés pour archivage. Après ce délai, ils sont automatiquement déplacés vers le dossier **dataLogPath/archives** en vue de leur compression. Par défaut, les fichiers .eml expirent après deux jours.
* **purgeArchivesDelay** : nombre de jours pendant lesquels les archives sont conservées dans le dossier **dataLogPath/`<archives>`**. Après cette période, ils sont définitivement supprimés. La purge commence lorsque le MTA est lancé. Par défaut, elle est exécutée tous les sept jours.
* **pollDelay** : fréquence de vérification (en secondes) des nouveaux e-mails envoyés entrant dans le dossier **dataLogPath**. Par exemple, si ce paramètre est défini sur 60, cela signifie que chaque minute, le processus d’archivage passe par les fichiers .eml dans les dossiers **dataLogPath/`<date and time>`**, applique une purge si nécessaire et envoie des copies d’e-mails à l’adresse Cci et/ou compresse les fichiers archivés au besoin.
* **acquireLimit** : nombre de fichiers .eml traités à la fois avant que le processus d’archivage ne soit à nouveau appliqué, en fonction du paramètre **pollDelay**. Par exemple, si vous définissez le paramètre **acquireLimit** sur 100 et le paramètre **pollDelay** sur 60, 100 fichiers .eml seront traités par minute.
* **smtpNbConnection** : nombre de connexions SMTP à l’adresse e-mail en Cci.

Veillez à ajuster ces paramètres en fonction du débit d’envoi des e-mails. Par exemple, dans une configuration où le MTA envoie 30 000 e-mails par heure, vous pouvez définir les paramètres **pollDelay** sur 600, **acquireLimit** sur 5 000 et **smtpNbConnection** sur 2. 5 000 e-mails seront alors envoyés à l’adresse Cci toutes les 10 minutes via 2 connexions SMTP.

## Configurer l’adresse e-mail en Cci (on-premise) {#configuring-the-bcc-email-address--on-premise-}

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

<!--
## Moving to the new Email BCC {#updated-email-archiving-system--bcc-}

[!BADGE On-premise & Hybrid]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"}

>[!IMPORTANT]
>
>The email archiving system (BCC) changed with Adobe Campaign 17.2 (build 8795). If you are upgrading from an older build and were already using email archiving capabilities, you must upgrade manually to the new email archiving system (BCC).

To do this, make the following changes to the **`config-<instance>.xml`** file:

1. Remove the **zipPath** parameter from the **`<archiving>`** node.
1. Set the **compressionFormat** parameter to **1** if needed.
1. Set the **archivingType** parameter to **1**.

Once email BCC is configured, make sure you select the **[!UICONTROL Email BCC]** option in the delivery template or the delivery. For more on this, see [this section](../../delivery/using/sending-messages.md#archiving-emails).
-->

## Bonnes pratiques en matière d&#39;Email Cci {#best-practices}

* **Boîte aux lettres d’adresses en Cci** : vérifiez qu’elle dispose de suffisamment de capacité pour archiver tous les e-mails envoyés par le MTA.
* **Mise en pool du MTA** : la fonctionnalité d’archivage en Cci fonctionne au niveau du MTA. Elle permet de dupliquer chaque e-mail envoyé par le MTA. Le MTA pouvant être mis en pool à travers plusieurs instances (par exemple de développement, de test ou de production), voire entre plusieurs clients (dans un environnement mid-sourcing), l’utilisation de cette fonctionnalité a une incidence sur la sécurité :

   * Si vous partagez un MTA avec plusieurs clients et que l&#39;un d&#39;eux active cette option, il aura accès à la totalité des emails provenant des autres clients utilisant le même MTA. Afin d&#39;éviter une telle situation, utilisez un MTA différent pour chaque client.
   * Si vous utilisez le même MTA entre plusieurs instances (développement, test, production) d’un même client, les messages envoyés depuis ces trois instances combinées seront dupliqués par l’option dataLogPath.

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