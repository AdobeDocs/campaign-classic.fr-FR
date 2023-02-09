---
product: campaign
title: Recommandations relatives au dimensionnement du matériel pour Campaign Classic v7
description: Recommandations relatives au dimensionnement du matériel pour Campaign Classic v7
exl-id: c47e73a0-dbd8-43f5-a363-7e6783dc7685
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '2512'
ht-degree: 100%

---

# Recommandations relatives au dimensionnement du matériel{#hardware-sizing-reco}

![](../../assets/v7-only.svg)

## Vue d’ensemble

>[!CAUTION]
>
>Cet article est uniquement fourni à titre de guide illustratif général. Vous devez contacter votre gestionnaire du succès client Adobe Campaign afin d’obtenir le dimensionnement exact dont vous avez besoin pour votre déploiement avant de démarrer un projet Campaign. N’acquérez et ne déployez **pas** de matériel ni d’infrastructure tant que cela n’est pas fait.

Ce document fournit des recommandations générales relatives au déploiement d’Adobe Campaign Classic v7 dans votre centre de données On-premise ou votre environnement cloud virtualisé. Ce type de déploiement, dit **hybride** ou de **mid-sourcing**, place l’instance marketing et la base de données marketing de Campaign sous votre contrôle opérationnel. Dans le même temps, les services Adobe Cloud Messaging sont utilisés pour envoyer des e-mails, des SMS ou des messages SMPP, et collecter les données d’ouverture d’e-mail, de bounce et de suivi des clics.

L’instance marketing est la partie de l’architecture Adobe Campaign qui stimule toute l’activité marketing. C’est également celle qui stocke toutes les données des destinataires et les données d’analyse renvoyées par les campagnes. L’instance marketing est un ensemble de serveurs On-premise exécutant les services Adobe Campaign et une base de données relationnelle.

>[!CAUTION]
>
>Les informations contenues dans ce document ne s’appliquent pas si vous utilisez une instance Adobe Campaign entièrement hébergée (déployée dans les services cloud d’Adobe).

La compatibilité logicielle est décrite en détail dans le document relatif à la [Matrice de compatibilité](../../rn/using/compatibility-matrix.md).


### Scénarios

Les diagrammes de déploiement et les recommandations relatives au dimensionnement du matériel sont fournis pour trois scénarios représentatifs :

1. [Taille moyenne](#scenario-1) : 5 millions de destinataires actifs dans le système.
1. [Grande taille](#scenario-2) : 20 millions de destinataires actifs dans le système.
1. [Entreprise](#scenario-3) : 50 millions de destinataires actifs, avec messagerie transactionnelle.

### Hypothèses

Ce document suppose également que les trois scénarios ont recours aux types d’utilisation suivants :

* Des campagnes par e-mail volumineuses sont envoyées deux fois par semaine à environ 50 % de vos destinataires actifs.
* Le publipostage est généré une fois par mois pour chaque destinataire du système.
* Des SMS sont envoyés à environ 10 % de vos destinataires actifs chaque mois.
* Le schéma de la base de données qui définit chaque destinataire a été étendu avec une table supplémentaire, laquelle contient environ 200 octets de données relatives à chaque destinataire.
* Le module Interaction d’Adobe Campaign est utilisé pour ajouter des offres aux e-mails sortants.
* Les données de tracking e-mail sont conservées pendant 90 jours dans le système de Campaign.

## Directives générales

Campaign est une application centrée sur la base de données. Les performances du serveur de la base de données sont donc essentielles. L’exécution de workflows, la segmentation, les téléchargements de données de tracking, les interactions entrantes, les analyses et d’autres activités génèrent de l’activité sur la base de données. En règle générale, la taille et la fréquence de ces opérations déterminent la taille des serveurs de votre base de données.

Les serveurs d’application de votre instance marketing nécessitent suffisamment de capacité au niveau du processeur et de la mémoire pour exécuter des workflows et répondre aux appels d’API SOAP, y compris les requêtes des utilisateurs de la console Campaign. La configuration requise pour le processeur peut être significative pour les workflows qui utilisent des interactions sortantes avec des règles d’offre complexes, les workflows qui exécutent du code JavaScript personnalisé et les applications web avec des niveaux de trafic élevés.

Les applications web de Campaign peuvent également être déployées sur les serveurs d’applications de l’instance marketing ou sur des systèmes de serveurs web distincts. Les charges de travail des applications web étant en conflit avec les workflows importants et les utilisateurs de la console Campaign, il est possible de déployer ces applications web et les interactions entrantes sur des serveurs distincts afin de garantir un fonctionnement fiable et optimal des fonctionnalités de base de Campaign.

Pour des raisons de sécurité et de disponibilité, Adobe recommande de séparer le trafic Internet du trafic généré par les utilisateurs professionnels. Pour cette raison, les diagrammes contiennent deux groupes de serveurs : le serveur web (Web1 et Web2 avec accès via Internet) et les serveurs d’applications (App1 et App2 avec processus d’entreprise).

Les expéditeurs d’e-mails commerciaux ont l’obligation légale de disposer d’une page web d&#39;opt-out fonctionnelle. Adobe recommande de disposer d’une machine redondante dans chacun des serveurs de ces groupes pour les scénarios de basculement. C’est d’autant plus vrai si Adobe Campaign héberge les pages d&#39;opt-out.

### Serveurs proxy inverses

L’architecture de Campaign applique un niveau de sécurité élevé en utilisant le protocole SSL par-dessus HTTP (HTTPS) pour communiquer entre votre instance marketing et Adobe Cloud Messaging. La sécurité, la fiabilité et la disponibilité sont renforcées par l’utilisation de serveurs proxy inverses dans un sous-réseau de « zone démilitarisée » (DMZ) afin d’isoler et de sécuriser la base de données et les serveurs d’instances marketing.

### Répartition de charge

La répartition de charge des serveurs d’applications est définie dans une configuration active/passive, avec terminaison HTTPS au niveau du proxy. La répartition de charge des serveurs web est définie dans une configuration active/active, avec terminaison HTTPS au niveau du proxy.

Adobe fournit la liste exclusive des chemins d’URL qui peuvent être relayés au serveur Adobe Campaign dans votre environnement de déploiement.

### Architecture

L’architecture générale est presque identique, quels que soient les volumes. Les exigences de sécurité et de haute disponibilité imposent un minimum de quatre serveurs. Ce chiffre retombe à deux serveurs si aucune WebApp n’est utilisée. Les variations de configuration se situent principalement au niveau du matériel, comme le cœur du processeur et la mémoire.

## Scénario 1 : Déploiement de taille moyenne{#scenario-1}

![](assets/scenario-1.png)

Volume estimé :

| Canal | Volume |
| ----------------------- | ----------------- |
| Destinataires actifs | 5 millions |
| E-mail | 4,2 millions/mois |
| Publipostage direct | 1 million/mois |
| SMS mobile | 100 000/mois |
| Pic du volume d’e-mails quotidien | 500 |

Pour ces volumes, une paire de systèmes de serveurs d’application Adobe Campaign fournit toutes les fonctionnalités pour les utilisateurs du client Adobe Campaign et l’exécution des workflows. Pour 5 millions de destinataires actifs et ce volume d’e-mail, les charges de travail du serveur d’application n’utilisent pas beaucoup les capacités du processeur ou de l’E/S. La pression s’exerce surtout sur la base de données.

Les serveurs web d’Adobe Campaign s’affichent dans la zone sécurisée.

### Serveurs web et d’application

Ce scénario recommande d’installer Adobe Campaign sur quatre machines, avec la spécification suivante :

**Processeur 3 Ghz+ quadruple cœur, 8 Go de RAM, RAID 1 ou 10, 2 x SSD de 80 Go**

Ces systèmes créent le serveur d’application de l’instance marketing, qui prend directement en charge les utilisateurs de votre console Campaign et exécute les workflows de campagne.

Configurez des proxys inverses dans le trafic de répartition de charge DMZ vers les serveurs web Adobe Campaign. Il n’est pas nécessaire d’installer la pile logicielle Adobe Campaign sur des ordinateurs proxy. Tout logiciel ou équipement réseau de proxy inverse peut être utilisé.

Les fonctionnalités de centre de préférences et d’opt-in/opt-out d’un abonnement peuvent être fournies par Campaign ou par votre propre site web. Si vous choisissez d’implémenter cette fonctionnalité sur votre site web, vous devez vous assurer que les informations de préférence et d’abonnement sont propagées à la base de données marketing de Campaign. Cela s’effectue généralement à travers la création de fichiers d’extraction qui sont automatiquement chargés par les workflows de Campaign.

La consommation d’espace disque sur les serveurs d’application dépend de la période de rétention des fichiers échangés avec les fournisseurs de services tiers (par exemple, les fournisseurs de services d’impression pour le publipostage direct). Cela dépend également de la taille et de la rétention des fichiers plats importés, comme les mises à jour d’abonnement ou de préférences de votre site web, ou des extraits de vos propres systèmes marketing ou CRM.

### Base de données

Les recommandations matérielles pour le serveur de la base de données sont les suivantes :

**Processeur 3 Ghz+ à 4 cœurs, 16 Go de RAM, RAID 1 ou 10, SSD de 128 Go au minimum**

L’estimation de la mémoire suppose une mise en cache complète d’environ 500 000 destinataires pour un lancement de campagne volumineuse, ainsi qu’un espace de mémoire tampon SGBD pour l’exécution des workflows, l’importation des données de tracking et d’autres activités simultanées.

L’espace disque requis dans la base de données pour stocker toutes les données techniques d’Adobe Campaign (campagnes, tracking, tables de travail, etc.) est estimé à environ 35 Go pour une période de rétention de trois mois. Si vous choisissez de conserver les données de tracking pendant 6 mois, la taille de la base de données passe à environ 40 Go. Cette taille passe à environ 45 Go dans le cas d’une rétention de 12 mois. Les données des destinataires consomment environ 5 Go pour cet environnement.

>[!CAUTION]
>
>Cette estimation n’inclut aucune donnée client additionnelle. Si vous prévoyez de répliquer des colonnes ou des tables de données client additionnelles dans la base de données d’Adobe Campaign, vous devez estimer l’espace disque supplémentaire requis pour cette opération. Les segments/listes téléchargés nécessitent également davantage d’espace de stockage en fonction de leur taille, fréquence et période de rétention.

En raison du volume d’informations traitées quotidiennement, l’évaluation IOPS du serveur de la base de données est essentielle. Par exemple, un jour de pic, vous pouvez déployer des campagnes ciblant 500 000 destinataires au total. Pour exécuter chaque opération, Adobe Campaign insère 500 000 enregistrements dans une table qui en contient environ 12 millions (la table des logs de diffusion). Pour offrir des performances acceptables lors du déploiement de la campagne, Adobe recommande un minimum de 60 000 IOPS en lecture/écriture aléatoire de 4 Ko pour ce scénario.


## Scénario 2 : Déploiement de grande taille{#scenario-2}

![](assets/scenario-2.png)

Volume estimé :

| Canal | Volume |
| ----------------------- | ----------------- |
| Destinataires actifs | 20 millions |
| E-mail | 42 millions/mois |
| Publipostage direct | 10 millions/mois |
| SMS mobile | 1 000 000/mois |
| Pic du volume d’e-mails quotidien | 5 000 000 |

### Serveurs web et d’application

Dans ce scénario, Adobe recommande d’installer Adobe Campaign sur quatre machines, deux serveurs d’application et deux serveurs Web, avec la spécification suivante :

**3 Ghz+ quatre cœurs, 8 Go de RAM, RAID 1 ou 10, SSD 80 Go**

Les serveurs d’application prennent directement en charge les utilisateurs de la console Campaign et l’exécution des workflows de campagne. Cette fonctionnalité est déployée sur deux serveurs identiques pour permettre une haute disponibilité ; ils partagent un système de fichiers NAS (Network-Attached Storage) pour activer le basculement.

Les serveurs Web hébergent des applications Web Campaign qui prennent en charge les 10 millions de destinataires actifs du système.

Voir [Scénario 1 : Déploiement de taille moyenne ](#scenario-1) pour plus de commentaires sur les proxies, les centres de préférences/la gestion des abonnements et l’utilisation de l’espace disque.

### Base de données

Les recommandations matérielles pour le serveur de la base de données sont les suivantes :

**3Ghz+ 8 cœurs, 64 Go de RAM, RAID 1 ou 10, SSD 2 x 320 Go ou RAID 10, SSD 640 Go minimum**

L’estimation de la mémoire suppose une mise en cache complète d’environ 5 000 000 de destinataires pour un lancement de campagne volumineux, ainsi qu’un espace mémoire tampon RDBMS pour l’exécution des workflows, l’importation de données de suivi et d’autres activités simultanées.

On estime que l’espace disque requis dans la base de données pour stocker l’ensemble des données techniques Adobe Campaign (campagnes, suivi, tables de travail, etc.) est d’environ 280 Go sur la base d’une période de conservation de 3 mois. Si vous choisissez de conserver les données de suivi pendant 6 mois, la taille de la base de données passe à environ 450 Go et une rétention de 12 mois nécessite environ 900 Go. Les données des destinataires consomment environ 15 Go pour cet environnement.

## Scénario 3 : Déploiement Entreprise avec Message Center{#scenario-3}

![](assets/scenario-3.png)

Volume estimé :

| Canal | Volume |
| ----------------------- | ----------------- |
| Destinataires actifs | 50 millions |
| E-mail | 108 millions/mois |
| Publipostage direct | 25 millions/mois |
| SMS mobile | 2,5 millions/mois |
| Messages transactionnels | 2,5 millions/mois |
| Pic du volume d’e-mails quotidien | 2,5 millions  |


Le déploiement qui prend en charge 50 millions de destinataires est essentiellement le même que dans le [Scénario 2](#scenario-2) : le trafic des applications Web de Campaign est acheminé vers les serveurs Web de Campaign. De ce fait, les rafales de trafic Web après les lancements de campagnes volumineuses n’ont aucune incidence sur les workflows de Campaign et les utilisateurs de la console cliente.

Ce déploiement comprend également des appels Message Center, pilotés à partir de vos propres sites Web et applications.


### Serveurs web et d’application

Dans ce scénario, Adobe recommande d’installer Adobe Campaign sur quatre machines, comme suit :

* Serveurs d’application
   **Deux systèmes, 3Ghz+ quatre cœurs, 8 Go de RAM, RAID 1 ou 10, SSD de 80 Go**

* Serveurs Web
   **Deux systèmes, 3Ghz+ quatre cœurs, 16 Go de RAM, RAID 1 ou 10, SSD de 80 Go**


Les serveurs d’application prennent directement en charge les utilisateurs de la console Campaign et l’exécution des workflows de campagne. Cette fonctionnalité est déployée sur deux serveurs identiques pour permettre une haute disponibilité ; ils partagent un système de fichiers NAS (Network-Attached Storage) pour activer le basculement.

Les serveurs Web hébergent des applications Web Campaign qui prennent en charge les 10 millions de destinataires actifs du système.

Voir [Scénario 1 : Déploiement de taille moyenne ](#scenario-1) pour plus de commentaires sur les proxies, les centres de préférences/la gestion des abonnements et l’utilisation de l’espace disque.

### Base de données

Les recommandations matérielles pour le serveur de la base de données sont les suivantes :

**Processeur 3 Ghz+ à 8 cœurs, 96 Go de RAM, RAID 1 ou 10, SSD de 1,5 To minimum**

L’estimation de la mémoire suppose une mise en cache complète d’environ 12 500 000 destinataires pour un lancement de campagne volumineuse, ainsi qu’un espace de mémoire tampon SGBD pour l’exécution des workflows, l’importation des données de tracking et d’autres activités simultanées.

L’espace disque requis dans la base de données pour stocker toutes les données techniques d’Adobe Campaign (campagnes, tracking, tables de travail, etc.) est estimé à environ 700 Go pour une période de rétention de 3 mois. Si vous choisissez de conserver les données de tracking pendant 6 mois, la taille de la base de données passe à environ 1,2 To. Cette taille passe à environ 2 To dans le cas d’une rétention de 12 mois. Les données des destinataires consomment environ 50 Go pour cet environnement.

## Directives relatives à la modification des hypothèses

Les hypothèses faites pour ces scénarios ont toutes un impact significatif sur les recommandations matérielles et l’architecture de déploiement. Cette section décrit les directives relatives aux différentes hypothèses. Contactez l’équipe de consultants d’Adobe Campaign pour obtenir des recommandations spécifiques à vos besoins.

* **Nombre de destinataires**
Les destinataires actifs requièrent à la fois un espace de stockage et un espace de mémoire tampon dans la base de données. De ce fait, un nombre plus élevé de destinataires nécessite généralement davantage de capacité au niveau de la mémoire et du processeur sur le serveur de base de données. Les augmentations du stockage sont relativement faibles pour les destinataires eux-mêmes, mais peuvent être significatives pour les données de tracking d’événements conservées pour les campagnes e-mail.

* **Taille de la campagne par e-mail**
La fréquence des lancements de campagne a un impact sur la configuration requise pour le processeur du serveur de base de données. Associées au publipostage direct, aux interactions entrantes et aux autres workflows, les opérations de segmentation des campagnes par e-mail placent une charge importante sur le serveur de base de données.

* **Fréquence de publipostage direct**
La fréquence du publipostage peut avoir une incidence sur la configuration requise pour le processeur du serveur de base de données. Associées aux lancements de campagne et aux autres workflows, les opérations de segmentation de publipostage direct placent une charge importante sur le serveur de base de données.

* **Volume des messages SMS**
Comme pour la taille des campagnes par e-mail, le volume des messages SMS ne place pas de charge importante sur les serveurs Campaign On-premise. La charge est principalement sur les serveurs Adobe Cloud Messaging sur le cloud. Comme pour les e-mails et le publipostage direct, la segmentation des campagnes par SMS peut placer une charge importante sur la base de données marketing. Par conséquent, la fréquence des lancements de campagnes par SMS et la complexité de la segmentation sont plus pertinentes que le volume des messages SMS.

* **Complexité du schéma de la base de données**
La quantité de données relatives à chaque destinataire actif requiert à la fois de l’espace de stockage et de l’espace de mémoire tampon dans la base de données. Par conséquent, un nombre plus élevé de destinataires nécessite généralement davantage de capacité au niveau de la mémoire et du processeur sur le serveur de base de données. Les schémas complexes nécessitent également la jonction de davantage de tables pour la segmentation. De ce fait, les opérations de segmentation peuvent s’exécuter beaucoup plus lentement et nécessiter davantage de capacité au niveau du processeur et de la mémoire dans la base de données lorsque les données sont réparties entre plusieurs tables.

   La mémoire du serveur de la base de données est estimée en veillant à ce que le pool de mémoire tampon de la base de données puisse contenir toutes les données des destinataires, ainsi que des tables temporaires pour exécuter les workflows, avec une marge supplémentaire pour les autres opérations de base de données.

* **Utilisation des interactions sortantes**
Les règles relatives aux interactions en mode batch sont évaluées dans les workflows qui transmettent toute la complexité du calcul à la base de données. Le principal facteur d’effort sur la base de données est le nombre total d’offres éligibles calculées lors d’un appel au moteur (taille de la cible X nombre moyen d’offres par destinataire avant de conserver les N meilleures offres). La vitesse du processeur du serveur de la base de données est le premier facteur de performance.

* **Utilisation de l’API SOAP ou des interactions entrantes**
Les règles et offres d’interactions entrantes sont évaluées dans la base de données marketing, ce qui nécessite d’importantes ressources de serveur de base de données, notamment au niveau du processeur. L’utilisation intensive des interactions entrantes ou des API SOAP nécessite des serveurs web distincts pour séparer la charge de travail des workflows Campaign en cours d’exécution.

* **Période de rétention des données de tracking**
L’augmentation de la rétention des données de tracking au-delà de 90 jours nécessite davantage de stockage dans la base de données. En outre, cela peut ralentir le système car les nouvelles données de tracking sont insérées dans des tables volumineuses. Les données de tracking ne sont plus utiles pour la segmentation des campagnes au-delà de 90 jours. Il est donc recommandé d’utiliser une période de rétention plus courte.

   Si vous avez besoin d’une analyse à long terme de l’expérience marketing des destinataires, il vous faut déplacer les données de tracking dans Adobe Analytics ou dans un autre système d’analyse.

## Virtualisation

Tous les serveurs Campaign sont de bons candidats à la virtualisation. Plusieurs problèmes doivent être résolus pour garantir une disponibilité adéquate et optimiser les performances.

* **Configuration de basculement**
Les serveurs en cluster, comme les serveurs d’application redondants sous un proxy avec équilibrage de charge, doivent être déployés sur un matériel distinct pour s’assurer que les deux machines virtuelles ne tombent pas en panne en cas de défaillance matérielle.

* **Configuration d’E/S**
Toute configuration RAID recommandée doit être conservée pour la sécurité de la base de données, afin de garantir que la perte d’un périphérique de stockage ne provoque pas de perte de données.

* **Performances d’E/S**
L’évaluation IOPS recommandée pour le stockage dans la base de données doit être respectée. Il est possible que les services cloud tels qu’Amazon EC2 n’offrent pas les performances requises. Ces services doivent alors être évalués avec soin. Par exemple, les volumes SSD fournis par Amazon EC2 sont actuellement évalués à 20 000 IOPS chacun. Consultez la [documentation Amazon](https://docs.aws.amazon.com/fr_fr/AWSEC2/latest/UserGuide/ebs-volume-types.html) pour en savoir plus. De ce fait, une configuration RAID à 4 volumes est évaluée à 80 000 IOPS, ce qui peut ne pas suffire.

Adobe recommande de tester les performances de chaque déploiement virtualisé d’Adobe Campaign avant la mise en production du système.

## Rubriques connexes

* [Processus de surveillance des campagnes](../../production/using/monitoring-processes.md)
* [Architecture générale de Campaign](../../installation/using/general-architecture.md)
* [Problèmes de performances et de débit](../../production/using/performance-and-throughput-issues.md)
* [Liste de contrôle relative à la sécurité et à la confidentialité](../../installation/using/get-started-security-privacy.md)
