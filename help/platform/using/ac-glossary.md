---
product: campaign
title: Glossaire pour Adobe Campaign
description: Glossaire pour Adobe Campaign
role: User, Data Architect
level: Beginner
hide: true
hidefromtoc: true
source-git-commit: cd26bf082d891e55bce489256dd9d43a1e3f243c
workflow-type: tm+mt
source-wordcount: '6453'
ht-degree: 12%

---

# Glossaire Adobe Campaign{#ac-glossary}

Vous trouverez ci-dessous la définition des termes et concepts clés dans Adobe Campaign, avec des liens vers la documentation connexe. Cliquez sur un terme pour en afficher la définition.

## A - D{#sec-1}

+++**Tests AB**

Le test A/B est une fonctionnalité qui permet à l&#39;utilisateur de définir deux à trois variantes d&#39;email : chaque variante est envoyée à des échantillons de population afin de déterminer laquelle a le meilleur résultat. Une fois déterminée, la variante gagnante est alors envoyée à la population ciblée restante.

En savoir plus sur [Test A/B](../../delivery/using/get-started-a-b-testing.md).
+++

+++**Gestion des accès**

La gestion des accès permet aux administrateurs d’attribuer des accès et des autorisations aux utilisateurs d’Adobe Campaign. Les autorisations incluent la possibilité d’afficher et/ou d’utiliser les fonctionnalités d’Adobe Campaign, telles que l’exécution des workflows, la définition de schémas et la gestion des audiences.

En savoir plus sur [Gestion des accès](access-management.md).
+++

+++**ACS Connector**

ACS Connector (Prime Offering) relie Adobe Campaign v7 et Adobe Campaign Standard. Il s&#39;agit d&#39;une fonctionnalité intégrée de Campaign v7 qui reproduit automatiquement les données vers Campaign Standard, associant le meilleur des deux applications. Campaign v7 contient des outils avancés pour gérer la Principale base de données marketing. La réplication des données depuis Campaign v7 permet à Campaign Standard d’exploiter les données enrichies dans un environnement convivial.

En savoir plus sur [ACS Connector](../../integrations/using/acs-connector-principles-and-data-cycle.md).
+++

+++**Activité**

Une activité est un élément de palette ajouté à un workflow pour définir une fonctionnalité d’exécution. L’activité est un conteneur qui exécute une tâche. Dans un workflow, une activité donnée peut produire plusieurs tâches, notamment en cas de boucle ou d&#39;actions récurrentes (périodiques).

En savoir plus sur [Activités de workflow](../../workflow/using/about-activities.md).
+++

+++**Principal profil**

Les profils sont considérés comme actifs s’ils ont été ciblés ou ont fait l’objet d’une communication via un canal au cours des 12 derniers mois. Conformément à votre contrat, chacune de vos instances Campaign est configurée avec un nombre spécifique de profils actifs comptabilisés à des fins de facturation.

En savoir plus sur [Profils principaux](../../platform/using/about-profiles.md#active-profiles).
+++

+++**Activité de workflow d’approbation**

*Contexte : Marketing distribué des campagnes*

L&#39;activité Validation en local est une activité de workflow qui permet de mettre en place un processus de validation des diffusions avant l&#39;envoi des messages.

En savoir plus sur les [Activité Validation locale](../../workflow/using/local-approval.md).
+++

+++**Audience**

Une audience est l’ensemble des profils ainsi obtenus qui répondent aux critères d’une définition de filtre, basée sur des règles et des attributs.

En savoir plus sur [Audiences](../../campaign/using/marketing-campaign-target.md).
+++

+++**Journal d’audit**

Le journal d’audit capture, en temps réel, une liste complète d’actions et d’événements se produisant dans votre instance Adobe Campaign. Il comprend un moyen en libre-service d’accéder à un historique de données pour vous aider à répondre à des questions telles que : ce qui est arrivé à vos workflows, qui les a mis à jour pour la dernière fois ou ce que vos utilisateurs ont fait dans l’instance.

En savoir plus sur [Suivi](../../production/using/audit-trail.md).
+++

+++**Campagnes automatisées**

Les campagnes qui s’exécutent selon un calendrier, par exemple pour cibler les destinataires qui ont un anniversaire ou un anniversaire. Peut également être utilisé pour exécuter une logique d’anticipation et de rétrospective, telle que qui a acheté hier ou qui doit payer demain.

En savoir plus sur [Campagnes](../../campaign/using/designing-marketing-campaigns.md).
+++

+++**Mode batch**

*Contexte : Interaction de campagne*

Dans le cadre de l&#39;interaction Campaign, le mode batch permet au moteur d&#39;offres de sélectionner la ou les meilleures offres pour un ensemble de contacts. Les règles d’éligibilité/priorisation sont appliquées à tous les contacts de l’ensemble.

En savoir plus sur [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Opération**

Campaign est une interface permettant de coordonner, définir et exécuter des campagnes marketing. Les campagnes peuvent contenir un ou plusieurs workflows, diffusions, documents et autres points de données associés dans une seule interface conviviale.

En savoir plus sur [Campagnes](../../campaign/using/designing-marketing-campaigns.md).
+++

+++**Processus de modification**

*Contexte : Interaction de campagne*

Dans le cadre d&#39;Interaction Campaign, le processus de basculement est un processus activé dans un environnement identifié, chargé de diriger l&#39;appel vers un environnement anonyme si le contact n&#39;a pas été identifié explicitement et/ou implicitement.

En savoir plus sur [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Canal**

Un canal est un moyen par lequel une communication est envoyée. Les canaux intégrés dans Adobe Campaign sont les suivants : email, SMS, courrier, notifications push, LINE et Twitter. Les canaux personnalisés peuvent être implémentés pour des exigences de canal non standard.

En savoir plus sur [Canaux](../../delivery/using/communication-channels.md).
+++

+++**Console cliente**

La console cliente Campaign est un client riche qui permet de se connecter à votre ou vos serveurs applicatifs Campaign. L’application exécutable de la console cliente (.exe) est installée sur un ordinateur disposant d’un système d’exploitation Microsoft Windows. La console cliente Campaign centralise toutes les fonctionnalités et tous les paramètres.

En savoir plus sur [Console cliente](../../platform/using/adobe-campaign-workspace.md).
+++

+++**Validation du contenu**

La validation du contenu est le processus par lequel un opérateur ou groupe distinct d&#39;opérateurs valide le contenu d&#39;une diffusion avant son envoi.

En savoir plus sur [Validation du contenu](../../campaign/using/marketing-campaign-approval.md).
+++

+++**Populations témoins**

Utilisez les Populations témoins pour mesurer l’impact de vos campagnes en excluant une partie de leur audience. Les opérateurs peuvent comparer le comportement de la population cible qui a bien reçu le message avec celui des contacts qui n&#39;ont pas été ciblés. En fonction des envois, les opérateurs pourront également cibler une population témoin dans les prochaines campagnes.

En savoir plus sur [Validation du contenu](../../campaign/using/marketing-campaign-target.md#defining-a-control-group).
+++

+++**Panneau de contrôle**

Le Panneau de Contrôle vous permet d’accroître l’efficacité de votre travail en tant qu’administrateur de produit d’Adobe Campaign, en vous permettant de gérer les paramètres et de suivre l’utilisation de chacune de vos instances. Dans son interface intuitive, vous pouvez facilement surveiller l&#39;utilisation des principales ressources ou effectuer certaines tâches administratives telles que l&#39;ajout d&#39;adresses IP à la liste autorisée, la surveillance de l&#39;espace de stockage SFTP, la gestion des clés, etc.

En savoir plus sur [Validation du contenu](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=fr).
+++

+++**Cubes**

*Contexte : Marketing Analytics*

Cube est un outil d’exploration des données intuitif Adobe Campaign qui permet aux utilisateurs de créer et de partager des rapports dynamiques.

En savoir plus sur [Cubes](../../reporting/using/about-cubes.md).
+++

+++**Ressources personnalisées**

Adobe Campaign est fourni avec un modèle de données prédéfini, où les types de données sont définis par l’installation de différents packages. Les opérateurs peuvent enrichir le modèle de données fourni en étendant les ressources pour ajouter des champs personnalisés ou des tables personnalisées, telles que des tables de transactions ou de produits.

En savoir plus sur [Ressources personnalisées](../../configuration/using/about-schema-edition.md).
+++

+++**Modèle de données**

Le modèle de données Campaign est un ensemble de schémas qui définissent les types de données et leurs relations (liens). Le modèle de données est une définition abstraite qui est mise en oeuvre physiquement avec une base de données qui contient les données réelles.

En savoir plus sur [Ressources personnalisées](../../configuration/using/about-data-model.md).
+++

+++**Workflow de nettoyage de la base de données**

Le workflow Nettoyage de la base supprime les données obsolètes afin d’éviter une croissance exponentielle de la base de données. Le workflow est déclenché automatiquement sans intervention de l’utilisateur.

En savoir plus sur [Workflow de nettoyage de la base de données](../../production/using/database-cleanup-workflow.md).
+++

+++**Serveur dédié**

*Contexte : Messages transactionnels*

Serveur(s) d’exécution dédié(s) pour utiliser les messages transactionnels. Un serveur peut généralement traiter jusqu’à 50 000 appels de moteur par heure. La désignation &quot;Serveur dédié&quot; n&#39;a pas nécessairement de corrélation 1:1 avec un serveur physique, car l&#39;Adobe peut utiliser les technologies de virtualisation pour obtenir l&#39;effet équivalent.

En savoir plus sur [Messages transactionnels](../../message-center/using/about-transactional-messaging.md).
+++

+++**Délivrabilité**

*Contexte : Délivrabilité des emails*

Mesure qui permet aux opérateurs de mesurer le succès d’une campagne atteignant la boîte de réception de leurs destinataires sans rebonds ou sans être marqués comme spam.

En savoir plus sur [Délivrabilité](../../delivery/using/about-deliverability.md).
+++

+++**Diffusion**

Une diffusion est un élément de communication marketing spécifique qui est envoyé à une audience sur un canal spécifique (email, SMS, notification push, etc.). Également appelé &quot;toucher&quot; dans la terminologie marketing.

En savoir plus sur [Diffusions](../../delivery/using/communication-channels.md).
+++

+++**Analyse des diffusions**

L’analyse de la diffusion est la préparation de la diffusion. Ce processus associe le contenu aux données de profil du destinataire pour produire l&#39;email personnalisé que le destinataire reçoit. La logique d’analyse de diffusion peut exclure les destinataires de la cible ou arrêter complètement la diffusion, en fonction de la logique définie. Ce processus inclut également l’évaluation de la logique de contenu dynamique et l’insertion d’offres spécifiques au profil de destinataire individuel.

En savoir plus sur [Analyse des diffusions](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).
+++

+++**Logs de diffusion**

Les logs de diffusion contiennent les informations générées lors de l&#39;envoi d&#39;un message. Ces logs indiquent le détail de l&#39;envoi, le message préparé, ignoré, envoyé ou en échec. Elles sont accessibles directement depuis le tableau de bord de la diffusion.

En savoir plus sur [Logs de diffusion](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).
+++

+++**Principes de diffusion**

*Contexte : Délivrabilité des emails*

Le service de conseil sur les fondamentaux de la délivrabilité d’Adobe Campaign fournit des conseils sur la délivrabilité des emails et la gestion de la réputation pour soutenir les clients qui utilisent les diffusions Adobe Campaign.

En savoir plus sur [Délivrabilité](../../delivery/using/about-deliverability.md).
+++

+++**Composition de diffusion**

*Contexte : Courrier*

Une composition est un ensemble structuré d&#39;éléments (documents, magasins, coupons promotionnels, etc.) créé par la société et pour une opération particulière. Il est utilisé dans le cadre de diffusions par publipostage direct.

En savoir plus sur [Courrier](../../delivery/using/about-direct-mail-channel.md).
+++

+++**Assistant de déploiement**

L’assistant de déploiement définit les paramètres de l’instance Campaign, tels que l’espace de noms par défaut, le planning de nettoyage de la base, les périodes de conservation des données et d’autres paramètres techniques.

En savoir plus sur [Assistant de déploiement](../../installation/using/deploying-an-instance.md#deployment-wizard).
+++

+++**Analyse descriptive**

L’analyse descriptive est un outil de reporting contextuel qui peut être utilisé pour examiner les données de la table de travail d’un workflow, les données sélectionnées dans un dossier ou pour réaliser des séances approfondies sur les cibles et exclusions des diffusions sélectionnées.

En savoir plus sur [Analyse descriptive](../../reporting/using/about-descriptive-analysis.md)
+++

+++**Marketing distribué**

*Contexte : Marketing distribué*

Le module complémentaire Marketing Distribué offre aux opérateurs Campaign un espace de travail collaboratif pour l&#39;implémentation des opérations entre les entités centrales (siège social, départements marketing, etc.) et les entités locales (points de vente, agences régionales, etc.). Cette coopération repose sur un espace de travail partagé appelé **liste des packages Campaign**, où des modèles d&#39;opération et des instances créés de manière centralisée sont proposés aux entités locales.

En savoir plus sur [Marketing distribué](../../distributed/using/about-distributed-marketing.md)
+++

+++**Répartition des valeurs**

La Répartition des valeurs est un outil qui permet de visualiser la répartition des valeurs d&#39;un attribut de schéma existant actuellement dans la base de données. Vous pouvez ainsi déterminer les valeurs disponibles, leur nombre et leur pourcentage, et éviter tout problème de mise en majuscules et d’orthographe des valeurs lors de la création d’une requête ou d’une expression.

En savoir plus sur [Marketing distribué](../../platform/using/defining-filter-conditions.md#selecting-data-to-extract)
+++

+++**Délégation de domaine**

La configuration de sous-domaine vous permet de configurer une sous-section de votre domaine (techniquement, une &quot;zone DNS&quot;) à utiliser avec Adobe Campaign.
La délégation de domaine permet à l’Adobe de contrôler et de gérer tous les aspects du DNS nécessaires à la diffusion, au rendu et au suivi des campagnes email.

En savoir plus sur [Délégation de domaine](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=fr)
+++

## E - H {#sec-2}

<!--
+++**E4X**

The version of Javascript that is used in Adobe Campaign Classic. Sometimes called ECMAScript, it is an extension of Javascript that allows the mixing of Javascript and XML primitives in the same code. Note that E4X is classified as a deprecated language. 
+++
-->

+++**Règles d’éligibilité**

*Contexte : Interaction de campagne*

Les règles d&#39;éligibilité sont des contraintes appliquées à un environnement, une catégorie ou une offre concernant la période de validité, la cible et le poids. Ils permettent aux opérateurs de s&#39;assurer qu&#39;une offre est en phase avec le contact ciblé. Dans l&#39;environnement des offres, les règles d&#39;éligibilité comprennent les règles de présentation appliquées aux offres et aux destinataires à cibler. Dans la catégorie , les règles d&#39;éligibilité permettent aux Opérateurs de limiter la validité de la catégorie dans le temps, de définir des thèmes d&#39;application et de déterminer les destinataires à cibler. Ils peuvent également définir un poids multiplicateur pour une période donnée. Ainsi, les opérateurs peuvent partager les règles relatives aux offres d&#39;autres catégories et ainsi simplifier leur gestion. Dans une offre, les règles d&#39;éligibilité permettent aux opérateurs de limiter la validité des offres dans le temps et de déterminer les destinataires à cibler.

En savoir plus sur [Règles d’éligibilité](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Offre éligible**

*Contexte : Interaction de campagne*

Une offre éligible est une offre répondant aux contraintes définies en amont qui peut être proposée de manière cohérente à une cible.

En savoir plus sur [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**E-mail Cci**

La fonctionnalité Email Cci envoie une copie exacte au format EML d’un email envoyé correspondant, qui est enregistrée dans une adresse email dédiée en Cci où les emails peuvent être traités et archivés par l’expéditeur dans un système externe.

En savoir plus sur [Email Cci](../../delivery/using/email-parameters.md#email-bcc).
+++

+++**Engagement relatif au volume d’emails**

Les emails anticipés envoyés par an comme indiqué dans la commande de ventes. Il s’agit de l’engagement total annuel en volume d’emails, y compris les emails envoyés mais non distribués en raison d’erreurs de diffusion telles que : la non-diffusion d&#39;un message, y compris, mais sans s&#39;y limiter, les erreurs d&#39;adresse email, les erreurs hard, les erreurs soft, les filtres email des clients et les listes bloquées email.
+++

+++**Appel de moteur**

Un appel au moteur est un appel au serveur qui démarre le traitement en temps réel côté serveur pour l’extraction des données, telles que les données relatives aux enquêtes, WebApps, JSSP, API, enregistrements d’applications mobiles, etc. Les appels de moteur doivent être concédés sous licence dans des packs de 5 000 appels de moteur par jour.
+++

+++**Activité d’enrichissement**

L&#39;activité Enrichissement est une activité de workflow avancée qui permet aux opérateurs d&#39;enrichir les données de la table de travail générée qui seront traitées dans le workflow. Cette activité est généralement utilisée à la suite des activités de ciblage ou d&#39;un import de fichier et avant les activités utilisant des données ciblées. Les enrichissements peuvent transformer les données de la transition entrante et configurer l&#39;activité pour compléter la transition sortante avec des données améliorées. Il permet à l’ opérateur de combiner des données provenant de plusieurs jeux de données ou de créer des liens vers une ressource temporaire.

En savoir plus sur [Activité d’enrichissement](../../workflow/using/enrichment.md).
+++

+++**Énumérations**

Une énumération est un type de données défini dans les schémas ou au niveau de la plateforme qui définit les valeurs d’entrée valides d’un champ. Les énumérations s’affichent dans l’interface utilisateur et dans les créateurs de requêtes sous la forme d’une liste de sélection.

En savoir plus sur [Enumérations](../../platform/using/managing-enumerations.md).
+++

+++**Vue Explorateur**

La vue Explorateur est un affichage hiérarchique des dossiers contenant des artefacts et des données Adobe Campaign. Notez que le système de dossiers dans Adobe Campaign ne fonctionne pas comme une vue d’ensemble classique, dans la mesure où chaque dossier contient des données d’un type spécifique, telles que Diffusions, Workflows ou Offres.

En savoir plus sur [Vue Explorateur](../../platform/using/adobe-campaign-explorer.md).
+++

+++**Comptes externes**

Les comptes externes sont des points d’entrée et de sortie pour que le produit se connecte à d’autres environnements et technologies. Les comptes externes définissent les paramètres de connexion que le produit utilise pour envoyer des données à d’autres sources ou pour recevoir des données de ces sources. Les types de compte externes standard sont les connexions aux sites SFTP, les télécoms pour prendre en charge l’envoi de SMS, les boîtes aux lettres pour les rebonds de traitement ou les connexions à des bases de données externes.

En savoir plus sur [Comptes externes](../../installation/using/external-accounts.md).
+++

+++**Gestion de la fatigue**

*Contexte : Optimisation des campagnes*

La gestion de la fatigue permet de contrôler la fréquence et la quantité des messages afin d&#39;éviter une sur-sollicitation des destinataires. Elle est souvent appliquée à l&#39;aide d&#39;une règle de typologie.

En savoir plus sur [Gestion de la fatigue](../../campaign-opt/using/pressure-rules.md).
+++

+++**Federated Data Access (FDA)**

Federated Data Access prend en charge l’extension du modèle de données client pour inclure une base de données tierce. Le module détecte automatiquement la structure des tables ciblées et utilise les données provenant des sources SQL. Vous pouvez accéder à des données externes sans modifier la structure des données Adobe Campaign.

En savoir plus sur [Federated Data Access](../../installation/using/about-fda.md).
+++

+++**Validation de l’extraction du fichier**

*Contexte : Courrier*

La validation de l&#39;extraction du fichier est le processus par lequel un opérateur ou un groupe distinct d&#39;opérateurs valide le contenu et la configuration d&#39;un fichier extrait avant son envoi à un fournisseur externe, par exemple pour une diffusion courrier.

En savoir plus sur [Validation de l’extraction du fichier](../../delivery/using/validating.md).
+++

+++**Dimension de filtrage**

La dimension de filtrage est le schéma qui contient les données ou attributs utilisés par une requête pour filtrer les lignes souhaitées. Le schéma Dimension de filtrage doit être directement lié à la dimension de ciblage définie pour permettre à Adobe Campaign de traverser la jointure de la base de données et de renvoyer les lignes du participant.

En savoir plus sur [Dimension de filtrage](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).
+++

+++**Dossier**

Un dossier est un élément de vue Explorateur qui contient des enregistrements de base de données d’un type de données spécifique. L’exception est le type de dossier générique utilisé comme élément organisateur et ne contenant aucune donnée lui-même, mais uniquement d’autres dossiers.

En savoir plus sur [Dossiers](../../platform/using/adobe-campaign-explorer.md).
+++

+++**Vue Dossier**

Le mode Dossier est un type de dossier Explorateur spécial qui est utilisé pour afficher tous les enregistrements d’un type de données sélectionné, quel que soit le dossier auquel il appartient. Les vues de dossier sont utilisées comme outil administratif pour gérer les données partitionnées ou les données distribuées entre de nombreux dossiers.

En savoir plus sur [Vue Dossier](../../platform/using/adobe-campaign-explorer.md).
+++

+++**Formulaires**

Forms définit la représentation de l’interface pour un type de schéma spécifique. Forms est le moyen utilisé pour créer et modifier facilement des éléments de données dans le produit, tels que Destinataires, Diffusions et Campagnes. Tous les éléments d’interface d’Adobe Campaign sont créés dans le produit lui-même à l’aide de Forms. Notez que les formulaires sont facultatifs et que tous les schémas ne comportent pas de formulaires.

En savoir plus sur [Forms](../../configuration/using/identifying-a-form.md).
+++

+++**Requête SQL générée**

Code SQL généré pour la base sous-jacente lorsqu’un opérateur manipule un schéma. Les schémas définissent les types de données qui sont ensuite implémentés à l’aide de tableaux et de colonnes de base de données. Le code SQL généré pour la manipulation de schémas (par exemple dans une requête) est basé sur le type de base de données installé. Ainsi, la base de données peut être changée de type et les requêtes dans Campaign restent inchangées. Adobe désigne cette fonctionnalité comme étant indépendante de la base de données.

En savoir plus sur [Requêtes SQL générées](../../platform/using/steps-to-create-a-query.md#step-6---preview-data).
+++

+++**Carte thermique**

La carte thermique des campagnes est un tableau présentant les informations d’exécution des workflows pendant une période de 24 heures. Il affiche la distribution des workflows sur la période par heure et par intervalles de 5 minutes. La carte thermique est utilisée pour évaluer la charge du serveur et déterminer les activités de workflow qui consomment le plus de ressources.

En savoir plus sur [Carte thermique](../../workflow/using/heatmap.md).
+++

+++**Déploiement hybride**

Le déploiement hybride est une combinaison de services à la demande et de logiciels on-premise déployés pour fonctionner ensemble.

En savoir plus sur [Déploiement hybride](../../installation/using/hosting-models.md#hybrid).

+++

## I - L {#sec-3}

+++**Mode d&#39;identification**

*Contexte : Interaction de campagne*

Fait référence au statut d’un contact. Il peut être explicite, implicite ou anonyme.

* **explicite** : le contact est identifié, il s’est authentifié sur l’interface du canal.
* **implicite** : le contact a été identifié par un cookie (de session ou permanent). Il peut être traité comme un contact anonyme ou comme un contact identifié.
* **anonyme** : le contact n&#39;a pas pu être identifié.

En savoir plus sur [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Diffusion d’images**

La fonctionnalité qui fournit les images incorporées dans les emails aux destinataires de la diffusion. L&#39;insertion des images à partir de la fonctionnalité &quot;Télécharger les images&quot; d&#39;un système de messagerie est ce qui génère une entrée &quot;ouverte&quot; dans les logs de tracking de Campaign.

En savoir plus sur [Diffusion d’images](../../delivery/using/defining-the-email-content.md#adding-images).
+++

+++**Interaction entrante**

*Contexte : Interaction de campagne*

Une interaction entrante est une interaction qui suit un appel entrant généré par l’action d’un contact sur un canal, tel que le web, le centre d’appel ou le mobile. Ce type d&#39;interaction est généralement traité en mode unitaire (par destinataire, par exemple).

En savoir plus sur [Interaction entrante](../../interaction/using/about-inbound-channels.md).
+++

+++**Inbox rendering**

L&#39;Inbox rendering est la génération des prévisualisations des emails. Ainsi, le message sera affiché de manière optimale aux destinataires sur divers clients web, webmails et appareils. Adobe Campaign exploite le canal Litmus, qui permet aux créateurs de contenu d’email de prévisualiser le contenu de leur message dans plus de 70 rendus d’email, tels que la boîte de réception Gmail ou le client Apple Mail.

En savoir plus sur [Inbox rendering](../../delivery/using/delivery-dashboard.md#delivery-rendering).
+++

+++**Paramètres de l&#39;instance**

Les paramètres d’instance sont les détails de configuration d’une instance Adobe Campaign. Ces paramètres sont définis dans l’assistant de déploiement (Outils>Avancé>Assistant de déploiement) ou dans les fichiers de configuration de serveur et/ou d’instance.

En savoir plus sur [Paramètres des instances](../../installation/using/about-initial-configuration.md).

+++

+++**Traitements (import et export)**

Les tâches sont gérées par un système d’assistant qui simplifie l’import et l’export de données vers et depuis le produit. Pour des raisons de simplicité et de cohérence, les tâches utilisent le système de création de modèles et peuvent être définies pour s’exécuter selon un planning.

En savoir plus sur [Tâches d’import et d’export](../../platform/using/get-started-data-import-export.md).
+++

+++**Listes**

Une liste est un jeu de données statique. Les listes sont des audiences ou des segments qui sont importés dans Campaign à partir d’autres sources (Audience Manager, Experience Platform, base de données, etc.) et qui sont affichés dans l’interface sous la forme de listes importées.

En savoir plus sur [Listes](../../platform/using/creating-and-managing-lists.md).
+++

+++**Cache local**

Informations stockées localement sur l’ordinateur de l’opérateur. Les informations mises en cache sont utilisées par la console pour réduire le trafic requis vers le serveur et améliorer les performances. L’effacement périodique du cache local (dans le menu Fichier ) met à jour les informations stockées et améliore les performances et la stabilité.

En savoir plus sur [Cache local](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).
+++

## M - P {#sec-4}

+++**Marketing Resource Management (MRM)**

*Contexte : Marketing Resource Management (MRM)*

Le **Marketing Resource Management (MRM)** dans Adobe Campaign, vous permet de contrôler les actions marketing en mode collaboratif en assurant une gestion complète et un suivi en temps réel des tâches, budgets et ressources marketing impliquées. Les opérateurs Adobe Campaign peuvent coordonner leurs actions et valider leur progression à toutes les étapes via des processus de validation complets et des outils de tracking appropriés : reporting, tracking des validations, notifications, forums de discussion, etc.

En savoir plus sur [MRM](../../mrm/using/about-marketing-resource-management.md).
+++

<!--
+++**Localization**

This template type is used to manage multilingual messages.  It is available for Email and SMS messages and useable in standalone mode, within a workflow or in a recurring delivery. In the multilingual feature templates, the language management is based on variants. Each variant represents one language.  This functionality is available only in Adobe Campaign Standard.  
+++
-->

+++**Droits nommés**

Droits d’accès granulaires à la base de données utilisés pour définir l’accès et les privilèges (rôles) d’un groupe d’opérateurs. Les droits nommés sont renseignés lors de l’installation du produit et en important divers packages qui définissent les fonctionnalités spécifiques de l’outil. Il est possible de créer des droits nommés personnalisés pour répondre aux besoins des clients.

En savoir plus sur [Droits nommés](../../platform/using/access-management-named-rights.md).
+++

+++**Espace de noms**

Une partition qui sépare les types de données client des types de données natifs d’Adobe Campaign dans le modèle de données. Également utilisé pour faciliter la migration des définitions d’une instance vers une autre, comme le déplacement d’un schéma ou d’un modèle de l’instance de développement vers l’instance de production.

En savoir plus sur [Espace de noms](../../configuration/using/about-schema-reference.md#identification-of-a-schema).
+++

+++**Barre de navigation**

Élément de navigation s’exécutant en haut de l’interface. La barre de navigation regroupe les différentes fonctionnalités principales de la plateforme. Cliquez sur un lien de la barre de navigation pour afficher l&#39;ensemble des fonctionnalités qui y sont liées. La liste des fonctions principales auxquelles vous pouvez accéder dépend des packages et des composants additionnels installés, ainsi que de vos droits d&#39;accès. La barre de navigation a pour but de simplifier la gestion des écrans et d’accroître la productivité.

En savoir plus sur [Barre de navigation](../../platform/using/adobe-campaign-workspace.md#browsing-pages).
+++

+++**Arborescence de navigation**

Navigation principale dans la vue Explorateur d’Adobe Campaign. L’arborescence de navigation fonctionne comme un explorateur de fichiers (par exemple, l’Explorateur Windows). Les dossiers peuvent contenir des sous-dossiers. La sélection d’un nœud affiche la vue correspondante. La vue affichée est une liste associée à un schéma et à un formulaire de saisie pour l&#39;édition de la ligne sélectionnée. Vous pouvez personnaliser l’arborescence de navigation et définir les autorisations sur les dossiers.

En savoir plus sur [Arborescence de navigation](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarch).
+++

+++**Objectifs**

*Contexte : Marketing Resource Management (MRM)*

Dans le cadre de l&#39;opération, du programme ou du plan, les opérateurs peuvent indiquer une liste d&#39;objectifs. Il s’agit de valeurs quantifiées à atteindre. A la fin de l&#39;opération, du programme ou du plan, le module MRM permet aux Opérateurs de comparer les objectifs et les résultats dans des rapports dédiés.

En savoir plus sur [Objectifs](../../mrm/using/creating-and-managing-tasks.md#expenses-and-revenues).
+++

+++**Catalogue d’offres**

*Contexte : Interaction de campagne*

Ensemble d’offres définies dans Adobe Campaign qui peuvent être sélectionnées lors d’une interaction. Le catalogue est organisé de manière hiérarchique avec chaque nœud correspondant à une catégorie.

En savoir plus sur [Catalogue d’offres](../../interaction/using/offer-catalog-overview.md).
+++

+++**Contact de l&#39;offre**

*Contexte : Interaction de campagne*

Un contact provenant d’une interaction entrante. Lors du traitement des appels au moteur, le contact est associé à une dimension de ciblage. Les contacts anonymes non identifiés sont rattachés à la dimension de ciblage des visiteurs. Il existe deux types de contacts, identifiés et anonymes :

* **Contact identifié** : contact s&#39;étant volontairement identifié sur le canal. Dans les interactions sortantes, le contact est systématiquement identifié.
* **Contact anonyme** : contact qui ne s&#39;est pas volontairement inscrit sur le canal mais qui peut être identifié implicitement au moyen d&#39;un cookie. Cette terminologie n&#39;a lieu d&#39;être que dans le cadre d&#39;interactions entrantes.

En savoir plus sur [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Environnement de conception d’offre**

*Contexte : Interaction de campagne*

L’offre **Environnement de conception** est l&#39;environnement dans lequel les opérateurs créent des offres, définissent des règles de typologie et sélectionnent le schéma qui sera ciblé par les offres. La table de stockage des propositions d&#39;offres générées est également définie par l&#39;environnement. Par défaut, le module complémentaire Interaction est fourni avec un **Conception** environnement et un **En direct** l’environnement qui y est lié. Les deux environnements sont préconfigurés pour cibler le tableau des destinataires intégrée.

En savoir plus sur [Environnements de conception](../../interaction/using/fundamental-principles.md).
+++

+++**arbitrages entre les moteurs d&#39;offres**

*Contexte : Interaction de campagne*

Sélection des offres qui seront affichées dans un environnement (offres éligibles). Le principe d&#39;arbitrage classe les offres par priorité en fonction des critères définis dans les catégories et les offres.

En savoir plus sur [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Optimisation du moteur d&#39;offres**

*Contexte : Interaction de campagne*

Processus de suppression des offres qui ne peuvent pas être sélectionnées. Exécutée avant l&#39;étape d&#39;arbitrage du moteur d&#39;offres.

En savoir plus sur [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Environnement d&#39;offre**

*Contexte : Interaction de campagne*

Le dossier racine qui définit un catalogue d’offres, ses emplacements disponibles et les filtres prédéfinis de l’environnement. Les opérateurs doivent créer un environnement pour chaque dimension de ciblage. Il existe deux types d’environnements d’offres : Concevoir et vivre.

En savoir plus sur [Environnements](../../interaction/using/fundamental-principles.md).
+++

+++**Environnement d’offre en direct**

*Contexte : Interaction de campagne*

Environnement associé à une campagne **Environnement de conception**. Il contient des offres en lecture seule dont le contenu et l&#39;éligibilité ont été validés via le **Environnement de conception**. Ils peuvent être sélectionnés pour la présentation sur un site web ou insérés dans un message sortant.

En savoir plus sur [Environnements en ligne](../../interaction/using/fundamental-principles.md).
+++

+++**Aperçu de l’offre**

*Contexte : Interaction de campagne*

Prévisualisez l’offre telle qu’elle s’affiche dans son dossier. Il est accessible à partir de l&#39;onglet Aperçu de l&#39;offre ou du profil du contact.

En savoir plus sur [Aperçu des offres](../../interaction/using/creating-an-offer.md#previewing-the-offer).
+++

+++**Règles de présentation des offres**

*Contexte : Interaction de campagne*

Règles de typologie référencées dans l&#39;environnement des offres qui permettent aux opérateurs d&#39;exclure des offres spécifiques en tenant compte de l&#39;historique des propositions des destinataires.

En savoir plus sur [Règles de présentation des offres](../../interaction/using/managing-offer-presentation.md#presentation-rules-overview).
+++

+++**Proposition d&#39;offres**

*Contexte : Interaction de campagne*

Une proposition d&#39;offre est le résultat de l&#39;action qui consiste à présenter une offre à un contact dans un emplacement donné, par exemple la bannière d&#39;un site web, un email ou un contenu SMS. Ce résultat est stocké dans la table des propositions d&#39;offre qui définit l&#39;offre, le destinataire et l&#39;horodatage, fournissant ainsi un enregistrement de toutes les offres reçues par un destinataire.

En savoir plus sur [Propositions d&#39;offres](../../interaction/using/creating-offer-spaces.md#offer-proposition-statuses).
+++

+++**Représentation de l&#39;offre**

*Contexte : Interaction de campagne*

Une proposition d&#39;offre est le résultat de l&#39;action qui consiste à présenter une offre à un contact dans un emplacement donné, par exemple la bannière d&#39;un site web, un email ou un contenu SMS. Ce résultat est stocké dans la table des propositions d&#39;offre qui définit l&#39;offre, le destinataire et l&#39;horodatage, fournissant ainsi un enregistrement de toutes les offres reçues par un destinataire.

En savoir plus sur [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Simulation d’offres**

*Contexte : Interaction de campagne*

Une simulation d&#39;offres permet aux Opérateurs de tester la répartition des offres dans une portée définie (date de diffusion, segment cible, nombre d&#39;offres, thème, etc.) avant d’envoyer les offres. Il peut être utilisé pour ajuster les priorités des offres et les règles d’éligibilité afin d’optimiser l’efficacité des offres.

En savoir plus sur [Simulation des offres](../../interaction/using/about-offers-simulation.md).
+++

+++**Un emplacement**

*Contexte : Interaction de campagne*

Un emplacement est un dossier définissant l’emplacement d’exposition de l’offre. Définir un emplacement permet de définir le canal utilisé, de construire le contenu de l&#39;offre et de spécifier les offres présentées. L&#39;emplacement est l&#39;interface entre le canal et le moteur d&#39;offres.

En savoir plus sur [Simulation des offres](../../interaction/using/creating-offer-spaces.md).
+++

+++**Thèmes de l&#39;offre**

*Contexte : Interaction de campagne*

Les thèmes des offres sont des mots-clés définis dans une catégorie qui permet aux opérateurs de filtrer les offres lors de leur présentation. Les thèmes permettent la sélection non hiérarchique d’offres à partir de la structure du catalogue.

En savoir plus sur [Thèmes de l&#39;offre](../../interaction/using/integrating-an-offer-via-the-wizard.md).
+++

+++**Poids de l&#39;offre**

*Contexte : Interaction de campagne*

Le poids de l&#39;offre est basé sur des formules qui définissent précisément la pertinence d&#39;une offre afin de permettre au moteur de sélectionner l&#39;offre la plus pertinente. Les poids sont définis dans les offres et les multiplicateurs sont définis dans les catégories. Les offres éligibles sont prises en compte dans l&#39;ordre décroissant de poids.

En savoir plus sur [Poids de l&#39;offre](../../interaction/using/creating-an-offer.md#offer-weight).
+++

+++**Les groupes d&#39;opérateurs**

Les groupes d&#39;opérateurs permettent de gérer les rôles des opérateurs Campaign. Vous définissez des groupes d’opérateurs auxquels vous attribuez des droits, puis vous associez les opérateurs à un ou plusieurs groupes. Vous pouvez ainsi réutiliser des droits et rendre les profils d’opérateurs plus cohérents. Il facilite également la gestion et la maintenance des profils.

En savoir plus sur [Groupes d&#39;opérateurs](../../platform/using/access-management-groups.md).
+++

+++**Opérateur**

Un opérateur est un utilisateur Adobe Campaign qui possède des autorisations pour se connecter et effectuer des actions. Les opérateurs sont associés à des groupes d&#39;opérateurs et héritent des droits et privilèges de ces groupes. Vous pouvez également attribuer des droits nommés directement aux opérateurs.

En savoir plus sur [Opérateurs](../../platform/using/access-management-operators.md).
+++

+++**Options**

Les options sont des variables au niveau de la plateforme qui sont utilisées pour définir les paramètres de l&#39;instance Campaign. Les options peuvent définir des délais (par exemple pour le workflow de nettoyage de la base) ou d’autres définitions globales au niveau de la plateforme.

En savoir plus sur [Options](../../installation/using/configuring-campaign-options.md).
+++

+++**Interaction sortante**

*Contexte : Interaction de campagne*

Une interaction sortante est un appel au moteur d&#39;interaction à partir d&#39;une liste de contacts (utilisé pour la diffusion d&#39;emails, de courriers, etc.). Les mêmes règles et processus sont appliqués à chaque contact. Ce type d&#39;interaction est généralement traité en mode batch.

En savoir plus sur [Interaction sortante](../../interaction/using/about-outbound-channels.md).
+++

+++**Export/import de package**

Un export de package est une opération qui consiste à générer un fichier XML contenant des définitions d’objets. Les packages sont utilisés pour migrer les fonctionnalités et les définitions d’une instance à une autre. Ils sont également utilisés pour ajouter des définitions de produit critiques aux systèmes de sauvegarde et de contrôle de code source.

En savoir plus sur [Export/import de package](../../platform/using/working-with-data-packages.md).
+++

+++**Palette**

La palette des workflows affiche les activités disponibles qui peuvent être ajoutées à un workflow. Ce composant est présenté sous forme d’onglets avec des activités de workflow regroupées logiquement selon leur utilisation. Les activités disponibles dans la palette sont déterminées par les modules complémentaires installés dans l’instance Campaign et par le contexte affichant le workflow.

En savoir plus sur [Palette](../../workflow/using/building-a-workflow.md#adding-and-linking-activities).
+++

+++**Suivi des performances**

Les informations de surveillance des performances s’affichent dans l’onglet Surveillance . Il affiche des mesures pour le système sous-jacent, telles que l’utilisation de la mémoire et du processeur, les statistiques du serveur SMTP, les processus du serveur et d’autres informations pertinentes.

En savoir plus sur [Surveillance des performances](../../production/using/monitoring-processes.md).
+++

+++**Blocs de personnalisation**

Adobe Campaign propose des blocs de personnalisation intégrés que vous pouvez insérer dans vos diffusions. Ils sont dynamiques, personnalisés et contiennent un rendu spécifique. Vous pouvez par exemple ajouter un logo, un message de salutations ou un lien vers une page miroir. Plusieurs blocs de personnalisation sont disponibles par défaut. Vous pouvez également définir des blocs de personnalisation personnalisés qui vous permettront d&#39;optimiser la personnalisation de votre diffusion. Les données réelles sont insérées dans chaque message généré lors de la phase d&#39;analyse de la diffusion.

En savoir plus sur [Blocs de personnalisation](../../delivery/using/personalization-blocks.md).
+++

+++**Champ de personnalisation**

Un champ de personnalisation est une référence de champ de données unique utilisée lors de la personnalisation d’une diffusion pour un destinataire spécifique. La valeur réelle des données est insérée lors de la phase d&#39;analyse de la diffusion.

En savoir plus sur [Champs de personnalisation](../../delivery/using/personalization-fields.md).
+++

+++**Variables de personnalisation**

Les variables de personnalisation sont des éléments de code dans une diffusion qui peuvent afficher du texte différent à différents destinataires en fonction des informations du destinataire. Ces champs peuvent être implémentés sous la forme d&#39;un champ de personnalisation ou d&#39;un bloc.

En savoir plus sur [Variables de personnalisation](../../delivery/using/about-personalization.md).
+++

+++**Plan**

Un plan est un type de dossier utilisé pour organiser les activités marketing selon un calendrier. Les dossiers de planification dans la vue Explorateur définissent des unités temporelles, telles qu’un an, un trimestre ou un mois. Les dossiers Plan peuvent être imbriqués et contenir d’autres dossiers Plan, programmes ou Campagnes.

En savoir plus sur [Formules](../../campaign/using/setting-up-marketing-campaigns.md).
+++

+++**Filtres prédéfinis**

Les filtres prédéfinis sont des requêtes qui ont été enregistrées pour réutilisation. L’utilisation de filtres prédéfinis augmente la productivité (car ils ne sont créés qu’une seule fois), contribue à créer de la cohérence (car tous les marketeurs peuvent les utiliser) et à réduire les compétences requises du marketeur, car il peut utiliser du code ou une logique qu’il pourrait ne pas être en mesure de créer lui-même.

En savoir plus sur [Filtres prédéfinis](../../configuration/using/creating-filters.md).
+++

<!--
+++**Predictive Engagement Scoring**

Predictive engagement scoring predicts the probability of a recipient engaging with a message and the probability of opting out (unsubscribing) within the next seven days after the next email send. The probabilities are further divided into buckets according to the specific risk of disengagement, medium, or low. The model also provides the risk percentile rank for the customers to understand where the rank of a certain customer in relation to others. 

Learn more about [Predictive Engagement Scoring](../../platforrm/using/creating-filters.md).
+++
-->

+++**Clé primaire**

La clé Principale est l’identifiant unique de chaque enregistrement dans une table de base de données. Une table doit posséder au moins une clef. Par convention, les clefs sont déclarées après la déclaration de l&#39;élément principal du schéma et à la suite des déclarations d&#39;index. Les clés Principal ne peuvent pas être composites (inclure plusieurs champs).

En savoir plus sur [Clé Principal](../../configuration/using/schema/key.md).
+++

+++**Profil**

Un profil est un enregistrement d’informations représentant un client final, un prospect ou un prospect. Chaque profil correspond à un enregistrement dans la table nmsRecipient ou une table externe contenant l&#39;identifiant du cookie, l&#39;identifiant client, l&#39;identifiant mobile ou toute autre information relative à un canal particulier.

En savoir plus sur [Profils](../../platform/using/about-profiles.md).
+++

+++**Programme**

Les dossiers de programmes et de sous-programmes organisent des activités marketing autour d’un objectif commercial, comme la fidélité, l’acquisition ou la vente croisée. Ils peuvent également représenter des périodes fiscales ou des tactiques de campagne, telles que des événements ou des newsletters. Chaque programme contient des campagnes liées à un calendrier, ce qui fournit une vue globale.

En savoir plus sur [Programmes](../../campaign/using/setting-up-marketing-campaigns.md).
+++

+++**Ressources publiques**

Le dossier Ressources publiques, dans Adobe Campaign, contient les images hébergées par le serveur applicatif. Les images des diffusions doivent être publiées sur le serveur applicatif (ou sur un serveur d&#39;hébergement d&#39;images, si Campaign est configuré de la sorte) pour apparaître dans les diffusions, telles que les emails.

En savoir plus sur [Ressources publiques](../../installation/using/deploying-an-instance.md#managing-public-resources).
+++

+++**Push**

Les notifications push sont des messages reçus par les applications mobiles. Les notifications push sont configurées pour fonctionner avec Adobe Campaign en incluant le code du SDK Experience Platform dans l’application mobile. Pour les notifications push, deux canaux de diffusion sont disponibles : iOS et Android.

En savoir plus sur [Push](../../delivery/using/about-mobile-app-channel.md).
+++

## Q - T {#sec-5}

+++**Destinataire**

Dans Adobe Campaign, les destinataires sont les profils par défaut ciblés pour l’envoi de diffusions (emails, SMS, etc.) à vos clients. Les données des destinataires stockées dans la base de données vous permettent de filtrer la cible et d&#39;ajouter des données de personnalisation. En règle générale, il s’agit d’informations personnelles, de contact, démographiques et transactionnelles, mais il peut s’agir de n’importe quel type d’informations prenant en charge le marketing et l’analyse.

En savoir plus sur [Destinataire](../../configuration/using/about-data-model.md).
+++

+++**Fonction de rendu**

*Contexte : Interaction de campagne*

La fonction de rendu est définie dans un emplacement. Il est utilisé pour construire sa représentation de l&#39;offre en fonction des attributs définis dans l&#39;offre. Il existe trois modes de fonction de rendu différents : HTML, XML et texte.

En savoir plus sur [Fonction de rendu](../../interaction/using/creating-offer-spaces.md).
+++

+++**Campagnes de reciblage**

Campagnes qui reciblent les destinataires d’une ou de plusieurs diffusions précédentes.
+++

+++**Extension de schéma**

L’extension de schéma vous permet de personnaliser les schémas d’usine pour mieux l’adapter à vos cas d’utilisation professionnels. Par exemple, vous pouvez ajouter le champ &quot;Fidélité&quot; à la table des destinataires.

En savoir plus sur [Extension de schéma](../../configuration/using/extending-a-schema.md).
+++

+++**Schéma**

Un schéma est un document XML qui définit un type de données spécifique. Les schémas sont implémentés en tant que tables de base de données dans la base de données du produit.  Les opérateurs manipulent les schémas dans Campaign et le produit convertit leurs actions en code SQL requis qui est ensuite exécuté sur la base de données. Notez que ces termes (schéma/tableau) sont souvent utilisés de manière interchangeable par les opérateurs, mais il s’agit d’éléments différents de l’architecture du produit.

En savoir plus sur [Schémas](../../configuration/using/about-schema-reference.md).
+++

+++**Adresses de contrôle**

Les adresses de contrôle permettent de cibler des destinataires qui ne correspondent pas aux critères de ciblage définis. Ainsi, les destinataires qui n’entrent pas dans le cadre de la diffusion peuvent la recevoir, comme tout autre destinataire cible.

En savoir plus sur [Adresses de contrôle](../../delivery/using/about-seed-addresses.md).
+++

<!--
+++**Send-time optimization**

To improve the open rate of your messages, you can manually define a sending time per recipient. Each profile will receive the message at the specified date and time, whenever possible. Defining a sending time can be done at the delivery level or using a workflow.

Learn more about [Send-time optimization](../../delivery/using/about-seed-addresses.md:).
+++
-->

+++**Service**

Adobe Campaign vous permet de créer et d’administrer des services d’information tels que des newsletters ou des mises à jour de produits, ainsi que de gérer les abonnements à ces services. Plusieurs services peuvent être définis en parallèle.

En savoir plus sur [Services](../../delivery/using/about-services-and-subscriptions.md).
+++

+++**Gestion SFTP**

Dans le Panneau de contrôle, vous pouvez interagir avec tous les serveurs SFTP qui sont connectés aux instances Campaign auxquelles vous avez accès. Le panneau de contrôle vous permet d’effectuer des actions sur vos serveurs SFTP, comme surveiller la capacité de stockage, gérer les listes autorisées d’adresses IP et gérer les clés SSH publiques.

En savoir plus sur [Gestion SFTP](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/about-sftp-management.html?lang=en).
+++

+++**Activité de services d’abonnements**

Cette activité de workflow permet de créer ou supprimer un abonnement à un service d&#39;information pour la population spécifiée par la transition.

En savoir plus sur [Activité de services d’abonnements](../../workflow/using/subscription-services.md).
+++

+++**Validation de la cible**

*Contexte : Marketing distribué des campagnes*

La validation de la cible est le processus par lequel un opérateur ou un groupe d&#39;opérateurs distinct doit valider la cible finale d&#39;une diffusion (après que la phase d&#39;analyse a généré la cible) avant que la diffusion ne puisse être envoyée.

En savoir plus sur [Validation de la cible](../../workflow/using/local-approval.md).
+++

+++**Données cibles**

Les données de la cible sont les données stockées dans la table de travail (transition) d&#39;un workflow. Ces données sont disponibles dans la diffusion pour la personnalisation du contenu de la diffusion ou pour définir la logique des éléments dynamiques de la diffusion.

En savoir plus sur [Données cibles](../../workflow/using/data-life-cycle.md#target-data).
+++

+++**Carte Target**

Il s’agit du mappage des canaux de diffusion sur un type de données spécifique. Adobe Campaign n’envoie pas en soi aux adresses électroniques ni aux numéros de téléphone, mais plutôt aux types de données. Les mappages cibles (parfois appelés mappages de diffusion) définissent la manière dont différents canaux de diffusion se connectent aux champs de données d’un schéma. Elle définit la manière dont Campaign envoie vers ce type de données à l’aide d’un champ ou d’une expression spécifique.

En savoir plus sur [Données cibles](../../delivery/using/define-the-right-audience.md#target-mappings).
+++

+++**Activités de ciblage**

Il s’agit d’activités de workflow spécifiques au ciblage, à la manipulation et au filtrage des populations. Ils permettent aux opérateurs de construire une ou plusieurs cibles en définissant des ensembles puis en partitionnant ou en combinant ces ensembles à l&#39;aide des opérations d&#39;intersection, d&#39;union ou d&#39;exclusion.

En savoir plus sur [Activités de ciblage](../../workflow/using/about-targeting-activities.md).
+++

+++**Targeting dimension**

Type de données généré (renvoyé) par une requête ou d’autres activités de workflow. Notez qu’Adobe Campaign renvoie uniquement la Principal de clé des lignes de la base de données du participant, quelle que soit la requête utilisée pour les obtenir.

En savoir plus sur [Dimension de ciblage](../../workflow/using/targeting-data.md).
+++

+++**Activité Tâche**

*Contexte : Marketing Resource Management (MRM)*

L&#39;activité de workflow Tâche intègre l&#39;action humaine dans la logique d&#39;un workflow. Vous pouvez définir deux scénarios : la première si la tâche est complétée et la seconde si la tâche n&#39;est pas complétée (si elle est manuellement indiquée comme non complétée ou si elle expire).

Les cas d’utilisation standard servent à incorporer des actions hors ligne dans une campagne ou à des actions personnalisées telles que les approbations.

Dans un workflow de campagne, l&#39;activité Tâche



En savoir plus sur [Activité Tâche](../../workflow/using/task.md).
+++

<!--
+++**Task**

One iteration of the defined functionality of a workflow activity. Each execution of a task has a unique task identifier.   

Learn more about [Tasks](../../workflow/using/about-workflows.md).
+++
-->

+++**Template**

Un modèle est un élément de conception utilisé pour créer un objet. Il contient les paramètres de l’objet et, éventuellement, le contenu de l’objet. Le système de création de modèles est utilisé pour créer des diffusions, des campagnes, des workflows et de nombreux autres éléments d&#39;Adobe Campaign. Les modèles d’usine disponibles sont définis par les packages installés. Les modèles peuvent ensuite être dupliqués et personnalisés selon les besoins par les opérateurs Campaign.
+++

<!--
+++**Test profiles**

Allows targeting of additional recipients who do not match the defined targeting criteria. They are added to a message’s audience to detect any fraudulent use of your recipient database or to ensure delivery. Seen as the Seed type in the Campaign interface.

Learn more about [Test profiles](../../workflow/using/about-workflows.md).
+++
-->

<!--
+++**Total database storage**

The aggregate size of the production and non-production instance(s) database storage managed by Adobe. 

Learn more about [Total database storage](../../workflow/using/about-workflows.md).
+++
-->

+++**Logs de tracking**

Le workflow technique de tracking récupère les données de tracking une fois que la diffusion a été envoyée et que le tracking a été activé. Ces données figurent dans l’onglet Tracking de votre diffusion. Vous pouvez trouver des informations sur les ouvertures et les clics sur un email ou d&#39;autres interactions avec un message reçu par le destinataire.

En savoir plus sur [Logs de tracking](../../delivery/using/accessing-the-tracking-logs.md).
+++

+++**Messages transactionnels**

Les messages transactionnels sont un module Campaign conçu pour gérer des notifications de déclencheur personnalisées générées à partir d’événements envoyés par un système d’information externe. Un message transactionnel est une communication individuelle et unique envoyée en temps réel à un utilisateur par un prestataire tel qu&#39;un site web. Il est particulièrement attendu, car il contient des informations importantes que le destinataire souhaite vérifier ou confirmer.

En savoir plus sur [Messages transactionnels](../../message-center/using/about-transactional-messaging.md).
+++

+++**Campagnes déclenchées**

Les campagnes déclenchées sont des campagnes exécutées lorsqu’une demande d’API est reçue dans un workflow. Les appels d’API sont consommés par une activité Signal dans le workflow qui lance l’exécution du workflow.

En savoir plus sur [Campagnes déclenchées](../../workflow/using/external-signal.md).
+++

<!--
+++**Triggers**

Signals that initiate execution of a workflow, delivery or other action. Typically an API call. 

Learn more about [Triggers](../../workflow/using/about-workflows.md).
+++
-->

+++**Règle de typologie**

*Contexte : Optimisation des campagnes*

Les règles de typologie sont des règles de fonctionnement qui sont mises en oeuvre dans le cadre de la phase d’analyse de la diffusion. Les règles de typologie sont des contrôles sur le contenu de la diffusion (Règles de contrôle) ou de la cible de la diffusion (Règles de filtrage) ou toute autre logique (Règles de pression) qui impose les exigences de l&#39;entreprise. Les règles sont des éléments granulaires qui peuvent être inclus dans une ou plusieurs typologies.

En savoir plus sur [Typologies](../../campaign-opt/using/about-campaign-typologies.md#typology-rules).
+++

+++**Typology**

*Contexte : Optimisation des campagnes*

Une typologie est un groupe de Règles de typologie qui sont appliquées à la phase d&#39;analyse d&#39;une diffusion. Une typologie de campagne peut contenir plusieurs règles de typologie, mais une diffusion ne peut référencer qu&#39;une seule typologie.

En savoir plus sur [Typologies](../../campaign-opt/using/about-campaign-typologies.md#typologies).
+++

## U - Z {#sec-6}

+++**Mode unitaire**

*Contexte : Interaction Campaign, messagerie transactionnelle*

En mode unitaire, un seul contact est traité par le moteur d&#39;offres au moment de l&#39;exécution. Ce mode est généralement utilisé pour les interactions entrantes et les messages transactionnels.

En savoir plus sur [Mode unitaire](../../interaction/using/about-inbound-channels.md).
+++

<!--
+++**Universes**

Application pages hosted by the Campaign instance. Used for approval forms, landing pages, opt-out forms, preference pages or to implement other business requirements.  

Learn more about [Universes](../../workflow/using/about-workflows.md).
+++
-->

+++**Des applications web**

Les applications web sont des pages d&#39;applications dynamiques et interactives hébergées par l&#39;instance Campaign. Il contient les données de la base et le contenu adapté aux droits de l&#39;utilisateur connecté. Par exemple, vous pouvez créer un formulaire d&#39;édition sur un extranet, ou des formulaires de notification incluant des données de la base avec des tableaux, graphiques, formulaires de saisie, etc. Cette fonctionnalité vous permet de concevoir et de publier des pages web dans lesquelles les utilisateurs peuvent rechercher ou saisir des informations.

En savoir plus sur [Applications web](../../web/using/about-web-applications.md).
+++

+++**Journal des workflows**

Le journal des workflows est le journal d’exécution étape par étape d’un workflow. Il contient l’historique ou le journal d’audit du workflow. Il est utilisé à des fins de développement, de dépannage ou de débogage.

En savoir plus sur [Journal des workflows](../../workflow/using/monitoring-workflow-execution.md).
+++

+++**Workflow**

Un workflow est une représentation visuelle du flux d&#39;exécution de l&#39;opération. Il permet d’orchestrer l’ensemble des processus et tâches dans les différents modules du serveur applicatif. Cet environnement graphique complet permet de concevoir des processus englobant segmentation, exécution de campagnes, traitement de fichiers, participation humaine, etc. Le moteur de workflow exécute et suit ces processus.

En savoir plus sur [Workflows](../../workflow/using/about-workflows.md).
+++

+++**Table de travail**

La table de travail contient toutes les informations véhiculées par les transitions de workflow. Chaque workflow utilise plusieurs tables de travail. Les données véhiculées dans ces tables peuvent être accélérées et utilisées tout au long du cycle de vie du workflow, à condition qu’elles ne soient pas purgées. En effet, les tables inutiles sont purgées chaque fois que le workflow est passivé, et éventuellement pendant l&#39;exécution des workflows les plus volumineux afin d&#39;éviter de surcharger le serveur.

En savoir plus sur [Tables de travail](../../workflow/using/about-workflows.md).
+++