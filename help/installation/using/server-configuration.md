---
product: campaign
title: Configuration de la sécurité du serveur
description: En savoir plus sur les bonnes pratiques relatives à la configuration du serveur
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 100%

---

# Paramètres de sécurité du serveur {#server-configuration}

## Protection des téléchargements de fichiers

Demandez aux utilisateurs quels types de fichiers ils téléchargent sur le serveur à l’aide de la console cliente de Campaign ou de l’interface Web. Pour rappel, les besoins de l’entreprise peuvent être les suivants :

* des images (jpg, gif, png, etc.),
* des contenus (zip, html, css, etc.),
* des ressources marketing (doc, xls, pdf, psd, tiff, etc.),
* des pièces jointes à des emails (doc, pdf, etc.),
* des fichiers ETL (txt, csv, tab, etc.)
* etc.

Ajoutez tous ces types de fichiers dans serverConf/shared/datastore/@uploadAllowlist (expression régulière Java valide). En savoir plus à ce propos sur [cette page](../../installation/using/file-res-management.md).

Adobe Campaign ne limite pas la taille des fichiers, mais vous pouvez la limiter en configurant IIS/Apache. En savoir plus dans [cette section](../../installation/using/web-server-configuration.md).

## Relais

Pour plus d’informations, reportez-vous à [cette page](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays).

Par défaut, toutes les pages dynamiques sont relayées automatiquement au serveur Tomcat local de la machine dont le module web est démarré. Vous pouvez choisir de ne pas relayer certaines d’entre elles. Si vous n’utilisez pas certains modules d’Adobe Campaign (tels que webapp, interaction, certains jsp), vous pouvez les supprimer des règles de relais.

Nous avons forcé la possibilité d’afficher par défaut les ressources des utilisateurs finaux à l’aide de HTTP (httpAllowed=&quot;true&quot;). Comme ces pages peuvent afficher certaines PII (contenu/adresse email), un bon d’échange ou une offre, vous devez forcer de nouveau HTTPS sur ces chemins.

Si vous utilisez des noms d’hôte différents (un nom d’hôte public et un nom d’hôte pour les opérateurs), vous pouvez également empêcher le relais de certaines ressources dont les opérateurs ont besoin sur le nom DNS public.

## Protection des connexions sortantes

La liste par défaut des URL pouvant être appelées par des codes JavaScript (workflows et autres) est limitée. Pour autoriser une nouvelle URL, l’administrateur doit la référencer dans le fichier [serverConf.xml](../../installation/using/the-server-configuration-file.md).

Il existe trois modes de protection des connexions :

* **Blocage** : toutes les URL qui ne figurent pas sur la liste autorisée sont bloquées et un message d’erreur s’affiche. Il s’agit du mode par défaut après un postupgrade.
* **Permissif** : toutes les URL qui ne figurent pas sur la liste autorisée sont autorisées.
* **Avertissement** : toutes les URL qui ne figurent pas sur la liste autorisée sont autorisées, mais l’interpréteur JS émet un avertissement pour que l’administrateur puisse les collecter. Ce mode ajoute des messages d’avertissement JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

Les nouveaux clients utiliseront le mode Blocking. S’ils souhaitent autoriser une nouvelle URL, ils doivent contacter leur administrateur pour l’ajouter à la liste autorisée.

Les clients existants provenant d’une migration peuvent utiliser pendant un certain temps le mode d’avertissement. Ils doivent entre-temps analyser le trafic sortant pour autoriser les URL.

## Restriction des commandes (côté serveur)

Plusieurs commandes sont incluses dans la liste bloquée et ne peuvent pas être exécutées à l’aide de la fonction execCommand. Un utilisateur Unix dédié fournit une sécurité supplémentaire pour exécuter des commandes externes. Pour les installations hébergées, cette restriction est appliquée automatiquement. Pour les installations On-premise, vous pouvez configurer manuellement cette restriction en suivant les instructions décrites sur [cette page](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). En outre, les activités de workflow **[!UICONTROL Script]** et **[!UICONTROL Tâche externe]** ne sont pas disponibles (instances nouvellement installées).

## Autres configurations

Vous pouvez ajouter des en-têtes HTTP supplémentaires à toutes les pages (pour plus d’informations, reportez-vous à [cette page](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)) :

* Vous pouvez ajouter d’autres en-têtes tels que HSTS, X-FRAME-OPTIONS, CSP et bien d’autres.
* Vous devez les tester dans un environnement de test avant de les appliquer en production.

  >[!IMPORTANT]
  >
  >L’ajout de certains en-têtes peut entraîner un dysfonctionnement d’Adobe Campaign.

Adobe Campaign vous permet de définir un mot de passe en clair dans l’élément `<dbcnx .../>`. N’utilisez pas cette fonctionnalité.

Par défaut, Adobe Campaign n’associe pas une session à une adresse IP spécifique, mais vous pouvez activer cette option pour empêcher tout vol de la session. Pour ce faire, dans le [fichier serverConf.xml](../../installation/using/the-server-configuration-file.md), définissez l’attribut checkIPConsistent sur **true** dans le nœud `<authentication>`.

Par défaut, le MTA d’Adobe Campaign n’utilise pas de connexion sécurisée pour envoyer du contenu au serveur SMTP. Vous devez activer cette fonctionnalité (laquelle peut réduire la vitesse des diffusions). Pour ce faire, définissez **enableTLS** sur **true** dans le nœud `<smtp ...>`.

Vous pouvez réduire la durée de vie d’une session dans le nœud d’authentification (attribut sessionTimeOutSec).
