---
solution: Campaign Classic
product: campaign
title: Configuration du serveur Campaign
description: Configuration du serveur Campaign
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
translation-type: tm+mt
source-git-commit: 0c83c989c7e3718a989a4943f5cde7ad4717fddc
workflow-type: tm+mt
source-wordcount: '2812'
ht-degree: 96%

---

# Configuration du serveur Campaign{#configuring-campaign-server}

La section ci-dessous décrit les configurations côté serveur qui peuvent être exécutées en fonction de vos besoins et des spécificités de votre environnement.

Ces configurations doivent être exécutées par les administrateurs et uniquement pour les modèles d’hébergement **On-premise.**

Pour les déploiements **hébergés**, les paramètres côté serveur peuvent uniquement être configurés par Adobe. Cependant, certains paramètres peuvent être configurés dans le panneau de contrôle (par exemple, la gestion des listes autorisées d&#39;adresses IP ou les autorisations d&#39;URL).

>[!NOTE]
>
>Le panneau de contrôle est accessible à tous les utilisateurs administrateurs. Les étapes permettant d’accorder un accès administrateur à un utilisateur sont présentées dans [cette section](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=fr#discover-control-panel).
>
>Notez que votre instance doit être hébergée sur AWS et mise à niveau avec la dernière version de [Gold Standard](../../rn/using/gs-overview.md) ou la dernière version de [GA (21.1)](../../rn/using/latest-release.md). Découvrez comment vérifier votre version dans [cette section](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Pour vérifier si votre instance est hébergée sur AWS, suivez les étapes détaillées dans [cette page](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

Pour plus d’informations, consultez les sections suivantes :

* [Documentation relative au Panneau de contrôle](https://docs.adobe.com/content/help/fr-FR/control-panel/using/control-panel-home.html)
* [Modèles d&#39;hébergement](../../installation/using/hosting-models.md)
* [Matrice des fonctionnalités On-premise et hébergées de Campaign Classic](../../installation/using/capability-matrix.md)
* [Etapes de configuration des modèles hybrides et hébergés](../../installation/using/hosting-models.md)

Les fichiers de configuration de Campaign Classic sont stockés dans le dossier **conf** du dossier d’installation d’Adobe Campaign. La configuration est répartie sur deux fichiers :

* **serverConf.xml** : configuration générale pour toutes les instances. Ce fichier regroupe les paramètres techniques du serveur Adobe Campaign : ces paramètres sont communs à toutes les instances. Vous trouverez ci-après la description de certains de ces paramètres. Les différents nœuds et paramètres sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** (où **instance** est le nom de l’instance) : configuration spécifique de l’instance. Si vous partagez votre serveur entre plusieurs instances, entrez les paramètres propres à chaque instance dans le fichier correspondant.

## Configurer Tomcat {#configuring-tomcat}

### Port par défaut pour Tomcat {#default-port-for-tomcat}

Lorsque le port d’écoute 8080 du serveur Tomcat est déjà occupé par une autre application requise pour votre configuration, vous devez remplacer le port 8080 par un port disponible (8090 par exemple). Pour le modifier, modifiez le fichier **server.xml** enregistré dans le répertoire **/tomcat-8/conf** du dossier d’installation d’Adobe Campaign.

Modifiez ensuite le port des pages de relais JSP. Pour ce faire, modifiez le fichier **serverConf.xml** enregistré dans le répertoire **/conf** du répertoire d’installation d’Adobe Campaign. Tous les paramètres disponibles dans le fichier **serverConf.xml** sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

### Mapping d&#39;un dossier sous Tomcat {#mapping-a-folder-in-tomcat}

Afin de définir les paramètres propres aux clients, vous pouvez créer un fichier **user_contexts.xml** dans le dossier **/tomcat-8/conf**, qui contient également le fichier **contexts.xml**.

Ce fichier contiendra des informations du type :

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Au besoin, cette opération doit être reproduite côté serveur.

## Personnalisation des paramètres de diffusion {#personalizing-delivery-parameters}

Les paramètres de diffusion sont définis dans le fichier de configuration **serverConf.xml**. Tous les paramètres disponibles dans **serverConf.xml** sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).

La configuration générale du serveur et les commandes sont détaillées dans la section [Paramétrage du serveur Campaign](../../installation/using/campaign-server-configuration.md).

En complément, vous pouvez procéder aux paramétrages suivants, selon vos besoins et votre configuration.

### Relais SMTP {#smtp-relay}

Le module MTA agit comme un agent de transfert de mails natif pour la diffusion par le protocole SMTP (port 25).

Il est cependant possible de le remplacer par un serveur de messagerie relais si la politique de sécurité l&#39;impose. Le cas échéant, le débit global sera le relais (si le débit du serveur relais est inférieur à celui d&#39;Adobe Campaign).

Dans ce cas, ces paramètres sont définis en configurant le serveur SMTP dans la section **`<relay>`**. Vous devez spécifier l’adresse IP (ou hôte) du serveur SMTP utilisé pour transférer l’email et son port associé (25 par défaut).

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>Ce mode de fonctionnement implique des limitations importantes sur les diffusions puisqu&#39;il peut réduire considérablement le débit en raison des performances propres au serveur relais (latence, bande passante...). De plus, la capacité de qualifier les erreurs de diffusion synchrones (détectées par l&#39;analyse du trafic SMTP) sera limitée et aucun envoi ne sera possible si le serveur relais n&#39;est pas disponible.

### Processus MTA child {#mta-child-processes}

Il est possible de contrôler la population de processus enfants (maxSpareServers par défaut 2) afin d’optimiser les performances de diffusion en fonction de la puissance CPU des serveurs et des ressources réseau disponibles. Cette configuration doit être effectuée dans la section **`<master>`** de la configuration MTA sur chaque ordinateur individuel.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Voir également la section [Optimisation de l’envoi d’emails](../../installation/using/email-deliverability.md#email-sending-optimization).

### Gérer le trafic SMTP sortant avec les affinités {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>La configuration des affinités doit être cohérente d’un serveur à l’autre. Nous vous recommandons de contacter Adobe pour obtenir une configuration d’affinité, car les modifications de configuration doivent être répliquées sur tous les serveurs d’applications qui exécutent la MTA.

Vous pouvez améliorer le trafic SMTP sortant grâce à des affinités avec les adresses IP.

Pour cela, les étapes sont les suivantes :

1. Saisissez les affinités dans la section **`<ipaffinity>`** du fichier **serverConf.xml**.

   Vous pouvez définir plusieurs noms pour une même affinité : ces noms doivent être séparés les uns des autres par le caractère **;**.

   Exemple:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   Reportez-vous au fichier **serverConf.xml** pour consulter les paramètres à utiliser.

1. Pour permettre la sélection de l&#39;affinité dans les listes déroulantes, vous devez ajouter le ou les noms des affinités dans l&#39;énumération **IPAffinity**.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >Les énumérations sont présentées dans [ce document](../../platform/using/managing-enumerations.md).

   Il est ensuite possible de sélectionner l&#39;affinité à utiliser, comme ci-dessous au niveau des typologies :

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >Vous pouvez également vous référer à la section [Configuration des serveurs de diffusion](../../installation/using/email-deliverability.md#delivery-server-configuration).

## Autorisations d’URL {#url-permissions}

La liste par défaut des URL pouvant être appelées par des codes JavaScript (workflows, etc.) de vos instances Campaign Classic est limitée. Il s’agit des URL qui permettent à vos instances de fonctionner correctement.

Par défaut, les instances ne sont pas autorisées à se connecter à des URL externes. Cependant, il est possible d’ajouter des URL externes à la liste des URL autorisées afin que votre instance puisse s’y connecter. Vous pouvez ainsi connecter vos instances Campaign à des systèmes externes, comme des serveurs SFTP ou des sites web, afin d’activer le transfert de fichiers et/ou de données.

Une fois qu’une URL est ajoutée, elle est référencée dans le fichier de configuration de l’instance (serverConf.xml).

Vous pouvez gérer les autorisations d’URL en fonction de votre modèle d’hébergement :

* **Hybride** ou **On-premise** : ajoutez les URL à autoriser dans le fichier **serverConf.xml**. Des informations détaillées sont disponibles dans la section ci-dessous.
* **Hébergé** : ajoutez les URL à autoriser via le **Panneau de contrôle**. Pour plus d’informations, consultez la [documentation dédiée](https://docs.adobe.com/content/help/fr-FR/control-panel/using/instances-settings/url-permissions.html).

   >[!NOTE]
   >
   >Le panneau de contrôle est accessible à tous les utilisateurs administrateurs. Les étapes permettant d’accorder un accès administrateur à un utilisateur sont présentées dans [cette section](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel).
   >
   >Notez que votre instance doit être hébergée sur AWS et mise à niveau avec la dernière version de [Gold Standard](../../rn/using/gs-overview.md). Découvrez comment vérifier votre version dans [cette section](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Pour vérifier si votre instance est hébergée sur AWS, suivez les étapes détaillées dans [cette page](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

Avec les modèles d’hébergement **Hybride** et **On-premise** , l’administrateur doit référencer une nouvelle **urlPermission** dans le fichier **serverConf.xml**. Tous les paramètres disponibles dans le fichier **serverConf.xml** sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).

Il existe trois modes de protection des connexions :

* **Blocage** : toutes les URL qui ne figurent pas sur la liste autorisée sont bloquées et un message d&#39;erreur s&#39;affiche. Il s&#39;agit du mode par défaut après un postupgrade.
* **Permissif** : toutes les URL qui ne figurent pas sur la liste autorisée sont autorisées.
* **Avertissement** : toutes les URL qui ne figurent pas sur la liste autorisée sont autorisées, mais l&#39;interpréteur JS émet un avertissement pour que l&#39;administrateur puisse les collecter. Ce mode ajoute des messages d’avertissement JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>Par défaut, le client des nouveaux clients utilise le **mode de blocage**. S&#39;ils ont besoin d&#39;autoriser une nouvelle URL, ils doivent contacter leur administrateur pour l&#39;ajouter à la liste autorisée.
>
>Les clients existants provenant d&#39;une migration peuvent utiliser pendant un certain temps le **mode d&#39;avertissement**. Ils doivent entre-temps analyser le trafic sortant pour autoriser les URL. Une fois la liste des URL autorisées définie, ils doivent contacter leur administrateur pour ajouter les URL à la liste autorisée et activer le **mode de blocage**.

## Sécurité et relais des pages dynamiques {#dynamic-page-security-and-relays}

Par défaut, toutes les pages dynamiques sont automatiquement liées au serveur Tomcat **local** de la machine dont le module web a démarré. Cette configuration est saisie dans la section **`<url>`** de la configuration du relais de requête pour le fichier **ServerConf.xml**. Tous les paramètres disponibles dans le fichier **serverConf.xml** sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).

Vous pouvez également relayer l&#39;exécution de la page dynamique sur un serveur **distant**, dans le cas où le module Web n&#39;est pas activé sur la machine. Pour cela, vous devez remplacer la valeur **localhost** par le nom de la machine distante pour les pages JSP et JSSP, les applications Web, les rapports et les chaînes.

Pour plus d’informations sur les différents paramètres disponibles, consultez le fichier de configuration **serverConf.xml**.

Pour les pages JSP, le paramétrage par défaut est le suivant :

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign utilise les pages JSP suivantes :

* /nl/jsp/**soaprouter.jsp** : connexion des consoles clientes et services Web (API SOAP),
* /nl/jsp/**m.jsp** : pages miroir,
* /nl/jsp/**logon.jsp** : accès aux rapports par le Web et au déploiement de la console cliente,
* /nl/jsp/**s.jsp** : utilisation du marketing viral (parrainage et réseaux sociaux).

Les JSSP utilisées pour Mobile App Channel sont les suivantes :

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Exemple:**

Vous pouvez empêcher la connexion des postes clients de l&#39;extérieur. Pour cela, il suffit de restreindre l&#39;exécution de **soaprouter.jsp** et de n&#39;autoriser que l&#39;exécution des pages miroirs, des liens viraux, des formulaires web et des ressources publiques.

Les paramètres sont les suivants :

```
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/> 
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="m.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="s.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="webForm.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/webApp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/jssp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/strings/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/interaction/pub*"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/>
```

Dans cet exemple, la valeur **`<IP_addresses>`** correspond à la liste des adresses IP (séparées par des virgules) ayant la permission d&#39;utiliser le module de relais pour ce masque.

>[!NOTE]
>
>Les valeurs doivent être adaptées selon votre configuration et vos contraintes réseau, en particulier si des paramétrages spécifiques ont été développés pour votre installation.

## Restreindre les commandes externes autorisées {#restricting-authorized-external-commands}

>[!NOTE]
>
>La configuration ci-après est requise uniquement pour les installations on-premise.

A partir du build 8780, les administrateurs techniques peuvent restreindre la liste des commandes externes autorisées pouvant être utilisées dans Adobe Campaign.

Pour ce faire, vous devez créer un fichier texte contenant la liste des commandes dont vous souhaitez empêcher l&#39;utilisation, par exemple :

```
ln
dd
openssl
curl
wget
python
python3
perl
ruby
sh
```

>[!IMPORTANT]
>
>Cette liste n&#39;est pas exhaustive.

Dans le nœud **exec** du fichier de configuration du serveur, vous devez référencer le fichier précédemment créé dans l&#39;attribut **blacklistFile**.

**Pour Linux uniquement** : dans le fichier de configuration du serveur, nous vous recommandons de spécifier un utilisateur dédié à l&#39;exécution de commandes externes afin d&#39;améliorer votre configuration de sécurité. Cet utilisateur est défini dans le nœud **exec** du fichier de configuration. Tous les paramètres disponibles dans le fichier **serverConf.xml** sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).

>[!NOTE]
>
>Si aucun utilisateur n’est spécifié, toutes les commandes sont exécutées dans le contexte utilisateur de l’instance Adobe Campaign. L’utilisateur doit être différent de celui qui exécute Adobe Campaign.

Par exemple :

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

Cet utilisateur doit être ajouté à la liste sudoer de l&#39;opérateur &#39;neolane&#39; Adobe Campaign.

>[!IMPORTANT]
>
>Vous ne devez pas utiliser de sudo personnalisé. Un sudo standard doit être installé sur le système.

## Gestion des en-têtes HTTP (HTTP Headers){#managing-http-headers}

Par défaut, tous les en-têtes HTTP ne sont pas relayés. Vous pouvez ajouter des en-tête spécifiques dans les réponses transmises par le relais. Pour cela :

1. Accédez au fichier **serverConf.xml**. Tous les paramètres disponibles dans **serverConf.xml** sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).
1. Dans le nœud **`<relay>`**, accédez à la liste des en-têtes HTTP relayés.
1. Ajoutez un élément **`<responseheader>`** comportant les attributs suivants :

   * **name** : nom de l&#39;en-tête
   * **value** : valeur de l&#39;en-tête.

   Par exemple :

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Tracking redondant {#redundant-tracking}

Lorsque plusieurs serveurs sont utilisés pour servir la redirection, ceux-ci devront pouvoir communiquer entre eux par des appels SOAP afin de partager les informations des URL à rediriger. Il se peut en effet qu&#39;au moment du démarrage de la diffusion tous les serveurs de redirection ne soient pas disponibles, et qu&#39;ils ne possèdent donc pas le même niveau d&#39;information.

>[!NOTE]
>
>Dans le cas d&#39;une architecture standard ou entreprise, le serveur applicatif principal doit être autorisé à télécharger des informations de tracking sur chaque machine.

Les URL des serveurs redondants doivent être renseignées dans la configuration de la redirection, via le fichier **serverConf.xml**. Tous les paramètres disponibles dans le fichier **serverConf.xml** sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).

**Exemple:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

La propriété **enableIf** est optionnelle (vide par défaut) et permet de n&#39;activer la connexion que si le résultat est vrai ; ceci afin d&#39;obtenir une configuration identique sur tous les serveurs de redirection.

Pour connaître le hostname de la machine, exécutez la commande suivante : **hostname -s**.

## Gestion des ressources publiques {#managing-public-resources}

Les ressources publiques sont présentées dans la section [Gestion des ressources publiques](../../installation/using/deploying-an-instance.md#managing-public-resources).

Elles sont stockées dans le répertoire **/var/res/instance** du répertoire d&#39;installation d&#39;Adobe Campaign.

L&#39;URL correspondante est la suivante : **http://serveur/res/instance** où **instance** est le nom de l&#39;instance de tracking.

Vous pouvez spécifier un autre répertoire en ajoutant un nœud au fichier **conf-`<instance>`.xml** pour configurer le stockage sur le serveur. Cela signifie d’ajouter les lignes suivantes :

```
<serverconf>
  <shared>
    <dataStore hosts="media*" lang="fra">
      <virtualDir name="images" path="/var/www/images"/>
     <virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)/"/>
    </dataStore>
  </shared>
</serverconf>
```

Dans ce cas, la nouvelle URL des ressources publiques indiquée dans la section supérieure de la fenêtre de l&#39;assistant de déploiement doit pointer sur ce dossier.

## Workflows en haute disponibilité et affinités {#high-availability-workflows-and-affinities}

Vous pouvez configurer plusieurs serveurs de workflow (wfserver) et les répartir sur plusieurs machines. Si vous optez pour une architecture de ce type, paramétrez le mode de connexion des répartiteurs de charge en fonction de l&#39;accès à Adobe Campaign.

Dans le cas d&#39;un accès depuis le web, choisissez le mode **load balancer** afin de limiter les temps de connexion.

Si l&#39;accès se fait depuis la console Adobe Campaign, préférez le mode **hash** ou **sticky ip**. Cela vous permet de maintenir la connexion entre le client riche et le serveur et d&#39;éviter qu&#39;une session utilisateur ne soit interrompue au cours d&#39;une opération d&#39;import ou d&#39;export par exemple.

Vous pouvez choisir de forcer l&#39;exécution d&#39;un workflow ou d&#39;une activité de workflow sur une machine particulière. Vous devez pour cela définir une ou plusieurs affinités au niveau du workflow ou de l&#39;activité concernée.

1. Créez la ou les affinités du workflow ou de l&#39;activité en la tapant dans le champ **[!UICONTROL Affinité]**.

   Vous pouvez choisir librement le nom des affinités. Cela dit, évitez les espaces ou les signes de ponctuation. Si vous utilisez des serveurs différents, indiquez des noms différents.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   La liste déroulante contient les affinités utilisées auparavant. La liste se complète au fur et à mesure avec les différentes valeurs saisies.

1. Ouvrez le fichier **nl6/conf/config-`<instance>.xml`**.
1. Modifiez la ligne correspondant au module **[!UICONTROL wfserver]** de la façon suivante :

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   Si vous définissez plusieurs affinités, elles doivent être séparées par une virgule sans espace :

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   La virgule qui suit le nom de l&#39;affinité est nécessaire afin que les workflows pour lesquels aucune affinité n&#39;est définie puissent s&#39;exécuter.

   Si vous souhaitez n&#39;exécuter que les workflows pour lesquels une affinité est définie, n&#39;ajoutez pas de virgule à la fin de la liste de vos affinités. Par exemple, modifiez la ligne de la façon suivante :

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## Redémarrage automatique des processus {#automatic-process-restart}

Par défaut, les différents processus Adobe Campaign redémarrent automatiquement à 6h (matin, heure du serveur) chaque jour.

Il est néanmoins possible de modifier ce paramétrage.

Pour cela, accédez au fichier **serverConf.xml** dans le répertoire **conf** de votre installation. Tous les paramètres disponibles dans **serverConf.xml** sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).

Chaque processus paramétré dans ce fichier dispose d&#39;un attribut **processRestartTime**. Vous pouvez modifier la valeur de cet attribut afin d&#39;adapter l&#39;heure de redémarrage de chaque processus à vos besoins.

>[!IMPORTANT]
>
>Ne supprimez pas cet attribut. Tous les processus doivent être redémarrés chaque jour.

## Limitation des fichiers téléchargeables {#limiting-uploadable-files}

Un nouvel attribut **uploadWhiteList** permet de restreindre les types de fichiers qu&#39;il est possible de télécharger sur le serveur Adobe Campaign.

Cet attribut est disponible au niveau de l&#39;élément **dataStore** du fichier **serverConf.xml.** Tous les paramètres disponibles dans le fichier **serverConf.xml** sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).

La valeur par défaut de cet attribut est **.+** et permet de télécharger n&#39;importe quel type de fichier.

Pour limiter les possibilités à certains formats, vous devez remplacer la valeur de l&#39;attribut par une expression régulière java valide. Vous pouvez entrer plusieurs valeurs en les séparant par une virgule.

Par exemple : **uploadWhiteList=&quot;.*.png,.*.jpg&quot;** vous permet de télécharger des formats PNG et JPG sur le serveur. Aucun autre format ne sera accepté.

>[!IMPORTANT]
>
>Sous Internet Explorer, le chemin complet des fichiers doit être vérifié par l&#39;expression régulière.

## Paramétrage de la connexion au proxy {#proxy-connection-configuration}

Vous pouvez connecter le serveur Campaign à un système externe par le biais d’un proxy, en utilisant par exemple une activité de workflow **Transfert de fichier**. Pour ce faire, vous devez configurer la section **proxyConfig** du fichier **serverConf.xml** à l’aide d’une commande spécifique. Tous les paramètres disponibles dans le fichier **serverConf.xml** sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).

Les connexions proxy suivantes sont possibles : HTTP, HTTPS, FTP, SFTP. Notez qu’à compter de la version 20.2 de Campaign, les paramètres de protocole HTTP et HTTPS sont **indisponibles**. Ces paramètres sont toujours mentionnés ci-dessous car ils restent disponibles dans les builds précédents, y compris le build 9032.

>[!CAUTION]
>
>Seul le mode d’authentification de base est pris en charge. L’authentification NTLM n’est pas prise en charge.
>
>Les proxys SOCKS ne sont pas pris en charge.


Vous pouvez utiliser la commande suivante :

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

les paramètres de protocole peuvent être &quot;http&quot;, &quot;https&quot; ou &quot;ftp&quot;.

Si vous définissez le protocole FTP sur le même port que le trafic HTTP/HTTPS, vous pouvez utiliser ce qui suit :

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

Les options &quot;http&quot; et &quot;https&quot; ne sont utilisées que lorsque le paramètre de protocole est &quot;ftp&quot; et indiquent si le tunneling sur le port spécifié sera effectué via HTTPS ou via HTTP.

Si vous utilisez des ports différents pour le trafic FTP/SFTP et HTTP/HTTPS sur le serveur proxy, vous devez définir le paramètre de protocole &quot;ftp&quot;.


Par exemple :

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

Puis saisissez le mot de passe.

Les connexions HTTP sont définies dans le paramètre proxyHTTP :

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

Les connexions HTTPS sont définies dans le paramètre proxyHTTPS :

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

Les connexions FTP/FTPS sont définies dans le paramètre proxyFTP :

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

Si vous utilisez le même proxy pour plusieurs types de connexions, seul le paramètre proxyHTTP sera défini avec useSingleProxy défini sur &quot;1&quot; ou &quot;true&quot;.

Si des connexions internes doivent passer à travers le proxy, ajoutez-les dans le paramètre override.

Si vous souhaitez désactiver temporairement la connexion au proxy, définissez le paramètre enabled sur &quot;false&quot; ou &quot;0&quot;.
