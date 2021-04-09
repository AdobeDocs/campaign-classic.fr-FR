---
solution: Campaign Classic
product: campaign
title: Confidentialité
description: En savoir plus sur les bonnes pratiques à suivre en matière de confidentialité.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
translation-type: tm+mt
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: tm+mt
source-wordcount: '778'
ht-degree: 94%

---

# Confidentialité {#privacy}

## Demandes d’accès à des informations personnelles

Adobe Campaign propose un ensemble d’outils pour vous aider à respecter la confidentialité dans le cadre du RGPD et de la CCPA.

Reportez-vous à [cette page](../../platform/using/privacy-management.md) pour obtenir des informations générales sur la gestion de la protection des données et les étapes de son implémentation dans Adobe Campaign. Vous trouverez également des bonnes pratiques, ainsi qu’une vue d’ensemble du processus utilisateur et des acteurs impliqués.

## Personnalisation des URL {#url-personalization}

Lorsque vous ajoutez des liens personnalisés à votre contenu, évitez toujours toute personnalisation dans la partie du nom d’hôte de l’URL afin d’éviter des failles de sécurité potentielles. Les exemples suivants ne doivent jamais être utilisés dans tous les attributs d’URL &lt;`a href="">` ou `<img src="">` :

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Recommandation

Pour valider et vous assurer que vous n’utilisez pas les éléments ci-dessus, exécutez une requête sur la table des URL de tracking à l’aide du [requêteur générique de Campaign](../../platform/using/steps-to-create-a-query.md) ou créez un workflow avec des critères de filtre dans l’[activité de requête](../../workflow/using/query.md).

Exemple :

1. Créez un workflow et ajoutez une activité Requête. En savoir plus.

1. Ouvrez l’activité Requête et créez un filtre sur la table nmsTrackingUrl comme suit : l’URL source commence par http://&lt;% ou l’URL source commence par https://&lt;%.

1. Exécutez le workflow et vérifiez s’il y a des résultats.

1. Si c’est le cas, ouvrez la transition sortante pour afficher la liste des URL.

<img src="assets/privacy-query-dynamic-url.png">

### Mécanisme de signature

Pour améliorer la sécurité, un nouveau mécanisme de signature pour les liens de tracking dans les emails a été ajouté dans le build 19.1.4 (9032@3a9dc9c) et est disponible dans le build 19.1.4 (9032@3a9dc9c) et Campaign 20.2. Cette option est activée par défaut pour tous les clients.

>[!NOTE]
>
>Lorsqu’un utilisateur clique sur une URL signée incorrecte, l’erreur suivante est renvoyée : « L’URL &quot;...&quot; demandée est introuvable ».

En outre, à compter des versions Campaign 20.2 et [!DNL Gold Standard], les clients hébergés et hybrides peuvent utiliser une amélioration pour désactiver les URL générées à partir des versions précédentes. Par défaut, cette option est désactivée. Vous pouvez contacter l’[Assistance clientèle](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) pour activer cette fonctionnalité.

Pour activer ce nouveau mécanisme, les clients On-premise doivent suivre la procédure suivante sur tous les serveurs Campaign :

1. Dans le fichier de configuration du serveur (serverConf.xml), définissez **blockRedirectForUnsignedTrackingLink** sur **true**.
1. Redémarrez le service **nlserver**.
1. Sur le serveur de tracking, redémarrez le serveur web (apache2 sur Debian, httpd sur CentOS/RedHat, IIS sous Windows).

Les clients qui s’exécutent sur [!DNL Gold Standard] 19.1.4 peuvent rencontrer des problèmes avec les diffusions de notification Push à l’aide du lien de suivi ou des diffusions à l’aide de balises d’ancrage. Si tel est le cas, Adobe recommande de désactiver le nouveau mécanisme de signature pour les liens de tracking :

Les **clients hébergés et hybrides** doivent contacter l’[Assistance clientèle](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) pour que ce mécanisme soit désactivé.

Les **clients On-premise** peuvent procéder comme suit :

1. Dans le fichier de configuration du serveur (serverConf.xml), remplacez **signEmailLinks** par **false**.
1. Redémarrez le service **nlserver**.
1. Sur le serveur de tracking, redémarrez le serveur web (apache2 sur Debian, httpd sur CentOS/RedHat, IIS sous Windows).

## Restriction des données

Vous devez vous assurer que les mots de passe cryptés ne sont pas accessibles par un utilisateur authentifié avec de faibles privilèges. Pour cela, il existe deux méthodes : restreindre l’accès aux champs de mots de passe uniquement ou à l’entité entière (un build >= 8770 est requis).

Cette restriction vous permet de supprimer les champs de mots de passe. Le compte externe reste toutefois accessible par tous les utilisateurs dans l’interface. Reportez-vous à [cette page](../../configuration/using/restricting-pii-view.md).

1. Accédez à **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Schémas de données]**.

1. Créez une **[!UICONTROL Extension d’un schéma]**.

   ![](assets/privacy-data-restriction.png)

1. Sélectionnez **[!UICONTROL Compte externe]** (extAccount).

1. Dans le dernier écran de l’assistant, vous pouvez modifier votre nouveau srcSchema afin de restreindre l’accès à tous les champs de mot de passe :

   Vous pouvez remplacer l’élément principal (`<element name="extAccount" ... >`) par :

   ```
   <element name="extAccount">
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
       <element name="s3Account">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
       </element>
       <element name="wapPush">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
       <element name="mms">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
   </element>
   ```

   Le srcSchema étendu peut ressembler à ceci :

   ```
   <srcSchema _cs="External Accounts (cus)" created="2017-05-12 07:53:49.691Z" createdBy-id="0"
               desc="Definition of external accounts (Email, SMS...) used by the modules"
               entitySchema="xtk:srcSchema" extendedSchema="nms:extAccount" img="" label="External Accounts"
               labelSingular="External account" lastModified="2017-05-12 08:33:49.365Z"
               mappingType="sql" md5="E9BB0CD6A4375F500027C86EA854E101" modifiedBy-id="0"
               name="extAccount" namespace="cus" xtkschema="xtk:srcSchema">
       <createdBy _cs="Administrator (admin)"/>
       <modifiedBy _cs="Administrator (admin)"/>
       <element name="extAccount">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
           <element name="s3Account">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
           </element>
           <element name="wapPush">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
           <element name="mms">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
       </element>
   </srcSchema>    
   ```

   >[!NOTE]
   >
   >Vous pouvez remplacer `$(loginId) = 0 or $(login) = 'admin'` par `hasNamedRight('admin')` pour autoriser tous les utilisateurs disposant du droit admin à voir ces mots de passe.

## Protection des pages contenant des PII

Nous conseillons fortement aux utilisateurs On-premise de protéger les pages pouvant contenir des informations personnelles, telles que les pages miroir, les applications web, etc.

Cette procédure est destinée à empêcher l’indexation de ces pages et à éviter ainsi un risque de sécurité potentiel. Voici quelques articles utiles :

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)
* [https://www.google.com/webmasters/tools/robots-testing-tool](https://www.google.com/webmasters/tools/robots-testing-tool)

Pour protéger vos pages, procédez comme suit :

1. Ajoutez un fichier robots.txt à la racine de votre serveur web (Apache ou IIS). Voici le contenu du fichier :

   ```
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   Pour IIS, reportez-vous à [cette page](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Pour Apache, vous pouvez placer le fichier dans **/var/www/robots.txt** (Debian).

1. Il arrive que l’ajout d’un fichier **robots.txt** ne soit pas suffisant en termes de sécurité. Par exemple, si un autre site web contient un lien vers votre page, il peut apparaître dans un résultat de recherche.

Outre le fichier **robots.txt**, il est conseillé d’ajouter un en-tête **X-Robots-Tag**. Vous pouvez le faire dans Apache ou IIS, ainsi que dans le fichier de configuration **serverConf.xml**.

Pour plus d’informations, reportez-vous à [cet article](https://developers.google.com/search/reference/robots_meta_tag).
