---
product: campaign
title: Configuration de Campaign Tomcat
description: Configuration de Campaign Tomcat
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
badge-v7-prem: label="On-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 100%

---

# Configurer Apache Tomcat {#configuring-tomcat}



Adobe Campaign utilise une **servlet web intégrée appelée Apache Tomcat** pour traiter les requêtes HTTP / HTTPS entre l’application et toute interface externe (y compris la console cliente, les liens d&#39;URL trackée, les appels SOAP, etc.). Un serveur web externe (généralement IIS ou Apache) se trouve souvent devant cette instance pour toutes les instances Adobe Campaign face à l&#39;extérieur.

Pour en savoir plus sur Tomcat dans Campaign et comment localiser votre version de Tomcat, [voir cette page](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>Cette procédure est limitée aux déploiements **On-Premise**.
>

## Port par défaut pour Apache Tomcat {#default-port-for-tomcat}

Lorsque le port d’écoute 8080 du serveur Tomcat est déjà occupé par une autre application requise pour votre configuration, vous devez remplacer le port 8080 par un port disponible (8090 par exemple). Pour le modifier, modifiez le fichier **server.xml** enregistré dans le répertoire **/tomcat-8/conf** du dossier d’installation d’Adobe Campaign.

Modifiez ensuite le port des pages de relais JSP. Pour ce faire, modifiez le fichier **serverConf.xml** enregistré dans le répertoire **/conf** du répertoire d’installation d’Adobe Campaign.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Mapper un dossier dans Apache Tomcat {#mapping-a-folder-in-tomcat}

Afin de définir les paramètres propres aux clients, vous pouvez créer un fichier **user_contexts.xml** dans le dossier **/tomcat-8/conf**, qui contient également le fichier **contexts.xml**.

Ce fichier contiendra des informations du type :

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Au besoin, cette opération doit être reproduite côté serveur.

## Masquer le rapport d’erreur Tomcat {#hide-tomcat-error-report}

Pour des raisons de sécurité, nous vous recommandons vivement de masquer le rapport d’erreur Tomcat. La procédure est la suivante.

1. Ouvrez le fichier **server.xml** qui se trouve dans le répertoire **/tomcat-8/conf** du dossier d’installation d’Adobe Campaign : `/usr/local/neolane/nl6/tomcat-8/conf`
1. Ajoutez l’élément suivant en bas après tous les éléments de contexte existants :

   ```
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. Redémarrez les serveurs web nlserver et Apache.
