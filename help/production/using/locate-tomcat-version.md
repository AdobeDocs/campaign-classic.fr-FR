---
solution: Campaign Classic
product: campaign
title: Localisation de la version de Tomcat en Adobe Campaign
description: Découvrez comment trouver la version actuelle du servlet Web Tomcat incorporé utilisé dans une instance d’Adobe Campaign.
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 49e49d5e35d14a31236cc4f78188cdf77353fbbf
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---


# Localisation de la version de Tomcat {#locate-tomcat-version}

Adobe Campaign utilise une servlet Web **intégrée appelée Apache Tomcat** pour traiter les requêtes HTTP/HTTPS entre l’application et toute interface externe (y compris la console client, les liens URL suivis, les appels SOAP, etc.). Il existe souvent un serveur Web externe (généralement IIS ou Apache) devant cette instance pour toutes les instances Adobe Campaign externes.

Suivez la procédure ci-dessous pour découvrir la version exacte de Tomcat utilisée dans une instance **Campaign Classic sur site** afin de résoudre les problèmes.

## Tomcat utilisé en Adobe Campaign

Tomcat s’exécute sur Java et nécessite l’installation du JDK. Pour plus d’informations, voir Kit de développement Java (JDK) dans la section [Campaign Compatibility Matrix](../../rn/using/compatibility-matrix.md).

Le Tomcat utilisé en Adobe Campaign est une version incorporée personnalisée qui n&#39;utilise pas toutes les fonctionnalités de la version complète de Tomcat disponible en général, et ne peut pas souffrir de toutes les vulnérabilités de la version complète. Le Tomcat ne devrait pas non plus être exposé à l&#39;Internet extérieur, et les instances d&#39;Adobe Campaign exposées devraient avoir un serveur Web externe (IIS, Apache, etc.) devant le Tomcat pour le protéger.

Les versions nouvelles ou mises à niveau des versions incorporées de Tomcat ne sont publiées qu&#39;avec de nouvelles versions d&#39;Adobe Campaign lui-même et non comme des correctifs distincts en dehors des versions Adobe Campaign.

## Comment localiser la version de Tomcat incorporé

Pour localiser la version de Tomcat incorporé dans une instance d’Adobe Campaign, suivez les étapes ci-dessous.

>[!NOTE]
>
>Vous devez avoir accès aux fichiers du serveur Adobe Campaign que vous devez vérifier. La procédure décrite ci-dessous ne s&#39;applique qu&#39;aux **modèles d&#39;hébergement sur site**.

1. Accédez au sous-dossier *\tomcat-7\lib* dans le dossier d’installation Adobe Campaign (par exemple, *C:\Program Files\ [Installation_folder]* sous Windows ou */usr/local/neolane/nl6* sous Linux).

   Si vous exécutez une ancienne version d’Adobe Campaign à l’aide de Tomcat v6, utilisez *\tomcat-6\lib*.

1. Copiez le fichier *catalina.jar* dans un dossier temporaire externe (votre bureau, par exemple) et renommez l’extension de .jar en .zip.

1. Décompressez le fichier copié. Il en résultera de nombreux sous-dossiers et fichiers.

1. Dans les fichiers/dossiers décompressés, ouvrez ou lisez le fichier contenu suivant à l’aide d’un éditeur de texte : *org/apache/catalina/util/ServerInfo.properties*. Vous devrez peut-être ajouter une extension .txt pour faciliter l’ouverture avec un éditeur de texte.

1. Une fois terminé, s’il se trouve sur un serveur, supprimez le ou les fichiers temporaires que vous avez créés.

Par exemple, le fichier *ServerInfo.properties* pour Adobe Campaign contient les informations suivantes, indiquant que Tomcat v8.5.X :

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.build=MM JJ AAAA HH:MM:SS*

Une fois que vous avez pu établir la version exacte de Tomcat utilisée dans une instance particulière, il peut vous aider à résoudre les problèmes liés à Tomcat.

>[!NOTE]
>
>La version majeure de Tomcat incorporé n’est mise à niveau que lorsque la version majeure d’Adobe Campaign change (bien que les versions plus anciennes ne soient plus officiellement prises en charge, les informations peuvent s’avérer utiles car certains clients exécutent toujours ces versions).
>
>Par exemple, Adobe Campaign v6.02 utilisera toujours Tomcat v6.x.