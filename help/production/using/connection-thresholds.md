---
product: campaign
title: Seuil de connexions
description: Seuil de connexions
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: ht
source-wordcount: '156'
ht-degree: 100%

---

# Seuil de connexions{#connection-thresholds}



Pour des serveurs soumis à de fortes charge, il se peut que le seuil de connexions soit dépassé. Dans tous les cas, il est utile d&#39;en connaître la raison.

Il existe trois seuils différents :

* Le **seuil de connexion web**, paramétré dans votre serveur web. Pour le modifier, contactez votre administrateur système.

* Le **seuil de connexion de base de données**. Pour le modifier, contactez votre administrateur de base de données.

* Le **seuil de connexion Adobe Campaign**, disponible à deux endroits :

   * **Côté Tomcat** : ensemble des requêtes arrivant effectivement sur le client Tomcat Adobe Campaign.

      Ce seuil est configuré dans le fichier **nl6/tomcat-8/conf/server.xml**. L&#39;attribut **maxThreads** permet d&#39;augmenter le seuil du nombre de requêtes traitées à la fois. Il peut être remplacé par 250, par exemple.

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

   * **Base de données** : ensemble de toutes les connexions ouvertes simultanément sur la base de données par un processus.

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
