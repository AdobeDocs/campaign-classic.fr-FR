---
title: Transformation en Unicode
seo-title: Transformation en Unicode
description: Transformation en Unicode
seo-description: null
page-status-flag: never-activated
uuid: 5f15b285-7377-453a-aa98-ca4cf14a4c80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: 0f5399a8-860d-4a1b-86a9-9011b973346b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Transformation en Unicode{#switching-to-unicode}

Soit une instance **prod** existante sous Linux/PostgreSQL, les étapes de transformation en Unicode de cette instance sont les suivantes :

1. Arrêter les processus qui écrivent dans la base :

   ```
   su - neolane
   nlserver shutdown
   ```

1. Dumper la base :

   ```
   su - postgres
   pg_dump mydatabase > mydatabase.sql
   ```

1. Créer une base Unicode :

   ```
   createdb -E UNICODE mydatabase_unicode
   ```

1. Restaurer la base :

   ```
   psql mydatabase_unicode < mydatabase.sql
   ```

1. Mettre à jour l&#39;option qui indique que la base est Unicode :

   ```
   psql mydatabase_unicode
   update XtkOption set sStringValue = 'u'||sStringValue where sName='XtkDatabaseId' and sStringValue not like 'u%';
   ```

1. Sur les serveurs de tracking :

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Ajouter le caractère **u** devant la valeur relative à l&#39;identifiant de la base de données (**databaseId**) :

   ```
   <web>
    <redirection databaseId="u7F0000010554364C" trackingPassword="myPassword="/>
   </web>
   ```

1. Sur les serveurs appelant la base :

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Modifier la référence de la base :

   ```
   <dataSource name="default">
    <dbcnx encrypted="1" 
    login="<dbuser>:<base_unicode>" password="xxxx="
    provider="postgresql" server="yyyy"/>
   </dataSource>
   ```

1. Redémarrer toutes les machines :

   ```
   /etc/init.d/apache stop
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   /etc/init.d/apache start
   ```

1. Valider la transformation. Pour cela, se connecter via la console Adobe Campaign et :

   * vérifier que les données s&#39;affichent correctement, notamment les caractères accentués,
   * lancer une diffusion et vérifier que la récupération du tracking fonctionne.

