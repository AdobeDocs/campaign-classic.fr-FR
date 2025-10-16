---
product: campaign
title: Glossaire pour Adobe Campaign
description: Glossaire pour Adobe Campaign
feature: Overview
role: User, Data Architect
level: Beginner
exl-id: 81f207a0-bb72-450b-abe4-0b229b6b1f3a
source-git-commit: 0507e0372a81351adc145dafdd3cbe5d5422dc00
workflow-type: tm+mt
source-wordcount: '6197'
ht-degree: 93%

---

# Glossaire Adobe Campaign{#ac-glossary}

Vous trouverez ci-dessous la définition des termes et concepts clés dans Adobe Campaign, avec des liens vers la documentation connexe. Cliquez sur un terme pour en afficher la définition.

## A - D{#sec-1}

+++**Tests AB**

Les tests AB désignent une fonctionnalité qui permet à l’utilisateur de définir deux à trois variantes d’email : chaque variante est envoyée à des échantillons de population afin de déterminer laquelle a le meilleur résultat. Une fois déterminée, la variante gagnante est alors envoyée à la population restante.

En savoir plus sur les [Tests AB](../../delivery/using/get-started-a-b-testing.md).
+++

+++**Gestion des accès**

La gestion des accès permet aux administrateurs d’attribuer des accès et des autorisations aux utilisateurs d’Adobe Campaign. Les autorisations incluent la possibilité d’afficher et/ou d’utiliser les fonctionnalités d’Adobe Campaign, telles que l’exécution des workflows, la définition de schémas et la gestion des audiences.

En savoir plus sur la [Gestion des accès](access-management.md).
+++

<!--
+++**ACS Connector**

ACS Connector (Prime Offering) bridges Adobe Campaign v7 and Adobe Campaign Standard. It is an integrated feature in Campaign v7 that automatically replicates data to Campaign Standard, uniting the best of both applications. Campaign v7 has advanced tools to manage the primary marketing database. The data replication from Campaign v7 allows Campaign Standard to leverage the rich data in a user-friendly environment. 

Learn more about [ACS Connector](../../integrations/using/acs-connector-principles-and-data-cycle.md).
+++
-->

+++**Activité**

Une activité est un élément de palette ajouté à un workflow pour définir une fonctionnalité d’exécution. L’activité est un conteneur qui exécute une tâche. Dans un workflow, une activité donnée peut engendrer plusieurs tâches, notamment en cas de boucle ou d’actions récurrentes (périodiques).

Pour en savoir plus sur les activités de workflow, consultez la [documentation de Campaign v8]&#x200B;(https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/activities)
.html){target="_blank"}.
+++

+++**Profil actif**

Les profils sont considérés comme actifs s’ils ont été ciblés ou ont fait l’objet d’une communication via un canal au cours des 12 derniers mois. Conformément à votre contrat, chacune de vos instances Campaign est configurée avec un nombre spécifique de profils actifs comptabilisés à des fins de facturation.

En savoir plus sur les [Profils actifs](../../platform/using/about-profiles.md#active-profiles).
+++

+++**Activité de workflow d’approbation**

*Contexte : marketing distribué de Campaign*

L’activité Validation en local est une activité de workflow qui permet de mettre en place un processus de validation des diffusions avant l’envoi des messages.

+++

+++**Audience**

Une audience est l’ensemble des profils obtenus qui répondent aux critères d’une définition de filtre, basée sur des règles et des attributs.

Pour en savoir plus sur les audiences, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html?lang=fr){target="_blank"}.
+++

+++**Journal d’audit**

Le journal d’audit capture, en temps réel, une liste complète d’actions et d’événements se produisant dans votre instance Adobe Campaign. Il propose également un accès en libre-service à un historique des données pour répondre à des questions telles que : ce qui est arrivé à vos workflows et qui les a mis à jour en dernier, ou ce que vos utilisateurs ont fait dans l’instance.

En savoir plus sur le [Journal d’audit](../../production/using/audit-trail.md).
+++

<!--
----DUPLICATE WITH THE "CAMPAIGN" ENTRY?---
+++**Automated campaigns**

Campaigns that run on a schedule, such as for targeting recipients who have a birthday or an anniversary. Can also be used to execute look-ahead and look-back logic, such as who purchased yesterday or who has a payment due tomorrow.

Learn more about [Campaigns](../../campaign/using/designing-marketing-campaigns.md).
+++
-->

+++**Mode batch**

*Contexte : Interaction de Campaign*

Dans le cadre d’Interaction de Campaign, le mode batch permet au moteur d’offres de sélectionner la ou les meilleures offres pour un ensemble de contacts. Les règles d’éligibilité/de priorisation sont appliquées à tous les contacts de l’ensemble.

En savoir plus sur [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Campagne**

Campaign est une interface permettant de coordonner, définir et exécuter des campagnes marketing. Les campagnes peuvent contenir un ou plusieurs workflows, diffusions, documents et autres points de données associés dans une seule interface conviviale.

En savoir plus sur les campagnes dans la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/campaigns/campaigns.html?lang=fr){target=_blank}.
+++

<!--
-----NOT USEFUL HERE?-----
+++**Changeover process**

*Context: Campaign Interaction*

In the context of Campaign Interaction, the changeover process is an activated process in an identified environment, responsible for directing the call to an anonymous environment if the contact has not been explicitly and/or implicitly identified.

Learn more about [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++
-->

+++**Canal**

Un canal est un moyen par lequel une communication est envoyée. Les canaux intégrés dans Adobe Campaign sont les suivants : e-mail, SMS, publipostage direct, notification push, LINE et X (anciennement Twitter). Les canaux personnalisés peuvent être implémentés pour des exigences de canal non standard.

En savoir plus sur les [canaux](../../delivery/using/communication-channels.md).
+++

+++**Console cliente**

La console cliente Campaign est un client riche qui vous permet de vous connecter à votre ou vos serveur(s) applicatif(s) Campaign. L’application exécutable de la console cliente (.exe) est installée sur un ordinateur disposant d’un système d’exploitation Microsoft Windows. La console cliente Campaign centralise toutes les fonctionnalités et tous les paramètres.

En savoir plus sur la [console cliente](../../platform/using/adobe-campaign-workspace.md).
+++

+++**Validation du contenu**

La validation du contenu est le processus par lequel un opérateur ou groupe distinct d’opérateurs approuve le contenu d’une diffusion avant son envoi.

Pour en savoir plus sur la validation du contenu, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-approval.html?lang=fr){target="_blank"}.

+++

+++**Populations témoins**

Vous pouvez utiliser des populations témoins pour mesurer l’impact de vos campagnes en excluant une partie de leur audience. Les opérateurs peuvent comparer le comportement de la population cible qui a bien reçu le message avec celui des contacts qui n’ont pas été ciblés. En fonction des logs d’envoi, les opérateurs peuvent également cibler une population témoin dans les prochaines campagnes.

Pour en savoir plus sur les populations témoins, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html#add-a-control-group){target="_blank"}.
+++

+++**Panneau de contrôle**

Le panneau de contrôle aide les administrateurs et administratrices de produit Adobe Campaign à accroître l’efficacité de leur travail, en leur permettant de gérer les paramètres et de suivre l’utilisation de chacune de leurs instances. Grâce à son interface intuitive, vous pouvez facilement surveiller l’utilisation des principales ressources ou effectuer certaines tâches administratives telles que l’ajout d&#39;adresses IP à la liste autorisée, la surveillance de l’espace de stockage SFTP, la gestion des clés, etc.

En savoir plus sur le [Panneau de contrôle](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=fr).
+++

+++**Cubes**

*Contexte : Analyse marketing*

Cube est un outil d’exploration des données intuitif Adobe Campaign qui permet aux utilisateurs de créer et de partager des rapports dynamiques.

En savoir plus sur [Cubes](../../reporting/using/ac-cubes.md).
+++

+++**Ressources personnalisées**

Adobe Campaign s’accompagne d’un modèle de données prédéfini, dans lequel les types de données sont définis par l’installation de différents packages. Les opérateurs peuvent enrichir le modèle de données fourni en étendant les ressources pour ajouter des champs personnalisés ou des tables personnalisées, comme des tables de transaction ou de produits.

En savoir plus sur les [ressources personnalisées](../../configuration/using/about-schema-edition.md).
+++

+++**Modèle de données**

Le modèle de données Campaign est un ensemble de schémas qui définissent les types de données et leurs relations (liens). Le modèle de données est une définition abstraite qui est mise en œuvre physiquement avec une base de données contenant les données réelles.

En savoir plus sur le [Modèle de données](../../configuration/using/about-data-model.md).
+++

+++**Workflow de nettoyage de la base de données**

Le workflow Nettoyage de la base de données supprime les données obsolètes afin d’éviter une croissance exponentielle de la base de données. Le workflow se déclenche automatiquement sans intervention de l’utilisateur.

En savoir plus sur le [workflow Nettoyage de la base de données](../../production/using/database-cleanup-workflow.md).
+++

<!--
----UNCLEAR----
+++**Dedicated server**

*Context: Transactional Messaging*

Dedicated execution server(s) to leverage Transactional Messaging. A server can typically process up to 50,000 Engine Calls per hour. The "Per-Dedicated Server" designation does not necessarily have a 1:1 correlation with a physical server as Adobe may utilize virtualization technologies to achieve the equivalent effect.

Learn more about [Transactional Messaging](../../message-center/using/about-transactional-messaging.md).
+++
-->

+++**Délivrabilité**

*Contexte : délivrabilité des e-mails*

La délivrabilité permet de mesurer le succès des campagnes atteignant la boîte de réception de vos destinataires, et ce, sans rebonds et sans être marquées comme spam. Plus précisément, la délivrabilité des e-mails désigne l’ensemble des caractéristiques qui déterminent la capacité d’un message à atteindre sa destination, via une adresse e-mail personnelle, dans un délai court, et avec la qualité attendue en termes de contenu et de format.

En savoir plus sur la [délivrabilité](../../delivery/using/about-deliverability.md).
+++

+++**Diffusion**

Une diffusion est un élément de communication marketing spécifique qui est envoyé à une audience sur un canal spécifique (e-mail, SMS, notification push, etc.). Également appelé « touche » dans la terminologie marketing.

En savoir plus sur les [diffusions](../../delivery/using/communication-channels.md).
+++

+++**Analyse des diffusions**

L’analyse de la diffusion est la préparation de la diffusion. Ce processus associe le contenu aux données de profil du destinataire pour produire l’e-mail personnalisé que le destinataire reçoit. En fonction de la logique définie, la logique d’analyse de diffusion peut exclure les destinataires de la cible ou arrêter complètement la diffusion. Ce processus inclut également l’évaluation de la logique de contenu dynamique et l’insertion d’offres spécifiques au profil de destinataire individuel.

Pour en savoir plus sur l’analyse des diffusions, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/delivery-analysis.html){target="_blank"}.
+++

+++**Logs de diffusion**

Les logs de diffusion contiennent les informations générées lors de l’envoi d’un message. Ces logs indiquent le détail de l’envoi, le message préparé, ignoré, envoyé ou en échec. Ils peuvent être testés directement depuis le tableau de bord de la diffusion.

En savoir plus sur les [logs de diffusion](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).
+++

<!--
----STRANGE IN DOCS?----
+++**Delivery fundamentals**

*Context: Email Deliverability*

Adobe Campaign Deliverability Fundamentals Consulting Service provides email deliverability consultation and reputation management to support customers using Adobe Campaign deliveries.

Learn more about [Deliverability](../../delivery/using/about-deliverability.md).
+++
-->

+++**Composition de diffusion**

*Contexte : publipostage direct*

Une composition de diffusion désigne un ensemble structuré d’éléments (documents, magasins, coupons promotionnels, etc.) créés dans l’entreprise et pour une campagne particulière. Elle est utilisée dans le cadre de diffusions par publipostage direct.

En savoir plus sur le [publipostage direct](../../delivery/using/about-direct-mail-channel.md).
+++

+++**Assistant de déploiement**

L’assistant de déploiement définit les paramètres de l’instance Campaign, tels que l’espace de noms par défaut, le planning de nettoyage de la base de données, les périodes de conservation des données et d’autres paramètres techniques.

En savoir plus sur l’[assistant de déploiement](../../installation/using/deploying-an-instance.md#deployment-assistant).
+++

+++**Analyse descriptive**

L’analyse descriptive est un outil de reporting contextuel permettant d’examiner les données de la table de travail d’un workflow, les données sélectionnées dans un dossier ou de réaliser des séances approfondies sur les cibles et exclusions des diffusions sélectionnées.

En savoir plus sur l’[analyse descriptive](../../reporting/using/about-descriptive-analysis.md).
+++

+++**Marketing distribué**

*Contexte : marketing distribué*

Le module complémentaire Marketing distribué offre aux opérateurs et opératrices Campaign un espace de travail collaboratif pour l’implémentation des campagnes entre les entités centrales (siège social, services marketing, etc.) et les entités locales (points de vente, agences régionales, etc.) Cette coopération repose sur un espace de travail partagé appelé la **liste des kits de campagne**, où des modèles et des instances de campagne conçus de manière centralisée sont proposés aux entités locales.

Pour en savoir plus sur le marketing distribué, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/distributed-marketing/about-distributed-marketing.html?lang=fr){target="_blank"}.
+++

+++**Répartition des valeurs**

La répartition des valeurs est un outil permettant de visualiser la répartition des valeurs d’un attribut de schéma existant actuellement dans la base de données. Vous pouvez ainsi déterminer les valeurs disponibles, leur nombre et leur pourcentage, et éviter tout problème de mise en majuscules et d’orthographe des valeurs lors de la création d’une requête ou d’une expression.

En savoir plus sur la [Répartition des valeurs](../../platform/using/about-queries-in-campaign.md).
+++

+++**Délégation de domaine**

La configuration de sous-domaine vous permet de configurer une sous-section de votre domaine (techniquement, une « zone DNS ») à utiliser avec Adobe Campaign.
La délégation de domaine permet à Adobe de contrôler et de gérer tous les aspects du DNS nécessaires à la diffusion, au rendu et au suivi des campagnes par e-mail.

En savoir plus sur la [Délégation de domaine](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=fr)
+++

## E - H {#sec-2}

<!--
----DEPRECATED------>
+++**E4X**

Adobe Campaign Classic utilise la version E4X de JavaScript. Également appelé ECMAScript, il s’agit d’une extension de JavaScript qui permet de combiner des primitives JavaScript et XML dans le même code. Notez que E4X est classé comme un langage obsolète.
+++


+++**Règles d’éligibilité**

*Contexte : Interaction de Campaign*

Les Règles d’éligibilité sont des contraintes appliquées à un environnement, une catégorie ou une offre, liées à la période de validité, la cible et le poids. Elles vous permettent de vous assurer qu’une offre est en phase avec le contact ciblé. Au niveau des environnements, les règles d’éligibilité comprennent les règles de présentation appliquées aux offres et les personnes à cibler. Dans la catégorie , les règles d’éligibilité permettent aux Opérateurs de limiter la validité de la catégorie dans le temps, de définir des thèmes d’application et de déterminer les destinataires à cibler. Elles peuvent également définir un poids multiplicateur pour une période donnée. Ainsi, les opérateurs peuvent partager les règles relatives aux offres d’autres catégories et ainsi simplifier leur gestion. Au niveau des offres, les règles d’éligibilité permettent de limiter la validité des offres dans le temps et de déterminer les personnes à cibler.

En savoir plus sur les [Règles d’éligibilité](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Offre éligible**

*Contexte : Interaction de Campaign*

Une offre éligible est une offre qui répond aux contraintes définies en amont et qui peut être proposée de façon cohérente à une cible.

En savoir plus sur l’[Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**E-mail Cci**

La fonctionnalité E-mail Cci envoie une copie exacte au format EML d’un e-mail diffusé correspondant, qui est enregistrée dans une adresse e-mail Cci où les e-mails peuvent être traités et archivés par l’expéditeur dans un système externe.

En savoir plus sur la fonctionnalité E-mail Cci dans la documentation de [Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/emails/email-bcc.html){target="_blank"}.
+++

<!--
-----STRANGE FOR DOCS?----
+++**Email volume commitment**

The anticipated emails sent per year as set forth in the Sales Order. This is the total annual email volume commitment, including emails sent but not delivered due to delivery errors such as: non-delivery of a message including but not limited to email address errors, hard bounces, soft bounces, email filters of mail clients, and email blacklists. 
+++
-->

<!--
-----USEFUL FOR DOCS?----
+++**Engine call**

An engine call is a server call that starts real-time processing on server side for the extraction of data, such as data relating to surveys, WebApps, JSSP, APIs, mobile app registrations, etc. Engine calls must be licensed in packs of 5,000 Engine Calls per day.
+++
-->

+++**Activité d’enrichissement**

L’activité d’enrichissement est une activité de workflow avancée qui permet aux opérateurs d’enrichir les données de la table de travail générée qui seront traitées dans le workflow. L’activité Enrichissement est généralement utilisée à la suite des activités de ciblage ou d’une importation de fichier et avant les activités qui consomment les données ciblées. Les enrichissements peuvent transformer les données de la transition entrante et configurer l’activité pour compléter la transition sortante avec des données améliorées. Ils permettent à l’opérateur de combiner des données provenant de plusieurs jeux de données ou de créer des liens avec une ressource temporaire.

Pour en savoir plus sur l’activité Enrichissement , consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/enrichment.html?lang=fr){target="_blank"}.
+++

+++**Énumérations**

Une énumération est un type de données défini dans les schémas ou au niveau de la plateforme qui définit les valeurs d’entrée valides d’un champ. Les énumérations s’affichent dans l’interface utilisateur et dans les créateurs de requêtes sous la forme d’une liste de sélection.

Découvrez comment **utiliser les énumérations** dans la documentation d’[Adobe Campaign v8 (console)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}.
+++

+++**Vue Explorateur**

La vue Explorateur est un affichage hiérarchique des dossiers contenant des artefacts et des données Adobe Campaign. Veuillez noter que le système de dossiers dans Adobe Campaign ne fonctionne pas comme une vue d’ensemble classique, dans la mesure où chaque dossier contient des données d’un type spécifique, telles que Diffusions, Workflows ou Offres.


En savoir plus sur l’interface utilisateur de Campaign dans la documentation d’[Adobe Campaign v8 (console)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

+++

+++**Comptes externes**

Les comptes externes sont des points d’entrée et de sortie pour que le produit se connecte à d’autres environnements et technologies. Les comptes externes définissent les paramètres de connexion que le produit utilise pour envoyer des données à d’autres sources ou pour recevoir des données de ces sources. Les types de compte externes standard sont les connexions aux sites SFTP, des télécommunications pour prendre en charge l’envoi de SMS, les boîtes aux lettres pour les rebonds de traitement ou les connexions à des bases de données externes.

En savoir plus sur les [Comptes externes](../../installation/using/external-accounts.md).
+++

+++**Gestion de la fatigue**

*Contexte : Optimisation de campagne*

La gestion de la fatigue vous aide à contrôler la fréquence et la quantité des messages afin d’éviter une sur-sollicitation des destinataires. Elle est souvent appliquée à l’aide d’une règle de typologie.

En savoir plus sur la gestion de la fatigue dans la documentation de [Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/pressure-rules.html?lang=fr){target="_blank"}.
+++

+++**Federated Data Access (FDA)**

Federated Data Access prend en charge l’extension du modèle de données client pour inclure une base de données tierce. Le module détecte automatiquement la structure des tables ciblées et utilise les données provenant des sources SQL. Vous pouvez ensuite accéder à des données externes sans modifier la structure des données Adobe Campaign.

En savoir plus sur [Federated Data Access](../../installation/using/about-fda.md).
+++

+++**Validation de l’extraction du fichier**

*Contexte : Publipostage direct*

La validation de l’extraction du fichier est le processus par lequel un opérateur ou un groupe distinct d’opérateurs approuve le contenu et la configuration d’un fichier extrait avant son envoi à un fournisseur externe, par exemple pour une diffusion par publipostage direct.

Pour en savoir plus sur la validation de l’extraction du fichier, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/direct-mail.html#validating){target="_blank"}.
+++

+++**Dimension de filtrage**

La dimension de filtrage est le schéma qui contient les données ou attributs utilisés par une requête pour filtrer les lignes souhaitées. Le schéma Dimension de filtrage doit être directement lié à la dimension de ciblage définie pour permettre à Adobe Campaign de traverser la jointure de la base de données et de renvoyer les lignes du participant.

Pour en savoir plus sur la dimension de filtrage, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html?lang=fr#targeting-and-filtering-dimensions){target="_blank"}.
+++

+++**Dossier**

Un dossier est un élément de la vue Explorateur contenant des enregistrements de base de données d’un type de données spécifique. L’exception est le type de dossier générique utilisé comme élément organisateur et ne contenant aucune donnée, mais uniquement d’autres dossiers.

En savoir plus sur l’interface utilisateur de Campaign dans la documentation d’[Adobe Campaign v8 (console)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

+++

+++**Vue Dossier**

La vue Dossier est un type de dossier Explorateur spécial permettant d’afficher tous les enregistrements d’un type de données sélectionné, quel que soit le dossier auquel il appartient. Les vues Dossier servent d’outil administratif pour gérer les données partitionnées ou les données distribuées entre de nombreux dossiers.

En savoir plus sur l’interface utilisateur de Campaign dans la documentation d’[Adobe Campaign v8 (console)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.
+++

+++**Formulaires**

Les formulaires définissent la représentation de l’interface pour un type de schéma spécifique. Les formulaires permettent de créer et de modifier facilement des éléments de données dans le produit, tels que les destinataires, les diffusions et les campagnes. Tous les éléments d’interface d’Adobe Campaign sont créés dans le produit lui-même à l’aide de formulaires. Notez que les formulaires sont facultatifs et que les schémas n’en comportent pas tous.

En savoir plus sur les [formulaires](../../configuration/using/identifying-a-form.md).
+++

<!--
-----USEFUL HERE?-----
+++**Generated SQL query**

The SQL code generated for the underlying database when an operator manipulates a schema. Schemas define the data types that are then implemented using database tables and columns. The SQL generated for schema manipulation (such as in a query) is based on the installed database type. Thus, the database can be swapped to a different type and the queries in Campaign remain unchanged. Adobe refers to this functionality as being database-agnostic.

Learn more about [Generated SQL queries](../../platform/using/steps-to-create-a-query.md#step-6---preview-data).
+++
-->

+++**Carte thermique**

La carte thermique de Campaign est un tableau présentant les informations d’exécution des workflows pendant une période de 24 heures. Elle affiche la distribution des workflows sur la période par heure et par intervalles de 5 minutes. La carte thermique permet d’évaluer la charge du serveur et de déterminer les activités de workflow qui consomment le plus de ressources.

Reportez-vous à la documentation de [Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/heatmap.html?lang=fr){target="_blank"}.
+++

+++**Déploiement hybride**

Le déploiement hybride est une combinaison de services à la demande et de logiciels on-premise déployés pour fonctionner ensemble.

En savoir plus sur le [Déploiement hybride](../../installation/using/hosting-models.md#hybrid).

+++

## I - L {#sec-3}

<!-- added more details but maybe still not clear/useful here? -->
+++**Mode d’identification**

*Contexte : Interaction de Campaign*

Le mode d’identification fait référence au statut d’un contact. Il peut être explicite, implicite ou anonyme.

* **Explicite** : le contact est identifié suite à sa connexion sur l’interface du canal.
* **Implicite** : le contact a été identifié par un cookie (de session ou permanent). Il peut être traité comme un contact anonyme ou comme un contact identifié.
* **Anonyme** : le contact n’a pas pu être identifié.

En savoir plus sur [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

<!--
----NOT USEFUL HERE?----
+++**Image serving**

The functionality that supplies the images embedded in emails to the delivery's recipients. The insertion of the images based on an emails system's "download images" functionality is what generates an "open" entry in Campaign's tracking logs.

Learn more about [Image serving](../../delivery/using/defining-the-email-content.md#adding-images).
+++
-->

+++**Interaction entrante**

*Contexte : Interaction de Campaign*

Une interaction entrante est une interaction qui suit un appel entrant généré par l’action d’un contact sur un canal, tel que le Web, le centre d’appel ou le mobile. Ce type d’interaction est généralement traité en mode unitaire (c’est-à-dire, par destinataire).

En savoir plus sur l’[Interaction entrante](../../interaction/using/about-inbound-channels.md).
+++

+++**Inbox rendering**

L’Inbox rendering est la génération de prévisualisations des e-mails. Ainsi, le message sera affiché de manière optimale aux destinataires sur divers clients web, webmails et appareils. Adobe Campaign utilise Litmus, qui permet aux créateurs de contenu d’e-mail de prévisualiser le contenu de leur message dans plus de 70 outils de rendu d’e-mail, tels que la boîte de réception Gmail ou le client Apple Mail.

En savoir plus sur l’[Inbox rendering](../../delivery/using/delivery-dashboard.md#delivery-rendering).
+++

+++**Paramètres des instances**

Les paramètres d’instance correspondent aux détails de configuration d’une instance Adobe Campaign. Ces paramètres sont définis dans l’assistant de déploiement (Outils > Avancé > Assistant de déploiement) ou dans les fichiers de configuration de serveur et/ou d’instance.

En savoir plus sur les [Paramètres des instances](../../installation/using/about-initial-configuration.md).

+++

+++**Traitements (import et export)**

Les traitements sont gérés par un système d’assistant qui simplifie l’import et l’export de données vers et depuis le produit. Par souci de simplicité et de cohérence, les traitements utilisent le système de création de modèles et peuvent être définis pour s’exécuter selon un planning.

En savoir plus sur les [Traitements d’importation et d’exportation](../../platform/using/get-started-data-import-export.md).
+++

+++**Listes**

Une liste est un jeu de données statique. Les listes sont des audiences ou des segments qui sont importés dans Campaign à partir d’autres sources (Audience Manager, Experience Platform, base de données, etc.) et qui sont affichés dans l’interface sous la forme de listes importées.

En savoir plus sur les [Listes](../../platform/using/creating-and-managing-lists.md).
+++

+++**Cache local**

Le cache local est l’information stockée localement sur l’ordinateur de l’opérateur ou de l’opératrice. Les informations mises en cache sont utilisées par la console pour réduire le trafic requis vers le serveur et améliorer les performances. L’effacement périodique du cache local (dans le menu Fichier) met à jour les informations stockées et améliore les performances et la stabilité.

En savoir plus sur le [Cache local](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).
+++

## M - P {#sec-4}

+++**Marketing Resource Management (MRM)**

*Contexte : Marketing Resource Management (MRM)*

Le module **Marketing Resource Management (MRM)** d’Adobe Campaign permet de piloter les actions marketing sur un mode collaboratif, en assurant la gestion complète et le tracking en temps réel des tâches, budgets et ressources marketing impliquées. Les opérateurs Adobe Campaign peuvent coordonner leurs actions et approuver leur progression à toutes les étapes via des processus de validation complets et des outils de tracking appropriés : reporting, tracking des approbations, notifications, forums de discussion, etc.

En savoir plus sur MRM dans la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/mrm/about-marketing-resource-management.html?lang=fr){target="_blank"}.
+++

<!--
----ACS?----
+++**Localization**

This template type is used to manage multilingual messages.  It is available for Email and SMS messages and useable in standalone mode, within a workflow or in a recurring delivery. In the multilingual feature templates, the language management is based on variants. Each variant represents one language.  This functionality is available only in Adobe Campaign Standard.  
+++
-->

+++**Droits nommés**

Droits d’accès à la base de données granulaire utilisés pour définir l’accès et les privilèges (rôles) d’un groupe d’opérateurs. Les droits nommés sont renseignés lors de l’installation du produit et en important divers packages qui définissent les fonctionnalités spécifiques de l’outil. Il est possible de créer des droits nommés personnalisés pour répondre aux besoins des clients.

En savoir plus sur les [Droits nommés](../../platform/using/access-management-named-rights.md).
+++

+++**Espace de noms**

L’espace de noms est une partition qui sépare les types de données de la clientèle des types de données natifs d’Adobe Campaign dans le modèle de données. Également utilisé pour faciliter la migration des définitions d’une instance vers une autre, comme le déplacement d’un schéma ou d’un modèle de l’instance de développement vers l’instance de production.

En savoir plus sur l’[Espace de noms](../../configuration/using/about-schema-reference.md#identification-of-a-schema).
+++

<!--
----generic, not specific to campaign----
+++**Navigation bar**

The navigation bar is the navigation element running across the top of the interface. The navigation bar regroups the various core capabilities of the platform. Click a navigation bar link to display the set of functionalities related to this capability. The list of core capabilities you can access depends on the packages and add-ons you have installed and on your access rights. The purpose of the Navigation bar is to simplify screen management and increase productivity.

Learn more about [Navigation Bar](../../platform/using/adobe-campaign-workspace.md#browsing-pages).
+++
-->

+++**Arborescence de navigation**

L’arborescence de navigation est la navigation principale dans la vue Explorateur d’Adobe Campaign. L’arborescence de navigation fonctionne comme un explorateur de fichiers (par exemple, l’Explorateur Windows). Les dossiers peuvent contenir des sous-dossiers. La sélection d’un nœud affiche la vue correspondante. La vue affichée est une liste associée à un schéma et à un formulaire de saisie pour la modification de la ligne sélectionnée. Vous pouvez personnaliser l’arborescence de navigation et définir les autorisations sur les dossiers.

En savoir plus sur l’interface utilisateur de Campaign dans la documentation d’[Adobe Campaign v8 (console)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

+++

+++**Objectifs**

*Contexte : Marketing Resource Management (MRM)*

Dans le cadre de l’opération, du programme ou du plan, les opérateurs peuvent indiquer une liste d’objectifs. Il s’agit de valeurs quantifiées à atteindre. À la fin de l’opération, du programme ou du plan, le module MRM permet aux opérateurs de comparer les objectifs et les résultats dans des rapports dédiés.

En savoir plus sur les objectifs dans la documentation d’[Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/mrm/creating-and-managing-tasks.html#expenses-and-revenues){target=_blank}.
+++

+++**Catalogue d&#39;offres**

*Contexte : Interaction de Campaign*

Un catalogue d’offres est un ensemble d’offres définies dans Adobe Campaign qui peuvent être sélectionnées lors d’une interaction. Le catalogue est organisé de manière hiérarchique avec chaque nœud correspondant à une catégorie.

En savoir plus sur le [Catalogue d’offres](../../interaction/using/offer-catalog-overview.md).
+++

+++**Contact d’offre**

*Contexte : Interaction de Campaign*

Un contact d’offre est un contact provenant d’une interaction entrante. Lors du traitement des appels au moteur, le contact est associé à une dimension de ciblage. Les contacts anonymes non identifiés sont rattachés à la dimension de ciblage des visiteurs. Il existe deux types de contacts, identifiés et anonymes :

* **Contact identifié** : contact s’étant volontairement identifié sur le canal. Dans les interactions sortantes, le contact est systématiquement identifié.
* **Contact anonyme** : contact qui ne s’est pas volontairement inscrit sur le canal mais qui peut être identifié implicitement au moyen d’un cookie. Cette terminologie n’a lieu d’être que dans le cadre d’interactions entrantes.

En savoir plus sur [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Environnement en édition d’offres**

*Contexte : interaction de Campaign*

L’**Environnement en édition** d’offres est l’environnement dans lequel les opérateurs créent des offres, définissent des règles de typologie et sélectionnent le schéma qui sera ciblé par les offres. Le tableau de stockage des propositions d’offres générées est également défini par l’environnement. Par défaut, le module complémentaire Interaction comprend un environnement **En édition** et un environnement **En ligne** qui lui est associé. Les deux environnements sont préconfigurés pour cibler le tableau des destinataires intégré.

En savoir plus sur les [Environnements en édition d’offres](../../interaction/using/fundamental-principles.md).
+++

+++**Arbitrage du moteur d’offres**

*Contexte : Interaction de Campaign*

Le moteur d’offres sélectionne les offres qui seront affichées dans un environnement (offres éligibles). Le principe d’arbitrage classe les offres par priorité en fonction des critères définis dans les catégories et les offres.

En savoir plus sur [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Optimisation du moteur d’offres**

*Contexte : Interaction de Campaign*

L’optimisation du moteur d’offres est le processus de suppression des offres qui ne sont pas éligibles à la sélection. Exécutée avant l’étape d’arbitrage du moteur d’offres.

En savoir plus sur [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Environnement d’offres**

*Contexte : Interaction de Campaign*

L’environnement d’offres est le dossier racine qui définit un catalogue d’offres, ses emplacements disponibles et les filtres prédéfinis de l’environnement. Les opérateurs doivent créer un environnement pour chaque dimension de ciblage. Il existe deux types d’environnements d’offres : en édition et en ligne.

En savoir plus sur les [Environnements d’offres](../../interaction/using/fundamental-principles.md).
+++

+++**Environnement en ligne d’offres**

*Contexte : Interaction de Campaign*

L’environnement en ligne d’offres est associé à un **Environnement en édition** de campagne. Il contient des offres en lecture seule dont le contenu et l’éligibilité ont été approuvés via l’**Environnement en édition**. Elles peuvent être sélectionnées pour une présentation sur un site web ou pour être insérées dans un message sortant.

En savoir plus sur les [Environnements en ligne d’offres](../../interaction/using/fundamental-principles.md).
+++

+++**Règles de présentation des offres**

*Contexte : Interaction de Campaign*

Les règles de présentation des offres sont des règles de typologie référencées dans l’environnement d’offres et permettent aux opérateurs et opératrices d’exclure des offres spécifiques en tenant compte de l’historique des propositions des destinataires.

En savoir plus sur les [Règles de présentation des offres](../../interaction/using/managing-offer-presentation.md#presentation-rules-overview).
+++

+++**Prévisualisation de l’offre**

*Contexte : Interaction de Campaign*

Il s’agit de la prévisualisation de l’offre telle qu’elle s’affiche dans son dossier. Elle est accessible à partir de l’onglet de prévisualisation des offres ou du profil du contact.

En savoir plus sur la [Prévisualisation de l’offre](../../interaction/using/creating-an-offer.md#previewing-the-offer).
+++

+++**Proposition d’offre**

*Contexte : Interaction de Campaign*

Une proposition d’offre est le résultat de l’action qui consiste à présenter une offre à un contact dans un emplacement donné, par exemple la bannière d’un site web, un e-mail ou un contenu SMS. Ce résultat est stocké dans la table des propositions d’offre qui définit l’offre, le destinataire ainsi que la date et l’heure, fournissant ainsi un enregistrement de toutes les offres reçues par un destinataire.

En savoir plus sur les [Propositions d’offre](../../interaction/using/creating-offer-spaces.md#offer-proposition-statuses).
+++

+++**Rendu de l’offre**

*Contexte : Interaction de Campaign*

Un rendu de l’offre est une information utilisée par le canal pour afficher l’offre. La représentation de l’offre peut être construite à partir de la fonction de rendu de l’emplacement sur lequel l’offre est représentée ou saisie directement dans l’interface (par exemple, dans le bloc HTML). Une offre peut être représentée par un emplacement.

En savoir plus sur [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Simulation d’offres**

*Contexte : Interaction de Campaign*

Une simulation d’offres permet aux opérateurs et opératrices de tester la répartition des offres dans une portée définie (date de diffusion, segment cible, nombre d’offres, thème, etc.) avant d’envoyer les offres. Cela peut être utilisé pour ajuster les priorités des offres et les règles d’éligibilité afin d’optimiser l’efficacité des offres.

En savoir plus sur la [Simulation d’offres](../../interaction/using/about-offers-simulation.md).
+++

+++**Emplacement**

*Contexte : Interaction de Campaign*

Un emplacement désigne un dossier définissant l’emplacement d’exposition de l’offre. Définir un emplacement permet de définir le canal utilisé, de construire le contenu de l’offre et de spécifier les offres présentées. L’emplacement est l’interface entre le canal et le moteur d’offres.

En savoir plus sur les [Emplacements](../../interaction/using/creating-offer-spaces.md).
+++

+++**Thèmes des offres**

*Contexte : Interaction de Campaign*

Les thèmes des offres sont des mots-clés définis dans une catégorie qui permettent aux opérateurs de filtrer les offres lors de leur présentation. Les thèmes permettent la sélection non hiérarchique d’offres à partir de la structure du catalogue.

En savoir plus sur les [Thèmes de l’offre](../../interaction/using/integrating-an-offer-via-the-wizard.md).
+++

+++**Poids de l’offre**

*Contexte : Interaction de Campaign*

Le poids de l’offre est basé sur des formules qui définissent précisément la pertinence d’une offre afin de permettre au moteur de sélectionner l’offre la plus pertinente. Les poids sont définis dans les offres et les multiplicateurs sont définis dans les catégories. Les offres éligibles sont prises en compte dans l’ordre de poids décroissant.

En savoir plus sur le [Poids de l’offre](../../interaction/using/creating-an-offer.md#offer-weight).
+++

+++**Opérateur**

Un opérateur est un utilisateur Adobe Campaign qui possède des autorisations pour se connecter et effectuer des actions. Les opérateurs sont associés à des groupes d’opérateurs et héritent des droits et privilèges de ces groupes. Vous pouvez également attribuer des droits nommés directement aux opérateurs.

En savoir plus sur les [Opérateurs](../../platform/using/access-management-operators.md).
+++

+++**Groupes d&#39;opérateurs**

Les groupes d’opérateurs permettent de gérer les rôles des opérateurs Campaign. Vous définissez des groupes d’opérateurs auxquels vous attribuez des droits, puis vous associez les opérateurs à un ou plusieurs groupes. Vous pouvez ainsi réutiliser des droits et rendre les profils d’opérateurs plus cohérents. Cela facilite également la gestion et la maintenance des profils.

En savoir plus sur les [groupes d’opérateurs](../../platform/using/access-management-groups.md).
+++

+++**Options**

Les options sont des variables au niveau de la plateforme qui servent à définir les paramètres de l’instance Campaign. Les options peuvent définir des délais (par exemple pour le workflow de nettoyage de la base de données) ou d’autres définitions globales au niveau de la plateforme.

En savoir plus sur les [options](../../installation/using/configuring-campaign-options.md).
+++

+++**Interaction sortante**

*Contexte : Interaction de Campaign*

Une interaction sortante appelle le moteur d’interaction à partir d’une liste de contacts (utilisée pour la diffusion d’e-mails, de publipostage direct, etc.). Les mêmes règles et processus sont appliqués à chaque contact. Ce type d&#39;interaction est généralement traité en mode batch.

En savoir plus sur l’[interaction sortante](../../interaction/using/about-outbound-channels.md).
+++

+++**Exporter/importer des packages**

Un export de package est une opération qui consiste à générer un fichier XML contenant des définitions d’objets. Les packages sont utilisés pour migrer les fonctionnalités et les définitions d’une instance à une autre. Ils sont également utilisés pour ajouter des définitions de produit critiques aux systèmes de sauvegarde et de contrôle de la source.

En savoir plus sur l’[exportation/importation de package](../../platform/using/working-with-data-packages.md).
+++

+++**Palette**

La palette du workflow affiche les activités disponibles qui peuvent être ajoutées à un workflow. Ce composant est présenté sous un format tabulé avec des activités de workflow regroupées logiquement selon leur utilisation. Les activités disponibles dans la palette sont déterminées par les modules complémentaires installés dans l’instance Campaign et par le contexte affichant le workflow.

Pour en savoir plus sur la palette, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html#add-and-link-activities){target="_blank"}.
+++

+++**Suivi des performances**

Les informations de surveillance des performances s’affichent dans l’onglet Surveillance. Celui-ci affiche des mesures pour le système sous-jacent, telles que l’utilisation de la mémoire et du processeur, les statistiques du serveur SMTP, les processus du serveur ainsi que d’autres informations pertinentes.

En savoir plus sur la [Surveillance des performances](../../production/using/monitoring-processes.md).
+++

+++**Blocs de personnalisation**

Adobe Campaign propose des blocs de personnalisation intégrés que vous pouvez insérer dans vos diffusions. Ils sont dynamiques, personnalisés et contiennent un rendu spécifique. Vous pouvez par exemple ajouter un logo, un message de salutations ou un lien vers une page miroir. Plusieurs blocs de personnalisation sont disponibles par défaut. Vous pouvez également définir des blocs de personnalisation personnalisés qui vous permettront d’optimiser la personnalisation de votre diffusion. Les données réelles sont insérées dans chaque message généré lors de la phase d’analyse de la diffusion.

Pour en savoir plus sur les blocs de personnalisation, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalization-blocks.html){target="_blank"}.
+++

+++**Champ de personnalisation**

Un champ de personnalisation est une référence de champ de données unique utilisée lors de la personnalisation d’une diffusion pour un destinataire spécifique. La valeur réelle des données est insérée lors de la phase d’analyse de la diffusion.

Pour en savoir plus sur les champs de personnalisation, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalization-fields.html){target="_blank"}.
+++

+++**Variables de personnalisation**

Les variables de personnalisation sont des éléments de code dans une diffusion qui peuvent afficher différents textes à différents destinataires en fonction des informations de ces derniers. Ces champs peuvent être implémentés sous la forme d’un champ ou d’un bloc de personnalisation.

En savoir plus sur les [variables de personnalisation](../../delivery/using/about-personalization.md).
+++

+++**Plan**

Un plan est un type de dossier utilisé pour organiser les activités marketing selon un calendrier. Les dossiers Plan dans la vue Explorateur définissent des unités temporelles, telles qu’un an, un trimestre ou un mois. Les dossiers Plan peuvent être imbriqués et contenir d’autres dossiers de planification, des dossiers de programmes ou des campagnes.

En savoir plus sur les plans dans la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=fr){target=_blank}.
+++

+++**Filtres prédéfinis**

Les filtres prédéfinis sont des requêtes qui ont été enregistrées pour réutilisation. L’utilisation de filtres prédéfinis augmente la productivité (car ils ne sont créés qu’une seule fois), contribue à assurer une cohérence (car tous les spécialistes marketing peuvent les utiliser) et à réduire les compétences requises du spécialiste marketing, car ce dernier peut utiliser du code ou une logique qu’il pourrait ne pas être en mesure de créer lui-même.

Pour plus d’informations sur les filtres, consultez la documentation [Campaign v8 (console)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/audience/create-filters){target=_blank}.
+++

<!--
----DEPRECATED----
+++**Predictive Engagement Scoring**

Predictive engagement scoring predicts the probability of a recipient engaging with a message and the probability of opting out (unsubscribing) within the next seven days after the next email send. The probabilities are further divided into buckets according to the specific risk of disengagement, medium, or low. The model also provides the risk percentile rank for the customers to understand where the rank of a certain customer in relation to others. 

Learn more about [Predictive Engagement Scoring](../../platform/using/creating-filters.md).
+++
-->

+++**Clé primaire**

La clé primaire est l’identifiant unique de chaque enregistrement dans une table de base de données. Une table doit posséder au moins une clé. Par convention, les clés sont déclarées après la déclaration de l’élément principal du schéma et à la suite des déclarations d’index. Les clés primaires ne peuvent pas être composites (c’est-à-dire, inclure plusieurs champs).

En savoir plus sur les [clés primaires](../../configuration/using/schema/key.md).
+++

+++**Profil**

Un « profil » est un enregistrement d’informations représentant un client final ou un prospect. Chaque profil correspond à un enregistrement dans la table nmsRecipient ou dans une table externe contenant un identifiant de cookie, un identifiant client, un identifiant mobile ou d’autres informations pertinentes pour un canal particulier.

En savoir plus sur les [profils](../../platform/using/about-profiles.md).
+++

+++**Programme**

Les dossiers de programmes et de sous-programmes organisent des activités marketing autour d’un objectif commercial, comme la fidélité, l’acquisition ou la vente croisée. Ils peuvent également représenter des périodes fiscales ou des tactiques de campagne, telles que des événements ou des newsletters. Chaque programme contient des campagnes liées à un calendrier, ce qui fournit une vue globale.

Pour en savoir plus sur les programmes, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=fr){target=_blank}.
+++

+++**Ressources publiques**

Le dossier Ressources publiques, dans Adobe Campaign, contient des images hébergées par le serveur d’applications. Les images des diffusions doivent être publiées sur le serveur d’applications (ou sur un serveur d’hébergement d’images, si Campaign est configuré de la sorte) pour apparaître dans les diffusions, telles que les e-mails.

En savoir plus sur les [ressources publiques](../../installation/using/deploying-an-instance.md#managing-public-resources).
+++

+++**Notification push**

*Contexte : canal applications mobiles*

Les notifications push sont des messages reçus par les applications mobiles. Les notifications push sont configurées pour fonctionner avec Adobe Campaign en incluant le code du SDK Experience Platform dans l’application mobile. Pour les notifications push, deux canaux de diffusion sont disponibles : iOS et Android.

En savoir plus sur les [notifications push](../../delivery/using/about-mobile-app-channel.md).
+++

## Q - T {#sec-5}

+++**Destinataire**

Dans Adobe Campaign, les destinataires sont les profils par défaut ciblés pour l’envoi de diffusions (e-mails, SMS, etc.) à votre clientèle. Les données des destinataires stockées dans la base de données vous permettent de filtrer la cible et d’ajouter des données de personnalisation. En règle générale, il s’agit d’informations personnelles, de contact, démographiques et transactionnelles, mais il peut s’agir de n’importe quel type d’informations prenant en charge le marketing et l’analyse.

En savoir plus sur les [destinataire](../../configuration/using/about-data-model.md).
+++

+++**Fonction de rendu**

*Contexte : Interaction de Campaign*

La fonction de rendu est définie dans un emplacement. Elle sert à construire son rendu de l’offre en fonction des attributs définis dans l’offre. Il existe trois modes de fonction de rendu différents : HTML, XML et texte.

En savoir plus sur la [fonction de rendu](../../interaction/using/creating-offer-spaces.md).
+++

<!--
-----DID NOT FIND IN ACC DOCS, ACS?----
+++**Retargeting campaigns**

Campaigns that re-target the recipients of a previous delivery or deliveries.
+++
-->

+++**Schéma**

Un schéma est un document XML associé à une table de la base de données, il définit la structuration des données et décrit la définition SQL de la table. Les opérateurs manipulent les schémas dans Campaign et le produit convertit leurs actions dans le code SQL requis qui est ensuite exécuté en fonction de la base de données.

En savoir plus sur les [schémas](../../configuration/using/about-schema-reference.md).
+++

+++**Extension de schéma**

L’extension de schéma vous permet de personnaliser les schémas d’usine pour mieux les adapter à vos cas d’utilisation professionnels. Par exemple, vous pouvez ajouter un nouveau champ « Fidélité » à la table des destinataires.

En savoir plus sur les [extensions de schéma](../../configuration/using/extending-a-schema.md).
+++

+++**Adresses de contrôle**

Les adresses de contrôle permettent de cibler des destinataires qui ne correspondent pas aux critères de ciblage définis. Ainsi, les destinataires qui n’entrent pas dans le cadre de la diffusion peuvent la recevoir, comme tout autre destinataire cible. Elles sont ajoutées à l’audience d’un message afin de détecter toute utilisation frauduleuse de votre base de données de destinataires ou d’assurer la diffusion.

En savoir plus sur les [adresses de contrôle](../../delivery/using/about-seed-addresses.md).
+++

<!--
-------ACS?-----
+++**Send-time optimization**

To improve the open rate of your messages, you can manually define a sending time per recipient. Each profile will receive the message at the specified date and time, whenever possible. Defining a sending time can be done at the delivery level or using a workflow.

Learn more about [Send-time optimization](../../delivery/using/about-seed-addresses.md:).
+++
-->

+++**Service**

Adobe Campaign vous permet de créer et d’administrer des services d’information tels que des newsletters ou des mises à jour de produits, ainsi que de gérer les abonnements à ces services. Plusieurs services peuvent être définis en parallèle.

En savoir plus sur les [services](../../delivery/using/about-services-and-subscriptions.md).
+++

+++**Gestion SFTP**

Dans le Panneau de contrôle, vous pouvez interagir avec tous les serveurs SFTP qui sont connectés aux instances Campaign auxquelles vous avez accès. Le panneau de contrôle vous permet d’effectuer des actions sur vos serveurs SFTP, comme surveiller la capacité de stockage, et gérer les listes autorisées d’adresses IP et les clés SSH publiques.

En savoir plus sur la [gestion des serveurs SFTP](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/about-sftp-management.html?lang=fr).
+++

+++**Activité de services d’abonnements**

Une activité de workflow des services d’inscriptions permet d’abonner ou de désabonner la population spécifiée dans la transition à un service d’information.

Pour en savoir plus sur l’activité de services d’abonnements, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/subscription-services.html?lang=fr){target="_blank"}.
+++

+++**Validation de la cible**

*Contexte : marketing distribué de Campaign*

La validation de la cible est le processus par lequel un opérateur ou un groupe d’opérateurs distinct doit approuver la cible finale d’une diffusion (après que la phase d’analyse a généré la cible) avant que la diffusion ne puisse être envoyée.

En savoir plus sur l’activité Validation de la cible dans la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/flow-control-activities/approval.html){target="_blank"}.
+++

+++**Données de la cible**

Les données de la cible sont les données stockées dans la table de travail (transition) d’un workflow. Ces données sont disponibles dans la diffusion pour la personnalisation du contenu de la diffusion ou pour définir la logique des éléments dynamiques de la diffusion.

En savoir plus sur les données de la cible dans la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/use-workflow-data.html#target-data){target="_blank"}.
+++

+++**Mapping de ciblage**

Le mapping de ciblage est le mapping des canaux de diffusion sur un type de données spécifique. Les mappings de ciblage définissent la manière dont différents canaux de diffusion se lient aux champs de données d’un schéma. Cela définit la manière dont Campaign effectue des envois vers ce type de données à l’aide d’un champ ou d’une expression spécifique.

Pour en savoir plus sur le mapping de ciblage, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/audience/add-profiles/target-mappings.html?lang=fr){target="_blank"}.
+++

+++**Activités de ciblage**

Les activités de ciblage sont des activités de workflow spécifiques au ciblage, à la manipulation des données de population et au filtrage des activités. Elles permettent aux opérateurs de construire une ou plusieurs cibles en définissant des ensembles, puis en divisant ou en combinant ces ensembles à l’aide des opérations d’intersection, d’union ou d’exclusion.

Pour en savoir plus sur les activités de ciblage, consultez la [documentation de Campaign v8]&#x200B;(https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/targeting-activities)
.html){target="_blank"}.
+++

+++**Dimension de ciblage**

La dimension de ciblage est le type de données généré (renvoyé) par une requête ou d’autres activités de workflow. Notez qu’Adobe Campaign renvoie uniquement la clé primaire des lignes de la base de données des répondants, quelle que soit la requête utilisée pour les obtenir.

En savoir plus sur la dimension de ciblage dans la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html){target="_blank"}.
+++

+++**Activité de tâche**

*Contexte : Gestion des ressources marketing (MRM)*

L’activité de workflow de tâche intègre l’action humaine à la logique d’un workflow. Vous pouvez définir deux scénarios : le premier si la tâche est terminée et le second si la tâche n’est pas terminée. Les cas d’utilisation standard servent à incorporer des actions hors ligne dans une campagne ou ciblent des actions personnalisées telles que les approbations.

Pour en savoir plus sur l’activité de tâche, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/mrm/creating-and-managing-tasks.html?lang=fr){target="_blank"}.
+++

<!--
-----NOT USEFUL, detail-----
+++**Task**

One iteration of the defined functionality of a workflow activity. Each execution of a task has a unique task identifier.   

Learn more about [Tasks](../../workflow/using/about-workflows.md).
+++
-->

+++**Modèle**

Un modèle est un élément de conception utilisé pour créer un objet. Il contient les paramètres de l’objet et, éventuellement, le contenu de l’objet. Le système de création de modèles permet de créer des diffusions, des campagnes, des workflows et de nombreux autres éléments d’Adobe Campaign. Les modèles d’usine disponibles sont définis par les packages installés. Les modèles peuvent ensuite être dupliqués et personnalisés selon les besoins des opérateurs Campaign.
+++

<!--
-----ACS -> SEEDS IN ACC-----
+++**Test profiles**

Allows targeting of additional recipients who do not match the defined targeting criteria. They are added to a message's audience to detect any fraudulent use of your recipient database or to ensure delivery. Seen as the Seed type in the Campaign interface.

Learn more about [Test profiles](../../workflow/using/about-workflows.md).
+++
-->

<!--
-----NOT FOR DOCS?-----
+++**Total database storage**

The aggregate size of the production and non-production instance(s) database storage managed by Adobe. 

Learn more about [Total database storage](../../workflow/using/about-workflows.md).
+++
-->

+++**Logs de tracking**

Le workflow technique de tracking récupère les données de tracking une fois que la diffusion a été envoyée et que le tracking a été activé. Ces données figurent dans l’onglet Tracking de votre diffusion. Vous trouverez des informations sur les ouvertures et les clics sur un e-mail ou d’autres interactions avec un message reçu par le destinataire.

En savoir plus sur les [logs de tracking](../../delivery/using/accessing-the-tracking-logs.md).
+++

+++**Messages transactionnels**

La messagerie transactionnelle est un module de Campaign conçu pour gérer les notifications de déclencheur personnalisées générées à partir d’événements envoyés par un système d’informations externe. Un message transactionnel est une communication individuelle et unique envoyée en temps réel à un utilisateur par un prestataire tel qu&#39;un site web. Il est particulièrement attendu, car il contient des informations importantes que le destinataire souhaite vérifier ou confirmer.

En savoir plus sur la [messagerie transactionnelle](../../message-center/using/about-transactional-messaging.md).
+++

&lt;!------- UTILE ICI ??----->
+++**Campagnes déclenchées**

Les campagnes déclenchées sont des campagnes exécutées lorsqu’un workflow reçoit une demande d’API. Les appels d’API sont consommés par une activité Signal dans le workflow qui lance l’exécution du workflow.

Pour en savoir plus sur les campagnes déclenchées, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/flow-control-activities/external-signal.html){target="_blank"}.
+++

<!--
-----NOT USEFUL-----
+++**Triggers**

Signals that initiate execution of a workflow, delivery or other action. Typically an API call. 

Learn more about [Triggers](../../workflow/using/about-workflows.md).
+++
-->

+++**Typologie**

*Contexte : optimisation des campagnes*

Une typologie est un groupe de règles de typologie qui sont appliquées à la phase d’analyse d’une diffusion. Une typologie de campagne peut contenir plusieurs règles de typologie, mais une diffusion ne peut référencer qu’une seule typologie.

Pour en savoir plus sur les typologies, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=fr){target="_blank"}.
+++

+++**Règle de typologie**

*Contexte : optimisation des campagnes*

Les règles de typologie sont des règles métier mises en œuvre dans le cadre de la phase d’analyse de la diffusion. Les règles de typologie sont des vérifications du contenu de la diffusion (règles de contrôle) ou la cible de la diffusion (règles de filtrage) ou toute autre logique (règles de pression) qui appliquent les exigences de l’entreprise. Les règles sont des éléments granulaires qui peuvent être inclus dans une ou plusieurs typologies.

Pour en savoir plus sur les règles de typologie, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=fr){target="_blank"}.
+++

## U - Z {#sec-6}

+++**Mode unitaire**

*Contexte : Interactions de Campaign, messagerie transactionnelle*

En mode unitaire, un seul contact est traité par le moteur d’offres au moment de l’exécution. Ce mode est généralement utilisé pour les interactions entrantes et les messages transactionnels.

En savoir plus sur le [mode unitaire](../../interaction/using/about-inbound-channels.md).
+++

+++**Applications web**

Les applications web sont des pages d’applications dynamiques et interactives hébergées par l’instance Campaign. Elles contiennent les données de la base de données et le contenu adapté aux droits de l’utilisateur connecté. Vous pouvez créer, par exemple, un formulaire d’édition sur un extranet, ou des formulaires de notification incluant des données issues de la base de données avec des tables, des graphiques, des formulaires de saisie, etc. Cette fonctionnalité permet de concevoir et de publier des pages web dans lesquelles les utilisateurs peuvent rechercher ou saisir des informations.

En savoir plus sur les [applications web](../../web/using/about-web-applications.md).
+++

+++**Workflow**

Un workflow est une représentation visuelle du flux d’exécution de la campagne. Il permet d’orchestrer l’ensemble des processus et des tâches dans les différents modules du serveur d’applications. Cet environnement graphique complet permet de concevoir des processus englobant segmentation, exécution de campagnes, traitement de fichiers, participation humaine, etc. Le moteur de workflow exécute et suit ces processus.

En savoir plus sur les [workflows](../../workflow/using/about-workflows.md).
+++

+++**Journal des workflows**

Le journal des workflows est le log d’exécution étape par étape d’un workflow. Il contient tout l’historique ou le journal d’audit du workflow. Il est utilisé à des fins de développement, de dépannage ou de débogage.

En savoir plus sur le journal des workflows dans la [documentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=fr){target="_blank"}.
+++

+++**Table de travail**

La table de travail contient toutes les informations transportées par les transitions de workflow. Chaque workflow utilise plusieurs tables de travail. La table de travail contient les résultats de son activité d’origine et son contenu est utilisé comme entrée de l’activité suivante (connectée) du workflow.  La manipulation (extension, personnalisation) de la table de travail est l’une des principales compétences d’un opérateur Adobe Campaign.

En savoir plus sur les [tables de travail](../../workflow/using/about-workflows.md).
+++
