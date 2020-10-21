---
title: Commencer avec les mises à niveau de la génération
description: Découvrez les étapes clés de la mise à niveau vers une nouvelle version
page-status-flag: never-activated
uuid: f24552d4-6bdf-411c-a1f2-b8f339c311f4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: f8e3633d-7232-44a5-842b-1a70c4f2bca2
translation-type: tm+mt
source-git-commit: 8ec525f400c29b986eadd888d29f1579860871c6
workflow-type: tm+mt
source-wordcount: '2366'
ht-degree: 47%

---


# Réalisation d’un upgrade de build{#performing-a-build-upgrade}

Cette section présente une présentation détaillée du processus de mise à niveau et des étapes à suivre pour identifier et résoudre les conflits.

La mise à niveau de la construction doit être effectuée avec prudence, ses impacts doivent être pleinement pris en considération au préalable et la procédure doit être menée à bien avec un niveau élevé de discipline. Pour garantir la réussite de la mise à niveau, veillez à ce que seuls les utilisateurs expérimentés exécutent les étapes décrites ci-dessous. En outre, nous vous recommandons vivement de contacter le service d’assistance [clientèle](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) Adobe avant de commencer la mise à niveau.

Les prérequis suivants doivent être remplis :

* maîtrise de l&#39;architecture de Campaign ;
* connaissances des systèmes et du côté serveur,
* permissions et droits administratifs.

Vous trouverez plus d’informations dans ces sections : [Mise à jour de Adobe Campaign](../../production/using/upgrading.md), [migration vers une nouvelle version](../../migration/using/about-migration.md).

For hosted and hybrid instances, you must request the build upgrade to Adobe Technical Operations team. For more on this, refer to the Frequently Asked Questions section at the bottom if this page. Also consult the [build upgrade FAQ](../../platform/using/faq-build-upgrade.md).

## Préparation de la mise à niveau

![](assets/do-not-localize/icon_planification.png)

Avant de commencer la mise à niveau de la build, vous devez effectuer une préparation complète comme décrit ci-dessous.
Une fois que le système est prêt à être mis à niveau, une mise à niveau de build prend **au moins** 2 heures.

L&#39;upgrade de build requiert les ressources suivantes :

* un architecte d&#39;Adobe - pour comprendre les structures de base de données (schémas prêts à l&#39;emploi et tout schéma supplémentaire ajouté, conceptions de campagne et toute fonctionnalité de chemin critique qui doit être lancée et testée dans un ordre spécifique).
* un responsable de projet : dans le cas où la mise à niveau de la build implique de nombreuses instances différentes (production, test, test) et d&#39;autres serveurs et applications tiers (bases de données, sites SFTP, prestataires de messagerie), il est préférable d&#39;avoir un responsable de projet pour coordonner tous les tests.
* Un administrateur Adobe Campaign : votre administrateur connaît la configuration du serveur, notamment : la sécurité, la disposition des dossiers, le reporting et les exigences en matière d&#39;import et d&#39;export. N&#39;effectuez pas d&#39;upgrade de build sans l&#39;aide de votre administrateur.
* un opérateur Adobe Campaign (utilisateur marketing) : une mise à niveau réussie dépend de la capacité de l’utilisateur à exécuter correctement ses tâches quotidiennes. Pour cette raison, incluez toujours au moins un de vos opérateurs quotidiens dans vos tests des serveurs mis à niveau.

### Planification

Voici les points essentiels pour planifier un upgrade de build :

1. Réservez au moins deux heures à l&#39;upgrade.
1. Communiquez les coordonnées de l&#39;équipe Adobe et du personnel du client.
1. Pour les instances hébergées : l&#39;équipe Adobe et le personnel du client coordonneront l&#39;heure et le responsable de l&#39;exécution de l&#39;upgrade.
1. Pour les instances on-premise : le personnel du client gère la totalité du processus. S&#39;il a besoin d&#39;aide pour les tests des workflows personnalisés et la logique des diffusions, il doit faire appel aux services de consulting.
1. Determine and confirm which version of Adobe Campaign you want to upgrade to - consult the [Adobe Campaign Classic release notes](../../rn/using/rn-overview.md).
1. Vérifiez que vous possédez les exécutables pour l&#39;upgrade.

### Personnes clés

Le processus de mise à niveau de la version nécessite l’implication des personnes suivantes :

* Adobe architecte : pour les architectures hébergées ou hybrides, l’architecte doit coordonner ses travaux avec le service à la clientèle Adobe Campaign.

* Chef de projet :
   * pour les installations sur site : le responsable de projet interne du client dirige la mise à niveau et gère les tests de cycle de vie.

   * pour l’installation hébergée : l’équipe d’hébergement collabore avec l’équipe d’assistance clientèle d’Adobe Campaign et le client pour coordonner le calendrier de mise à niveau pour toutes les instances.

* Administrateur Adobe Campaign :
   * pour les installations sur site : l’administrateur effectue la mise à niveau.

   * pour les installations hébergées : l’équipe d’hébergement effectue la mise à niveau.

* Opérateur Adobe Campaign\utilisateur marketing : l&#39;opérateur exécute des tests sur les instances de développement, de test et de production.

### Préparation de la mise à niveau vers la version

Avant de commencer la mise à niveau de la build, les clients sur site doivent effectuer la préparation suivante :

1. Vérifiez que tout travail de développement peut être exporté avant l&#39;upgrade. Exportez-le sous la forme de packages.

1. Effectuez une sauvegarde complète des bases de données pour toutes les instances des environnements source et cible.

1. Procurez-vous la dernière version du fichier [de configuration du](../../installation/using/the-server-configuration-file.md)serveur.

1. Téléchargez la dernière version. [En savoir plus sur le centre](https://docs.adobe.com/content/help/fr-FR/experience-cloud/software-distribution/home.html)de téléchargement.

You also need to know all the [useful command lines](../../installation/using/command-lines.md) before starting a build upgrade:

* **nlserver pdump** : répertorie les processus en cours d&#39;exécution.
* **nlserver pdump -who** : répertorie les sessions clientes actives.
* **nlserver monitor -missing** : répertorie les propriétés manquantes.
* **début nlserver process@instanceName**: début d’un processus
* **nlserver stop process@instanceName**: arrête un processus
* **redémarrage du serveur nlserver process@instanceName**: redémarre un processus
* **nlserver shutdown**: arrête tous les processus Campaign
* **nlserver watchdog -svc** : démarre le processus watchdog (UNIX uniquement).

## Effectuer la mise à niveau

![](assets/do-not-localize/icon_process.png)

Les procédures ci-dessous ne sont effectuées que par des clients **sur site** . Pour les clients hébergés, il est pris en charge par l’équipe d’hébergement. Pour mettre à jour Adobe Campaign vers une nouvelle version, la procédure détaillée est décrite ci-dessous.

### Duplicata de l&#39;environnement

Voici comment vous duplicata un environnement Adobe Campaign, afin de restaurer un environnement source à un environnement cible, ce qui donne deux environnements de travail identiques.

Pour ce faire, procédez comme suit :

1. Créer une copie des bases de données de toutes les instances de l&#39;environnement-source.

1. Restaurer ces copies sur toutes les instances de l&#39;environnement-cible.

1. Exécutez le script de cautérisation **nms:freezeInstance.js** sur l&#39;environnement-cible avant sa mise en route. Ceci arrête l’interaction de tous les processus avec l’extérieur : journaux, suivi, diffusions, workflows de campagne, etc.

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. Vérifier la mise en garde, comme suit :

   * Check that the only delivery part is the one which ID is set to **0**:

      ```
      SELECT * FROM neolane.nmsdeliverypart;
      ```

   * Vérifiez que la mise à jour des statuts des diffusions est correcte :

      ```
      SELECT iSate, count(*) FROM neolane.nmsdeliveryGroup By iProd;
      ```

   * Vérifiez que la mise à jour des statuts des workflows est correcte :

      ```
      SELECT iState, count (*) FROM neolane.xtkworkflowGROUP BY iState;
      SELECT iStatus, count (*) FROM neolane.xtkworkflowGROUP BY iStatus;
      ```

### Arrêter les services

Afin de pouvoir remplacer tous les fichiers par la nouvelle version, il est nécessaire d&#39;arrêter toutes les instances du service nlserverservice.

1. Arrêtez les services suivants :

   * services Web (IIS) : **iisreset /stop**
   * service Adobe Campaign : **net stop nlserver6**

   >[!NOTE]
   >
   >Assurez-vous que le serveur de redirection (webmdl) est arrêté, de sorte que le fichier nlsrvmod.dll utilisé par IIS puisse être remplacé par la nouvelle version.

1. Validate that no tasks are active by running the **nlserver pdump** command. If there are no tasks, then the output should resemble the following:

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. Vérifiez dans le Gestionnaire de Tâches Windows que tous les processus ont été arrêtés.

### Mise à niveau de l’application Adobe Campaign Server

1. Exécutez le fichier **Setup.exe** . Si vous devez télécharger ce fichier, accédez [au Centre](https://docs.adobe.com/content/help/fr-FR/experience-cloud/software-distribution/home.html)de téléchargement.

1. Select the installation mode: **Update** or **Repair**.

1. Cliquez sur **Suivant**.

1. Cliquez sur **Terminer** : le programme d&#39;installation copie alors les nouveaux fichiers.

1. Lorsque l&#39;opération est terminée, cliquez sur **Terminer**.

### synchroniser les ressources

1. Ouvrez la ligne de commande.

1. Exécutez la commande **nlserver config -postupgrade -allinstances** afin d&#39;effectuer les opérations suivantes :

   * synchroniser les ressources
   * mettre à jour les schémas,
   * mettre à jour la base de données.

   >[!NOTE]
   >
   >Cette opération ne doit être effectuée qu’une seule fois sur un serveur d’applications web nlserverweb.

   Pour synchroniser une seule base de données, exécutez la commande suivante :

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. Vérifiez si la synchronisation a généré des erreurs ou des avertissements.

### Redémarrer les services

Les services suivants doivent être redémarrés :

* services web (IIS) : **issreset /start**
* service Adobe Campaign : **net start nlserver6**

### Mise à jour des consoles client

Sur la machine sur laquelle est installé le serveur applicatif Adobe Campaign (nlserverweb), téléchargez puis copiez le fichier suivant :


    ```
    Setup-client-7.xxxx.exe dans [chemin de l&#39;application]\datakit\nl\en\jsp
    ```

Ainsi, à la prochaine connexion des postes clients, une fenêtre indiquera aux utilisateurs la disponibilité d&#39;une nouvelle mise à jour et leur proposera de la télécharger et de l&#39;installer.

### Tâches supplémentaires spécifiques

Certaines configurations nécessitent des tâches supplémentaires spécifiques pour la mise à jour vers une nouvelle version.

#### Messages transactionnels

Lorsque la messagerie transactionnelle (Centre de messages) est activée sur votre instance Campaign, vous devez effectuer les étapes supplémentaires suivantes pour effectuer la mise à niveau :

1. Mettez à jour le serveur de production Message Center vers la version choisie.
1. Exécutez le script de postupgrade.
1. Effectuez des tests et vérifiez que les emails sont bien reçus par le biais de l&#39;instance de production Message Center.
1. Mettez à niveau les clients et effacez le cache.
1. Exportez les packages :
   * Exportez les packages à l&#39;aide de l&#39;outil d&#39;export de package client
   * Importez le package de schémas
   * Déconnectez le client et reconnectez-le
   * Mettez à jour la base de données
   * Déconnectez-vous puis reconnectez-vous
   * Importez le package Admin
   * Importez le package Content
   * Importez le package Content Management
   * Déconnectez-vous puis reconnectez-vous
   * Réalisez un contrôle d&#39;intégrité rapide des workflows

1. Publiez les modèles de Message Center pour vous assurer que l&#39;interface entre les serveurs et l&#39;instance Message Center fonctionne.
1. Exécutez des tests pour vous assurer que les courriers électroniques sont correctement reçus par l’intermédiaire de l’instance de production Message Center.
1. Effectuez des tests de workflow en production pour vérifier que les diffusions sont bien reçues.

#### Mid-sourcing

Dans le cadre d’un environnement de midsourcing, vous devez effectuer les étapes supplémentaires suivantes pour effectuer la mise à niveau :

1. Contactez le service à la clientèle [de l’](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) Adobe pour coordonner la mise à niveau du serveur de Midsourcing.
1. Vérifiez que la version a été mise à jour en exécutant un lien de test. Par exemple :

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>Le serveur de Midsourcing doit toujours exécuter la même version (ou plus récente) que pour les serveurs marketing.


## En cas de conflit

### Identifier les conflits

Vous devez vérifier le résultat de la synchronisation. Cette procédure ne doit être suivie que par les clients on-premise. Pour les clients hébergés, elle est gérée par l&#39;équipe d&#39;hébergement. Le résultat de la synchronisation peut être consulté de deux manières différentes :

Dans l&#39;interface de ligne de commande, les erreurs sont matérialisées par un triple chevron &quot;&quot;>&quot; et la synchronisation est arrêtée automatiquement. Les avertissements sont matérialisés par un chevron doublon &quot;&quot;&quot; et doivent être résolus une fois la synchronisation terminée. A la fin de la mise à niveau, un résumé s’affiche dans l’invite de commande. Il peut ressembler à ceci :

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

Si l&#39;avertissement concerne un conflit de ressources, il requiert l&#39;intervention de l&#39;utilisateur pour être résolu.

The **postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** file contains the synchronization result. It is available by default in the following directory: **installationDirectory/var/instanceName/postupgrade**. Les erreurs et les avertissements sont indiqués par les attributs d’erreur et d’avertissement.

### Analyser les conflits

**Comment un conflit est-il détecté ?**

Les conflits se trouvent dans le fichier postupgrade.log sur le serveur en question ou dans l’interface client Campaign (Administration > Configuration > Gestion des packages > Modifier les conflits).

Le document ayant l&#39;identifiant ‘stockOverview’ et le type ‘nms:webApp’ est en conflit avec la nouvelle version.

Lorsqu&#39;un conflit est détecté, vérifiez si les conditions suivantes sont remplies :

* L&#39;objet a-t-il été modifié ou personnalisé par le client ?
* L&#39;objet a-t-il changé dans le produit ?

Si aucune de ces deux conditions n&#39;est applicable, il s&#39;agit d&#39;un faux positif. Si ces deux conditions sont applicables, un conflit réel a été détecté.

**L&#39;objet a-t-il été modifié par le client ?**

1. Identifiez l&#39;objet en conflit.
1. Demandez au client s&#39;il a modifié l&#39;objet.
1. L&#39;examen de l&#39;objet relève-t-il une anomalie ?
1. La date de dernière modification est-elle définie dans le code de l&#39;objet ?
1. Examinez le code XML depuis le conflit pour les attributs “_conflict”. Peut-il s&#39;agir d&#39;une personnalisation ?

**L&#39;objet a-t-il changé dans le nouveau build ?**

1. Existe-t-il des « suspects habituels » tels que des applications web ou des rapports intégrés (&#39;deliveryValidation&#39;, &#39;deliveryOverview&#39; ou &#39;budget&#39;, par exemple).
1. Recherchez des mises à jour dans les journaux des modifications.
1. Demandez à des experts Adobe Campaign.
1. Comparez les versions du code pour rechercher des différences avec la commande diff.

### Résoudre un conflit

Pour résoudre un conflit, procédez de la manière suivante :

1. Dans l&#39;explorateur d&#39;Adobe Campaign, accédez à **Administration > Paramétrage > Gestion des packages > Edition des conflits**.

1. Sélectionnez le conflit que vous souhaitez résoudre dans la liste.
Il existe trois options pour résoudre les conflits : **Acceptez la nouvelle version**, **Conservez la version** actuelle, **Fusionnez le code (et déclarez comme résolu)**, **Ignorez le conflit (non recommandé)**.

**Dans quels cas accepter la nouvelle version ?**

* Lorsque vous souhaitez utiliser les fonctionnalités standards.
* Lorsque vous ne disposez pas de personnalisations (toutes les personnalisations seront supprimées).

**Dans quels cas conserver la version actuelle ?**

* Lorsque vous disposez de personnalisations.
* Lorsque vous ne souhaitez pas effectuer de fusion.
* Lorsque vous n&#39;avez pas besoin de correctifs pour l&#39;objet en conflit depuis l&#39;upgrade.

**Dans quels cas effectuer une fusion ?**

* Seuls les formulaires, les rapports et les applications web peuvent être fusionnés.
* Certaines fusions mineures peuvent être réalisées sans maîtriser le code.
* Les fusions plus complexes doivent être réalisées par une personne qui dispose des compétences adéquates.
* Voir [Exécution d’une fusion](#perform-a-merge).

**Que se passe-t-il si vous ignorez les conflits ?**

* Le conflit existe toujours.
* L&#39;objet n&#39;est pas mis à niveau.
* Effets à long terme : incompatibilités de versions, client ne tirant pas parti des correctifs.

>[!CAUTION]
>Il est fortement recommandé de résoudre les conflits.


### Exécution d’une fusion{#perform-a-merge}

Il existe différents types de fusions :

1. Fusion facile : les éléments personnalisés et nouveaux sont petits et sans rapport, et aucun codage n’est requis.
1. Aucune modification : acceptation de la nouvelle version, seule la date de dernière mise à jour a été modifiée, seuls les commentaires, les onglets, les espaces et les nouvelles lignes ont été changés (enregistrement accidentel, par exemple).
1. Modifications négligeables : seule une ligne a été modifiée, par exemple xpathToLoad.
1. Fusion complexe : lorsque du code est requis. Des compétences en développement sont nécessaires. Voir Fusion [](#complex-merges)complexes.

#### Comment fusionner ?

1. Bénéficiez des trois versions : la version originale, la nouvelle version et la version personnalisée.
1. Exécutez un &quot;diff&quot; entre les versions d’origine et les nouvelles versions.
1. Isolez les modifications.
1. S&#39;il n&#39;existe aucune modification, résolvez le conflit en conservant la version actuelle.

#### Où trouver le code ?

1. Le code intégré est stocké dans des fichiers XML dans le dossier datakit. Recherchez le fichier XML correspondant à l’objet en conflit. Exemple : installationDirectory\datakit\nms\fra\form\recipient.xml
1. Récupérez la version d’origine : via le centre [de](https://docs.adobe.com/content/help/fr-FR/experience-cloud/software-distribution/home.html) téléchargement ou une autre installation non mise à niveau du produit.
1. Récupérez la nouvelle version : via le centre [de](https://docs.adobe.com/content/help/fr-FR/experience-cloud/software-distribution/home.html) téléchargement ou les fichiers installés par le client.
1. Récupérez la version personnalisée : récupérez le code source de l&#39;objet depuis le client Campaign.

### Comment créer une comparaison de fichiers

1. Installez un éditeur de texte ou de fusion tel que Notepad++, AraxisMerge ou WinMerge.
1. Ouvrez le fichier d&#39;origine et le nouveau fichier dans l&#39;éditeur.
1. Comparez les deux fichiers (recherchez les différences).
1. Identifiez les différences.

### Comment fusionner ?

1. Commencez à partir de la version personnalisée.
1. Appliquez les modifications.
1. Résolvez le conflit en le déclarant résolu.
1. Recherchez les non-régressions.

Si vous choisissez de résoudre le conflit manuellement, procédez comme suit :

1. In the lower section of the window, search for the **_conflict_string_** to locate the entities with conflicts. The entity installed with the new version contains the new argument, the entity that matches the previous version contains the custom argument.
1. Supprimez la version que vous ne souhaitez pas conserver. Effacez la chaîne **_conflict_argument_** de l’entité que vous gardez.
1. Positionnez-vous sur le conflit que vous venez de résoudre. Cliquez sur l&#39;icône **Actions** et sélectionnez **Déclarer comme résolu**.
1. Enregistrez vos modifications : le conflit est désormais résolu.

#### Fusions complexes{#complex-merges}

1. Comprendre ce que fait le changement : rétroconcevoir les modifications, examiner les journaux de modifications, assurer le suivi des experts Adobe Campaign.
1. Décidez quoi faire avec le changement.
1. Comprendre ce que font les personnalisations : ingénierie inverse des modifications

Voici la procédure pour effectuer une fusion complexe :

1. Copiez des blocs de code depuis l&#39;ensemble de modifications
1. Collez-les dans la version personnalisée
1. Test de non-régressions de la personnalisation
1. Vérifiez le fonctionnement des modifications
1. Tests d’acceptation des utilisateurs
1. Effectuez les tests dans un environnement de test.


>[!CAUTION]
>Des compétences en développement sont nécessaires pour effectuer des fusions complexes.


**Rubriques connexes :**

* [FAQ sur l’upgrade de build](../../platform/using/faq-build-upgrade.md)
* [Notes de mise à jour de Campaign Classic ](../../rn/using/rn-overview.md)
* [Options d’aide et de support pour les Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)
* [Programme Gold Standard](https://helpx.adobe.com/fr/campaign/kb/gold-standard.html)