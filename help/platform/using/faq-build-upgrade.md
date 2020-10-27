---
title: FAQ sur l’upgrade de build
description: Questions courantes relatives aux mises à niveau de la version Campaign
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
translation-type: tm+mt
source-git-commit: cb96a238f4c8e413377ce6102b065b91badfe6db
workflow-type: tm+mt
source-wordcount: '2023'
ht-degree: 8%

---


# Build Upgrade FAQ {#build-upgrade-faq}

Adobe Campaign fait l&#39;objet de mises à jour régulières. If you are familiar with our published [Release Notes](../../rn/using/rn-overview.md), you are probably aware of the fact that on the average 2/3 minor versions packed with new features, improvements and fixes are released every year. En outre, nous publions périodiquement des builds avec des correctifs cumulatifs uniquement. Cette cadence régulière de mises à jour vise à obtenir les dernières et les meilleures mises à votre disposition, à garder votre environnement en sécurité et à améliorer votre expérience avec notre produit.

Il est essentiel que nos clients exécutent la version la plus récente d&#39;Adobe Campaign. Il permet également à l&#39;Adobe d&#39;aider beaucoup plus efficacement en cas de problèmes - identifier, reproduire et résoudre un problème sur une ancienne version prend généralement plus de temps, sans parler du fait que certains problèmes que vous pourriez rencontrer ont peut-être déjà été résolus dans une version récente.

Nous avons donc lancé le programme [Gold Standard](https://helpx.adobe.com/fr/campaign/kb/gold-standard.html) pour travailler en collaboration avec nos clients afin de mettre à jour leurs environnements de façon proactive et régulière.

## Qu&#39;est-ce qu&#39;une mise à niveau de version ?

Une mise à niveau de build est une mise à jour du logiciel Adobe Campaign Classic vers le dernier numéro de build sécurisé, tout en restant dans le même niveau de build principal/secondaire. Par exemple : Campagne Classic v7 build 9026 vers Campaign v7 build 9032.

En savoir plus [dans cette section](../../rn/using/rn-overview.md).

## Quelle est la dernière version de Adobe Campaign Classic ?

La dernière version du Campaign Classic, y compris les nouvelles fonctionnalités et la documentation, est détaillée dans les dernières Notes [de](../../rn/using/latest-release.md)mise à jour.

## Comment puis-je savoir quelle version j’exécute ?

Consultez votre version dans le menu **[!UICONTROL Aide > A propos de...]** de la console du client Adobe Campaign. La zone **[!UICONTROL À propos]** contient des informations détaillées sur la version et la version que vous exécutez à la fois pour la console et le serveur.

En savoir plus [dans cette section](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Que signifie le statut de build ?

Depuis Campaign Classic 19.2, un statut est associé à chaque build.

En savoir plus [dans cette section](../../rn/using/rn-overview.md).

## Est-ce qu&#39;une mise à niveau de version est identique à une mise à niveau de version ?

Non. Une mise à niveau de build est une mise à jour incrémentielle au sein d&#39;une version majeure donnée, alors qu&#39;une mise à niveau de version est un changement d&#39;une version majeure à une autre. Les mises à niveau des bâtiments sont simples, car elles n&#39;impliquent généralement pas de modifications majeures d&#39;architecture, de technique ou de modèle de données.

Les mises à niveau de version comportent généralement des modifications techniques importantes et, selon la profondeur de la configuration pour un client donné, peuvent nécessiter des modifications importantes de la configuration et/ou une réimplémentation partielle.

Par exemple, à l’aide des informations du serveur de la capture d’écran de la section précédente :

* Une mise à niveau de build impliquerait de passer de la version 6880 à toute version supérieure à 6880. Par exemple, v6.1.1 crée 8222 en v6.1.1 crée 8666

* Une mise à niveau de version impliquerait de passer de la version 6.0.2 à toute version supérieure à 6.0.2. Par exemple : v6.0.1 build 222 à v6.1.1 build 8666

## Dois-je sauvegarder mes données avant ces mises à jour ?

Adobe effectuera une sauvegarde de votre système avant toute modification. Cependant, si un travail de personnalisation essentiel se trouve dans votre système de non-production (serveurs de développement ou d’évaluation), il est HAUTEMENT RECOMMANDÉ que vous exportiez ce travail en tant que package avant toute mise à niveau.

Pour plus d&#39;informations, [regardez cette vidéo](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).

## Quand les mises à niveau auront-elles lieu ?

Les clients se verront proposer une plage de dates parmi lesquelles choisir. Les modifications du système de production ne sont pas effectuées en période de vacances.

Les mises à niveau de la compilation peuvent être effectuées du lundi au jeudi et les vendredis ne sont utilisés que pour les instances autres que les instances de production.

## Combien de temps durera la mise à niveau de la version ?

Le temps nécessaire à la mise à niveau d&#39;une version dépend de plusieurs facteurs :

* Taille de la base de données à sauvegarder ou à restaurer (les bases de données plus volumineuses nécessitent plus de temps pour être mises à niveau)
* La taille des environnements (beaucoup de nos clients ont plusieurs serveurs différents qui gèrent chacun des fonctions spécifiques, avec des environnements plus volumineux nécessitant plus de temps pour la mise à niveau)
* La complexité du système (certains systèmes ont des services et des connexions plus dépendants à vérifier, ce qui nécessite une vérification de la stabilité et des performances de ces systèmes)

La mise à niveau de la version est un processus en deux étapes :

1. Préparation du système pour la mise à niveau - En tenant compte des spécificités de votre environnement, cette phase conduit essentiellement à une mise à niveau complète sur un environnement hors production. Une fois que l&#39;environnement modernisé a été mis en évidence d&#39;un point de vue technique et fonctionnel, la phase 2 peut se produire. Cette première phase, en fonction des facteurs susmentionnés, peut prendre de quelques jours à quelques semaines.

1. La mise à niveau elle-même : l’environnement de production est mis à niveau. Cette phase est généralement effectuée en quelques heures. Pour les environnements très complexes, il faut s&#39;attendre à une interruption plus longue. Dans le événement où quelque chose ne va pas, une stratégie de restauration est définie et peut être exécutée.

For more information, [refer to this document](https://helpx.adobe.com/fr/campaign/kb/acc-build-upgrade.html).

## Quelles ressources sont nécessaires pour la mise à niveau de la version ?

L&#39;upgrade de build requiert les ressources suivantes :

* Architecte d&#39;Adobe - Pour les architectures hébergées ou de messagerie cloud/hybrides, l&#39;architecte doit coordonner ses travaux avec le service d&#39;assistance clientèle.
* Gestionnaire de projets - Hébergé : l’équipe d’hébergement collabore avec l’équipe d’assistance clientèle et le client pour coordonner le calendrier de mise à niveau pour toutes les instances.
* Administrateur Adobe Campaign - Hébergé : l’équipe d’hébergement effectue la mise à niveau.
* Opérateur Adobe Campaign\utilisateur marketing : l’opérateur exécute des tests sur les instances de développement, de test et de production.

## Comment puis-je me préparer à la mise à niveau de la version ?

Dans vos systèmes de développement et d’évaluation, exportez tout travail essentiel et à conserver. Pour plus d&#39;informations, [regardez cette vidéo](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).

Actualisez vos connaissances sur les workflows et diffusions de cheminement critiques développés dans vos cahiers d&#39;exercices (ou par votre équipe de consultants/partenaire) en examinant la documentation fournie à votre équipe à la fin de votre mise en oeuvre.

Identifiez les périodes de faible volume ou de faible trafic qui seraient idéales pour les fenêtres de maintenance car elles produiront le plus faible impact commercial.

Consultez la liste de contrôle de mise à niveau [de la version ci-dessous](#check-list) et vos plans de test et assurez-vous que les ressources disponibles pour effectuer ces tests sont disponibles dans les 24 à 48 heures. de l’achèvement d’une mise à niveau.

For more information, [refer to this document](https://helpx.adobe.com/fr/campaign/kb/acc-build-upgrade.html).

## Peut-on effectuer des mises à niveau la nuit ou pendant les heures de bureau ?

Les mises à niveau peuvent être effectuées en dehors des heures d&#39;ouverture. Il est toujours recommandé de mettre à niveau l’environnement pendant les heures creuses lorsque les utilisateurs professionnels ne sont pas connectés à l’instance.

## Quels sont les coûts associés à une mise à niveau de version ?

L’installation de la mise à niveau de build pour les clients hébergés n’entraîne aucun coût. S’il existe des développements personnalisés dans le système, le client devra identifier les ressources nécessaires pour tester ces développements après la mise à niveau et pour corriger les problèmes rencontrés avec ces développements personnalisés.

## L&#39;instance est-elle accessible pendant l&#39;upgrade ?

Non. Le serveur est arrêté lors d’une mise à niveau afin de s’assurer que l’intégrité des données est préservée pendant la mise à niveau du produit. Une fois terminé, il est redémarré et tous les services reprennent.

## Les courriels continueront-ils à être envoyés depuis Message Center pendant le processus de mise à niveau ?

Lorsque la mise à niveau a lieu pour Message Center (RT), elle n&#39;envoie pas de messages électroniques à partir de l&#39;instance. Notez que tout processus arrêté lors de l’arrêt d’un système Campaign est automatiquement relancé lors du redémarrage du système. Cela inclut les calculs de diffusions principales ou planifiées, de suivi et de mesures pour les diffusions précédemment envoyées.

## Les workflows continueront-ils à s&#39;exécuter et à envoyer les diffusions ?

Non. Lors de la mise à niveau de la build, les services de workflow et de messagerie sont arrêtés. Cela signifie que les workflows ne s’exécuteront pas et que les diffusions ne seront pas envoyées. Ils reprennent une fois le système redémarré. Cependant, l’Adobe conseille vivement que tous les workflows de chemin critiques soient vérifiés après une mise à niveau afin de s’assurer qu’ils sont en cours d’exécution et en bonne santé.

## Mes liens de tracking fonctionnent-ils toujours pendant l&#39;upgrade ?

Le suivi des liens fonctionnera pendant la mise à niveau. Il ne sera pas possible d’envoyer de nouveaux emails pendant la mise à niveau, mais les liens de tracking inclus dans les messages déjà envoyés seront opérationnels.

## Dois-je être disponible pendant le processus de mise à niveau de la version ?

Oui. Les clients doivent fournir à l’Adobe un point de contact disponible pendant ou immédiatement après la mise à niveau de leur instance de production.  L&#39;Adobe communiquera avec cette personne par courriel à moins que d&#39;autres dispositions ne soient prises. Cela garantira une transition en douceur et une validation immédiate des tâches critiques. L’Adobe contactera le client une fois la mise à niveau de la version terminée pour confirmation.

## Dois-je mettre à jour la console client ?

Oui. La console cliente doit se trouver sur la même version ou sur une version plus récente que l’instance du serveur. Une fois la mise à niveau terminée, votre console client doit vous inviter à effectuer la mise à niveau vers la dernière version afin de vous assurer qu’elle reste alignée sur la version du serveur.

## Quel est le plan de restauration ? Les sauvegardes de mes données sont-elles conservées ?

Le plan de restauration consiste à restaurer le système avec la dernière sauvegarde disponible. Les sauvegardes sont stockées pendant 7 jours pour les clients du centre de données et pendant 14 jours pour les clients du service Web Amazon (AWS).

## Quelle est la durée de la restauration ?

Cela dépend de la taille de sauvegarde de la base de données. Le temps moyen nécessaire est de 4 heures.

## Quels types de tests sont effectués sur mon système après la mise à niveau ?

Reportez-vous à la liste de contrôle [de mise à niveau de build ci-dessous](#check-list).

## Quel type de test dois-je effectuer après ma mise à niveau ?

Les environnements de développement et d’étape sont mis à niveau de manière séquentielle ou ensemble, mais une approbation est nécessaire avant la mise à niveau de l’instance de production. Cela permet à chaque client d&#39;effectuer des tests approfondis avant de se déconnecter de toute modification apportée à la production.

Reportez-vous à la liste de contrôle de mise à niveau de la [version de liste ci-dessous](#check-list). Les clients doivent exécuter des tests similaires ainsi que d’autres tests dont ils peuvent avoir besoin pour l’environnement.

## À quelle fréquence dois-je effectuer une mise à niveau de build ?

Afin d&#39;assurer des performances optimales, la disponibilité et la sécurité du système, l&#39;Adobe s&#39;associera avec les clients pour s&#39;assurer que les systèmes sont mis à niveau au moins une fois par an.

## Y aura-t-il une fermeture pour une mise à niveau de build ?

Oui. Le serveur est arrêté lors d’une mise à niveau afin de s’assurer que l’intégrité des données est préservée pendant la mise à niveau du produit. Une fois terminé, il est redémarré et tous les services reprennent.

## Qui dois-je contacter pour ouvrir le ticket de mise à niveau vers la version ?

Si vous rencontrez des problèmes après une mise à niveau de build, contactez le service à la clientèle [de l’](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)Adobe. Le service à la clientèle planifie les dates de création et ouvre les tickets de mise à niveau de build.

En savoir plus sur les options [d&#39;aide et de support pour les Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)

## Créer une liste de contrôle de mise à niveau {#check-list}

### Liste de contrôle post-mise à niveau du serveur Cloud Messaging

1. Envoyer une diffusion de test
   1. Validation des logs de diffusion et du processus associé
   1. Valider les logs de tracking mis à jour
   1. Validation des liens de page miroir et de suivi
1. Confirmer que tous les workflows techniques sont à l&#39;état démarré
1. Vérifier que tous les processus sont également principaux

### Liste de contrôle de post-mise à niveau du serveur marketing

* Pouvez-vous vous connecter au serveur ? Vérifiez que la console client Campaign fonctionne sans fenêtres contextuelles d’erreur/d’avertissement.
* Veillez à utiliser la même version de console que celle de la version de création après la mise à niveau.
* Avez-vous des applications Web qui insèrent des données dans la base de données Campaign ? Si tel est le cas, exécutez-les et vérifiez qu’ils peuvent insérer de nouveaux enregistrements via l’API.
* Pouvez-vous envoyer un message électronique de test avec succès ? Créez une nouvelle diffusion à l’aide d’un modèle connu, envoyez-la à un destinataire de test, vérifiez la personnalisation, supprimez le lien, page miroir tout le travail.
* Tous vos workflows de chemin critiques sont-ils en cours d&#39;exécution ? Vérifiez les workflows, ouvrez le journal de processus, vérifiez qu’il n’y a pas d’erreurs.
* Tous vos dossiers sont-ils présents, visibles et accessibles ? Parcourez les différents dossiers et cochez-les.
tout le contenu est affiché et présent.
* Vos diffusions arrivent-elles avec le bon fuseau horaire ?

   * Vérifiez la date de création et la date de modification avec l’horodatage et le fuseau horaire.
   * Vérifier que l&#39;exécution du Planificateur fonctionne dans un workflow à l&#39;heure spécifiée
   * Récupère la liste des workflows en état PAUSED et FAILED. Début et surveillance
   * Exécution de tests AB pour un scénario
   * Tester les notifications Push avec leur fonctionnalité de suivi pour les liens profonds
   * Test d&#39;envoi de SMS
   * Si une FDA externe est connectée, testez si les données sont envoyées dans les deux sens.
   * Si vous utilisez des intégrations telles que Adobe Campaign-Adobe Experience Manager, Adobe Campaign-Adobe Analytics, testez si elles fonctionnent encore comme avant.

**Voir aussi**

* [Réalisation d’un upgrade de build](../../production/using/build-upgrade.md)
* [Notes de mise à jour de Campaign Classic ](../../rn/using/rn-overview.md)
* [Options d’aide et de support pour les Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)
* [Programme Gold Standard](https://helpx.adobe.com/fr/campaign/kb/gold-standard.html)