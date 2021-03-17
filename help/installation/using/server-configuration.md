---
solution: Campaign Classic
product: campaign
title: Configuration du serveur
description: En savoir plus sur les meilleures pratiques de configuration du serveur.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '1159'
ht-degree: 71%

---


# Configuration du serveur {#server-configuration}

## Paramétrage des zones de sécurité

>[!IMPORTANT]
>
>A partir du build 8977, l’interface Security Zones Self Service n’est plus disponible.
>
>* Si vous êtes hébergé sur AWS, l’ajout d’IP à la liste autorisée doit être effectué dans Panneau de Contrôle. Pour plus d’informations, consultez la [documentation dédiée](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html).
>* Si votre instance n’est pas hébergée sur AWS, contactez l’équipe de support Adobe pour ajouter les adresses IP à la liste autorisée.

>
>
Pour vérifier si votre instance est hébergée sur AWS, suivez les étapes présentées dans [cette section](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

* Vérifiez que le proxy inverse n&#39;est pas autorisé dans subNetwork. Si c&#39;est le cas, l&#39;**ensemble** du trafic est détecté comme provenant de cette adresse IP locale et est donc considéré comme digne de confiance.

* Limitez l&#39;utilisation de sessionTokenOnly=&quot;true&quot; :

   * Avertissement : si cet attribut est défini sur true, l&#39;opérateur peut être exposé à une **attaque CRSF**.
   * De plus, le cookie sessionToken n&#39;étant pas défini avec un flag httpOnly, certains codes JavaScript côté client peuvent le lire.
   * L&#39;utilisation de Message Center avec plusieurs instances d&#39;exécution requiert toutefois l&#39;activation de l&#39;option sessionTokenOnly : créez une nouvelle zone de sécurité avec l&#39;option sessionTokenOnly définie sur &quot;true&quot; et ajoutez **uniquement les adresses IP nécessaires** à cette zone.

* Si possible, définissez all allowHTTP, showErrors sur false (non pour localhost) et vérifiez-les.

   * allowHTTP = &quot;false&quot; : force les opérateurs à utiliser le protocole HTTPS.
   * showErrors = &quot;false&quot; : masque les erreurs techniques (y compris celles de SQL). Cet attribut empêche l&#39;affichage d&#39;un trop grand nombre d&#39;informations, mais il limite la possibilité des marketeurs de corriger les erreurs (sans demander des informations supplémentaires à un administrateur).

* Définissez allowDebug sur true uniquement sur les adresses IP utilisées par les utilisateurs marketing/administrateurs qui doivent créer (ou plutôt prévisualiser) des questionnaires, webApps et rapports. Ce flag permet d&#39;afficher les règles de relais et de les déboguer pour ces adresses IP.

* Ne définissez jamais les attributs allowEmptyPassword, allowUserPassword et allowSQLInjection sur true. Ils ne servent qu&#39;à faciliter la migration depuis la v5 vers la v6.0 :

   * L&#39;attribut **allowEmptyPassword** permet aux opérateurs de disposer d&#39;un mot de passe vide. Si c&#39;est votre cas, demandez à tous les opérateurs de définir un mot de passe avec un délai. Une fois ce délai passé, définissez cet attribut sur la valeur false.

   * L&#39;attribut **allowUserPassword** permet aux opérateurs d&#39;envoyer leurs identifiants en tant que paramètres (afin qu&#39;ils puissent être connectés par Apache/IIS/un proxy). Cette fonctionnalité était auparavant utilisée pour simplifier l&#39;utilisation de l&#39;API. Vous pouvez vérifier dans votre « livre de recettes » (ou dans les spécifications) si des applications tierces utilisent cet attribut. Si c&#39;est le cas, vous devez demander à ces tiers de changer la façon dont ils utilisent notre API et supprimer cette fonctionnalité dès que possible.

   * **** allowSQLInjectionpermet à l&#39;utilisateur d&#39;effectuer des injections SQL en utilisant une ancienne syntaxe. Dès que possible, effectuez les corrections décrites dans [cette page](../../migration/using/general-configurations.md) pour pouvoir définir cet attribut sur false. Vous pouvez utiliser /nl/jsp/ping.jsp?zones=true pour vérifier le paramétrage de votre zone de sécurité. Cette page affiche l&#39;état actif des mesures de sécurité (calculé avec ces flags de sécurité) pour l&#39;adresse IP actuelle.

* Cookie HttpOnly/useSecurityToken : reportez-vous au flag **sessionTokenOnly**.

* Limitez le nombre d’adresses IP ajoutées à la liste autorisée : dans les zones de sécurité, nous avons ajouté les 3 plages pour les réseaux privés. Il est peu probable que vous utilisiez toutes ces adresses IP. Donc gardez uniquement ceux dont vous avez besoin.

* Mettez à jour l&#39;opérateur interne/webApp pour qu&#39;il soit accessible uniquement dans localhost.

## Protection des téléchargements de fichiers

Demandez aux utilisateurs quels types de fichiers ils téléchargent sur le serveur à l&#39;aide de l&#39;interface web/nlclient. Pour rappel, les besoins de l&#39;entreprise peuvent être les suivants :

* des images (jpg, gif, png, etc.),
* des contenus (zip, html, css, etc.),
* des ressources marketing (doc, xls, pdf, psd, tiff, etc.),
* des pièces jointes à des emails (doc, pdf, etc.),
* des fichiers ETL (txt, csv, tab, etc.)
* etc.

Ajoutez tous ces types de fichiers dans serverConf/shared/datastore/@uploadAllowlist (expression régulière Java valide). En savoir plus sur [cette page](../../installation/using/configuring-campaign-server.md#limiting-uploadable-files).

Adobe Campaign ne limite pas la taille du fichier. Mais vous pouvez le faire en configurant IIS/Apache. En savoir plus dans [cette section](../../installation/using/web-server-configuration.md).

## Relais

Pour plus d&#39;informations, consultez [cette page](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays).

Par défaut, toutes les pages dynamiques sont relayées automatiquement au serveur Tomcat local de la machine dont le module Web est démarré. Vous pouvez choisir de ne pas relayer certaines d&#39;entre elles. Si vous n&#39;utilisez pas certains modules d&#39;Adobe Campaign (tels que webapp, interaction, certaines pages jsp), vous pouvez les supprimer des règles de relais.

Nous avons forcé la possibilité d’afficher par défaut les ressources des utilisateurs finaux à l’aide de HTTP (httpAllowed=&quot;true&quot;). Comme ces pages peuvent afficher certaines PII (contenu/adresse email), un bon d’échange ou une offre, vous devez forcer de nouveau HTTPS sur ces chemins.

Si vous utilisez des noms d&#39;hôte différents (un nom d&#39;hôte public et un nom d&#39;hôte pour les opérateurs), vous pouvez également empêcher le relais de certaines ressources dont les opérateurs ont besoin sur le nom DNS public.

## Protection des connexions sortantes

La liste par défaut des URL pouvant être appelées par des codes JavaScript (workflows, etc.) est limitée. Pour autoriser une nouvelle URL, l’administrateur doit la référencer dans le fichier [serverConf.xml](../../installation/using/the-server-configuration-file.md).

Il existe trois modes de protection des connexions :

* **Blocking** : toutes les URL qui ne figurent pas sur la liste autorisée sont bloquées et un message d’erreur s’affiche. Il s&#39;agit du mode par défaut après un postupgrade.
* **Permissive** : toutes les URL qui ne figurent pas sur la liste autorisée sont autorisées.
* **Avertissement**  : toutes les URL ne figurant pas sur la liste autorisée sont autorisées, mais l’interprète JS émet un avertissement afin que l’administrateur puisse les collecter. Ce mode ajoute des messages d’avertissement JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

Les nouveaux clients utiliseront le mode de blocage. S’ils souhaitent autoriser une nouvelle URL, ils doivent contacter leur administrateur pour l’ajouter à la liste autorisée.

Les clients existants provenant d&#39;une migration peuvent utiliser pendant un certain temps le mode d&#39;avertissement. Ils doivent entre-temps analyser le trafic sortant pour autoriser les URL.

## Restriction des commandes (côté serveur)

Plusieurs commandes sont blacklistées et ne peuvent pas être exécutées à l&#39;aide de la fonction execCommand. Un utilisateur Unix dédié fournit une sécurité supplémentaire pour exécuter des commandes externes. Pour les installations hébergées, cette restriction est automatiquement appliquée. Pour les installations sur site, vous pouvez configurer manuellement cette restriction en suivant les instructions de [cette page](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). En outre, les activités de flux de travaux **[!UICONTROL Script]** et **[!UICONTROL Tâche externe]** ne sont pas disponibles (instances nouvellement installées).

## Autres paramétrages

Vous pouvez ajouter des en-têtes HTTP supplémentaires pour toutes les pages (pour plus d’informations, voir [cette page](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)) :

* Vous pouvez ajouter d&#39;autres en-têtes tels que HSTS, X-FRAME-OPTIONS, CSP, etc.
* Vous devez les tester dans un environnement de test avant de les appliquer en production.

   >[!IMPORTANT]
   >
   >Adobe Campaign peut être rompu en ajoutant certains en-têtes.

Adobe Campaign vous permet de définir un mot de passe simple dans l’élément `<dbcnx .../>`. N’utilisez pas cette fonctionnalité.

Par défaut, Adobe Campaign n’associe pas une session à une adresse IP spécifique, mais vous pouvez activer cette option pour empêcher tout vol de la session. Pour ce faire, dans le fichier [serverConf.xml](../../installation/using/the-server-configuration-file.md), définissez l’attribut checkIPConsistent sur **true** dans le noeud `<authentication>`.

Par défaut, Adobe Campaign MTA n’utilise pas de connexion sécurisée pour envoyer du contenu au serveur SMTP. Vous devez activer cette fonction (peut réduire la vitesse de diffusion). Pour ce faire, définissez **enableTLS** sur **true** dans le noeud `<smtp ...>`.

Vous pouvez réduire la durée de vie d&#39;une session dans le nœud d&#39;authentification (attribut sessionTimeOutSec).
