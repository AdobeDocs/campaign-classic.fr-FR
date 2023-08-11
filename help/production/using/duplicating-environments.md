---
product: campaign
title: Duplication d'environnements
description: Duplication d'environnements
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
badge-v7-prem: label="On-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 2c933fc5-1c0a-4c2f-9ff2-90d09a79c55a
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '1321'
ht-degree: 100%

---

# Duplication d&#39;environnements{#duplicating-environments}



## Introduction {#introduction}

### Vue d&#39;ensemble {#overview}

>[!IMPORTANT]
>
>Si vous n&#39;avez pas accès au serveur et à la base de données (environnements hébergés), vous ne serez pas en mesure d&#39;effectuer les procédures décrites ci-dessous. Veuillez contacter Adobe.

L&#39;utilisation d&#39;Adobe Campaign requiert l&#39;installation et le paramétrage d&#39;un ou plusieurs environnements : développement, test, pré-production, recette, production, etc.

Chaque environnement contient une instance Adobe Campaign et chaque instance Adobe Campaign est liée à une ou plusieurs bases de données. Le serveur applicatif peut exécuter un ou plusieurs processus : la quasi totalité de ces processus accèdent directement à la base de données de l&#39;instance.

Cette section présente les procédures à appliquer pour dupliquer un environnement Adobe Campaign, c&#39;est-à-dire pour restaurer un environnement-source dans un environnement-cible, et ainsi disposer de deux environnements de travail identiques.

Pour cela, les étapes sont les suivantes :

1. Créer une copie des bases de données de toutes les instances de l&#39;environnement-source,
1. Restaurer ces copies sur toutes les instances de l&#39;environnement-cible,
1. Exécutez le script de cautérisation **nms:freezeInstance.js** sur l&#39;environnement-cible avant sa mise en route.

   Les serveurs et leur configuration ne sont pas impactés par cette procédure.

   >[!NOTE]
   >
   >Dans Adobe Campaign, une **cautérisation** regroupe les actions qui permettent l&#39;arrêt des processus qui interagissent avec l&#39;extérieur : logs, tracking, diffusions, workflows de campagnes, etc.\
   >Cette étape est nécessaire afin de ne pas diffuser des messages plusieurs fois (une fois depuis l&#39;environnement nominal, une fois depuis l&#39;environnement dupliqué).

   >[!IMPORTANT]
   >
   >Un environnement peut contenir plusieurs instances. Chaque instance Adobe Campaign est sujette à un contrat de licence. Le nombre d&#39;environnements autorisés est mentionné dans votre contrat de licence.\
   >La procédure proposée ci-après vous permet de transférer un environnement sans pour autant impacter le nombre d&#39;environnements et d&#39;instances installées.

### Avant de commencer {#before-you-start}

>[!IMPORTANT]
>
>Il est vivement recommandé de réaliser des sauvegardes complètes des bases de données de toutes les instances des environnements-source et cible avant toute manipulation. En cas de problème, vous pourrez ainsi restaurer ces sauvegardes et retrouver la configuration initiale.

Afin de mettre en oeuvre la procédure décrite ci-dessous, l&#39;environnement-source et l&#39;environnement-cible doivent disposer du même nombre d&#39;instances. Elles doivent avoir la même finalité (instance marketing, de diffusions) et une configuration similaire. La configuration technique doit correspondre aux pré-requis logiciels. Les mêmes composants doivent être installés dans les deux environnements.

## Mise en œuvre {#implementation}

### Procédure de transfert {#transfer-procedure}

Nous vous proposons ici de comprendre les étapes de transfert d&#39;un environnement-source vers un environnement-cible à travers un cas pratique : l&#39;objectif est de restaurer un environnement de production (instance **prod**) dans un environnement de développement (instance **recette**) afin de travailler dans un contexte qui soit le plus proche possible de la plateforme &#39;live&#39;.

Les étapes ci-dessous doivent être réalisées avec précaution : certains processus peuvent être en cours lors de la copie des bases de données de l&#39;environnement-source. La procédure de cautérisation (Etape 3 ci-après) permet de ne pas diffuser les messages plusieurs fois aux mêmes destinataires et de conserver la cohérence des données.

>[!IMPORTANT]
>
>* La procédure ci-dessous est valide en langage PostgreSQL, si le langage SQL est différent (Oracle, par exemple), les requêtes SQL doivent être adaptées.
>* Dans les exemples de commandes proposés ci-après, on considère une instance **prod** et une instance **recette** existantes sous PostgreSQL.
>

### Etape 1 - Sauvegarder les données de l&#39;environnement-source (prod) {#step-1---make-a-backup-of-the-source-environment--prod--data}

Copier les bases de données

Vous devez au préalable copier toutes les bases de données de l&#39;environnement-source. Le mode de réalisation de cette opération dépend du moteur de la base de données et est sous la responsabilité de l&#39;administrateur des bases de données.

Sous PostgreSQL, la commande est la suivante :

```
pg_dump mydatabase > mydatabase.sql
```

### Etape 2 - Exporter la configuration de l&#39;environnement cible (recette) {#step-2---export-the-target-environment-configuration--dev-}

La plupart des éléments de configuration diffèrent d&#39;un environnement à l&#39;autre : comptes externes (mid-sourcing, routing, etc.), options techniques (nom de la plateforme, DatabaseId, adresses email et URL par défaut, etc.).

Avant de restaurer la base source sur la base cible, vous devez exporter la configuration de l&#39;environnement cible (recette). Vous devez exporter le contenu des deux tables suivantes : **xtk:option** et **nms:extaccount**.

Cet export permet de conserver la configuration de la recette et de ne rafraîchir que les données de la recette (workflows, modèles, applications Web, detinataires, etc.).

Pour cela, effectuez un export de package pour les deux éléments suivants :

* Dans un fichier &#39;options_recette.xml&#39;, exporter la table **xtk:option**, sans les enregistrements avec les noms internes suivants : &#39;WdbcTimeZone&#39;, &#39;NmsServer_LastPostUpgrade&#39; et &#39;NmsBroadcast_RegexRules&#39;.
* Dans un fichier &#39;extaccount_recette.xml&#39;, exporter la table **nms:extAccount** pour tous les enregistrements dont l&#39;ID est différent de 0 (@id &lt;> 0).

Vérifiez dans chaque fichier que le nombre d&#39;options/de comptes exportés est égal au nombre de lignes à exporter.

>[!NOTE]
>
>Le nombre de lignes à exporter dans un export de package est de 1000 lignes. Si le nombre d&#39;options ou de comptes externes est supérieur à 1000, il faut procéder à plusieurs exports.
> 
>Pour plus d’informations, consultez [cette section](../../platform/using/working-with-data-packages.md#exporting-packages).

>[!NOTE]
>
>Lors de l’export de la table nmsextaccount, les mots de passe associés aux comptes externes (par exemple les mots de passe pour Mid-sourcing, Message Center, SMPP, IMS et d’autres comptes externes) ne sont pas exportés. Assurez-vous d’avoir préalablement accès aux mots de passe corrects, car ils devront peut-être être entrés de nouveau une fois les comptes externes réimportés dans l’environnement.

### Etape 3 - Arrêter l&#39;environnement cible (recette) {#step-3---stop-the-target-environment--dev-}

Vous devez arrêter les processus Adobe Campaign sur tous les serveurs de l&#39;environnement-cible. Le mode de réalisation de cette opération dépend de votre système d&#39;exploitation.

Vous pouvez arrêter tous les processus ou seulement ceux qui écrivent dans la base de données.

Pour arrêter tous les processus, les commandes sont les suivantes :

* Sous Windows :

  ```
  net stop nlserver6
  ```

* Sous Linux :

  ```
  /etc/init.d/nlserver6 stop
  ```

Vérifiez que tous les processus sont bien arrêtés via la commande suivante :

```
nlserver pdump
```

>[!NOTE]
>
>Sous Windows, le processus **webmdl** peut être encore actif sans impacter le reste des opérations.

Vous pouvez également vérifier qu&#39;aucun processus système ne subsiste.

Pour cela :

* Sous Windows : ouvrez le **Gestionnaire des tâches** et vérifiez l’absence de tout processus **nlserver.exe**.
* Sous Linux : exécutez la commande **ps aux | grep nlserver** et vérifiez l’absence de tout processus **nlserver**.

### Etape 4 - Restaurer les bases de données dans l&#39;environnement-cible (recette) {#step-4---restore-the-databases-in-the-target-environment--dev-}

Pour restaurer les bases de données-sources dans l&#39;environnement-cible, la commande est la suivante :

```
psql mydatabase < mydatabase.sql
```

### Etape 5 - Cautériser l&#39;environnement-cible (recette) {#step-5---cauterize-the-target-environment--dev-}

Afin d&#39;éviter tout dysfonctionnement, les processus relatifs à l&#39;envoi des diffusions et à l&#39;exécution des workflows ne doivent pas s&#39;exécuter automatiquement au moment de l&#39;activation de l&#39;environnement-cible.

Pour cela, exécutez la commande suivante :

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### Etape 6 - Vérifier la cautérisation {#step-6---check-cauterization}

1. Vérifier que le seul deliverypart est celui dont l&#39;ID est égal à 0 :

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. Vérifiez que la mise à jour des statuts des diffusions est correcte :

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. Vérifiez que la mise à jour des statuts des workflows est correcte :

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### Etape 7 - Redémarrer le processus Web de l&#39;environnement-cible (recette) {#step-7---restart-the-target-environment-web-process--dev-}

Sur l&#39;environnement-cible, redémarrez les processus Adobe Campaign sur tous les serveurs.

>[!NOTE]
>
>Avant de redémarrer Adobe Campaign sur l&#39;environnement **recette**, il est possible d&#39;appliquer une procédure de sécurité supplémentaire : ne démarrer que le module **web**.
>  
>Pour cela, éditez le fichier configuration de votre instance (**config-dev.xml**), puis ajoutez le caractère « _ » devant les options autoStart=&quot;true&quot; pour chaque module (mta, stat, etc.).

Exécuter la commande suivant afin de démarrer le processus web :

```
nlserver start web
```

Vérifier que seul le processus web est démarré à l&#39;aide de la commande suivante :

```
nlserver pdump
```

Vérifer visuellement que l&#39;accès à la console client fonctionne.

### Etape 8 - Importer les options et les comptes externes dans l&#39;environnement-cible (recette) {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>Seul le processus web doit être lancé à cette étape. Dans le cas contraire, arrêtez les autres processus en cours d’exécution avant de continuer.

Vérifier avant toutes choses les valeurs de plusieurs lignes des fichiers avant l&#39;import (par exemple : &#39;NmsTracking_Pointer&#39; pour la table des options et les comptes d&#39;envoi ou de mid-sourcing pour la table des comptes externes).

Pour importer la configuration de la base de données de l&#39;environnement-cible (recette) :

1. Ouvrir la console d&#39;administration de la base de données et purger les comptes externes (table nms:extAccount) dont l&#39;ID est différent de 0 (@id &lt;> 0).
1. Au niveau de la console Adobe Campaign, importer le package options_recette.xml précédemment créé via la fonctionnalité d&#39;import de package.

   Vérifier que les options ont bien été mises à jour dans le noeud **[!UICONTROL Administration > Plateforme > Options]**.

1. Au niveau de la console Adobe Campaign, importer le package extaccount_recette.xml précédemment créé via la fonctionnalité d&#39;import de package.

   Vérifier que les comptes externes ont bien été importés dans le noeud **[!UICONTROL Administration > Plateforme > Comptes externes]** .

### Etape 9 - Redémarrer l&#39;ensemble des processus et changer les utilisateurs (recette) {#step-9---restart-all-processes-and-change-users--dev-}

Pour démarrer les processus Adobe Campaign, les commandes sont les suivantes :

* Sous Windows :

  ```
  net start nlserver6
  ```

* Sous Linux :

  ```
  /etc/init.d/nlserver6 start
  ```

Vérifier que les processus sont bien démarrés via la commande suivante :

```
nlserver pdump
```

Changer les utilisateurs pour retrouver les utilisateurs qui existaient auparavant sur la plateforme de recette.
