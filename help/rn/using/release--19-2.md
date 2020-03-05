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
source-git-commit: fd7bc26fe12a26d8fb0dcccd2135b799e76b52bd

---


# Version 19.2{#release-19-2}

[Créer une mise à niveau](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) | Versions [du](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) Panneau de configuration| Mises à jour [de la documentation](../../rn/using/documentation-updates.md) | Versions [précédentes](../../rn/using/release--19-1.md) | Fonctions [obsolètes](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/green3.png"/><strong>Disponibilité générale</strong></td>
   <td><img src="assets/blue3.png"/><strong>Candidat à la libération</strong></td> 
   <td><img src="assets/orange3.png"/><strong>Plus disponible</strong></td> 
   <td><img src="assets/red3.png"/><strong>Obsolète</strong></td> 
  </tr> 
   <tr> 
   <td>Dernière version stable disponible. Création validée en production.<br> </td>
   <td>Génération validée par Adobe. En attente de vérification de la production.<br> </td>
   <td>Version plus récente disponible avec correctifs de bogues. La mise à jour est requise.<br> </td>
   <td>Contient des régressions connues. La mise à jour est obligatoire.<br> </td>
  </tr> 
 </tbody> 
</table>

La **dernière version** stable est 9032 (205c981c3). Click [here](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/blue_2.png) Version 19.2.3 - Version 9081 {#release-19-2-3-build-9081}

_7 février 2020_

**Améliorations**

* Correction d’un problème de régression en raison de l’implémentation de la certification SSL, en raison duquel la connexion de l’utilisateur échouait sur le serveur Windows. (NÉO-20629)
* Correction d’un problème qui affichait un numéro de balise de version incorrect dans le menu **À propos** .

## ![](assets/orange_2.png) Version 19.2 - Version 9080 {#release-19-2-build-9080}

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
   <td> <p>L’ACCP est la nouvelle loi sur la protection des renseignements personnels de l’État de Californie qui harmonise et modernise les exigences en matière de protection des données qui entreront en vigueur le 1er janvier 2020. Cette loi s'applique aux clients Adobe Campaign qui détiennent des données pour des personnes concernées résidant en Californie.</p>
    <p>Outre les fonctionnalités de confidentialité déjà disponibles (notamment la gestion du consentement, les paramètres de rétention des données et les rôles utilisateur), Adobe Campaign vous aide à mieux vous préparer à l’application CCPA :</p>
    <ul>
      <li>Droit d'accès et droit de suppression : nous tirons parti des capacités qui ont été ajoutées pour le RGPD. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">En savoir plus</a></li>
      <li>Vous pouvez déterminer si un consommateur a choisi de ne pas vendre de renseignements personnels. Pour ce faire, vous devez étendre le tableau Profils et ajouter un champ <strong>d’exclusion pour l’ACCP</strong> . <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">En savoir plus</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Surveillance en direct du flux de travail</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Vous pouvez désormais surveiller l’état d’exécution de tous les processus de votre instance à l’aide de vues prédéfinies.</p>
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
<td> <p>Adobe Campaign vous permet de tester le nouveau format interactif <a href="https://amp.dev/about/email/">AMP pour le courrier électronique</a> , qui permet aux spécialistes du marketing d’inclure des composants AMP dans les messages afin d’améliorer l’expérience du courrier électronique grâce à un contenu riche, dynamique et interactif, directement exploitable dans le message lui-même.</p>
   <p>Cette fonctionnalité est publiée en version bêta publique.</p>
   <p>For more information, refer to the <a href="../../delivery/using/defining-interactive-content.md">detailed documentation</a> and the <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">tutorial video</a>.</p><br /></td> 
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
<td> <p>Les SMS sécurisés sont maintenant pris en charge via le connecteur SMPP Générique étendu, ce qui permet une connexion chiffrée au fournisseur.</p> <p><strong>Avertissement</strong> Cette fonctionnalité nécessite un certificat à jour sur tous les serveurs. Les certificats non valides, révoqués ou expirés génèrent des erreurs affectant les capacités d'envoi SMS globales.</p><p>Pour plus d'informations, consultez la <a href="https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html">documentation détaillée</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Améliorations de la sécurité**

* Correction des vulnérabilités de script intersite stockées dans l’interface de campagne - validation des données d’entrée et codage de sortie. (NEO-16810)
* Correction d’un problème de sécurité sur l’autorisation de profil qui pouvait autoriser l’accès à des données non autorisées, en renforçant la stratégie de restriction de connexion. (NEO-14445)

**Améliorations**

* Optimisation de la consommation de mémoire pour les notifications Push.
* Pour optimiser les performances et le stockage, la gestion du fichier **logins.log** a été améliorée. Le fichier est maintenant divisé en plusieurs fichiers, un par jour avec un maximum de 365 fichiers conservés. [En savoir plus](../../production/using/log-files.md)
* Le compte externe Microsoft Dynamics CRM peut désormais être configuré à l’aide des informations d’identification de mot de passe (mot de passe + nom d’utilisateur) ou du certificat (clé privée). [En savoir plus](../../platform/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Certaines améliorations ont été apportées au connecteur Hadoop FDA pour améliorer la fiabilité
* Un garde-fou spécifique a été ajouté pour vérifier l&#39;espace disque avant de permettre le transfert des ressources publiques sur le serveur.
* De nouvelles options [de](../../installation/using/configuring-campaign-options.md) campagne ont été ajoutées :
   * L&#39;option de configuration **WdbcKillSessionPolicy** vous permet d&#39;affecter le comportement Arrêt **** inconditionnel sur tous les processus et requêtes de base de données PostgreSQL.
   * L&#39;option **NmsOperation_DeliveryPreparingWindow** vous permet de définir le nombre de jours au-dessus desquels les livraisons avec un statut incohérent seront exclues du nombre de livraisons en cours.
   * L&#39;option **WdbcOptions_TempDbName** vous permet de configurer une base de données distincte pour les tables de travail sur Microsoft SQL Server. Cela optimise les sauvegardes et la réplication. [En savoir plus](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * L&#39;option **XtkCleanup_NoStats** a été améliorée pour PostgreSQL afin de mieux contrôler le comportement de l&#39;étape d&#39;optimisation du stockage du processus de nettoyage de la base de données. [En savoir plus](../../production/using/database-cleanup-workflow.md#statistics-update)
* Un mécanisme de verrouillage de compte a été ajouté à l’API **logon()** . Elle empêche toute nouvelle tentative de connexion après un certain nombre de tentatives consécutives d’échec de connexion au cours d’une période donnée.
* Une nouvelle option **Maximum personalization run time** dans les propriétés de diffusion vous permet de définir un délai d’expiration pour le délai d’exécution de la personnalisation, afin d’empêcher que la phase de personnalisation ne s’exécute trop longtemps. [En savoir plus](../../delivery/using/personalization-fields.md#timing-out-personalization)
* L’option de protocole **** ftp a été ajoutée pour vous permettre d’utiliser une configuration proxy pour les connexions SFTP. [En savoir plus](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)
* Nouvelle prise en charge de l’accès par proxy à un serveur externe SFTP pour les environnements sur site.
* Un garde-fou spécifique a été ajouté pour empêcher l&#39;installation de packages qui ne sont pas compatibles avec l&#39;instance Campaign. [En savoir plus](../../installation/using/installing-campaign-standard-packages.md)

_Systèmes obsolètes_

Les systèmes suivants sont désormais [obsolètes](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html) pour les implémentations de Campaign Classic :
* Apache 2.2
* Centos 6

Vérifiez que vous utilisez les versions prises en charge des systèmes répertoriés dans la dernière matrice de compatibilité des campagnes. [En savoir plus](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

_SDK de campagne mobile_

La version 1.0.26 du SDK iOS est désormais disponible. Dans cette nouvelle version, nous avons ajouté la prise en charge d’iOS 13. Cette nouvelle version prend désormais en charge la priorité des notifications et le nouveau processus de gestion des jetons d’enregistrement pour les notifications Push iOS 13. Si vous exécutez des applications sur une version précédente du SDK, vous devez recompiler vos applications avec le nouveau SDK. Pour obtenir le SDK, contactez le service à la clientèle d’Adobe.

**Correctifs**

* Correction d’un blocage de la console qui pouvait se produire lors de l’ajout d’une table liée vide dans l’activité de flux de travaux **Data Loading (RDBMS)** . (NEO-12213)
* Correction d’un problème en raison duquel certains messages ne pouvaient pas être traités par le serveur d’approvisionnement intermédiaire. (NEO-12395)
* Correction d’un problème dans le processus de nettoyage de la base de données lors de l’utilisation de l’option Bande de requête avec Teradata. (NEO-12399)
* Correction d’un problème affectant l’analyse de remise avec la règle de typologie incluant le domaine ne.jp. (NEO-12609)
* Correction d’un problème lié aux SMS sur les mises à jour TLS qui impliquaient une stratégie de certificat plus restrictive. Ces mises à jour peuvent entraîner un échec de connexion entre les serveurs de marketing et de mi-sourcing dans le cas d’un certificat obsolète. (NEO-17698)
* Correction d’un problème lors de l’utilisation du bouton **Tester la connexion** sur un compte externe dans un environnement de milieu de gamme avec l’authentification Vault. (NEO-12722)
* Correction d’un problème sur les requêtes utilisant des fonctions de date avec une connexion Hadoop de la FDA. (NEO-12847)
* Correction d’un problème lors du remplacement d’une image dans l’éditeur de courrier électronique. (NEO-13098)
* Correction d’un problème susceptible d’entraîner des erreurs après la mise à niveau sur les dossiers qui avaient été supprimés ou déplacés vers un autre emplacement. (NEO-13118)
* Correction d’un problème d’affichage d’image lors de l’utilisation de l’option **Définir l’image par taille** d’écran du périphérique sur les messages LINE. (NEO-13228)
* Correction d’un problème de préparation de remise lorsque l’option **Exclure l’adresse en double pendant la remise** était désélectionnée. (NEO-13240)
* Correction d’un problème dans les processus lors de l’utilisation de l’activité de transfert **de** fichier pour télécharger des fichiers à l’aide de l’option **Supprimer les fichiers source après le transfert** , avec un nom contenant un espace. (NEO-13411)
* Correction d’un problème de nettoyage du cache de Tomcat qui pouvait entraîner des problèmes de mémoire. (NEO-13456)
* Correction d’un problème lors de l’installation du **contrôle du moteur d’offre avec le package intégré d’instance** d’exécution sur une instance de contrôle existante s’exécutant dans Microsoft SQL 2017. (NEO-13539)
* Correction d’un blocage de la console qui pouvait se produire lors de la dévérification des URL suivies dans un courrier électronique, à partir de l’onglet Contenu **du** texte. (NEO-13545)
* Correction d’un problème de codage sur le nom de l’expéditeur chinois. (NEO-13837)
* Correction d&#39;une erreur qui pouvait se produire lors de l&#39;affichage des données de réponse à l&#39;enquête à partir de l&#39;Explorateur. (NEO-14590)
* Correction d’un problème susceptible d’entraîner une incohérence entre la classification du journal de livraison et la table de quarantaine. (NEO-16547)
* Correction d’un problème avec les clés DKIM qui n’étaient pas incorporées dans les courriers électroniques. (NEO-16804)
* Correction d’un problème qui affichait un code d’erreur incorrect lorsqu’un jeton de session non valide était utilisé dans le contexte d’appels d’API pour déclencher des événements. Le code d’erreur était &quot;HTTP 200 OK&quot; au lieu de &quot;HTTP 403 interdit&quot;. (NEO-16826)
* Correction d’un problème lors de l’affichage des rapports de remise via un accès Web. (NEO-17015)
* Correction d’un problème d’authentification IMS lors de la connexion à Adobe Campaign. (NEO-17312)
* Correction d’un problème qui empêchait la suppression des courriers électroniques mis en quarantaine par le processus Gestion de la confidentialité. (NEO-17314)
* Correction de problèmes de débit après la mise à niveau vers la version 9031 avec la base de données SQL. (NEO-17558)
* Correction d’un problème qui affectait CRM Connector avec Salesforce. (NEO-17712)
* Correction d’un problème de délai d’expiration lors de l’importation de données à partir d’un SFTP externe. (NEO-19723)
* Correction d’un problème lors de l’accès aux modèles prédictifs. (NEO-19713)
* Correction d’un problème affectant l’échantillonnage aléatoire dans l’activité de flux de travaux **fractionné** avec la base de données Hadoop FDA. (NEO-16636)

