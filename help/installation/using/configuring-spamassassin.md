---
product: campaign
title: Paramétrage de SpamAssassin
description: Paramétrage de SpamAssassin
feature: Installation, Instance Settings
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 1f1004e2-dcd2-4ec5-98ec-720c205646d5
TQID: https://experienceleague.adobe.com/vdeIEtt5-uhrKN-DcrRJQRmKV2zGin7BuXkPia4b25g
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 1029
ht-degree: 64%

---

# Paramétrage de SpamAssassin{#configuring-spamassassin}



>[!NOTE]
>
>Certaines configurations ne peuvent être effectuées que par Adobe pour les déploiements hébergés par Adobe. Par exemple, pour accéder aux fichiers de configuration du serveur et de l’instance. Pour en savoir plus sur les différents déploiements, consultez la section [Modèles d&#39;hébergement](../../installation/using/hosting-models.md) ou [cette page](../../installation/using/capability-matrix.md).

## Vue d&#39;ensemble {#overview}

SpamAssassin est un logiciel conçu pour filtrer les e-mails indésirables. Conjointement avec ce logiciel, Adobe Campaign peut attribuer un score aux emails et déterminer si un message est susceptible d&#39;être considéré comme indésirable avant le lancement de la diffusion. Pour ce faire, SpamAssassin doit être installé et configuré sur le ou les serveurs applicatifs d&#39;Adobe Campaign et requiert un certain nombre de modules additionnels en Perl pour fonctionner.

Le déploiement et l&#39;intégration de SpamAssassin décrits dans ce chapitre reposent sur l&#39;installation logicielle par défaut, tout comme les règles de filtrage et de scores, qui sont celles fournies par SpamAssassin sans aucune modification ni optimisation. L’attribution des scores et la qualification des messages reposent exclusivement sur la configuration des options de SpamAssassin et sur les règles de filtrage. Les administrateurs réseau sont chargés de les adapter aux besoins de leur entreprise.

>[!IMPORTANT]
>
>La qualification des emails comme indésirables par SpamAssassin repose entièrement sur les règles de filtrage et de scoring.
>
>Ces règles doivent donc être mises à jour au moins une fois par jour pour que votre installation de SpamAssassin et son intégration dans Adobe Campaign soient entièrement fonctionnelles et pour garantir la pertinence des scores attribués à vos diffusions avant envoi.
>
>Cette mise à jour est de la responsabilité de l&#39;administrateur serveur qui héberge SpamAssassin.

L’utilisation de SpamAssassin dans Adobe Campaign donne une indication sur le comportement possible des serveurs de messagerie qui utilisent SpamAssassin lorsqu’ils reçoivent des emails envoyés par Adobe Campaign. Cependant, il est possible que les serveurs de messagerie des fournisseurs d&#39;accès Internet ou les serveurs de messagerie en ligne considèrent toujours les messages envoyés par Adobe Campaign comme indésirables.

Le déploiement de SpamAssassin et de ses modules en Perl nécessite impérativement que les serveurs d&#39;application Adobe Campaign sur lesquels ils sont installés aient accès à Internet via une connexion HTTP (flux TCP/80).

## Installation sur une machine Windows {#installing-on-a-windows-machine}

Pour installer et configurer SpamAssassin sous Windows afin d&#39;en permettre l&#39;intégration avec Adobe Campaign, les étapes sont les suivantes :

1. Installer SpamAssassin
1. Intégrer SpamAssassin dans Adobe Campaign

### Installation de SpamAssassin {#installing-spamassassin}

1. Connectez-vous au [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/fr/campaign.html) à l’aide de vos informations d’identification d’utilisateur. En savoir plus sur la distribution de logiciels sur [cette page](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=fr).
1. Téléchargez le fichier **Neolane Spam Assassin (Windows Installation) (2.0)** (neolane_spamassassin.2.0.zip).
1. Copiez ce fichier sur le serveur Adobe Campaign puis décompressez-le.

   >[!NOTE]
   >
   >Vous pouvez décompresser le fichier où vous le souhaitez, à condition que le chemin d’accès soit composé de l’un des caractères d’expression régulière suivants : **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. Le chemin d’installation ne doit pas contenir d’espaces.

1. Accédez au dossier dans lequel vous avez décompressé le fichier puis double-cliquez sur le fichier **run_me.bat** afin de lancer le script d&#39;installation.

   Si un Shell Windows apparaît et reste affiché durant plusieurs secondes, attendez que l’installation et la mise à jour soient terminées, puis cliquez sur **Entrée**.

   Si le shell Windows n’apparaît pas ou s’il apparaît puis disparaît instantanément, procédez comme suit : double-cliquez sur le fichier **portableShell.bat** afin d&#39;afficher un shell Windows et vérifiez que le chemin du shell correspond au dossier dans lequel le fichier **spamassassin.zip** a été décompressé. Si ce n’est pas le cas, accédez-y à l’aide de la commande **cd**.

   Saisissez **run_me.bat** puis cliquez sur **Entrée** pour lancer le processus d’installation et de mise à jour. L’opération renvoie l’une des valeurs suivantes afin d’indiquer le résultat de la mise à jour.

   * **0** : une mise à jour a été effectuée.
   * **1** : aucune nouvelle mise à jour n&#39;était disponible.
   * **2** : aucune nouvelle mise à jour n&#39;était disponible.
   * **3** : la mise à jour a échoué lors de la vérification préalable.
   * **4** ou plus : une erreur s&#39;est produite.

1. Vérifiez que l&#39;installation de SpamAssassin s&#39;est bien déroulée en effectuant le test GTUBE (Generic Test for Unsolicited Bulk Email) selon la procédure décrite ci-après :

   1. Créez un fichier texte et enregistrez-le sous **C:\TestSpamMail.txt**.
   1. Insérez le contenu suivant dans ce fichier :

      ```
      Subject: Test Spam Mail (GTUBE)
      Message-ID: <1010101@example.net>
      Date: MM-DD-YY
      From: Sender <sender@example.net>
      To: Recipient <recipient@example.net>
      Precedence: junk
      MIME-Version: 1.0
      Content-Type: text/plain; charset=us-ascii
      Content-Transfer-Encoding: 7bit
      
      XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
      ```

   1. Double-cliquez sur le fichier **portableShell.bat** afin d&#39;afficher un Shell Windows puis lancez la commande suivante (où « `<root>` » désigne le dossier créé lors de la décompression du fichier **spamassassin.zip**) :

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      Le contenu de cet e-mail de test déclenche un score de 1 000 points par SpamAssassin. Cela signifie qu’il a été détecté comme indésirable et que l’installation a réussi et est entièrement fonctionnelle.

### Intégration de SpamAssassin dans Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. Editez le fichier **`[INSTALL]/conf/serverConf.xml`**. Tous les paramètres disponibles dans le fichier **serverConf.xml** sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).
1. Modifiez la valeur de l&#39;attribut **spamCheck** des éléments **command** dans le nœud **Web**. Pour cela, exécutez la commande suivante :

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >Tous les chemins doivent être absolus.

   Arrêtez puis redémarrez le service **[!UICONTROL Adobe Campaign]**.

1. Vérifiez l&#39;intégration de SpamAssassin dans Adobe Campaign en effectuant le test GTUBE (Generic Test for Unsolicited Bulk Email) :

   Double-cliquez sur le fichier **portableshell.bat**. Cela déclenche l&#39;affichage d&#39;un shell Windows. Exécutez ensuite la commande suivante :

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   Le contenu de cet e-mail de test déclenche l&#39;attribution de 1 000 points par SpamAssassin. Cela signifie qu’il a été détecté comme indésirable et que l’intégration à Adobe Campaign a été réussie et est entièrement fonctionnelle.

1. Mettez à jour les règles de filtrage et de scores de SpamAssassin

   Pour une première mise à jour des règles de filtrage et de scores, lancez **portableShell.bat** et exécutez la commande suivante :

   ```
   sa-update --no-gpg
   ```

   Pour effectuer la mise à jour automatisée des règles de filtrage et de scores, utilisez cette même commande dans une tâche système planifiée :

   ```
   sa-update --no-gpg
   ```

## Installation sur une machine Linux {#installing-on-a-linux-machine}

### Etapes d&#39;installation sous Debian {#installation-steps-in-debian}

* Au besoin, installez Perl et SpamAssassin à l&#39;aide de la commande suivante :

  ```
  apt-get install spamassassin libxml-writer-perl
  ```

* Dans le fichier **serverConf.xml** (disponible sous `/usr/local/[INSTALL]/nl6/conf/`), modifiez la ligne **spamCheck** comme suit :

  ```
  <spamCheck command="perl
  /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
  ```

### Etapes d&#39;installation sous RHEL/CentOS {#installation-steps-in-rhel-centos}

Au besoin, installez Perl et récupérez les packages à l&#39;aide de CPAN :

```
cpan Digest::SHA1
cpan HTML::Parser
cpan Net::DNS
cpan Mail::SPF 
cpan XML::LibXML
cpan XML::Writer
cpan Mail::SpamAssassin
```

### Mise à jour des règles de filtrage {#updating-filter-rules}

Les règles de filtrage peuvent être mises à jour automatiquement à l’aide de l’outil **sa-update**. Pour plus d’informations, consultez le site web officiel de SpamAssassin [https://spamassassin.apache.org/](https://spamassassin.apache.org/).

Sous Debian, la mise à jour est automatique et quotidienne.

Si cela ne devait pas être le cas (par exemple, dans le cas d&#39;une installation manuelle de Debian), créez un script afin d&#39;automatiser la mise à jour des jeux de règles.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

Insérez ce script dans **crontab** à l&#39;aide de la commande suivante :

```
crontab-e
```

### Optimisation des performances {#performance-optimization}

Pour améliorer les performances sous Linux, modifiez le fichier **/etc/spamassassin/local.cf** et ajoutez la ligne suivante à la fin du fichier :

```
dns_available no
```
