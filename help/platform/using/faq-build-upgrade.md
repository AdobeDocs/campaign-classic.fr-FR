---
product: campaign
title: FAQ sur la mise à niveau des builds
description: Questions courantes relatives aux upgrades de build Campaign
feature: Upgrade, Troubleshooting
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 85e2135d-a1a3-44f0-a4f9-de38db5c8726
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '2005'
ht-degree: 99%

---

# FAQ sur la mise à niveau des builds {#build-upgrade-faq}



Adobe Campaign fait l&#39;objet de mises à jour régulières. Si vous connaissez les [notes de mise à jour](../../rn/using/rn-overview.md) que nous publions, vous savez probablement déjà que nous proposons en moyenne deux à trois versions mineures par an contenant de nouvelles fonctionnalités, des améliorations et des correctifs. En outre, nous publions périodiquement des builds avec des correctifs cumulatifs uniquement. Cette cadence régulière de mises à jour vise à vous proposer les fonctionnalités les plus appropriées et les plus récentes, en préservant la sécurité de votre environnement et en améliorant votre expérience avec notre produit.

C&#39;est pourquoi il est essentiel que nos clients exécutent la version la plus récente d&#39;Adobe Campaign. Nous pouvons ainsi vous aider plus efficacement si vous rencontrez des problèmes ; l&#39;identification, la reproduction et la résolution d&#39;un problème sur un ancien build prend généralement plus de temps, sans compter que vos éventuels problèmes peuvent avoir été corrigés dans un build récent.

En tant qu’utilisateur hébergé, vous bénéficiez automatiquement de la mise à niveau annuelle de Campaign avec la dernière version stable, et n’avez aucune action à effectuer. Les clients On-premise et hybrides peuvent également bénéficier de cette version. Si vous migrez depuis un ancien build, nous vous recommandons d’effectuer d’abord la mise à niveau vers cette version. [En savoir plus](../../rn/using/rn-overview.md).

## Qu&#39;est-ce qu&#39;un upgrade de build ?

Un upgrade de build, c&#39;est lorsque le logiciel Adobe Campaign Classic est mis à jour vers le numéro de build sécurisé le plus récent, tout en restant au même niveau de build majeur/mineur. Par exemple : Campaign Classic v7 build 9026 vers Campaign v7 build 9032.

En savoir plus [dans cette section](../../rn/using/rn-overview.md).

## Quelle est la dernière version d&#39;Adobe Campaign Classic ?

La version la plus récente de Campaign Classic, y compris les nouvelles fonctionnalités et la documentation, est présentée dans les dernières [notes de mise à jour](../../rn/using/latest-release.md).

## Comment déterminer la version que j&#39;exécute ?

Déterminez votre version dans le menu **[!UICONTROL Aide > A propos...]** de la console cliente Adobe Campaign. La boîte de dialogue **[!UICONTROL A propos]** contient des informations détaillées sur la version et le build que vous exécutez sur la console et le serveur.

En savoir plus [dans cette section](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Que signifie le statut de build ?

Depuis Campaign Classic 19.2, un statut est associé à chaque build.

En savoir plus [dans cette section](../../rn/using/rn-overview.md).

## Une mise à niveau de build équivaut-il à une mise à niveau de version ?

Non. Une mise à niveau de build est une mise à jour incrémentale au sein d’une version majeure donnée, tandis que mise à niveau de version correspond au passage d’une version majeure à une autre. Les mises à niveau de build sont simples, car ils n’impliquent généralement aucun changement majeur du point de vue technique, architectural ou des modèle de données.

En revanche, les mises à niveau de version s’accompagnent souvent de changements techniques importants et, selon le niveau de configuration d’un client donné, peuvent nécessiter des changements notables de la configuration et/ou une nouvelle implémentation partielle.

Par exemple, si l&#39;on reprend les informations de serveur figurant dans la capture d&#39;écran de la section précédente :

* Une mise à niveau de build signifierait passer de la build 9342 à n’importe quelle build supérieure à 9342. Par exemple, de v7.1 build 9342 à v7.1 build 9342.

* Une mise à niveau de version signifierait passer de la version 6 à n’importe quelle version plus récente.  Par exemple, de v6.1.1 build 8666 à v7.1 build 9342.

## Dois-je sauvegarder mes données avant d&#39;effectuer ces mises à jour ?

Adobe réalisera une sauvegarde de votre système avant tout changement. Toutefois, si votre système hors production (serveurs de développement ou de test) a fait l’objet de personnalisations critiques, nous vous RECOMMANDONS FORTEMENT d’exporter ces personnalisations sous la forme d’un package avant toute mise à niveau.

<!--
![](assets/do-not-localize/how-to-video.png) For more information, [watch this how to video](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).-->

## Quand les mises à jour auront-elles lieu ?

Les clients pourront effectuer un choix parmi plusieurs dates. Les changements des systèmes de production ne sont pas effectués les jours fériés.

Les upgrades de build peuvent être réalisés du lundi au jeudi, le vendredi étant réservé aux instances hors production.

## Combien de temps durera l&#39;upgrade de build ?

La durée de l&#39;upgrade de build dépend de plusieurs facteurs :

* La taille de la base de données à sauvegarder ou à restaurer (l&#39;upgrade de bases de données plus volumineuses dure généralement plus longtemps).
* La taille des environnements (nombre de nos clients possèdent différents serveurs gérant des fonctions spécifiques, et l&#39;upgrade des environnements de plus grande taille prend plus de temps).
* La complexité du système (certains systèmes présentent davantage de services et de connexions dépendants à vérifier, et la stabilité et les performances de tels systèmes doivent être vérifiées).

L&#39;upgrade de build est un processus en deux étapes :

1. Préparation du système à l&#39;upgrade : tenant compte des spécificités de votre environnement, cette phase conduit essentiellement à un upgrade complet sur un environnement hors production. Une fois l&#39;environnement mis à niveau validé du point de vue technique et fonctionnel, il est possible de passer à la phase 2. En fonction des facteurs mentionnés ci-dessus, la première phase peut prendre entre plusieurs jours et deux semaines.

1. L&#39;upgrade lui-même : l’environnement de production est mis à niveau.  Cette phase prend généralement quelques heures. Dans le cas d&#39;environnements très complexes, vous devez prévoir un temps d’arrêt plus long. En cas de problème, une stratégie de restauration est définie et peut être exécutée.

Pour plus d&#39;informations, [voir ce document](https://helpx.adobe.com/fr/campaign/kb/acc-build-upgrade.html).

## Quelles sont les ressources nécessaires pour l&#39;upgrade de build ?

L&#39;upgrade de build requiert les ressources suivantes :

* Architecte Adobe : l&#39;architecte doit se charger de la coordination avec l&#39;assistance clientèle en cas d&#39;architecture hébergée ou Cloud Messaging/hybride.
* Chef de projet - Hébergé : l&#39;équipe chargée de l&#39;hébergement s&#39;associera à l&#39;équipe de l&#39;assistance clientèle et au client pour coordonner le calendrier de l&#39;upgrade pour toutes les instances.
* Administrateur Adobe Campaign - Hébergé : l&#39;équipe chargée de l&#39;hébergement réalise l&#39;upgrade.
* Opérateur Adobe Campaign\utilisateur marketing : l&#39;opérateur effectue des tests sur les instances de développement, de test et de production.

## Comment me préparer à l&#39;upgrade de build ?

Dans vos systèmes de développement et d’évaluation, exportez tous les travaux critiques et qui doivent être préservés.

<!--For more information please [watch this how to video](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).-->

Rafraîchissez vos connaissances des workflows de chemin critique et des diffusions développées dans vos runbooks (ou par votre équipe/partenaire consultant) en consultant la documentation fournie à votre équipe au terme de l&#39;implémentation.

Identifiez les heures de faible volume ou trafic qui seraient idéales pour les fenêtres de maintenance, car elles auront le plus faible impact sur l’entreprise.

Consultez notre [liste de contrôle d&#39;upgrade de build ci-dessous](#check-list) et vos plans de test, et vérifiez que les ressources qui peuvent réaliser ces tests sont disponibles dans les 24/48 heures suivant un upgrade.

Pour plus d’informations, [consultez cette section](../../production/using/build-upgrade.md).

## Les upgrades peuvent-ils être effectués le soir ou en dehors des heures de bureau ?

Les upgrades peuvent être réalisés en dehors des heures de bureau. Nous recommandons toujours d&#39;effectuer un upgrade de l&#39;environnement en dehors des heures de bureau lorsqu&#39;aucun utilisateur d’entreprise n&#39;est connecté à l&#39;instance.

## Quels sont les coûts associés à un upgrade de build ?

L&#39;installation de l&#39;upgrade de build n’engendre aucun coût pour les clients hébergés. Si le système comprend des développements personnalisés, le client devra identifier les ressources nécessaires pour les tester après l&#39;upgrade et corriger les éventuels problèmes associés.

## L&#39;instance est-elle accessible pendant l&#39;upgrade ?

Non. Le serveur est arrêté au cours d&#39;un upgrade de façon à assurer l&#39;intégrité des données lors de cette opération. Une fois l&#39;upgrade terminé, il est redémarré et tous les services reprennent.

## Les emails continueront-ils à être envoyés depuis Message Center au cours du processus d&#39;upgrade ?

Lorsque l&#39;upgrade s’applique à Message Center (RT), celui-ci n&#39;enverra pas d&#39;emails à partir de l&#39;instance. Notez que tout processus arrêté lors de l&#39;arrêt d&#39;un système Campaign est repris automatiquement au redémarrage du système. Cela comprend les diffusions actives ou planifiées, le suivi ainsi que les calculs des mesures pour les diffusions envoyées précédemment.

## Les workflows continueront-ils à s&#39;exécuter et à envoyer les diffusions ?

Non. Au cours de l&#39;upgrade de build, les services de workflow et de messagerie sont arrêtés. Cela signifie que les workflows ne s&#39;exécuteront pas et que les diffusions ne sont pas envoyées. Ils reprendront une fois le système redémarré. Cependant, Adobe vous conseille fortement de vérifier les workflows de chemin critique après un upgrade pour vous assurer qu&#39;ils s&#39;exécutent correctement.

## Mes liens de tracking fonctionnent-ils toujours pendant l&#39;upgrade ?

Les liens de tracking présents dans les e-mails déjà envoyés ne fonctionneront pas pendant la mise à niveau, car tous les serveurs sont arrêtés. Ils seront à nouveau opérationnels une fois la mise à niveau terminée et les serveurs redémarrés.

## Dois-je être disponible pendant l&#39;upgrade de build ?

Oui. Les clients doivent indiquer à Adobe un point de contact disponible au cours de l&#39;upgrade ou immédiatement après l&#39;upgrade de leur instance de production.  Adobe contactera cette personne par email en l’absence d’autres arrangements. Cela assurera une transition fluide et une validation immédiate des tâches critiques. Adobe contactera le client une fois l&#39;upgrade de build terminé pour confirmation.

## Dois-je mettre à jour la console cliente ?

Oui. La console cliente doit présenter le même build que l&#39;instance de serveur. Une fois l&#39;upgrade réalisé, votre console cliente doit vous inviter à effectuer un upgrade vers le build le plus récent afin de vous assurer qu&#39;elle reste alignée sur le build du serveur.

## Quel est le plan de restauration ? Les sauvegardes de mes données sont-elles conservées ?

Le plan de restauration consiste à restaurer le système avec la sauvegarde la plus récente disponible. Les sauvegardes sont stockées pendant 7 jours pour les clients du centre de données et pendant 14 jours pour les clients sur Amazone Web Service (AWS).

## Quelle est la durée de la restauration ?

Elle dépend de la taille de sauvegarde de la base de données. La durée moyenne est de 4 heures.

## Quels types de tests sont réalisés sur mon système après l&#39;upgrade ?

Reportez-vous à la [liste de contrôle d’upgrade de build ci-dessous](#check-list).

## Quel type de test dois-je effectuer après mon upgrade ?

Les environnements de développement et de test sont mis à niveau en séquence ou ensemble, mais une signature est nécessaire avant l&#39;upgrade de l&#39;instance de production. Chaque client peut ainsi réaliser des tests avant de valider tout changement pour son passage en production.

Reportez-vous à la [liste de contrôle d&#39;upgrade de build ci-dessous](#check-list). Les clients doivent exécuter des tests similaires ainsi que d&#39;autres qui peuvent être nécessaires pour l&#39;environnement.

## À quelle fréquence dois-je réaliser un upgrade de build ?

Pour assurer un niveau optimal de performances, de disponibilité et de sécurité du système, Adobe collaborera avec les clients en vue d&#39;assurer que les systèmes sont mis à niveau au moins une fois par an.

## Y aura-t-il un temps d&#39;arrêt lors d&#39;un upgrade de build ?

Oui. Le serveur est arrêté au cours d&#39;un upgrade de façon à assurer l&#39;intégrité des données lors de cette opération. Une fois l&#39;upgrade terminé, le serveur est redémarré et tous les services reprennent.

## Qui dois-je contacter pour ouvrir le ticket d&#39;upgrade de build ?

Si vous rencontrez des problèmes après un upgrade de build, contactez l&#39;[assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Cette équipe planifie les dates de build et ouvre les tickets correspondants.

En savoir plus dans [Options d&#39;aide et de support pour Campaign Classic](../../support.md)

## Liste de contrôle d&#39;upgrade de build {#check-list}

### Liste de contrôle du serveur Cloud Messaging après upgrade

1. Envoyer une diffusion test
   1. Valider les logs de diffusion et le workflow associé
   1. Valider la mise à jour des logs de tracking
   1. Valider les liens de page miroir et de tracking
1. Confirmer que tous les workflows techniques sont à l&#39;état démarré
1. Vérifier que tous les processus sont également actifs

### Liste de contrôle du serveur marketing après upgrade

* Est-il possible de se connecter au serveur ? Vérifier que la console cliente Campaign fonctionne sans erreur/message d&#39;avertissement.
* Veiller à utiliser la même version de console que la version de build après l&#39;upgrade.
* Des applications web insèrent-elles des données dans la base de données Campaign ? Si tel est le cas, les exécuter et vérifier qu&#39;elles peuvent insérer de nouveaux enregistrements via l&#39;API.
* Est-il possible d&#39;envoyer un email de test ? Créer une diffusion à l&#39;aide d&#39;un modèle connu, l&#39;envoyer à un destinataire de test et vérifier que la personnalisation, le lien de désabonnement et la page miroir fonctionnent.
* Tous vos workflows de chemin critique sont-ils exécutés ? Vérifier les workflows, ouvrir un journal de workflow et vérifier qu&#39;il n&#39;y a pas d&#39;erreur.
* Tous vos dossiers sont-ils présents, visibles et accessibles ? Accéder aux différents dossiers et vérifier que l&#39;ensemble
du contenu est présent et s&#39;affiche.
* Toutes vos diffusions sont-elles effectuées dans le fuseau horaire approprié ?

   * Vérifier la date de création et de modification avec la date, l&#39;heure et le fuseau horaire.
   * Vérifier que l&#39;exécution du planificateur se déroule dans un workflow à l&#39;heure spécifiée.
   * Récupérer la liste des workflows qui sont en état EN PAUSE et EN ÉCHEC. Les démarrer et les surveiller.
   * Exécuter un test AB pour un scénario.
   * Tester les notifications push avec les fonctionnalités de tracking pour les liens profonds.
   * Tester l&#39;envoi de SMS.
   * Si un FDA externe est connecté, tester si les données sont envoyées dans les deux sens.
   * Si vous utilisez des intégrations telles qu&#39;Adobe Campaign-Adobe Experience Manager, Adobe Campaign-Adobe Analytics, tester si elles fonctionnent encore comme avant.

**Voir aussi**

* [Réalisation d&#39;un upgrade de build](../../production/using/build-upgrade.md)
* [Notes de mise à jour de Campaign Classic ](../../rn/using/rn-overview.md)
* [Options d&#39;aide et de support pour Campaign Classic](../../support.md)
* [Programme de mise à niveau annuelle](../../rn/using/rn-overview.md#yearly-upgrade)
