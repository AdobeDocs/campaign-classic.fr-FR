---
product: campaign
title: Configuration de Campaign Tomcat
description: Configuration de Campaign Tomcat
feature: Installation, Instance Settings
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 76%

---

# Configurer Apache Tomcat {#configuring-tomcat}

Adobe Campaign utilise une **servlet web intégrée appelée Apache Tomcat** pour traiter les requêtes HTTP / HTTPS entre l’application et toute interface externe (y compris la console cliente, les liens d&#39;URL trackée, les appels SOAP, etc.). Un serveur web externe (généralement IIS ou Apache) se trouve souvent devant cette instance pour toutes les instances Adobe Campaign face à l&#39;extérieur.

Pour en savoir plus sur Tomcat dans Campaign et comment localiser votre version de Tomcat, [voir cette page](../../production/using/locate-tomcat-version.md).

>[!AVAILABILITY]
>
> Depuis la v7.4.1, Tomcat 10.1 est la version par défaut.
>


## Port par défaut pour Apache Tomcat {#default-port-for-tomcat}


>[!NOTE]
>
>Cette procédure est limitée aux déploiements **On-premise**.
>

Lorsque le port d’écoute 8080 du serveur Tomcat est déjà occupé par une autre application requise pour votre configuration, vous devez remplacer le port 8080 par un port disponible (8090 par exemple). Pour la modifier, modifiez la variable **server.xml** enregistré dans le fichier **/tomcat-X/conf** du dossier d’installation Adobe Campaign.

Modifiez ensuite le port des pages de relais JSP. Pour ce faire, modifiez le fichier **serverConf.xml** enregistré dans le répertoire **/conf** du répertoire d’installation d’Adobe Campaign.

```xml
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Mapper un dossier dans Apache Tomcat {#mapping-a-folder-in-tomcat}


>[!NOTE]
>
>Cette procédure est limitée aux déploiements **On-premise**.
>

Pour définir les paramètres propres aux clients, vous pouvez créer une **user_contexts.xml** dans le fichier **/tomcat-X/conf** , qui contient également la variable **contexts.xml** fichier .

Ce fichier contiendra des informations du type :

```xml
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Au besoin, cette opération doit être reproduite côté serveur.

## Masquer le rapport d’erreur Tomcat {#hide-tomcat-error-report}


>[!NOTE]
>
>Cette procédure est limitée aux déploiements **On-premise**.
>
>Cette modification n&#39;est plus nécessaire à partir de Campaign v7.4.1.
>

Pour des raisons de sécurité, nous vous recommandons vivement de masquer le rapport d’erreur Tomcat. Procédez comme suit :

1. Ouvrez le **server.xml** situé dans le fichier **/tomcat-X/conf** répertoire du dossier d’installation d’Adobe Campaign :  `/usr/local/neolane/nl6/tomcat-X/conf`
1. Ajoutez l’élément suivant en bas après tous les éléments de contexte existants :

   ```xml
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. Redémarrez les serveurs web nlserver et Apache.
