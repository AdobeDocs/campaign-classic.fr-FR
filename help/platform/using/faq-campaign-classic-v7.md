---
product: campaign
title: Questions fréquentes sur Campaign Classic
description: Questions spécifiques à l’architecture, au déploiement et aux fonctionnalités d’Adobe Campaign Classic v7
feature: Overview, Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
source-git-commit: 295e3596d9291cbcc55e2d264309141526c3806b
workflow-type: ht
source-wordcount: '1535'
ht-degree: 100%

---

# Questions fréquentes de Campaign Classic v7 {#campaign-classic-v7-faq}

Ces questions fréquentes abordent des questions spécifiques à l’architecture d’Adobe Campaign Classic v7, aux modèles de déploiement et aux fonctionnalités spécifiques à la v7.

**Pour obtenir des réponses complètes aux questions courantes sur Campaign** (workflows, diffusions, audiences, reporting, personnalisation, etc.), consultez les [**questions fréquentes complètes sur Campaign v8**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html?lang=fr){target="_blank"}, qui fournissent des réponses détaillées organisées par rubrique.

## Architecture et déploiement de Campaign Classic v7 {#v7-architecture}

### Quels sont les modèles d’hébergement disponibles dans Campaign Classic v7 ? {#what-are-the-hosting-models-available-in-campaign-classic-v7}

Adobe Campaign Classic v7 propose trois modèles de déploiement :

* **Hébergé (Managed Services)** - Entièrement géré par Adobe sur l’infrastructure Adobe
* **On-premise** - Installé et géré sur votre propre infrastructure
* **Hybride** - Architecture de midsourcing avec mélange de composants cloud et on-premise

Chaque modèle de déploiement possède des capacités et des responsabilités de gestion différentes. La disponibilité des modules, options et configurations dépend de votre type de déploiement.

[Cliquez ici pour en savoir plus](../../installation/using/hosting-models.md) sur les modèles d’hébergement et leurs différences.

**Note :** Campaign v8 est exclusivement disponible en tant que Managed Cloud Services. [Découvrez Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/new/whats-new.html){target="_blank"}.

### Quelles sont les différences entre un environnement on-premise et un environnement hébergé ? {#what-are-the-differences-when-working-on-premise-vs-in-a-hosted-environment}

Adobe Campaign Classic v7 est proposé avec un ensemble de modules et d’options. La disponibilité de ces modules et leur configuration dépend du [type de déploiement](../../installation/using/hosting-models.md) de votre installation : hébergée (Managed Services), hybride ou on-premise.

Principales différences :

* **On-premise** - Contrôle total de l’installation, de l’infrastructure et de la configuration. Nécessite des ressources informatiques internes pour la maintenance, les mises à niveau et la sécurité.
* **Hébergé/Managed Services** - Infrastructure et maintenance gérées par Adobe. Mises à niveau automatiques et sécurité renforcée. Accès direct au serveur limité.
* **Hybride** - Combine les avantages des deux modèles. Instance marketing hébergée par Adobe, gestion d’exécution/de midsourcing séparée.

[Cliquez ici pour consulter la matrice des fonctionnalités complète](../../installation/using/capability-matrix.md).

### Comment migrer depuis on-premise/hybride vers Adobe Managed Services ? {#how-do-i-migrate-from-on-premise-hybrid-to-adobe-managed-services}

La migration vers Adobe Managed Services améliore l’évolutivité, la sécurité et réduit les frais informatiques. Il s’agit souvent d’un tremplin avant de passer à Campaign v8.

**Points clés :**

* Aucun outil de migration automatisée disponible : planification et exécution manuelles requises
* Support Adobe Professional Services vivement recommandé
* Les avantages incluent l’infrastructure cloud, les correctifs de sécurité automatiques, l’assistance d’expertes et d’experts et un accès plus facile à v8.
* La migration implique les vérifications nécessaires, l’audit de l’environnement, le nettoyage des données, la migration intermédiaire et le basculement en production.

**Prise en main :** contactez votre représentant ou représentante Adobe pour évaluer votre environnement et développer un plan de migration détaillé avec Adobe Professional Services.

En savoir plus sur la [migration vers Managed Services](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic-blogs/migrate-your-adobe-campaign-v7-onprem-hybrid-environment-to/ba-p/681605?profile.language=fr){target="_blank"}.

## Mises à niveau de build (Campaign Classic v7) {#build-upgrades-v7}

### Qu’est-ce qu’une mise à niveau de build dans Campaign Classic v7 ? {#what-is-a-build-upgrade-v7}

Une mise à niveau de build est lorsque le logiciel Adobe Campaign Classic v7 est mis à jour vers le numéro de build sécurisé le plus récent, tout en restant au même niveau de build majeur/mineur. Par exemple : Campaign Classic v7 build 9026 vers Campaign v7 build 9032.

Adobe Campaign fait l’objet de mises à jour régulières. Des versions mineures sont publiées avec de nouvelles fonctionnalités, des améliorations et des correctifs. Des builds avec des correctifs cumulatifs uniquement sont également publiés périodiquement.

En savoir plus [dans cette section](../../rn/using/rn-overview.md).

### Comment effectuer une mise à niveau de Campaign Classic v7 vers la dernière version ? {#how-can-i-upgrade-campaign-classic-v7}

Adobe Campaign Classic utilise toute une gamme de technologies pour offrir une valeur ajoutée. Cette combinaison de technologies requiert que vous effectuiez régulièrement une mise à niveau de votre ou vos instances Campaign Classic v7 afin que les toutes dernières versions soient utilisées pour offrir une sécurité, une stabilité et des performances supérieures.

**Pour les clientes et clients hébergés :** vous bénéficiez automatiquement de la mise à niveau annuelle de Campaign avec la version stable la plus récente. Adobe gère le processus de mise à niveau et coordonne le timing avec vous.

**Pour les clientes et clients on-premise/hybrides :** vous êtes responsable de l’exécution des mises à niveau. Adobe recommande vivement d’effectuer une mise à niveau au moins une fois par an.

[Lisez cette section](../../production/using/build-upgrade.md) pour savoir comment mettre à jour votre environnement et consultez les [questions fréquentes sur la mise à niveau de build](../../platform/using/faq-build-upgrade.md) sur ce sujet spécifique.

### Quelle est la dernière version d’Adobe Campaign Classic v7 ? {#what-is-the-latest-version-v7}

La version la plus récente de Campaign Classic v7, y compris les nouvelles fonctionnalités et la documentation, est présentée dans les dernières [notes de mise à jour](../../rn/using/latest-release.md).

### Comment déterminer la version de Campaign Classic v7 que j’exécute ? {#how-do-i-know-which-version-v7}

Vérifiez les numéros de version et de build depuis le menu **[!UICONTROL Aide > À propos...]** de la console cliente d’Adobe Campaign. La boîte de dialogue **[!UICONTROL À propos]** contient des informations détaillées sur la version et le build que vous exécutez sur la console et le serveur.

En savoir plus [dans cette section](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

### Une mise à niveau de build équivaut-elle à une mise à niveau de version ? {#is-build-upgrade-same-as-version-upgrade}

Non. Une mise à niveau de build est une mise à jour incrémentale au sein d’une version majeure donnée, tandis que mise à niveau de version correspond au passage d’une version majeure à une autre. Les mises à niveau de build sont simples et n’impliquent généralement pas de changement majeur du point de vue technique, architectural ou des modèle de données.

Les mises à niveau de build (par exemple, v7 vers v8) s’accompagnent généralement de modifications techniques importantes et peuvent nécessiter des modifications de configuration ou une nouvelle implémentation partielle en fonction de vos personnalisations.

## Configuration de Campaign Classic v7 {#v7-configuration}

### Puis-je changer la langue de l’interface de Campaign Classic v7 ? {#can-i-change-language-v7}

La langue de Campaign Classic v7 est sélectionnée lors de la création de l’instance. **Vous ne pouvez pas la changer par la suite.**

L’interface d’utilisation d’Adobe Campaign v7 est disponible en quatre langues : anglais, français, allemand et japonais. La console cliente et le serveur doivent être définis avec la même langue. Chaque instance de Campaign Classic v7 ne peut s’exécuter que dans une seule langue.

Pour l’anglais, lors de l’installation de Campaign v7, vous pouvez sélectionner l’anglais américain ou l’anglais britannique : les formats de date et d’heure sont différents.

[En savoir plus dans cette section](../../installation/using/creating-an-instance-and-logging-on.md).

**Note :** l’interface d’utilisation web de Campaign v8 permet aux utilisateurs et utilisatrices de changer la langue de leur interface indépendamment. [En savoir plus](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/connect.html?lang=fr#language-pref){target="_blank"}.

### Comment configurer des zones de sécurité dans Campaign Classic v7 ? {#how-can-i-configure-security-zones-v7}

L’interface des zones de sécurité en libre-service peut être utilisée pour gérer les entrées de la configuration Zone de sécurité VPN d’un déploiement Adobe Campaign Classic v7. Elle s’applique principalement aux déploiements on-premise et hybrides uniquement.

Lisez [cette section](../../installation/using/security-zones.md) pour plus d’informations sur les zones de sécurité dans Campaign v7.

[Cliquez ici pour en savoir plus](https://helpx.adobe.com/fr/campaign/kb/configuring-security-zones-self-service.html){target="_blank"} sur l’interface d’utilisation des zones de sécurité en libre-service.

**Note :** les clientes et clients hébergés/Managed Services doivent contacter Adobe pour configurer les zones de sécurité.

### Adobe Campaign Classic v7 peut-il s’intégrer à LDAP ? {#can-campaign-classic-integrate-with-ldap}

Oui. En tant que **client ou cliente on-premise/hybride**, vous pouvez intégrer Campaign Classic v7 à votre annuaire LDAP pour une authentification et une gestion centralisées des utilisateurs et utilisatrices.

Cette intégration permet ce qui suit :

* Les utilisateurs et utilisatrices peuvent s’authentifier auprès de l’annuaire LDAP de votre entreprise.
* Une gestion centralisée des utilisateurs et utilisatrices et des droits
* Une synchronisation automatique des groupes d’utilisateurs et d’utilisatrices et des autorisations
* Des fonctionnalités d’authentification unique

[Cliquez ici pour découvrir](../../installation/using/connecting-through-ldap.md) comment configurer l’intégration LDAP dans Campaign Classic v7.

**Note :** l’intégration LDAP est disponible pour les déploiements on-premise et hybrides. Les clientes et clients hébergés utilisent Adobe IMS pour l’authentification.

### Quelles sont les bonnes pratiques en matière de sécurité pour les déploiements on-premise ? {#security-best-practices-on-premise}

Les déploiements on-premise et hybrides nécessitent une configuration et un renforcement de la sécurité supplémentaires par rapport aux environnements hébergés.

**Principaux domaines de sécurité :**

* Configuration de la sécurité du réseau et du pare-feu
* Accès à la base de données et sa sécurité
* Renforcement du système d’exploitation
* Autorisations de fichiers et contrôles d’accès
* Configuration des zones de sécurité
* Chiffrement (données au repos et en transit)
* Gestion des accès des utilisateurs et utilisatrices
* Correctifs de sécurité standard
* Journalisation et surveillance des audits

Consultez la [Liste de contrôle relative à la configuration de la sécurité](https://helpx.adobe.com/fr/campaign/kb/acc-security.html){target="_blank"} pour découvrir les éléments essentiels à contrôler en ce qui concerne la configuration et le renforcement de la sécurité pour les déploiements on-premise.

### Comment vider le cache de la console cliente ? {#how-do-i-clear-console-cache}

Le vidage du cache de la console cliente Campaign résout de nombreux problèmes courants d’affichage et de fonctionnalité. Le cache stocke les fichiers de configuration locaux qui peuvent parfois être corrompus ou obsolètes.

**Quand vider le cache :**

* Les nouveaux éléments de branding ne s’affichent pas correctement.
* Échec inattendu des fonctions d’export/d’import
* Les éléments d’interface ne sont pas mis à jour après des modifications de configuration.
* Problèmes de performances ou réponse lente de la console
* Après la mise à niveau vers une nouvelle version de la console cliente

**Comment vider le cache :**

1. **Vidage temporaire du cache (à essayer en premier) :**
   * Ouvrir la console cliente Campaign
   * Accéder au menu **[!UICONTROL Fichier]**
   * Sélectionner **[!UICONTROL Vider le cache local…]**
   * Confirmer l’action lorsque vous recevez l’invitation.
   * Redémarrer la console cliente

2. **Vidage définitif du cache (si le vidage temporaire ne résout pas le problème) :**
   * Effectuer d’abord un vidage temporaire du cache
   * Se déconnecter et fermer complètement la console cliente
   * Accéder à :
      * Windows 7/10 : `C:\Users\<Username>\AppData\Roaming\Neolane\NL_5\`
      * Windows XP : `C:\Documents and Settings\<Username>\Application Data\Neolane\NL_5\`
   * Supprimer tous les fichiers XML nommés `nlclient-config-<alphanumerical value>.xml` et leurs dossiers associés
   * **Important :** ne PAS supprimer le fichier `nlclient_cnx.xml`
   * Redémarrer la console cliente

En savoir plus dans la [documentation de la console cliente Campaign](../../platform/using/launching-adobe-campaign.md).

## Accès à l’aide {#getting-help}

### Où puis-je trouver plus d’informations sur Campaign Classic v7 ? {#where-to-find-more-info-v7}

**Documentation et ressources :**

* [Documentation de Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html?lang=fr){target="_blank"} - Documentation complète
* [Notes de mise à jour de Campaign Classic v7](../../rn/using/latest-release.md) - Informations de version les plus récentes
* [Matrice de compatibilité Campaign Classic](../../rn/using/compatibility-matrix.md) - Systèmes et versions pris en charge
* [Tutoriels Campaign Classic](https://experienceleague.adobe.com/fr/docs/campaign-classic-learn/tutorials/overview.html?lang=fr){target="_blank"} - Tutoriels vidéo

**Pour les questions courantes sur Campaign :**

Consultez les [**questions fréquentes complètes sur Campaign v8**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html?lang=fr){target="_blank"} qui fournissent des réponses détaillées sur les sujets suivants :

* Prise en main de Campaign
* Profils et audiences
* Conception et diffusion de messages
* Workflows et automatisation
* Rapports et analyses
* Paramètres et configuration de Campaign
* Ressources de développement
* Confidentialité et conformité

**Communauté et support :**

* [Forums de la communauté Campaign](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community?profile.language=fr){target="_blank"}
* [Support Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}
* [Panneau de contrôle (clientes et clients hébergés)](https://experienceleague.adobe.com/fr/docs/control-panel/using/control-panel-home.html?lang=fr){target="_blank"}

### Dois-je migrer de Campaign Classic v7 vers Campaign v8 ? {#should-i-migrate-to-v8}

Campaign v8 est une plateforme stratégique d’Adobe idéale pour les organisations qui ont besoin de campagnes volumineuses, d’une interface d’utilisation web moderne, d’avantages natifs du cloud et d’un support sur le long terme. La prise en charge de Campaign Classic v7 prendra fin dans les années à venir.

**Envisagez de migrer vers Campaign v8 dans les situations suivantes :**

* Vous gérez des volumes de données importants ou rencontrez des problèmes de performances.
* Vous souhaitez réduire les frais informatiques et la gestion de l’infrastructure (la version v8 est Managed Cloud Services uniquement).
* Vous avez besoin d’une interface d’utilisation moderne et de l’intégration Adobe Experience Platform.
* Vous souhaitez disposer d’une technologie évolutive avec des mises à jour automatiques.
* Vous êtes actuellement sur des services hébergés/gérés (chemin de migration plus facile).

**Remarques importantes :**

* Campaign v8 est exclusivement disponible en tant que Managed Cloud Services (aucune option on-premise/hybride).
* Nécessite une planification de la migration des personnalisations et des intégrations.
* L’architecture FFDA offre des performances, mais nécessite certaines adaptations des workflows/API.

**Étapes suivantes :** contactez votre représentant ou représentante Adobe pour évaluer la préparation à la migration et accéder aux outils de migration.

En savoir plus :

* [Vue d’ensemble de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/new/whats-new.html){target="_blank"}
* [Transition de Campaign Classic v7 vers v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/v7-to-v8.html?lang=fr){target="_blank"}
* [Questions fréquentes complètes sur Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html?lang=fr){target="_blank"}

**Pour obtenir des réponses détaillées aux questions courantes de Campaign sur les workflows, les diffusions, les audiences, le reporting, la personnalisation, et bien d’autres encore**, consultez les [questions fréquentes complètes sur Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html?lang=fr){target="_blank"}.
