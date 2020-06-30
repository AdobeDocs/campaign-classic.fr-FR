---
title: Paramétrage de SpamAssassin
seo-title: Paramétrage de SpamAssassin
description: Paramétrage de SpamAssassin
seo-description: null
page-status-flag: never-activated
uuid: 327548c0-d621-4417-9fc9-b0bf30251dc0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: aa37bdc6-0f85-4eca-859f-e8b15083cfb5
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 1a9d4c9eadf996d37481f33636eae98e482ac115
workflow-type: ht
source-wordcount: '986'
ht-degree: 100%

---


# Paramétrage de SpamAssassin{#configuring-spamassassin}

>[!NOTE]
>
>Certains paramétrages côté serveur ne peuvent être réalisés que par Adobe pour les déploiements hébergés par Adobe, par exemple pour accéder aux fichiers de configuration de l&#39;instance et du serveur. Pour plus d&#39;informations sur les différents déploiements, reportez-vous à la section [Modèles d&#39;hébergement](../../installation/using/hosting-models.md) ou à [cet article](https://helpx.adobe.com/fr/campaign/kb/acc-on-prem-vs-hosted.html).

## Présentation {#overview}

SpamAssassin est un logiciel destiné à filtrer les emails indésirables. Intégré à Adobe Campaign, il permet d’attribuer un score aux emails créés dans la plateforme et d’évaluer le risque que les messages soient considérés comme indésirables par les messageries des destinataires avant qu’une diffusion ne soit lancée. Pour cela, SpamAssassin doit être installé et configuré sur le ou les serveurs d’application d’Adobe Campaign et requiert un certain nombre de modules additionnels en Perl pour fonctionner.

Le déploiement et l&#39;intégration de SpamAssassin décrits dans ce chapitre sont basés sur l&#39;installation par défaut du logiciel, de même que les règles de filtrage et de scores qui sont celles fournies par SpamAssassin sans modification ou optimisation aucune. L&#39;attribution des scores et la qualification des messages reposant exclusivement sur la configuration des options de SpamAssassin et sur l&#39;utilisation des jeux de règles de filtrage, il reviendra à chaque administrateur réseau de les adapter aux besoins de son entreprise.

>[!IMPORTANT]
>
>La qualification des emails comme indésirables par SpamAssassin repose entièrement sur les règles de filtrage et de scoring.
>
>Ces règles doivent donc être mises à jour au moins une fois par jour pour que votre installation de SpamAssassin et son intégration dans Adobe Campaign soient entièrement fonctionnelles et pour garantir la pertinence des scores attribués à vos diffusions avant envoi.
>
>Cette mise à jour est de la responsabilité de l&#39;administrateur serveur qui héberge SpamAssassin.

L&#39;utilisation de SpamAssassin dans Adobe Campaign permet de donner une indication sur le comportement éventuel des serveurs de messagerie, utilisant eux-mêmes SpamAssassin, à la réception des emails envoyés par Adobe Campaign. Il se peut toutefois que les serveurs de messagerie des fournisseurs d&#39;accès Internet ou les messageries Web considèrent malgré tout les messages envoyés par Adobe Campaign comme indésirables.

Le déploiement de SpamAssassin et de ses modules en Perl nécessite impérativement que les serveurs d&#39;application Adobe Campaign sur lesquels ils sont installés aient accès à Internet via une connexion HTTP (flux TCP/80).

## Installation sur une machine Windows {#installing-on-a-windows-machine}

Pour installer et configurer SpamAssassin sous Windows afin d&#39;en permettre l&#39;intégration avec Adobe Campaign, les étapes sont les suivantes :

1. Installer SpamAssassin
1. Intégrer SpamAssassin dans Adobe Campaign

### Installation de SpamAssassin {#installing-spamassassin}

1. Connectez-vous au [portail Extranet](http://support.neolane.net) à l&#39;aide de vos identifiants.
1. Accédez au **Centre de Téléchargement** puis parcourrez la page jusqu&#39;à atteindre la section **Utils**.
1. Téléchargez le fichier **Neolane Spam Assassin (Windows Installation) (2.0)** (neolane_spamassassin.2.0.zip).
1. Copiez ce fichier sur le serveur Adobe Campaign puis décompressez-le.

   >[!NOTE]
   >
   >Vous pouvez décompresser le fichier à l&#39;emplacement de votre choix. Cependant, assurez-vous que le chemin d&#39;accès à ce dernier comporte uniquement des caractères de l&#39;expression régulière suivante : **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. Le chemin d&#39;installation ne doit pas comporter d&#39;espace.

1. Accédez au dossier dans lequel vous avez décompressé le fichier puis double-cliquez sur le fichier **run_me.bat** afin de lancer le script d&#39;installation.

   Si un Shell Windows apparaît et reste affiché durant plusieurs secondes, attendez que l&#39;installation et la mise à jour soient terminées puis appuyez sur **Entrée**.

   Si le Shell Windows n&#39;apparaît pas ou s&#39;il apparaît puis disparaît instantanément, procédez comme suit : double-cliquez sur le fichier **portableShell.bat** afin d&#39;afficher un Shell Windows. Assurez-vous que le chemin du Shell correspond au dossier dans lequel le fichier **spamassassin.zip** a été décompressé. Si ce n&#39;est pas le cas, accédez-y grâce à la commande **cd**.

   Entrez **run_me.bat** puis appuyez sur **Entrée** afin de lancer le processus d&#39;installation et de mise à jour. L&#39;opération renvoie l&#39;une des valeurs suivantes afin d&#39;indiquer le résultat de la mise à jour :

   * **0** : une mise à jour a été effectuée.
   * **1** : aucune nouvelle mise à jour n&#39;était disponible.
   * **2** : aucune nouvelle mise à jour n&#39;était disponible.
   * **3** : la mise à jour a échoué lors de la vérification préalable.
   * **4** ou plus : une erreur s&#39;est produite.

1. Vérifiez que l&#39;installation de SpamAssassin s&#39;est bien déroulée en effectuant le test GTUBE (Generic Test for Unsolicited Bulk Email) selon la procédure décrite ci-après :

   1. Créez un fichier texte et enregistrez-le sous **C:\TestSpamMail.txt**.
   1. Insérez le contenu suivant dans ce fichier :

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

      Le contenu de cet e-mail de test déclenche l&#39;attribution par SpamAssassin d&#39;un score de 1000 points au message. Cela signifie qu&#39;il a bien été détecté comme indésirable et que l&#39;installation a été correctement réalisée et est désormais fonctionnelle.

### Intégration de SpamAssassin dans Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. Editez le fichier **`[INSTALL]/conf/serverConf.xml`**. Tous les paramètres disponibles dans le fichier **serverConf.xml** sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).
1. Modifiez la valeur de l&#39;attribut **spamCheck** de l&#39;élément **command** du nœud **Web**. Pour cela, exécutez la commande suivante :

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >Tous les chemins doivent être absolus.

   Arrêtez puis redémarrez le service **[!UICONTROL Adobe Campaign]**.

1. Vérifiez l&#39;intégration de SpamAssassin dans Adobe Campaign en effectuant le test GTUBE (Generic Test for Unsolicited Bulk Email) :

   Double-cliquez sur le fichier **portableShell.bat** afin d&#39;afficher un Shell Windows puis lancez la commande suivante :

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   Le contenu de cet e-mail de test déclenche l&#39;attribution par SpamAssassin d&#39;un score de 1000 points au message. Cela signifie qu&#39;il a bien été détecté comme indésirable et que l&#39;intégration dans Adobe Campaign a été correctement réalisée. Elle est désormais fonctionnelle.

1. Mettez à jour les règles de filtrage et de scores de SpamAssassin

   Pour une première mise à jour des règles de filtrage et de scores, lancez **portableShell.bat** et exécutez la commande suivante :

   ```
   sa-update --no-gpg
   ```

   Pour effectuer la mise à jour automatisée des règles de filtrage et de scores, utilisez cette même commande dans une tâche système planifiée :

   ```
   sa-update --no-gpg
   ```

## Installation sur une machine Linux {#installing-on-a-linux-machine}

### Etapes d&#39;installation sous Debian {#installation-steps-in-debian}

* Au besoin, installez Perl et SpamAssassin à l&#39;aide de la commande suivante :

   ```
   apt-get install spamassassin libxml-writer-perl
   ```

* Dans le fichier **serverConf.xml** (disponible sous `/usr/local/[INSTALL]/nl6/conf/`), modifiez la ligne **spamCheck** comme suit :

   ```
   <spamCheck command="perl
   /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
   ```

### Etapes d&#39;installation sous RHEL/CentOS {#installation-steps-in-rhel-centos}

Au besoin, installez Perl et récupérez les packages à l&#39;aide de CPAN :

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

Les règles de filtrage peuvent être mises à jour automatiquement à l&#39;aide de l&#39;outil **sa-update**. Reportez-vous au site officiel de SpamAssasin [http://spamassassin.apache.org/](http://spamassassin.apache.org/) pour plus d&#39;informations.

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

Pour améliorer les performances sous Linux, éditez le fichier **/etc/spamassassin/local.cf** et ajoutez la ligne suivante à la fin du fichier :

```
dns_available no
```

