---
title: Seuil de connexions
seo-title: Seuil de connexions
description: Seuil de connexions
seo-description: null
page-status-flag: never-activated
uuid: a4b6959a-0f5b-41a2-b4c3-d7d6613d1a18
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f3db77db-94cc-4d75-a59b-2dddce776759
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Seuil de connexions{#connection-thresholds}

Pour des serveurs soumis à de fortes charge, il se peut que le seuil de connexions soit dépassé. Dans tous les cas, il est utile d&#39;en connaître la raison.

Il existe trois seuils différents :

1. Le seuil de connexions Web, paramétré dans votre serveur web. Pour le modifier, contactez votre administrateur système.
1. Le seuil de connexions base de données. Pour le modifier, contactez votre administrateur de base de données.
1. Le seuil de connexions Adobe Campaign, disponible à deux endroits :

   * Côté Tomcat : ensemble des requêtes arrivant effectivement sur le client Tomcat Adobe Campaign.

      Ce seuil est paramétré dans le fichier **nl6/tomcat-7/conf/server.xml**. L&#39;attribut **maxThreads** permet d&#39;augmenter le seuil des requêtes traitées simultanément. Il peut être augmenté à 250, par exemple.

      ```
      <Connector protocol="HTTP/1.1" port="8080"
                     maxThreads="75"
                     minSpareThreads="5"
                     enableLookups="true" redirectPort="8443"
                     acceptCount="100" connectionTimeout="20000"
                     disableUploadTimeout="true" />
          <Engine name="Tomcat-Standalone" defaultHost="localhost">
            <Host name="localhost" appBase="./"
                  unpackWARs="true" autoDeploy="true">
      ```

   * Côté base de données : ensemble de toutes les connexions ouvertes simultanément sur la base de données par un processus.

      Ce seuil est paramétré dans le fichier **nl6/conf/serverConf.xml**. L&#39;attribut **maxCnx** situé dans **datasource pool** permet d&#39;augmenter le seuil des requêtes traitées simultanément.

      ```
          <!-- Data source
               -->
            <dataSource name="default">
              <dbcnx NChar="" bulkCopyUtility="" dbSchema="" encrypted="" login="" password="" provider="" server="" timezone="" unicodeData="" useTimestampTZ=""/>
              <sqlParams funcPrefix="">
                <postConnectSQL/>
              </sqlParams>
              <pool aliveTestDelaySec="600" freeCnx="0" maxCnx="90" maxIdleDelaySec="1200"/>
            </dataSource>
      ```

