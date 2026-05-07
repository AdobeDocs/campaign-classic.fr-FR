---
product: campaign
title: Prise en main des mises à niveau de build
description: Découvrez les étapes principales d’une mise à niveau vers un nouveau build
feature: Monitoring, Upgrade
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: c5a9c99a-4078-45d8-847b-6df9047a2fe2
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '2422'
ht-degree: 84%

---

# Réalisation d’une mise à niveau de build{#performing-a-build-upgrade}



Cette section présente la procédure détaillée pour réaliser une mise à niveau et les étapes nécessaires pour identifier et résoudre les conflits.

La mise à niveau de la build doit être effectuée avec précaution, ses impacts doivent être entièrement pris en compte au préalable et la procédure doit être menée à bien avec un haut niveau de discipline. Pour garantir une mise à niveau réussie, assurez-vous que seuls des utilisateurs experts effectuent les étapes décrites ci-dessous. De plus, il est vivement recommandé de contacter l’[Assistance clientèle d’Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) avant de commencer une mise à niveau.

Les prérequis suivants doivent être remplis :

* maîtrise de l&#39;architecture de Campaign ;
* connaissances des systèmes et du côté serveur,
* Autorisations et droits administratifs.

Vous trouverez plus d’informations dans ces sections : [Mise à jour d’Adobe Campaign](../../production/using/upgrading.md), [Migration vers une nouvelle version](../../migration/using/about-migration.md).

Pour les instances hybrides et hébergées, vous devez demander un upgrade de build à l&#39;équipe d&#39;exploitation technique Adobe. Pour plus d’informations, consultez la section Forum aux questions située au bas de cette page. Consultez également le [FAQ sur la mise à niveau des builds](../../platform/using/faq-build-upgrade.md).

## Préparer la mise à niveau

![](assets/do-not-localize/icon_planification.png)

Avant de commencer la mise à niveau de build, vous devez effectuer une préparation complète, comme décrit ci-après.
Une fois que le système prêt, une mise à niveau dure **au moins** 2 heures.

La mise à niveau de build requiert les ressources suivantes :

* Un architecte Adobe : pour comprendre les structures de base de données (schémas d&#39;usine et autres schémas ajoutés, conceptions de campagnes et fonctionnalités de chemin critique devant être démarrées et testées dans un ordre spécifique).
* Un chef de projet : dans le cas où la mise à niveau de build implique plusieurs instances différentes (production, intermédiaire, test) et d’autres serveurs et applications tiers (bases de données, sites SFTP, fournisseurs de services de messagerie), il est recommandé de faire appel à un chef de projet pour coordonner tous les tests.
* un administrateur Adobe Campaign : votre administrateur connaît la configuration du serveur, notamment : la sécurité, la disposition des dossiers, le compte rendu des performances et les exigences en matière d’import et d’export. N&#39;effectuez pas de mise à niveau de build sans l&#39;aide de votre administrateur.
* un opérateur ou une opératrice Adobe Campaign (utilisateur ou utilisatrice marketing) : la réussite d’une mise à niveau dépend de la capacité de l’utilisateur ou de l’utilisatrice à effectuer correctement ses tâches quotidiennes. Pour cette raison, incluez toujours au moins un de vos opérateurs quotidiens dans vos tests des serveurs mis à niveau.

### Planification

Voici les points essentiels pour planifier une mise à niveau de build :

1. Réservez au moins deux heures à la mise à niveau.
1. Communiquez les coordonnées de l&#39;équipe Adobe et du personnel du client.
1. Pour les instances hébergées : l’équipe Adobe et le personnel du client coordonneront l’heure et le responsable de l’exécution de la mise à niveau.
1. Pour les instances on-premise : le personnel du client gère la totalité du processus. S&#39;il a besoin d&#39;aide pour les tests des workflows personnalisés et la logique des diffusions, il doit faire appel aux services de consulting.
1. Déterminez et confirmez la version vers laquelle vous souhaitez mettre à niveau Adobe Campaign. Consultez les [notes de mise à jour d’Adobe Campaign Classic](../../rn/using/rn-overview.md)
1. Vérifiez que vous possédez les exécutables pour la mise à niveau.

### Acteurs clés

La mise à niveau de build requiert l’implication des personnes suivantes :

* Architecte Adobe : l’architecte doit se charger de la coordination avec l’assistance clientèle d’Adobe Campaign en cas d’architecture hébergée ou hybride.

* Chef de projet :
   * Pour les installations On Premise : le chef de projet interne du client dirige la mise à niveau et gère les tests de cycle de vie.

   * Pour les installations hébergées : l’équipe d’hébergement s’associera à l’équipe de l’Assistance clientèle Adobe Campaign et au client pour coordonner la chronologie de la mise à niveau pour toutes les instances.

* Administrateur Adobe Campaign :
   * Pour les installations On-Premise : l’équipe chargée de l’administration effectue la mise à niveau.

   * Pour les installations hébergées : l’équipe chargée de l’hébergement effectue la mise à niveau.

* Opérateur Adobe Campaign\utilisateur marketing : l&#39;opérateur effectue des tests sur les instances de développement, de test et de production.

### Préparer la mise à niveau de build

Avant de commencer la mise à niveau de build, les clients On-Premise doivent effectuer la préparation suivante :

1. Vérifiez que tout travail de développement peut être exporté avant la mise à niveau. Exportez-le sous la forme de packages.

1. Effectuez une sauvegarde complète des bases de données pour toutes les instances des environnements source et cible.

1. Obtenez la dernière version du [fichier de configuration du serveur](../../installation/using/the-server-configuration-file.md).

1. [Téléchargez le dernier build](https://experience.adobe.com/#/downloads/content/software-distribution/fr/campaign.html). [En savoir plus](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=fr).

Vous devez également connaître [toutes les lignes de commande utiles](../../installation/using/command-lines.md) avant de commencer une mise à niveau de build :

* **nlserver pdump** : répertorie les processus en cours d&#39;exécution.
* **nlserver pdump -who** : répertorie les sessions clientes actives.
* **nlserver monitor -missing** : répertorie les propriétés manquantes.
* **nlserver start process@instance-name** : démarre un processus.
* **nlserver stop process@instance-name** : arrête un processus.
* **nlserver restart process@instance-name** : redémarre un processus.
* **nlserver shutdown** : arrête tous les processus de Campaign.
* **nlserver watchdog -svc** : démarre le processus watchdog (UNIX uniquement).

## Réaliser la mise à niveau

![](assets/do-not-localize/icon_process.png)

Seuls les clients **On-Premise** doivent suivre ces procédures. Pour les clients hébergés, elles sont gérées par l&#39;équipe d&#39;hébergement. Pour mettre à jour Adobe Campaign vers un nouveau build, les étapes suivantes doivent être effectuées.

### Dupliquer l&#39;environnement

Cette section décrit comment dupliquer un environnement Adobe Campaign, afin de restaurer un environnement source dans un environnement cible, et ainsi disposer de deux environnements de travail identiques.

Pour ce faire, procédez comme suit :

1. Créez une copie des bases de données de toutes les instances de l&#39;environnement-source.

1. Restaurez ces copies sur toutes les instances de l&#39;environnement-cible.

1. Exécutez le script de cautérisation **nms:freezeInstance.js** sur l’environnement cible avant de le démarrer. (cela permettra l&#39;arrêt de tous les processus qui interagissent avec l&#39;extérieur : logs, tracking, diffusions, workflows de campagne, etc.).

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. Vérifiez la cautérisation, comme suit :

   * Vérifiez que le seul fragment de diffusion (deliverypart) est celui dont l&#39;ID est égal à **0** :

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

   * Services web (IIS) : **iisreset /stop**
   * service Adobe Campaign : **net stop nlserver6**

   >[!NOTE]
   >
   >Assurez-vous que le serveur de redirection (webmdl) est arrêté afin que le fichier nlsrvmod.dll, qui est utilisé par IIS, puisse être remplacé par la nouvelle version.
   >

1. Vérifiez qu’aucune tâche n’est active en exécutant la commande **nlserver pdump**. S’il n’existe aucune tâche, la sortie doit ressembler à ce qui suit :

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. Vérifiez le Gestionnaire de tâches de Windows afin de vous assurer que tous les processus sont arrêtés.

### Mettre à niveau l’application serveur Adobe Campaign

1. Exécutez le fichier **Setup.exe**. Si vous devez télécharger ce fichier, accédez [au Centre de téléchargement](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html).

1. Sélectionnez le mode d&#39;installation : **Mise à jour** ou **Réparation**.

1. Cliquez sur **Suivant**.

1. Cliquez sur **Terminer** : le programme d&#39;installation copie alors les nouveaux fichiers.

1. Lorsque l&#39;opération est terminée, cliquez sur **Terminer**.

### Synchroniser les ressources

1. Ouvrez la ligne de commande.

1. Exécutez la commande **nlserver config -postupgrade -allinstances** afin d&#39;effectuer les opérations suivantes :

   * synchroniser les ressources,
   * mettre à jour les schémas,
   * mettre à jour la base de données.

   >[!NOTE]
   >
   >Cette opération n&#39;est à effectuer qu&#39;une seule fois et uniquement sur un serveur applicatif nlserverweb.
   >

   Pour n&#39;effectuer la synchronisation que sur une seule base, utilisez la commande suivante :

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. Vérifiez si la synchronisation a généré des erreurs ou des avertissements.

### Redémarrer les services

Les services suivants doivent être redémarrés :

* services web (IIS) : **issreset /start**
* service Adobe Campaign : **net start nlserver6**

### Mise à jour des consoles clientes

La console cliente doit présenter le même build que l&#39;instance de serveur.

Sur la machine sur laquelle est installé le serveur applicatif Adobe Campaign (nlserverweb), téléchargez puis copiez le fichier suivant :

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

Ainsi, à la prochaine connexion des postes clients, une fenêtre indiquera aux utilisateurs la disponibilité d&#39;une nouvelle mise à jour et leur proposera de la télécharger et de l&#39;installer.

### Tâches supplémentaires spécifiques

Pour effectuer la mise à jour vers un nouveau build, certaines configurations impliquent des tâches supplémentaires spécifiques.

#### Messages transactionnels

Si les messages transactionnels (Message Center) sont activés sur votre instance Campaign, vous devez effectuer les étapes supplémentaires ci-après dans le cadre de la mise à niveau :

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
   * Importez le module de contenu
   * Importez le package de gestion de contenu
   * Déconnectez-vous puis reconnectez-vous
   * Réalisez un contrôle d&#39;intégrité rapide des workflows

1. Publiez les modèles de Message Center pour vous assurer que l&#39;interface entre les serveurs et l&#39;instance Message Center fonctionne.
1. Effectuez des tests pour vérifier que les emails sont bien reçus par le biais de l&#39;instance de production Message Center.
1. Effectuez des tests de workflow en production pour vérifier que les diffusions sont bien reçues.

#### Mid-sourcing

Dans le contexte d’un environnement de mid-sourcing, vous devez effectuer les étapes supplémentaires ci-après dans le cadre de la mise à niveau :

1. Contactez l’[Assistance clientèle d’Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) pour coordonner la mise à niveau du serveur de mid-sourcing.
1. Vérifiez que la version a été mise à jour en exécutant un lien de test, Par exemple :

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>Le serveur de mid-sourcing doit toujours exécuter la même version (ou une version plus récente) que les serveurs marketing.
>

## En cas de conflits

### Identifier les conflits

Vous devez vérifier le résultat de la synchronisation. Cette procédure est effectuée uniquement par les clients On-Premise. Pour les clients hébergés, elles sont gérées par l&#39;équipe d&#39;hébergement. Le résultat de la synchronisation peut être consulté de deux manières différentes :

Dans l&#39;interface de ligne de commande, les erreurs sont matérialisées par un triple chevron &#39;>>>&#39; et la synchronisation s&#39;arrête automatiquement. Les avertissements sont signalés par un double chevron « >> » et doivent être résolus une fois la synchronisation terminée. A la fin du postupgrade, un résumé est affiché dans l&#39;invite de commande. Par exemple :

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

Si l&#39;avertissement concerne un conflit de ressources, il requiert l&#39;intervention de l&#39;utilisateur pour être résolu.

Le fichier de **postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** contient le résultat de la synchronisation. Il est disponible par défaut dans le répertoire suivant : **installationDirectory/var/`<instance-name>`/postupgrade**. Les erreurs et les avertissements sont indiqués par les attributs d&#39;erreur et d&#39;avertissement.

### Analyser les conflits

**Comment un conflit est-il détecté ?**

Il est possible de détecter des conflits dans le fichier postupgrade.log situé sur le serveur en question ou dans l&#39;interface du client Campaign (Administration > Paramétrage > Gestion des packages > Edition des conflits).

Le document d&#39;identifiant &#39;stockOverview&#39; et de type &#39;nms:webApp&#39; est en conflit avec la nouvelle version.

Lorsqu&#39;un conflit est détecté, vérifiez si les conditions suivantes sont remplies :

* L&#39;objet a-t-il été modifié ou personnalisé par le client ?
* L&#39;objet a-t-il changé dans le produit ?

Si aucune de ces conditions ne s’applique, il s’agit d’un faux positif. Si ces deux conditions s&#39;appliquent, un véritable conflit a été constaté.

**L&#39;objet a-t-il été modifié par le client ?**

1. Identifiez l&#39;objet en conflit.
1. Demandez au client s&#39;il a modifié l&#39;objet.
1. L&#39;examen de l&#39;objet relève-t-il une anomalie ?
1. La date de dernière modification est-elle définie dans le code de l&#39;objet ?
1. Examinez le code XML du conflit pour trouver les attributs « _Conflict ». Ressemble-t-il à une personnalisation ?

**L&#39;objet a-t-il changé dans le nouveau build ?**

1. Des « suspects habituels ? » Applications Web ou rapports natifs (ex : &#39;deliveryValidation&#39;, &#39;deliveryOverview&#39;, &#39;budget&#39;).
1. Recherchez des mises à jour dans les logs des modifications.
1. Renseignez-vous auprès des utilisateurs experts d’Adobe Campaign.
1. Comparez les versions du code pour rechercher des différences avec la commande diff.

### Résoudre un conflit

Pour résoudre un conflit, procédez de la manière suivante :

1. Dans l&#39;explorateur d&#39;Adobe Campaign, accédez à **Administration > Paramétrage > Gestion des packages > Edition des conflits**.

1. Sélectionnez le conflit que vous souhaitez résoudre dans la liste.
Il existe trois façons de résoudre un conflit : **accepter la nouvelle version**, **conserver la version actuelle**, **fusionner le code (et déclarer le conflit comme résolu)**, **ignorer le conflit (non recommandé)**.

**Dans quels cas accepter la nouvelle version ?**

* Lorsque vous souhaitez utiliser les fonctionnalités standards.
* Lorsque vous ne disposez pas de personnalisations (toutes les personnalisations seront supprimées).

**Dans quels cas conserver la version actuelle ?**

* Lorsque vous disposez de personnalisations.
* Lorsque vous ne souhaitez pas effectuer de fusion.
* Lorsque vous n’avez pas besoin de correctifs pour l’objet en conflit depuis la mise à niveau.

**Dans quels cas effectuer une fusion ?**

* Seuls les formulaires, les rapports et les applications web peuvent être fusionnés.
* Certaines fusions mineures peuvent être réalisées sans maîtriser le code.
* Les fusions plus complexes doivent être réalisées par une personne qui dispose des compétences adéquates.
* Voir [Réaliser une fusion](#perform-a-merge).

**Que se passe-t-il si vous ignorez les conflits ?**

* Le conflit existe toujours.
* L’objet n’est pas mis à niveau.
* Effets à long terme : incompatibilités de versions, client ne tirant pas parti des correctifs.

>[!IMPORTANT]
>Il est vivement recommandé de résoudre les conflits.
>

### Réaliser une fusion{#perform-a-merge}

Il existe différents types de fusions :

1. Fusion simple : les éléments nouveaux et personnalisés sont petits et non liés, et aucun code n&#39;est nécessaire.
1. Aucune modification : acceptez la nouvelle version, seule la date de dernière mise à jour a été modifiée, seuls les commentaires, onglets, espaces ou nouvelles lignes ont été modifiés. Exemple : enregistrement accidentel.
1. Modifications mineures : une seule ligne a été modifiée. Exemple : xpathToLoad
1. Fusion complexe : lorsque le codage est requis. Des compétences de développement sont nécessaires. Voir [Fusion complexes](#complex-merges).

#### Comment fusionner ?

1. Procurez-vous les trois versions : la version d&#39;origine, la nouvelle version et la version personnalisée.
1. Comparez la nouvelle version à celle d&#39;origine pour rechercher les différences.
1. Isolez les modifications.
1. S&#39;il n&#39;existe aucune modification, résolvez le conflit en conservant la version actuelle.

#### Où trouver le code ?

1. Le code intégré est stocké dans des fichiers XML dans le dossier datakit. Recherchez le fichier XML qui correspond à l&#39;objet en conflit, par exemple : DossierInstallation\datakit\nms\fra\form\recipient.xml
1. Récupérez la version d’origine : via le [centre de téléchargement](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) ou une autre installation non mise à niveau du produit.
1. Récupérez la nouvelle version : via le [centre de téléchargement](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) ou les fichiers installés par le client.
1. Récupérez la version personnalisée : récupérez le code source de l&#39;objet depuis le client Campaign.

### Comment créer une comparaison de fichiers

1. Installez un éditeur de texte ou de fusion tel que Notepad++, AraxisMerge ou WinMerge.
1. Ouvrez le fichier d&#39;origine et le nouveau fichier dans l&#39;éditeur.
1. Comparez les deux fichiers (recherchez les différences).
1. Identifiez les différences.

### Comment fusionner ?

1. Commencez à partir de la version personnalisée.
1. Appliquez les modifications.
1. Résolvez le conflit en le déclarant comme résolu.
1. Effectuez un test de non-régression.

Si vous choisissez de résoudre le conflit manuellement, procédez comme suit :

1. Dans la section inférieure de la fenêtre, recherchez l’**_Conflict_string_** pour localiser les entités en conflit. L&#39;entité installée avec la nouvelle version contient le nouvel argument, l&#39;entité correspondant à la version précédente contient l&#39;argument personnalisé.
1. Supprimez la version que vous ne souhaitez pas conserver. Effacez la chaîne **_conflict_argument_** de l&#39;entité que vous gardez.
1. Positionnez-vous sur le conflit que vous venez de résoudre. Cliquez sur l&#39;icône **Actions** et sélectionnez **Déclarer comme résolu**.
1. Enregistrez vos modifications : le conflit est désormais résolu.

#### Fusions complexes{#complex-merges}

1. Comprendre l&#39;impact de la modification : effectuez une rétroconception des modifications, examinez les logs des modifications, renseignez-vous auprès des experts Adobe Campaign.
1. Décider de ce qu&#39;il faut faire de la modification.
1. Comprendre l&#39;impact des personnalisations : effectuez une rétroconception des modifications

Voici la procédure pour effectuer une fusion complexe :

1. Copiez des blocs de code depuis l&#39;ensemble de modifications
1. Collez-les dans la version personnalisée
1. Testez la non-régression de la personnalisation
1. Vérifiez le fonctionnement des modifications
1. Réalisez des tests d&#39;acceptation des utilisateurs
1. Effectuez les tests dans un environnement de test.


>[!IMPORTANT]
>Des compétences en développement sont nécessaires pour effectuer des fusions complexes.
>

**Rubriques connexes :**

* [FAQ sur la mise à niveau de build](../../platform/using/faq-build-upgrade.md)
* [Notes de mise à jour de Campaign Classic](../../rn/using/rn-overview.md)
* [Options d&#39;aide et de support pour Campaign Classic](../../support.md)
* [Programme de mise à niveau annuelle de Campaign](../../rn/using/rn-overview.md)
