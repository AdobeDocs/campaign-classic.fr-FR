---
solution: Campaign Classic
product: campaign
title: Configuration de la sécurité du serveur
description: En savoir plus sur les meilleures pratiques de configuration du serveur
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
translation-type: tm+mt
source-git-commit: ae4f86f3703b9bfe7f08fd5c2580dd5da8c28cbd
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 59%

---

# Paramètres de sécurité du serveur {#server-configuration}

## Protection des téléchargements de fichiers

Identifiez avec les utilisateurs opérationnels le type de fichiers qu’ils téléchargent sur le serveur à l’aide de la console client Campaign ou de l’interface Web. Pour rappel, les besoins de l’entreprise peuvent être les suivants :

* des images (jpg, gif, png, etc.),
* des contenus (zip, html, css, etc.),
* des ressources marketing (doc, xls, pdf, psd, tiff, etc.),
* des pièces jointes à des emails (doc, pdf, etc.),
* des fichiers ETL (txt, csv, tab, etc.)
* etc.

Ajoutez tous ces types de fichiers dans serverConf/shared/datastore/@uploadAllowlist (expression régulière Java valide). En savoir plus sur [cette page](../../installation/using/file-res-management.md).

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
