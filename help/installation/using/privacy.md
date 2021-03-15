---
solution: Campaign Classic
product: campaign
title: Confidentialité
description: En savoir plus sur les meilleures pratiques à suivre en matière de confidentialité.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 768fe62db4efd1217c22973c7e5dc31097d67bae
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 52%

---


# Confidentialité {#privacy}

## Demandes d’accès à des informations personnelles

Adobe Campaign propose un ensemble d’outils pour vous aider à respecter la vie privée dans le cadre du RGPD et de la CCPA.

Consultez [cette page](../../platform/using/privacy-management.md) pour obtenir des informations générales sur la gestion de la confidentialité et les étapes de mise en oeuvre en Adobe Campaign. Vous trouverez également des bonnes pratiques, ainsi qu’une vue d&#39;ensemble du processus utilisateur et des acteurs impliqués.

## Personnalisation des URL {#url-personalization}

Lorsque vous ajoutez des liens personnalisés à votre contenu, évitez toujours toute personnalisation dans la partie nom d’hôte de l’URL afin d’éviter des failles de sécurité potentielles. Les exemples suivants ne doivent jamais être utilisés dans tous les attributs d’URL &quot;a0/> ou `<img src="">` :`a href="">`

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Recommandations

Pour vérifier que vous n’utilisez pas les éléments ci-dessus, exécutez une requête sur la table d’URL de suivi via [Campaign Requêteur générique](../../platform/using/steps-to-create-a-query.md) ou créez un processus avec des critères de filtre dans l’[activité de requête](../../workflow/using/query.md).

Exemple :

1. Créez un processus et ajoutez une activité de Requête. En savoir plus.

1. Ouvrez l’activité de Requête et créez un filtre sur la table nmsTrackingUrl comme suit : débuts URL source avec http://&lt;% ou débuts URL source avec https://&lt;%.

1. Exécutez le workflow et vérifiez s’il y a des résultats.

1. Si c’est le cas, ouvrez la transition sortante pour afficher la liste des URL.

<img src="assets/privacy-query-dynamic-url.png">

### Mécanisme de signature

Pour améliorer la sécurité, un nouveau mécanisme de signature pour le suivi des liens dans les courriels a été introduit dans la version 19.1.4 (9032@3a9dc9c) et est disponible dans les versions 19.1.4 (9032@3a9dc9c) et Campaign 20.2. Cette option est activée par défaut pour tous les clients.

>[!NOTE]
>
>Lorsqu’un utilisateur clique sur une URL signée incorrecte, l’erreur suivante est renvoyée : « L’URL &quot;...&quot; demandée est introuvable. »

En outre, à compter de la version Campaign 20.2 et de la version Gold Standard, les clients hébergés et hybrides peuvent utiliser une amélioration pour désactiver les URL générées à partir des versions précédentes. Par défaut, cette option est désactivée. Vous pouvez contacter le [service d’assistance clientèle](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) pour activer cette fonction.

Pour activer ce nouveau mécanisme, les clients on-premise doivent suivre la procédure suivante sur tous les serveurs Campaign :

1. Dans le fichier de configuration du serveur (serverConf.xml), définissez **blockRedirectForUnsignedTrackingLink** sur **true**.
1. Redémarrez le service **nlserver** .
1. Sur le serveur de suivi, redémarrez le serveur web (apache2 sur Debian, httpd sur CentOS/RedHat, IIS sur Windows).

Les clients qui s’exécutent sur Gold Standard 19.1.4 peuvent rencontrer des problèmes avec les diffusions de notification Push à l’aide d’un lien de suivi ou de diffusions à l’aide de balises d’ancrage. Si tel est le cas, l’Adobe recommande de désactiver le nouveau mécanisme de signature pour le suivi des liens :

**Les** clients hébergés et hybrides doivent contacter  [Customer ](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) Career pour que ce mécanisme soit désactivé.

**Les** clients sur site peuvent suivre l&#39;étape suivante :

1. Dans le fichier de configuration du serveur (serverConf.xml), remplacez **signEmailLinks** par **false**.
1. Redémarrez le service **nlserver** .
1. Sur le serveur de suivi, redémarrez le serveur web (apache2 sur Debian, httpd sur CentOS/RedHat, IIS sur Windows).

## Restriction des données

Vous devez vous assurer que les mots de passe cryptés ne sont pas accessibles par un utilisateur authentifié avec de faibles privilèges. Pour cela, il existe deux méthodes : restreindre l’accès aux champs de mots de passe uniquement ou à l’entité entière (un build >= 8770 est requis).

Cette restriction vous permet de supprimer les champs de mots de passe. Le compte externe reste toutefois accessible par tous les utilisateurs dans l’interface. Consultez à ce sujet [cette page](../../configuration/using/restricting-pii-view.md).

1. Accédez à **[!UICONTROL Administration]** > **[!UICONTROL Paramétrage]** > **[!UICONTROL Schémas de données]**.

1. Créez une **[!UICONTROL Extension d&#39;un schéma]**.

   ![](assets/privacy-data-restriction.png)

1. Sélectionnez **[!UICONTROL Compte externe]** (extAccount).

1. Dans le dernier écran de l&#39;assistant, vous pouvez éditer le nouveau srcSchema pour restreindre l&#39;accès à tous les champs de mot de passe :

   Vous pouvez remplacer l’élément principal (`<element name="extAccount" ... >`) par :

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

   Ainsi, votre schéma srcSchema étendu peut ressembler à :

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
   >Vous pouvez remplacer `$(loginId) = 0 or $(login) = 'admin'` par `hasNamedRight('admin')` pour permettre à tous les utilisateurs disposant du droit d’administration de voir ces mots de passe.

## Protection des pages contenant des PII

Nous conseillons fortement aux utilisateurs on-premise de protéger les pages pouvant contenir des informations personnelles, telles que les pages miroir, les applications web, etc.

Cette procédure est destinée à empêcher l&#39;indexation de ces pages et ainsi d&#39;éviter un risque de sécurité potentiel. Voici quelques articles utiles :

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)
* [https://www.google.com/webmasters/tools/robots-testing-tool](https://www.google.com/webmasters/tools/robots-testing-tool)

Pour protéger vos pages, suivez ces étapes :

1. Ajoutez un fichier robots.txt à la racine de votre serveur web (Apache ou IIS). Voici le contenu du fichier :

   ```
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   Pour IIS, consultez [cette page](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Pour Apache, vous pouvez placer le fichier dans **/var/www/robots.txt** (Debian).

1. Parfois, l&#39;ajout d&#39;un fichier **robots.txt** n&#39;est pas suffisant en termes de sécurité. Par exemple, si un autre site Web contient un lien vers votre page, il peut apparaître dans les résultats de la recherche.

Outre le fichier **robots.txt**, il est conseillé d&#39;ajouter un en-tête **X-Robots-Tag**. Vous pouvez le faire dans Apache ou IIS, ainsi que dans le fichier de configuration **serverConf.xml**.

Pour plus d&#39;informations, consultez [cet article](https://developers.google.com/search/reference/robots_meta_tag).
