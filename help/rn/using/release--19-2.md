---
title: Version 19.2
seo-title: Version 19.2
description: Version 19.2
seo-description: null
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e4a8812a85c8c98cdf38145a2b1649530adab89d
workflow-type: tm+mt
source-wordcount: '1372'
ht-degree: 99%

---


# Version 19.2{#release-19-2}

[Upgrade de build](https://helpx.adobe.com/fr/campaign/kb/acc-build-upgrade.html) | [Versions du Panneau de contrôle](https://docs.adobe.com/content/help/fr-FR/control-panel/using/release-notes.html) | [Mises à jour de la documentation](../../rn/using/documentation-updates.md) | [Versions précédentes](../../rn/using/release--19-1.md) | [Fonctionnalités obsolètes](https://helpx.adobe.com/fr/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/do-not-localize/green3.png"/><strong>Disponibilité générale</strong></td>
   <td><img src="assets/do-not-localize/blue3.png"/><strong>Version diffusable</strong></td> 
   <td><img src="assets/do-not-localize/orange3.png"/><strong>Plus disponible</strong></td> 
   <td><img src="assets/do-not-localize/red3.png"/><strong>Obsolète</strong></td> 
  </tr> 
   <tr> 
   <td>Dernier build stable disponible. Build validé en production.<br> </td>
   <td>Build validé par Adobe. En attente de vérification de la production.<br> </td>
   <td>Build le plus récent disponible avec correctifs. Mise à jour requise.<br> </td>
   <td>Contient des régressions connues. La mise à jour est obligatoire.<br> </td>
  </tr> 
 </tbody> 
</table>

La **dernière version** stable est Gold Standard 10. Cliquez [ici](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/do-not-localize/orange_2.png) Version 19.2.3 - Build 9081 {#release-19-2-3-build-9081}

_7 février 2020_

**Améliorations**

* Correction d’un problème de régression lié à l’implémentation de la certification SSL, en raison duquel la connexion de l’utilisateur échouait sur Windows Server. (NEO-20629)
* Correction d’un problème qui affichait un numéro de balise de version incorrect dans le menu **À propos**.

## ![](assets/do-not-localize/orange_2.png) Version 19.2 - Build 9080 {#release-19-2-build-9080}

_2 décembre 2019_

**Nouveautés**

<table> 
 <thead> 
  <tr> 
   <th> <strong>California Consumer Privacy Act (CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>La CCPA est la nouvelle loi sur la protection des renseignements personnels de l'État de Californie. Elle a pour objectif d'harmoniser et de moderniser les exigences en matière de protection des données qui entreront en vigueur le 1er janvier 2020. Cette loi s'applique aux clients Adobe Campaign qui détiennent des données pour des personnes concernées résidant en Californie.</p>
    <p> Outre les fonctionnalités de protection des données déjà disponibles (notamment la gestion du consentement, les paramètres de conservation des données et les rôles utilisateur), Adobe Campaign vous aide à mieux vous préparer à l'application de la réglementation CCPA :</p>
    <ul>
      <li>Droit d'accès et droit de suppression : nous tirons parti des capacités qui ont été ajoutées pour le RGPD. <a href="https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html#righttoaccess">En savoir plus</a></li>
      <li>Vous pouvez vérifier si un consommateur a choisi de ne pas vendre de renseignements personnels. Pour ce faire, vous devez étendre la table des profils et ajouter un champ <strong>Opt-Out pour CCPA</strong>. <a href="https://helpx.adobe.com/fr/campaign/kb/acc-privacy.html#ccpa">En savoir plus</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Surveillance en ligne des workflows</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Vous pouvez désormais surveiller le statut d'exécution de tous les workflows de votre instance à l'aide de vues prédéfinies.</p>
   <p>Pour plus d'informations, consultez la <a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">documentation détaillée</a>.</p></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Contenu interactif avec AMP</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Adobe Campaign offre la possibilité de tester le nouveau format interactif <a href="https://amp.dev/about/email/">AMP pour email</a>. Ce format permet aux spécialistes du marketing d'incorporer des composants AMP dans les messages pour améliorer l'expérience d'utilisation des emails grâce à un contenu riche, dynamique et interactif, directement exploitable dans le message lui-même.</p>
   <p> Cette fonctionnalité est diffusée en version bêta publique.</p>
   <p>Pour plus d'informations, consultez la <a href="../../delivery/using/defining-interactive-content.md">documentation détaillée</a> et regardez le <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">tutoriel vidéo</a>.</p><br /></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Messages SMS sécurisés (TLS)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Les SMS sécurisés sont maintenant pris en charge via le connecteur SMPP Générique étendu, ce qui permet une connexion chiffrée au fournisseur.</p> <p><strong>Avertissement</strong> Cette fonctionnalité nécessite un certificat à jour sur tous les serveurs. Les certificats non valides, révoqués ou parvenus à expiration génèrent des erreurs qui affectent les capacités globales d'envoi de SMS.</p><p>Pour plus d'informations, consultez la <a href="https://helpx.adobe.com/fr/campaign/kb/sms-connector-protocol-and-settings.html">documentation détaillée</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Améliorations de la sécurité**

* Correction des vulnérabilités de la génération de scripts intersites stockés de l&#39;interface de Campaign - validation des données d&#39;entrée et codage en sortie. (NEO-16810)
* Correction d&#39;un problème de sécurité concernant l&#39;autorisation de profil qui pouvait accepter l&#39;accès à des données non autorisées. Les règles de restriction de connexion ont été renforcées. (NEO-14445)

**Améliorations**

* Optimisation de la consommation de mémoire pour les notifications Push.
* Pour optimiser les performances et le stockage, la gestion du fichier **logins.log** a été améliorée. Le fichier est maintenant divisé en plusieurs fichiers, un par jour, avec un maximum de 365 fichiers conservés. [En savoir plus](../../production/using/log-files.md)
* Le compte externe Microsoft Dynamics CRM peut désormais être configuré à l&#39;aide des informations d&#39;identification (mot de passe + nom d&#39;utilisateur) ou du certificat (clé privée). [En savoir plus](../../platform/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Certaines améliorations ont été apportées au connecteur Hadoop FDA pour améliorer la fiabilité
* Une barrière de sécurité spécifique a été ajoutée pour vérifier l&#39;espace disque avant de permettre le transfert des ressources publiques sur le serveur.
* De nouvelles [options Campaign](../../installation/using/configuring-campaign-options.md) ont été ajoutées :
   * L&#39;option de configuration **WdbcKillSessionPolicy** permet d&#39;influer sur le comportement **Arrêt inconditionnel** pour tous les workflows et les requêtes de base de données PostgreSQL.
   * L&#39;option **NmsOperation_DeliveryPreparingWindow** permet de définir le nombre de jours au-delà desquels les diffusions dont le statut est incohérent seront exclues du nombre de diffusions en cours.
   * L&#39;option **WdbcOptions_TempDbName** permet de configurer une base de données distincte pour les tables de travail de Microsoft SQL Server. Cette configuration permet d&#39;optimiser les sauvegardes et la réplication. [En savoir plus](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * L&#39;option **XtkCleanup_NoStats** a été améliorée pour PostgreSQL afin de mieux contrôler le comportement de l&#39;étape d&#39;optimisation du stockage du workflow de nettoyage de la base de données. [En savoir plus](../../production/using/database-cleanup-workflow.md#statistics-update)
* Un mécanisme de verrouillage de compte a été ajouté à l&#39;API **logon()**. Il empêche toute nouvelle tentative de connexion après un certain nombre de tentatives consécutives de connexion ayant échoué pour une période donnée.
* Une nouvelle option **Durée maximale d&#39;exécution de la personnalisation** des propriétés de diffusion permet de définir un délai d&#39;expiration pour la durée d&#39;exécution de la personnalisation. Ce mécanisme empêche que cette durée ne soit trop longue. [En savoir plus](../../delivery/using/personalization-fields.md#timing-out-personalization)
* L&#39;option **protocole ftp** a été ajoutée pour vous permettre d&#39;utiliser une configuration proxy pour les connexions SFTP. [En savoir plus](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)
* Nouvelle prise en charge de l&#39;accès par proxy à un serveur SFTP externe pour les environnements on-premise.
* Une barrière de sécurité spécifique a été ajoutée pour empêcher l&#39;installation de packages incompatibles avec l&#39;instance Campaign. [En savoir plus](../../installation/using/installing-campaign-standard-packages.md)

_Systèmes obsolètes_

Les systèmes suivants sont désormais [obsolètes](https://helpx.adobe.com/fr/campaign/kb/deprecated-and-removed-features.html) pour les implémentations de Campaign Classic :
* Apache 2.2
* Centos 6

Vérifiez que vous disposez des versions prises en charge des systèmes répertoriés dans la dernière matrice de compatibilité Campaign. [En savoir plus](https://helpx.adobe.com/fr/campaign/kb/compatibility-matrix.html)

_SDK Campaign Mobile_

Le build 1.0.26 du SDK iOS est désormais disponible. Dans ce nouveau build, nous avons ajouté la prise en charge d&#39;iOS 13. Cette nouvelle version prend désormais en charge la priorité des notifications et le nouveau processus de gestion des jetons d&#39;enregistrement pour les notifications Push iOS 13. Si vous exécutez des applications correspondant à une version précédente du SDK, vous devez recompiler vos applications avec le nouveau. Pour obtenir le SDK, contactez l&#39;Assistance clientèle Adobe.

**Correctifs**

* Correction d&#39;un blocage de la console qui pouvait se produire lors de l&#39;ajout d&#39;une table liée vide dans l&#39;activité de workflow **Chargement (SGBD)**. (NEO-12213)
* Correction d&#39;un problème en raison duquel certains messages ne pouvaient pas être traités par le serveur de Mid-sourcing. (NEO-12395)
* Correction d&#39;un problème dans le workflow de nettoyage de la base de données lors de l&#39;utilisation de l&#39;option query banding avec Teradata. (NEO-12399)
* Correction d&#39;un problème affectant l&#39;analyse des diffusions avec une règle de typologie incluant le domaine ne.jp. (NEO-12609)
* Correction d&#39;un problème lié aux SMS pour les mises à jour TLS qui impliquaient des règles de certificat plus restrictives. Ces mises à jour peuvent entraîner un échec de la connexion entre les serveurs de marketing et de Mid-sourcing en cas de certificat obsolète. (NEO-17698)
* Correction d&#39;un problème en cas d&#39;utilisation du bouton **Tester la connexion** pour un compte externe dans un environnement de Mid-sourcing avec l&#39;authentification Vault. (NEO-12722)
* Correction d&#39;un problème concernant les requêtes utilisant des fonctions de date avec une connexion FDA Hadoop. (NEO-12847)
* Correction d&#39;un problème survenant lors du remplacement d&#39;une image dans l&#39;éditeur d&#39;email. (NEO-13098)
* Correction d&#39;un problème susceptible d&#39;entraîner des erreurs après un upgrade pour les dossiers antérieurement supprimés ou déplacés vers un autre emplacement. (NEO-13118)
* Correction d&#39;un problème d&#39;affichage d&#39;image lors de l&#39;utilisation de l&#39;option **Définir les images par taille d&#39;écran d&#39;appareil** avec les messages LINE. (NEO-13228)
* Correction d&#39;un problème de préparation de diffusion lorsque l&#39;option **Exclure les adresses en double lors de la diffusion** est désélectionnée. (NEO-13240)
* Correction d&#39;un problème dans les workflows survenant lors de l&#39;utilisation de l&#39;activité **Transfert de fichier** pour télécharger des fichiers dont le nom contient un espace, à l&#39;aide de l&#39;option **Effacer les fichiers source après leur transfert**. (NEO-13411)
* Correction d&#39;un problème de nettoyage du cache de Tomcat qui pouvait entraîner des problèmes de mémoire. (NEO-13456)
* Correction d&#39;un problème lors de l&#39;installation du package intégré **Pilotage du moteur d&#39;offre avec instance d&#39;exécution** sur une instance de contrôle existante s&#39;exécutant dans Microsoft SQL 2017. (NEO-13539)
* Correction d&#39;un blocage de la console pouvant survenir lors de la désélection des URL trackées dans un email dans l&#39;onglet **Contenu texte**. (NEO-13545)
* Correction d&#39;un problème de codage du nom d&#39;un expéditeur chinois. (NEO-13837)
* Correction d&#39;une erreur pouvant survenir lors de l&#39;affichage des données relatives aux réponses à un questionnaire dans l&#39;Explorateur. (NEO-14590)
* Correction d&#39;un problème susceptible d&#39;entraîner une incohérence entre la classification du log de diffusion et la table de quarantaine. (NEO-16547)
* Correction d&#39;un problème avec les clés DKIM non incorporées dans les emails. (NEO-16804)
* Correction d&#39;un problème qui affichait un code d&#39;erreur incorrect lorsqu&#39;un jeton de session non valide était utilisé dans le contexte d&#39;appels d&#39;API pour déclencher des événements. Le code d&#39;erreur était &quot;HTTP 200 OK&quot; au lieu de &quot;HTTP 403 Forbidden&quot;. (NEO-16826)
* Correction d&#39;un problème lors de l&#39;affichage des rapports de diffusion via un accès Web. (NEO-17015)
* Correction d&#39;un problème d&#39;authentification IMS lors de la connexion à Adobe Campaign. (NEO-17312)
* Correction d&#39;un problème qui empêchait la suppression des emails mis en quarantaine par le processus de gestion des données personnelles. (NEO-17314)
* Correction de problèmes de débit après l&#39;upgrade vers le build 9031 avec la base de données SQL. (NEO-17558)
* Correction d&#39;un problème qui affectait le connecteur CRM avec Salesforce. (NEO-17712)
* Correction d&#39;un problème de timeout lors de l&#39;importation de données à partir d&#39;un SFTP externe. (NEO-19723)
* Correction d&#39;un problème lors de l&#39;accès aux modèles prédictifs. (NEO-19713)
* Correction d&#39;un problème affectant l&#39;échantillonnage aléatoire dans l&#39;activité de workflow **Partage** avec la base de données Hadoop FDA. (NEO-16636)

