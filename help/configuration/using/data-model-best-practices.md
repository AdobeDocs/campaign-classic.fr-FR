---
title: Utilisation du tableau Destinataire d’Adobe Campaign Classic
description: Découvrez comment utiliser le tableau de destinataires prêt à l’emploi dans Adobe Campaign Classic lors de la conception de votre modèle de données.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ad3aedeb18cfce809f959ccb62cb27928877c9d2

---


# Meilleures pratiques du modèle de données{#data-model-best-practices}

Ce document présente les principales recommandations lors de la conception de votre modèle de données Adobe Campaign.

Pour une meilleure compréhension des tableaux intégrés aux campagnes et de leur interaction, consultez la section Modèle [de données](../../configuration/using/about-data-model.md) Campaign Classic.

Lisez cette [documentation](../../configuration/using/about-schema-reference.md) pour commencer à utiliser les schémas de campagne. Découvrez comment configurer des schémas d’extension afin d’étendre le modèle de données conceptuel de la base de données Adobe Campaign dans ce [document](../../configuration/using/about-schema-edition.md).

## Présentation {#overview}

Le système Adobe Campaign est extrêmement flexible et peut être étendu au-delà de l’implémentation initiale. Cependant, même si les possibilités sont infinies, il est essentiel de prendre des décisions judicieuses et de construire des bases solides pour commencer à concevoir votre modèle de données.

Ce document présente les cas d’utilisation courants et les bonnes pratiques pour apprendre à concevoir correctement votre outil Adobe Campaign.

## Architecture du modèle de données {#data-model-architecture}

Adobe Campaign Standard est un puissant système de gestion de campagne cross-canal qui peut vous aider à aligner vos stratégies en ligne et hors ligne pour créer des expériences client personnalisées.

### Approche axée sur le client {#customer-centric-approach}

Bien que la plupart des fournisseurs de services de messagerie communiquent avec les clients par le biais d’une approche centrée sur la liste, Adobe Campaign s’appuie sur une base de données relationnelle afin de tirer parti d’une vision plus large des clients et de leurs attributs.

Cette approche axée sur le client est présentée dans le graphique ci-dessous. La table **Destinataire** en gris représente la table client principale autour de laquelle tout est construit :

![](assets/customer-centric-data-model.png)

Pour accéder à la description de chaque tableau, accédez à **[!UICONTROL Admin > Configuration > Data schemas]**, sélectionnez une ressource dans la liste et cliquez sur l’ **[!UICONTROL Documentation]** onglet.

Le modèle de données par défaut d’Adobe Campaign est présenté dans ce [document](https://final-docs.campaign.adobe.com/doc/AC/en/technicalResources/_Datamodel_Description_of_the_main_tables.html).

>[!NOTE]
>
>Adobe Campaign Classic permet de créer un tableau client personnalisé. Cependant, dans la plupart des cas, il est recommandé de tirer parti de la table [de](../../configuration/using/default-recipient-table.md) destinataires standard qui comporte déjà des tables et des fonctionnalités supplémentaires préconçues.

### Données pour Adobe Campaign {#data-for-campaign}

Quelles données doivent être envoyées à Adobe Campaign ? Il est essentiel de déterminer les données requises pour vos activités marketing.

>[!NOTE]
>
>Adobe Campaign n’est ni un entrepôt de données, ni un outil de création de rapports. Par conséquent, n’essayez pas d’importer tous les clients possibles et leurs informations associées dans Adobe Campaign, ni d’importer des données qui ne seront utilisées que pour créer des rapports.

Pour décider si un attribut est nécessaire ou non dans Adobe Campaign, demandez-vous s’il relève de l’une des catégories suivantes :

* Attribut utilisé pour la **segmentation**
* Attribut utilisé pour les processus **de gestion des** données (calcul agrégé, par exemple)
* Attribut utilisé pour la **personnalisation**

Si vous ne tombez dans aucune de ces catégories, il est probable que vous n’ayez pas besoin de cet attribut dans Adobe Campaign.

### Choix des types de données {#data-types}

Pour garantir une architecture et des performances optimales de votre système, suivez les bonnes pratiques ci-dessous pour configurer les données dans Adobe Campaign.

* Un tableau volumineux doit comporter principalement des champs numériques et des liens vers des tableaux de référence (lorsque vous travaillez avec une liste de valeurs).
* L’attribut **expr** permet de définir un attribut de schéma sous la forme d’un champ calculé plutôt que d’une valeur d’ensemble physique dans une table. Cela peut permettre d’accéder aux informations dans un format différent (par exemple, pour l’âge et la date de naissance) sans avoir à stocker les deux valeurs. Il s’agit d’un bon moyen d’éviter la duplication des champs. Par exemple, la table Destinataire utilise une expression pour le domaine, qui est déjà présente dans le champ Courriel.
* Toutefois, lorsque le calcul de l’expression est complexe, il n’est pas recommandé d’utiliser l’attribut **expr** car le calcul à la volée peut avoir un impact sur les performances de vos requêtes.
* Le type **XML** est un bon moyen d’éviter de créer trop de champs. Mais il prend aussi de l&#39;espace disque car il utilise une colonne CLOB dans la base de données. Cela peut également conduire à des requêtes SQL complexes et avoir un impact sur les performances.
* La longueur d’un champ de **chaîne** doit toujours être définie avec la colonne. Par défaut, la longueur maximale dans Adobe Campaign est de 255, mais Adobe conseille de raccourcir le champ si vous savez déjà que la taille ne dépassera pas une longueur plus courte.
* Dans Adobe Campaign, un champ plus court est acceptable que dans le système source si vous êtes certain que la taille du système source a été surestimée et n’aurait pas été atteinte. Cela peut signifier une chaîne plus courte ou un entier plus petit dans Adobe Campaign.

### Choix des champs {#choice-of-fields}

Un champ doit être stocké dans un tableau s’il a un objectif de ciblage ou de personnalisation. En d’autres termes, si un champ n’est pas utilisé pour envoyer un courriel personnalisé ou comme critère dans une requête, il prend de l’espace disque alors qu’il est inutile.

Pour les instances hybrides et sur site, la FDA (Federated Data Access, fonctionnalité facultative permettant d’accéder aux données externes) répond à la nécessité d’ajouter un champ &quot;à la volée&quot; lors d’un processus de campagne. Vous n&#39;avez pas besoin de tout importer si vous avez la FDA. Pour plus d’informations, voir [A propos de l’accès](../../platform/using/about-fda.md)aux données fédérées.

### Choix des clés {#choice-of-keys}

Outre le code **automatique** défini par défaut dans la plupart des tableaux, vous devez envisager d’ajouter des clés logiques ou professionnelles (numéro de compte, numéro de client, etc.). Il peut être utilisé ultérieurement pour les importations/rapprochement ou les packages de données. For more on this, see [Identifiers](#identifiers).

Des clés efficaces sont essentielles à la performance. Les types de données numériques doivent toujours être préférés comme clés pour les tableaux.

Pour la base de données SQLServer, vous pouvez envisager d’utiliser &quot;index en grappe&quot; si des performances sont requises. Comme Adobe ne gère pas cette tâche, vous devez la créer dans SQL.

### Espaces de disque logiques dédiés {#dedicated-tablespaces}

L’attribut tablespace du schéma vous permet de spécifier un espace disque logique dédié pour une table.

L’assistant d’installation vous permet de stocker des objets par type (données, temporaires et index).

Les espaces disque logiques dédiés sont meilleurs pour le partitionnement, les règles de sécurité et permettent une administration fluide et flexible, une optimisation et des performances optimales.

## Identificateurs {#identifiers}

Les ressources Adobe Campaign comportent trois identifiants et il est possible d’ajouter un identifiant supplémentaire.

Le tableau suivant décrit ces identifiants et leur objectif.

| Identifiant | Description | Bonnes pratiques |
|--- |--- |--- |
| Id | <ul><li>L’ID est la clé primaire physique d’une table Adobe Campaign. Pour les tableaux prêts à l’emploi, il s’agit d’un nombre 32 bits généré à partir d’une séquence.</li><li>Cet identifiant est généralement propre à une instance Adobe Campaign spécifique. </li><li>Un ID généré automatiquement peut être visible dans une définition de schéma. Recherchez l’attribut *autopk=&quot;true&quot;* .</li></ul> | <ul><li>Les identifiants générés automatiquement ne doivent pas être utilisés comme référence dans un processus ou dans une définition de package.</li><li>Il ne faut pas présumer que l’identifiant sera toujours un nombre croissant.</li><li>L’ID d’un tableau prêt à l’emploi est un nombre 32 bits et ce type ne doit pas être modifié. Ce numéro provient d’une &quot;séquence&quot; couverte dans la section portant le même nom.</li></ul> |
| Nom (ou nom interne) | <ul><li>Ces informations sont un identifiant unique d’un enregistrement dans un tableau. Cette valeur peut être mise à jour manuellement, généralement avec un nom généré.</li><li>Cet identifiant conserve sa valeur lorsqu’il est déployé dans une autre instance d’Adobe Campaign et ne doit pas être vide.</li></ul> | <ul><li>Renommez le nom d’enregistrement généré par Adobe Campaign si l’objet doit être déployé d’un environnement à un autre.</li><li>Lorsqu’un objet possède un attribut d’espace de noms (*schéma* , par exemple), cet espace de noms commun est exploité sur tous les objets personnalisés créés. Certains espaces de noms réservés ne doivent pas être utilisés : *nms*, *xtk*.</li><li>Lorsqu’un objet n’a pas d’espace de noms (*flux de travail* ou *diffusion* , par exemple), cette notion d’espace de noms est ajoutée comme préfixe d’un objet de nom interne : *namespaceMyObjectName*.</li><li>N’utilisez pas de caractères spéciaux tels que l’espace &quot;&quot;, la demi-colonne &quot;:&quot; ou le tiret &quot;-&quot;. Tous ces caractères seraient remplacés par un trait de soulignement &quot;_&quot; (caractère autorisé). Par exemple, &quot;abc-def&quot; et &quot;abc:def&quot; sont stockés en tant que &quot;abc_def&quot; et remplacent les uns des autres.</li></ul> |
| Libellé | <ul><li>Le libellé est l’identifiant de l’entreprise d’un objet ou d’un enregistrement dans Adobe Campaign.</li><li>Cet objet autorise des espaces et des caractères spéciaux.</li><li>Il ne garantit pas le caractère unique d&#39;un enregistrement.</li></ul> | <ul><li>Il est recommandé de déterminer une structure pour les libellés de vos objets.</li><li>Il s’agit de la solution la plus conviviale pour identifier un enregistrement ou un objet pour un utilisateur d’Adobe Campaign.</li></ul> |

## Clés internes personnalisées {#custom-internal-keys}

Les clés principales sont requises pour chaque table créée dans Adobe Campaign.

La plupart des organisations importent des enregistrements à partir de systèmes externes. Bien que la clé physique de la table Destinataire soit l’attribut &quot;id&quot;, il est possible de déterminer une clé personnalisée en outre.

Cette clé personnalisée est la clé primaire d’enregistrement réelle dans le système externe alimentant Adobe Campaign.

Lorsqu’une table prête à l’emploi comporte à la fois une clé automatique et une clé interne, la clé interne est définie comme index unique dans la table de base de données physique.

Lorsque vous créez un tableau personnalisé, vous disposez de deux options :
* Combinaison de clé générée automatiquement (id) et de clé interne (personnalisée). Cette option est intéressante si votre clé système est une clé composite ou non un entier. Les entiers offriront des performances plus élevées dans les grandes tables et se joindront aux autres tables.
* Utilisation de la clé primaire comme clé primaire du système externe. Cette solution est généralement préférable, car elle simplifie l’approche d’importation et d’exportation des données, avec une clé cohérente entre les différents systèmes. La fonction Autopk doit être désactivée si la clé est nommée &quot;id&quot; et qu’elle doit être remplie avec des valeurs externes (et non pas avec une génération automatique).

>[!IMPORTANT]
>
>Un autopk ne doit pas être utilisé comme référence dans les processus.

## Séquences {#sequences}

La clé primaire Adobe Campaign est un identifiant généré automatiquement pour toutes les tables prêtes à l’emploi et peut être identique pour les tables personnalisées. Voir à ce propos [cette section](#identifiers).

Cette valeur provient de ce qu’on appelle une **séquence**, qui est un objet de base de données utilisé pour générer une séquence de nombres.

Il existe deux types de séquences :
* **Partagé**: plusieurs tables choisiraient leur id dans la même séquence. Cela signifie que si un id &#39;X&#39; est utilisé par une table, aucune autre table partageant la même séquence n&#39;aurait d&#39;enregistrement avec cet id &#39;X&#39;. **XtkNewId** est la séquence partagée par défaut disponible dans Adobe Campaign.
* **Dédié**: une seule table sélectionne ses identifiants dans la séquence. Le nom de la séquence contient généralement le nom de la table.

La séquence est un nombre entier de valeurs 32 bits, avec un nombre maximal fini de valeurs disponibles : 2,14 milliards. Après avoir atteint la valeur maximale, la séquence revient à 0 afin de recycler les identifiants. Si les anciennes données n’ont pas été purgées, le résultat sera une violation de clé unique, qui deviendra un bloqueur pour l’intégrité et l’utilisation de la plateforme. Adobe Campaign ne serait pas en mesure d’envoyer des communications (lorsqu’elle a un impact sur la table du journal de distribution) et les performances seraient fortement affectées.

Par conséquent, un client envoyant 6 milliards de courriels par an avec une période de rétention de 180 jours pour ses journaux serait à court d&#39;identifiants en 4 mois. Pour éviter un tel problème, veillez à avoir des paramètres de purge en fonction de vos volumes. Voir à ce propos [cette section](#data-retention).

Lorsqu’une table personnalisée est en cours de création dans Adobe Campaign avec une clé primaire comme autoPK, une séquence personnalisée dédiée doit être systématiquement associée à cette table.

Par défaut, une séquence personnalisée aura des valeurs allant de +1 000 à +2,1 BB. Techniquement, il est possible d&#39;obtenir une gamme complète de 4BB en activant des identifiants négatifs. Cette valeur doit être utilisée avec soin et un id sera perdu lors du passage d’un nombre négatif à un nombre positif : l’enregistrement 0 est généralement ignoré par Adobe Campaign Classic dans les requêtes SQL générées.

**Rubriques connexes :**
* Pour plus d’informations sur la fonction de génération **automatique de** séquence, reportez-vous à ce [document](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html).
* Pour en savoir plus sur l&#39;épuisement des séquences, regardez cette [vidéo](https://helpx.adobe.com/customer-care-office-hours/campaign/sequences-exhaustion-campaign-classic.html).

## des index ;{#indexes}

Les index sont essentiels aux performances. Lorsque vous déclarez une clé dans le schéma, Adobe crée automatiquement un index sur les champs de la clé. Vous pouvez également déclarer d’autres index pour les requêtes qui n’utilisent pas la clé.

Adobe recommande de définir des index supplémentaires, car ils peuvent améliorer les performances.

Gardez toutefois à l’esprit les points suivants :

* L’utilisation de l’index est liée à votre modèle d’accès. L&#39;optimisation de l&#39;indexation est souvent un élément clé de la conception des bases de données et doit être géré par des experts. L&#39;ajout d&#39;index est souvent un processus itératif lié à la maintenance de la base de données. Il est effectué au fil du temps, étape par étape, pour résoudre les problèmes de performance lorsqu’ils surviennent.
* Les index augmentent la taille globale du tableau (pour stocker l’index lui-même).
* L’ajout d’un index sur des colonnes peut améliorer les performances de l’accès en lecture aux données (SELECT), mais peut réduire les performances de l’accès en écriture aux données (UPDATE).
* Comme cela a une incidence sur les performances lors de l’insertion de données, les index doivent être limités en taille et en nombre.
* N’ajoutez pas d’index lorsque cela n’est pas nécessaire. Assurez-vous qu’il est nécessaire et qu’il augmente les performances globales de vos requêtes (test et apprentissage).
* En général, un index est efficace si vous savez que vos requêtes ne rapporteront pas plus de 10 % des enregistrements.
* Sélectionnez soigneusement les index à définir.
* Ne supprimez pas les index natifs des tables prêtes à l’emploi.

<!--When you are performing an initial import with very high volumes of data insert in Adobe Campaign database, it is recommended to run that import without custom indexes at first. It will allow to accelerate the insertion process. Once you’ve completed this important import, it is possible to enable the index(es).-->

## Liens et cardinalité {#links-and-cardinality}

### Liens {#links}

Attention à la &quot;propre&quot; intégrité sur les grandes tables. La suppression d’enregistrements dont l’intégrité est propre à des tables larges peut arrêter l’instance. La table est verrouillée et les suppressions sont faites une par une. Il est donc préférable d&#39;utiliser une intégrité &quot;neutre&quot; sur les tables enfants qui ont de gros volumes.

La déclaration d’un lien en tant que jointure externe n’est pas une bonne chose pour les performances. L’enregistrement d’ID zéro émule la fonctionnalité de jointure externe. Il n’est pas nécessaire de déclarer des jointures externes si le lien utilise le lien automatique.

Bien qu’il soit possible de joindre n’importe quel tableau dans un processus, Adobe recommande de définir des liens communs entre les ressources directement dans la définition de la structure de données.

Le lien doit être défini en fonction des données réelles contenues dans les tableaux. Une mauvaise définition peut avoir un impact sur les données récupérées via des liens, par exemple la duplication inattendue d’enregistrements.

Nommez votre lien de manière cohérente avec le nom de la table : le nom du lien doit aider à comprendre ce qu&#39;est la table distante.

Ne donnez pas le nom d’un lien avec &quot;id&quot; comme suffixe. Par exemple, nommez-le &quot;transaction&quot; plutôt que &quot;transactionId&quot;.

Par défaut, Adobe Campaign crée un lien à l’aide de la clé primaire de la table externe. Pour plus de clarté, il est préférable de définir explicitement la jointure dans la définition du lien.

Un index sera ajouté aux attributs utilisés dans un lien.

Les liens créés par et modifiés en dernier sont présents dans de nombreux tableaux. Il est possible de désactiver l&#39;index en utilisant l&#39;attribut noDbIndex sur le lien, si ces informations ne sont pas utilisées par l&#39;entreprise.

### Cardinalité {#cardinality}

Lorsque vous concevez un lien, assurez-vous que l’enregistrement cible est unique lorsqu’une relation 1-1 a été déclarée. Sinon, la jointure peut renvoyer plusieurs enregistrements alors qu’un seul est attendu. Cela entraîne des erreurs lors de la préparation de la remise lorsque &quot;la requête renvoie plus de lignes que prévu&quot;. Définissez le nom du lien sur le même nom que le schéma cible.

Définissez un lien avec une cardinalité (1-N) dans le schéma du côté (1). Par exemple, la relation Destinataire (1) - (N) Transaction doit être définie dans le schéma de transaction.

Notez qu’une cardinalité inversée d’un lien est (N) par défaut. Il est possible de définir un lien (1-1) en ajoutant l&#39;attribut revCardinality=&#39;single&#39; à la définition du lien.

Si le lien inverse ne doit pas être visible pour l’utilisateur, vous pouvez le masquer avec la définition de lien revLink=&#39;_NONE_&#39;. Un bon exemple d’utilisation pour cela consiste à définir un lien entre le destinataire et la dernière transaction terminée, par exemple. Il vous suffit de voir le lien du destinataire à la dernière transaction et aucun lien inverse n’est nécessaire pour être visible à partir de la table de transaction.

Les liens qui effectuent une jointure externe (1-0.1) doivent être utilisés avec soin, car cela aura un impact sur les performances du système.

## Conservation des données - Nettoyage et purge {#data-retention}

Adobe Campaign n’est ni un entrepôt de données, ni un outil de création de rapports. Par conséquent, pour garantir de bonnes performances de la solution Adobe Campaign, la croissance de la base de données doit rester sous contrôle. Pour ce faire, il peut être utile de suivre certaines des meilleures pratiques ci-dessous.

Par défaut, les journaux de diffusion et de suivi d’Adobe Campaign ont une durée de rétention de 180 jours. Un processus de nettoyage s’exécute pour supprimer tout journal plus ancien.

* Si vous souhaitez conserver les journaux plus longtemps, cette décision doit être prise soigneusement en fonction de la taille de la base de données et du volume des messages envoyés. Pour rappel, la séquence Adobe Campaign est un entier de 32 bits.
* Il est recommandé de ne pas avoir plus d&#39;un milliard de documents à la fois dans ces tableaux (environ 50 % des 2,14 milliards d&#39;ID disponibles) pour limiter les risques de consommation de tous les ID disponibles. Pour ce faire, certains clients devront réduire la durée de rétention en dessous de 180 jours.

>[!IMPORTANT]
>
>Les tableaux personnalisés ne sont pas purgés avec le processus de nettoyage standard. Bien que cela ne soit pas nécessaire le premier jour, n’oubliez pas de créer un processus de purge pour vos tables personnalisées, car cela pourrait entraîner des problèmes de performances.

Il existe quelques solutions pour minimiser le besoin d’enregistrements dans Adobe Campaign :
* Exportez les données dans un entrepôt de données en dehors d’Adobe Campaign.
* Générez des valeurs agrégées qui utilisent moins d’espace tout en étant suffisantes pour vos pratiques marketing. Par exemple, vous n’avez pas besoin de l’historique complet des transactions client dans Adobe Campaign pour suivre les derniers achats.

Vous pouvez déclarer l’attribut &quot;deleteStatus&quot; dans un schéma. Il est plus efficace de marquer l&#39;enregistrement comme supprimé, puis de reporter la suppression dans la tâche de nettoyage.

## Performances {#performance}

Afin d’assurer de meilleures performances à tout moment, suivez les bonnes pratiques ci-dessous.

### Recommandations générales {#general-recommendations}

* Evitez d’utiliser des opérations telles que &quot;CONTAINS&quot; dans les requêtes. Si vous savez ce qui est attendu et souhaitez être filtré, appliquez la même condition avec un opérateur &quot;ÉGAL À&quot; ou d’autres opérateurs de filtre spécifiques.
* Evitez de vous joindre aux champs non indexés lors de la création de données dans des processus.
* Essayez de vous assurer que les processus tels que l’importation et l’exportation se produisent en dehors des heures de bureau.
* Assurez-vous qu&#39;il y ait un horaire pour toutes les activités quotidiennes et respectez le calendrier.
* Si un ou quelques processus quotidiens échouent et s’il est obligatoire de les exécuter le même jour, assurez-vous qu’il n’y a pas de processus conflictuels en cours d’exécution au démarrage du processus manuel, car cela pourrait affecter les performances du système.
* Assurez-vous qu’aucune campagne quotidienne n’est exécutée pendant le processus d’importation ou lorsqu’un processus manuel est exécuté.
* Utilisez un ou plusieurs tableaux de référence plutôt que de dupliquer un champ dans chaque ligne. Lorsque vous utilisez des paires clé/valeur, il est préférable de choisir une clé numérique.
* Une chaîne courte reste acceptable. Si des tableaux de références sont déjà en place dans un système externe, réutiliser le même type facilitera l’intégration des données avec Adobe Campaign.

### Relations de un à plusieurs {#one-to-many-relationships}

* La conception des données a un impact sur la convivialité et la fonctionnalité. Si vous concevez votre modèle de données avec de nombreuses relations de type &quot;un à plusieurs&quot;, il devient plus difficile pour les utilisateurs de construire une logique significative dans l’application. Il peut s’avérer difficile pour les spécialistes du marketing non technique de construire et de comprendre correctement la logique de filtre &quot;un à plusieurs&quot;.
* Il est bon d&#39;avoir tous les champs essentiels dans un tableau car cela facilite la création de requêtes par les utilisateurs. Il est parfois également judicieux de dupliquer certains champs d’un tableau à l’autre si cela permet d’éviter une jointure.
* Certaines fonctionnalités intégrées ne pourront pas faire référence à des relations de type &quot;un à plusieurs&quot;, par exemple la formule de pondération d’offre et les livraisons.

## Grandes tables {#large-tables}

Adobe Campaign repose sur des moteurs de base de données tiers. Selon le fournisseur, l’optimisation des performances pour les tableaux plus volumineux peut nécessiter une conception spécifique.

Vous trouverez ci-dessous quelques bonnes pratiques courantes à suivre lors de la conception de votre modèle de données à l’aide de tableaux volumineux et de jointures complexes.

* Lors de l’utilisation de tables de destinataires personnalisées supplémentaires, veillez à disposer d’une table de journaux dédiée pour chaque mappage de remise.
* Réduisez le nombre de colonnes, notamment en identifiant celles qui ne sont pas utilisées.
* Optimisez les relations du modèle de données en évitant les jointures complexes, telles que les jointures sur plusieurs conditions et/ou plusieurs colonnes.
* Pour les clés de jointure, utilisez toujours des données numériques plutôt que des chaînes de caractères.
* Réduisez autant que possible la profondeur de rétention du journal. Si vous avez besoin d’un historique plus détaillé, vous pouvez agréger le calcul et/ou gérer des tables de journaux personnalisées pour stocker un historique plus volumineux.

### Taille des tableaux {#size-of-tables}

La taille de la table est une combinaison du nombre d’enregistrements et du nombre de colonnes par enregistrement. Les deux peuvent affecter les performances des requêtes.

* Un tableau de **petite taille** est similaire au tableau Livraison.
* Un tableau de taille **** moyenne est identique à celui du tableau Destinataire. Il a un enregistrement par client.
* Un tableau de **grande taille** est similaire au tableau du journal de grande taille. Il contient de nombreux enregistrements par client.
Par exemple, si votre base de données contient 10 millions de destinataires, la table de journal large contient entre 100 et 200 millions de messages et la table de remise contient quelques milliers d&#39;enregistrements.

Sur PostgreSQL, une ligne ne doit pas dépasser 8 Ko pour éviter le mécanisme [TOAST](https://wiki.postgresql.org/wiki/TOAST) . Par conséquent, essayez de réduire autant que possible le nombre de colonnes et la taille de chaque ligne pour préserver les performances optimales du système (mémoire et processeur).

Le nombre de lignes affecte également les performances. La base de données Adobe Campaign n’est pas conçue pour stocker des données historiques qui ne sont pas activement utilisées à des fins de ciblage ou de personnalisation ; il s’agit d’une base de données opérationnelle.

Pour éviter tout problème de performances lié au nombre élevé de lignes, conservez uniquement les enregistrements nécessaires dans la base de données. Tout autre enregistrement doit être exporté vers un entrepôt de données tiers et supprimé de la base de données opérationnelle d’Adobe Campaign.

Voici quelques bonnes pratiques concernant la taille des tableaux :

* Concevez de grands tableaux avec moins de champs et plus de données numériques.
* N’utilisez pas de type grand nombre de colonnes (ex : Int64) pour stocker de petits nombres comme des valeurs booléennes.
* Supprimez les colonnes inutilisées de la définition de tableau.
* Ne conservez pas les données historiques ou inactives dans votre base de données Adobe Campaign (exportation et nettoyage).

Voici un exemple :

![](assets/transaction-table-example.png)

Dans cet exemple :
* Les tableaux *Transactions* et Elément *de* transaction sont volumineux : plus de 10 millions.
* Les tables *Produit* et *Magasin* sont plus petites : moins de 10 000.
* Le libellé et la référence du produit ont été placés dans la table *Produit* .
* La table *Transaction Item* ne comporte qu&#39;un lien vers la table *Product* , qui est numérique.

<!--For more detailed best practices on how to optimize the database design for larger volumes, see [Campaign Classic Data model Best practices](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).-->