---
product: campaign
title: Configuration de Campaign Tomcat
description: Configuration de Campaign Tomcat
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 78%

---

# Configurer Apache Tomcat {#configuring-tomcat}

![](../../assets/v7-only.svg)

Adobe Campaign utilise une **servlet web intégrée appelée Apache Tomcat** pour traiter les requêtes HTTP / HTTPS entre l’application et toute interface externe (y compris la console cliente, les liens d&#39;URL trackée, les appels SOAP, etc.). Un serveur web externe (généralement IIS ou Apache) se trouve souvent devant cette instance pour toutes les instances Adobe Campaign face à l&#39;extérieur.

Pour en savoir plus sur Tomcat dans Campaign et comment localiser votre version de Tomcat, [voir cette page](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>Cette procédure est limitée aux déploiements **On-Premise**.

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

Pour des raisons de sécurité, nous vous recommandons vivement de masquer le rapport d’erreur Tomcat. Voici les étapes.

1. Ouvrez le **server.xml** situé dans le fichier **/tomcat-8/conf** répertoire du dossier d’installation d’Adobe Campaign :  `/usr/local/neolane/nl6/tomcat-8/conf`
1. Ajoutez l’élément suivant en bas après tous les éléments de contexte existants :

   ```
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```
1. Redémarrez les serveurs web nlserver et Apache.
