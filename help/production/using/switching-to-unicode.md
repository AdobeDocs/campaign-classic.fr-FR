---
product: campaign
title: Transformation en Unicode
description: Transformation en Unicode
feature: Monitoring
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: ht
source-wordcount: '130'
ht-degree: 100%

---

# Transformation en Unicode{#switching-to-unicode}



Soit une instance **prod** existante sous Linux/PostgreSQL, les étapes de transformation en Unicode de cette instance sont les suivantes :

1. Arrêter les processus qui écrivent dans la base :

   ```
   su - neolane
   nlserver shutdown
   ```

1. Dumper la base :

   ```
   su - postgres
   pg_dump mydatabase > mydatabase.sql
   ```

1. Créer une base Unicode :

   ```
   createdb -E UNICODE mydatabase_unicode
   ```

1. Restaurer la base :

   ```
   psql mydatabase_unicode < mydatabase.sql
   ```

1. Mettre à jour l&#39;option qui indique que la base est Unicode :

   ```
   psql mydatabase_unicode
   update XtkOption set sStringValue = 'u'||sStringValue where sName='XtkDatabaseId' and sStringValue not like 'u%';
   ```

1. Sur les serveurs de tracking :

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Ajouter le caractère **u** devant la valeur relative à l&#39;identifiant de la base de données (**databaseId**) :

   ```
   <web>
    <redirection databaseId="u7F0000010554364C" trackingPassword="myPassword="/>
   </web>
   ```

1. Sur les serveurs appelant la base :

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Modifier la référence de la base :

   ```
   <dataSource name="default">
    <dbcnx encrypted="1" 
    login="<dbuser>:<base_unicode>" password="xxxx="
    provider="postgresql" server="yyyy"/>
   </dataSource>
   ```

1. Redémarrer toutes les machines :

   ```
   /etc/init.d/apache stop
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   /etc/init.d/apache start
   ```

1. Valider la transformation. Pour cela, se connecter via la console Adobe Campaign et :

   * vérifier que les données s&#39;affichent correctement, notamment les caractères accentués,
   * lancer une diffusion et vérifier que la récupération du tracking fonctionne.
