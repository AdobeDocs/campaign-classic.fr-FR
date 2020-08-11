---
title: Paramétrage du serveur Campaign
seo-title: Paramétrage du serveur Campaign
description: Paramétrage du serveur Campaign
seo-description: null
page-status-flag: never-activated
uuid: a1fadad2-e888-4dd8-bc1f-04df16ba7d46
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: f296676e-3bf1-47da-8239-f5ae54e52fc0
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 4869eb41f942a89c48bc213913c44b70ae777bfc
workflow-type: ht
source-wordcount: '555'
ht-degree: 100%

---


# Paramétrage du serveur Campaign{#campaign-server-configuration}

La section suivante présente les paramétrages obligatoires du serveur pour garantir le bon fonctionnement d&#39;Adobe Campaign dans la plupart des configurations.

D’autres configurations sont disponibles dans [Paramétrage du serveur Campaign](../../installation/using/configuring-campaign-server.md).

>[!NOTE]
>
>Les paramétrages côté serveur ne peuvent être réalisés que par Adobe pour les déploiements hébergés par Adobe. Pour plus d&#39;informations sur les différents déploiements, reportez-vous à la section [Modèles d&#39;hébergement](../../installation/using/hosting-models.md) ou à [cet article](https://helpx.adobe.com/fr/campaign/kb/acc-on-prem-vs-hosted.html).

## Identifiant &#39;internal&#39;{#internal-identifier}

L&#39;identifiant **internal** est un login technique à utiliser lors de la phase d&#39;installation, pour les paramétrages techniques d&#39;administration et de maintenance. Ce login n&#39;est pas associé à une instance.

L&#39;opérateur connecté avec cet identifiant possède tous les droits, sur toutes les instances. Après une nouvelle installation, cet identifiant n&#39;a pas de mot de passe. Vous devez définir ce mot de passe manuellement.

Utilisez la commande suivante :

```
nlserver config -internalpassword
```

Les informations suivantes sont alors affichées. Saisissez et confirmez le nouveau mot de passe :

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Fichiers de configuration {#configuration-files}

Les fichiers de configuration sont enregistrés dans le dossier **conf** du dossier d’installation Adobe Campaign. La configuration est répartie sur deux fichiers :

* **`config-<instance>.xml`** (où **instance** est le nom de l&#39;instance) : configuration spécifique d&#39;une instance. Si vous mutualisez votre serveur entre plusieurs instances, vous devez enregistrer les paramètres spécifiques à chaque instance dans son fichier associé.
* **serverConf.xml** : configuration générale pour toutes les instances. Ce fichier regroupe les paramètres techniques du serveur Adobe Campaign : ces paramètres sont communs à toutes les instances. Vous trouverez ci-après la description de certains de ces paramètres. Consultez le fichier lui-même pour afficher tous les paramètres disponibles. Les différents nœuds et paramètres sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).

Vous pouvez configurer le répertoire de stockage (répertoire **var**) des données Adobe Campaign (logs, téléchargements, redirections, etc.). Pour cela, utilisez la variable système **XTK_VAR_DIR** :

* Sous Windows, indiquez la valeur suivante dans la variable système **XTK_VAR_DIR**.

   ```
   D:\log\AdobeCampaign
   ```

* Sous Linux, rendez-vous dans le fichier **customer.sh** et indiquez : **export XTK_VAR_DIR=/app/log/AdobeCampaign**.

   Voir à ce sujet la section [Personnaliser les paramètres](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).

## Activation des processus {#enabling-processes}

L’activation (ou la désactivation) des processus Adobe Campaign se fait sur le serveur à partir des fichiers **config-default.xml** et **`config-<instance>.xml`**.

Pour appliquer les modifications dans ces fichiers, si le service Adobe Campaign est démarré, vous devez exécuter la commande **nlserver config -reload**.

On distingue deux types de processus : multi-instance et mono-instance.

* **multi-instance** : un seul processus est démarré pour toutes les instances, il s&#39;agit des processus **web**, **syslogd** et **trackinglogd**.

   L’activation peut être configurée à partir du fichier **config-default.xm**.

   Déclaration d&#39;un serveur Adobe Campaign pour l&#39;accès aux consoles clientes et pour la redirection (tracking) :

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   Dans cet exemple, le fichier est modifié à l’aide d’une commande **vi** sous Linux. Il peut être modifié à l’aide de n’importe quel éditeur **.txt** ou **.xml**.

* **mono-instance** : un processus est démarré par instance (modules : **mta**, **wfserver**, **inMail**, **sms** et **stat**).

   L&#39;activation est paramétrable à partir du fichier de configuration de l&#39;instance :

   ```
   config-<instance>.xml
   ```

   Déclaration d&#39;un serveur pour la diffusion, l&#39;exécution des instances de workflow et la récupération des mails rebond :

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

## Paramètres de diffusion {#delivery-settings}

Les paramètres de diffusion doivent être configurés dans le dossier **serverConf.xml**.

* **Configuration DNS** : renseignez le domaine de diffusion ainsi que les adresses IP (ou host) des serveurs DNS utilisés pour répondre aux requêtes DNS de type MX par le module MTA à partir de **`<dnsconfig>`**.

   >[!NOTE]
   >
   >Le paramètre **nameServers** est indispensable pour une installation sous Windows. Pour une installation Linux, il doit être laissé vide.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

Les autres paramètres de diffusion disponibles dans ce fichier sont présentés dans la section [Personnalisation des paramètres de diffusion](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).

Consultez également la section [Délivrabilité des emails](../../installation/using/email-deliverability.md).
