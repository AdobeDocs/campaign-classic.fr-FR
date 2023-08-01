---
product: campaign
title: Gestion des fichiers et des ressources
feature: Installation, Application Settings
description: Découvrez comment configurer la gestion des fichiers et des ressources dans Campaign
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
badge-v7-prem: label="on-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 98%

---

# Gestion des fichiers et des ressources{#file-and-resmanagement}



## Limiter le format des fichiers chargés {#limiting-uploadable-files}

Utilisez l’attribut **uploadWhiteList** pour limiter les types de fichiers disponibles pour téléchargement sur le serveur Adobe Campaign.

Cet attribut est disponible au niveau de l&#39;élément **dataStore** du fichier **serverConf.xml.** Tous les paramètres disponibles dans le fichier **serverConf.xml** sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).

La valeur par défaut de cet attribut est **.+** et vous permet de charger n’importe quel type de fichier.

Pour limiter les formats possibles, remplacez la valeur d’attribut par une expression java régulière valide. Vous pouvez saisir plusieurs valeurs en les séparant par une virgule.

Par exemple : **uploadWhiteList=&quot;.&#42;.png,.&#42;.jpg&quot;** vous permet de télécharger des formats PNG et JPG sur le serveur. Aucun autre format ne sera accepté.

Vous pouvez également empêcher le téléchargement de fichiers importants en configurant le serveur Web. [En savoir plus](web-server-configuration.md)

>[!NOTE]
>
>L’attribut **uploadWhiteList** sert à limiter les types de fichiers disponibles au téléchargement sur le serveur Adobe Campaign. Toutefois, lorsque le mode de publication est **Serveur(s) de tracking** ou **Autres serveurs Adobe Campaign**, l’attribut **uploadWhitelist** doit également être mis à jour sur ces serveurs.

## Paramétrage de la connexion au proxy {#proxy-connection-configuration}

Vous pouvez connecter le serveur Campaign à un système externe par le biais d’un proxy, en utilisant par exemple une activité de workflow **Transfert de fichier**. Pour ce faire, vous devez configurer la section **proxyConfig** du fichier **serverConf.xml** à l’aide d’une commande spécifique. Tous les paramètres disponibles dans le fichier **serverConf.xml** sont répertoriés dans cette [section](../../installation/using/the-server-configuration-file.md).

Les connexions proxy suivantes sont possibles : HTTP, HTTPS, FTP, SFTP. Notez qu’à compter de la version 20.2 de Campaign, les paramètres de protocole HTTP et HTTPS sont **indisponibles**. Ces paramètres sont toujours mentionnés ci-dessous car ils restent disponibles dans les builds précédents, y compris le build 9032.

>[!CAUTION]
>
>Seul le mode d’authentification de base est pris en charge. L’authentification NTLM n’est pas prise en charge.
>
>Les proxys SOCKS ne sont pas pris en charge.
>

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

Si vous souhaitez désactiver temporairement la connexion au proxy, définissez le paramètre activ » sur &quot;false&quot; ou &quot;0&quot;.

Si vous devez utiliser le connecteur HTTP/2 iOS via un proxy, les modes de proxy HTTP suivants sont pris en charge :

* HTTP sans authentification
* Authentification de base HTTP

Pour activer le mode proxy, la modification suivante doit être effectuée dans le fichier `serverconf.xml` :

```
<nmac useHTTPProxy="true">
```

Pour plus d&#39;informations sur ce connecteur HTTP/2 iOS, consultez cette [page](../../delivery/using/about-mobile-app-channel.md).

## Gérer les ressources publiques {#managing-public-resources}

Pour être accessibles publiquement, les images utilisées dans les emails et les ressources publiques associées aux opérations doivent être présentes sur un serveur accessible de l’extérieur. Elles peuvent ensuite être mises à la disposition de destinataires ou d’opérateurs externes. [En savoir plus](../../installation/using/deploying-an-instance.md#managing-public-resources).

Les ressources publiques sont stockées dans le répertoire **/var/res/instance** du répertoire d’installation d’Adobe Campaign.

L&#39;URL correspondante est la suivante : **http://serveur/res/instance** où **instance** est le nom de l&#39;instance de tracking.

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
