---
product: campaign
title: Localisation de la version de Tomcat dans Adobe Campaign
description: Découvrez comment trouver la version actuelle de la servlet web Tomcat intégrée utilisée dans une instance d’Adobe Campaign
feature: Monitoring
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 100%

---

# Localisation de la version de Tomcat{#locate-tomcat-version}

Adobe Campaign utilise une **servlet web intégrée appelée Apache Tomcat** pour traiter les requêtes HTTP / HTTPS entre l’application et toute interface externe (y compris la console cliente, les liens d&#39;URL trackée, les appels SOAP, etc.). Un serveur web externe (généralement IIS ou Apache) se trouve souvent devant cette instance pour toutes les instances Adobe Campaign face à l&#39;extérieur.

Suivez la procédure ci-dessous pour découvrir la version exacte de Tomcat utilisée dans une **instance Campaign Classic on-premise** afin de résoudre les problèmes.

## Tomcat utilisé dans Adobe Campaign

Tomcat s’exécute sur Java et nécessite l’installation du JDK. Pour plus d’informations, voir Kit de développement Java (JDK) dans la section [Matrice de compatibilité Campaign](../../rn/using/compatibility-matrix.md).

La version de Tomcat utilisée dans Adobe Campaign est une version intégrée personnalisée qui n&#39;utilise pas toutes les fonctionnalités de la version complète de Tomcat disponible en général. Elle peut donc ne pas présenter toutes les vulnérabilités de la version complète. Le Tomcat ne devrait pas non plus être exposé à l’Internet extérieur. Par ailleurs, les instances d’Adobe Campaign exposées devraient avoir un serveur web externe (IIS, Apache, etc.) devant le Tomcat pour le protéger.

Les versions nouvelles ou mises à niveau des versions intégrées de Tomcat ne sont publiées qu’avec de nouvelles builds d’Adobe Campaign et non comme des correctifs distincts en dehors des versions Adobe Campaign.

>[!AVAILABILITY]
>
>
>* À compter de Campaign v7.4.1, Tomcat 10.1 est la version par défaut.
>
>* Adobe Campaign Classic n’utilise pas les protocoles WebSocket et HTTP2.
>


## Comment localiser la version de Tomcat intégrée

Pour localiser la version de Tomcat intégrée dans une instance d’Adobe Campaign, suivez les étapes ci-dessous.

>[!NOTE]
>
>Vous devez avoir accès aux fichiers du serveur Adobe Campaign que vous devez vérifier. La procédure décrite ci-dessous ne s&#39;applique qu&#39;aux **modèles d&#39;hébergement on-premise**.

1. Accédez au sous-dossier *\tomcat-11\lib* dans le dossier d’installation Adobe Campaign (par exemple, *C:\Program Files\ [dossier_d’installation]* sous Windows ou */usr/local/neolane/nl6* sous Linux).

1. Copiez le fichier *catalina.jar* dans un dossier temporaire externe (votre bureau, par exemple) et remplacez l’extension .jar par .zip.

1. Décompressez le fichier copié. Vous obtiendrez de nombreux sous-dossiers et fichiers.

1. À l&#39;intérieur des fichiers / dossiers décompressés, ouvrez ou lisez le fichier contenu suivant à l’aide d’un éditeur de texte : *org/apache/catalina/util/ServerInfo.properties*. Vous devrez peut-être ajouter une extension .txt pour faciliter l’ouverture avec un éditeur.

1. Une fois terminé, s’il se trouve sur un serveur, supprimez le ou les fichiers temporaires que vous avez créés.

Par exemple, le fichier *ServerInfo.properties* pour Adobe Campaign contient les informations suivantes, indiquant Tomcat v11.X :

*`server.info=Apache Tomcat/11.X`*

*`server.number=A.B.X.Y`*

*`server.built=MM DD YYY HH:MM:SS`*

Une fois que vous avez pu déterminer la version exacte de Tomcat utilisée dans une instance particulière, vous pouvez plus facilement résoudre les problèmes liés à Tomcat.

>[!NOTE]
>
>La version majeure de Tomcat intégrée n’est mise à niveau que lorsque la version majeure d’Adobe Campaign change (bien que les versions plus anciennes ne soient plus officiellement prises en charge, les informations peuvent s’avérer utiles car certains clients exécutent toujours ces versions).
>

