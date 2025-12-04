---
product: campaign
title: FAQ Campaign Classic
description: Questions spécifiques à l’architecture, au déploiement et aux fonctionnalités de Adobe Campaign Classic v7
feature: Overview, Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
source-git-commit: 295e3596d9291cbcc55e2d264309141526c3806b
workflow-type: tm+mt
source-wordcount: '1535'
ht-degree: 6%

---

# FAQ sur Campaign Classic v7 {#campaign-classic-v7-faq}

Cette FAQ aborde des questions spécifiques à l&#39;architecture de Adobe Campaign Classic v7, aux modèles de déploiement et aux fonctionnalités spécifiques à la v7.

**Pour obtenir des réponses complètes aux questions courantes sur Campaign** (workflows, diffusions, audiences, rapports, personnalisation, etc.), reportez-vous à la [**FAQ complète sur Campaign v8**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}, qui fournit des réponses détaillées organisées par rubrique.

## Architecture et déploiement de Campaign Classic v7 {#v7-architecture}

### Quels sont les modèles d’hébergement disponibles dans Campaign Classic v7 ? {#what-are-the-hosting-models-available-in-campaign-classic-v7}

Adobe Campaign Classic v7 propose trois modèles de déploiement :

* **Hébergé (Managed Services)** - Entièrement géré par Adobe sur l’infrastructure Adobe
* **On-premise** - Installé et géré sur votre propre infrastructure
* **Hybride** - Architecture de mid-sourcing avec mélange de composants cloud et on-premise

Chaque modèle de déploiement possède des capacités et des responsabilités de gestion différentes. La disponibilité des modules, options et configurations dépend de votre type de déploiement.

[Cliquez ici pour en savoir plus](../../installation/using/hosting-models.md) sur les modèles d’hébergement et leurs différences.

**Remarque :** Campaign v8 est exclusivement disponible en tant que Managed Cloud Services. [Découvrez Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html){target="_blank"}.

### Quelles sont les différences entre un environnement on-premise et un environnement hébergé ? {#what-are-the-differences-when-working-on-premise-vs-in-a-hosted-environment}

Adobe Campaign Classic v7 est fourni avec un ensemble de modules et d’options. La disponibilité de ces modules et leur configuration dépendent du [type de déploiement](../../installation/using/hosting-models.md) de votre installation : hébergée (Managed Services), hybride ou on-premise.

Principales différences :

* **On-premise** - Contrôle total de l’installation, de l’infrastructure et de la configuration. Nécessite des ressources informatiques internes pour la maintenance, les mises à niveau et la sécurité.
* **Hébergé/Managed Services** - Infrastructure et maintenance gérées par Adobe. Mises à niveau automatiques et sécurité renforcée. Accès direct au serveur limité.
* **Hybride** : associe les avantages des deux modèles. Instance marketing hébergée par Adobe, exécution/mid-sourcing gérée séparément.

[Cliquez ici pour consulter la matrice complète des fonctionnalités](../../installation/using/capability-matrix.md).

### Comment migrer d’on-premise/hybride vers Adobe Managed Services ? {#how-do-i-migrate-from-on-premise-hybrid-to-adobe-managed-services}

La migration vers Adobe Managed Services améliore l’évolutivité, la sécurité et réduit les frais informatiques. Il s’agit souvent d’un tremplin avant de passer à Campaign v8.

**Points clés :**

* Aucun outil de migration automatisée disponible : planification et exécution manuelles requises
* Prise en charge de Adobe Professional Services vivement recommandée
* Les avantages incluent l’infrastructure cloud, les correctifs de sécurité automatiques, l’assistance d’experts et un accès plus facile à v8
* La migration implique une diligence raisonnable, un audit de l’environnement, un nettoyage des données, une migration d’évaluation et un basculement en production

**Prise en main :** contactez votre représentant Adobe pour évaluer votre environnement et développer un plan de migration détaillé avec Adobe Professional Services.

En savoir plus sur la [&#x200B; migration vers Managed Services &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic-blogs/migrate-your-adobe-campaign-v7-onprem-hybrid-environment-to/ba-p/681605){target="_blank"}.

## Mises à niveau des builds (Campaign Classic v7) {#build-upgrades-v7}

### Qu&#39;est-ce qu&#39;une mise à niveau de build dans Campaign Classic v7 ? {#what-is-a-build-upgrade-v7}

Une mise à niveau de build survient lorsque le logiciel Adobe Campaign Classic v7 est mis à jour vers le numéro de build sécurisé le plus récent, tout en restant au même niveau de build majeur/mineur. Par exemple : Campaign Classic v7 build 9026 vers Campaign v7 build 9032.

Adobe Campaign fait l&#39;objet de mises à jour régulières. Les versions mineures sont publiées avec de nouvelles fonctionnalités, des améliorations et des correctifs. En outre, les versions avec correctifs cumulatifs uniquement sont publiées périodiquement.

En savoir plus [dans cette section](../../rn/using/rn-overview.md).

### Comment effectuer une mise à niveau de Campaign Classic v7 vers la dernière version ? {#how-can-i-upgrade-campaign-classic-v7}

Adobe Campaign Classic utilise toute une gamme de technologies pour offrir de la valeur ajoutée. Cette combinaison de technologies nécessite une mise à niveau régulière de votre ou vos instances Campaign Classic v7 afin de vous assurer que les versions les plus récentes sont utilisées pour offrir une sécurité, une stabilité et des performances supérieures.

**Pour les clients hébergés :** vous bénéficiez automatiquement de la mise à niveau annuelle de Campaign avec la dernière version stable. Adobe gère le processus de mise à niveau et coordonne le timing avec vous.

**Pour les clients on-premise/hybrides :** vous êtes responsable de l’exécution des mises à niveau. Adobe recommande vivement d’effectuer la mise à niveau au moins une fois par an.

[Lisez cette section](../../production/using/build-upgrade.md) pour savoir comment mettre à jour votre environnement, et lisez [FAQ sur la mise à niveau de build](../../platform/using/faq-build-upgrade.md) pour des questions détaillées sur ce sujet spécifique.

### Quelle est la dernière version de Adobe Campaign Classic v7 ? {#what-is-the-latest-version-v7}

La dernière version de Campaign Classic v7, y compris les nouvelles fonctionnalités et la documentation, est présentée en détail dans les dernières [notes de mise à jour](../../rn/using/latest-release.md).

### Comment savoir quelle version de Campaign Classic v7 j’exécute ? {#how-do-i-know-which-version-v7}

Vérifiez les numéros de version et de build depuis le menu **[!UICONTROL Aide > À propos...]** de la console cliente Adobe Campaign. La zone **[!UICONTROL À propos]** contient des informations détaillées sur la version et la version que vous exécutez pour la console et le serveur.

En savoir plus [dans cette section](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

### Une mise à niveau de build est-elle identique à une mise à niveau de version ? {#is-build-upgrade-same-as-version-upgrade}

Non. Une mise à niveau de build est une mise à jour incrémentale au sein d’une version majeure donnée, tandis que mise à niveau de version correspond au passage d’une version majeure à une autre. Les mises à niveau de build sont simples et n’impliquent généralement pas de modifications majeures du point de vue architectural, technique ou du modèle de données.

Les mises à niveau de version (par exemple, v7 vers v8) s’accompagnent généralement de modifications techniques importantes et peuvent nécessiter des modifications de configuration ou une nouvelle implémentation partielle selon vos personnalisations.

## Configuration de Campaign Classic v7 {#v7-configuration}

### Puis-je changer la langue de l&#39;interface de Campaign Classic v7 ? {#can-i-change-language-v7}

La langue Campaign Classic v7 est sélectionnée lors de la création de l’instance. **Vous ne pouvez pas le modifier par la suite.**

L&#39;interface utilisateur d&#39;Adobe Campaign v7 est disponible en 4 langues : anglais, français, allemand et japonais. La console cliente et le serveur doivent être définis avec la même langue. Chaque instance de Campaign Classic v7 ne peut s’exécuter que dans une seule langue.

Pour l&#39;anglais, lors de l&#39;installation de Campaign v7, vous pouvez sélectionner l&#39;anglais (États-Unis) ou l&#39;anglais (Royaume-Uni) : ils diffèrent en termes de formats de date et d&#39;heure.

[En savoir plus dans cette section](../../installation/using/creating-an-instance-and-logging-on.md).

**Remarque :** l’interface utilisateur web de Campaign v8 permet aux utilisateurs de modifier leur langue d’interface indépendamment. [En savoir plus](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/connect.html#language-pref){target="_blank"}.

### Comment configurer des zones de sécurité dans Campaign Classic v7 ? {#how-can-i-configure-security-zones-v7}

L’interface Security Zones Self Service peut être utilisée pour gérer les entrées de la configuration Zone de sécurité VPN d’un déploiement Adobe Campaign Classic v7. Cela s’applique principalement aux déploiements On-Premise et hybrides.

Lisez [cette section](../../installation/using/security-zones.md) pour en savoir plus sur les zones de sécurité dans Campaign v7.

[Cliquez ici pour en savoir plus](https://helpx.adobe.com/fr/campaign/kb/configuring-security-zones-self-service.html){target="_blank"} sur l’interface utilisateur en libre-service de la zone de sécurité.

**Remarque :** les clients hébergés/Managed Services doivent contacter Adobe pour configurer les zones de sécurité.

### Adobe Campaign Classic v7 peut-il s’intégrer à LDAP ? {#can-campaign-classic-integrate-with-ldap}

Oui. En tant que **client On-premise/hybride**, vous pouvez intégrer Campaign Classic v7 à votre annuaire LDAP pour une authentification et une gestion des utilisateurs centralisées.

Cette intégration permet d’effectuer les opérations suivantes :

* Utilisateurs à authentifier dans l’annuaire LDAP de votre entreprise
* Gestion centralisée des utilisateurs et des droits
* Synchronisation automatique des groupes d’utilisateurs et des autorisations
* Fonctionnalités d’authentification unique

[Cliquez ici pour découvrir comment &#x200B;](../../installation/using/connecting-through-ldap.md) l&#39;intégration LDAP dans Campaign Classic v7.

**Remarque :** intégration LDAP est disponible pour les déploiements on-premise et hybrides. Les clients hébergés utilisent Adobe IMS pour l’authentification.

### Quelles sont les bonnes pratiques de sécurité pour les déploiements on-premise ? {#security-best-practices-on-premise}

Les déploiements On-premise et hybrides nécessitent une configuration et un renforcement de la sécurité supplémentaires par rapport aux environnements hébergés.

**Principaux domaines de sécurité :**

* Configuration de la sécurité réseau et du pare-feu
* Accès et sécurité de la base de données
* Renforcement du système d’exploitation
* Autorisations de fichiers et contrôles d’accès
* Configuration des zones de sécurité
* Chiffrement (données au repos et en transit)
* Gestion des accès des utilisateurs et utilisatrices
* Correctifs de sécurité standard
* Journalisation et surveillance des audits

Lisez la [Liste de contrôle relative à la configuration de la sécurité](https://helpx.adobe.com/campaign/kb/acc-security.html){target="_blank"} pour découvrir les éléments clés à vérifier en ce qui concerne le renforcement et la configuration de la sécurité pour les déploiements on-premise.

### Comment effacer le cache de la console cliente ? {#how-do-i-clear-console-cache}

L’effacement du cache de la console cliente Campaign résout de nombreux problèmes courants d’affichage et de fonctionnalité. Le cache stocke les fichiers de configuration locaux qui peuvent parfois être corrompus ou obsolètes.

**Quand vider le cache :**

* Les nouveaux éléments de branding ne s’affichent pas correctement
* Échec inattendu des fonctions d’exportation/d’importation
* Les éléments d’interface ne se mettent pas à jour après les modifications de configuration
* Problèmes de performances ou réponse lente de la console
* Après la mise à niveau vers une nouvelle version de la console cliente

**Comment vider le cache :**

1. **Effacer le cache logiciel (essayez d’abord) :**
   * Ouvrir la console cliente Campaign
   * Accéder au menu **[!UICONTROL Fichier]**
   * Sélectionnez **[!UICONTROL Effacer le cache local...]**
   * Confirmer l’action lorsque vous y êtes invité
   * Redémarrez la console cliente

2. **Effacement du cache dur (si l’effacement souple ne résout pas le problème) :**
   * Effacer d&#39;abord le cache logiciel
   * Déconnectez-vous et fermez complètement la console cliente
   * Accédez à :
      * Windows 7/10 : `C:\Users\<Username>\AppData\Roaming\Neolane\NL_5\`
      * Windows XP : `C:\Documents and Settings\<Username>\Application Data\Neolane\NL_5\`
   * Supprimez tous les fichiers XML nommés `nlclient-config-<alphanumerical value>.xml` et les dossiers associés
   * **Important :** ne supprimez PAS `nlclient_cnx.xml` fichier
   * Redémarrer la console cliente

En savoir plus dans la [documentation de la console cliente Campaign](../../platform/using/launching-adobe-campaign.md).

## Accès à l’aide {#getting-help}

### Où puis-je trouver plus d&#39;informations sur Campaign Classic v7 ? {#where-to-find-more-info-v7}

**Documentation et ressources :**

* [Documentation de Campaign Classic v7 &#x200B;](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html?lang=fr){target="_blank"} - Documentation complète
* [Notes de mise à jour de Campaign Classic v7 &#x200B;](../../rn/using/latest-release.md) - Informations récentes
* [Matrice de compatibilité Campaign Classic &#x200B;](../../rn/using/compatibility-matrix.md) - Systèmes et versions pris en charge
* [Tutoriels Campaign Classic &#x200B;](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=fr){target="_blank"} - Tutoriels vidéo

**Pour les questions courantes sur Campaign :**

Reportez-vous à la section [**FAQ complète de Campaign v8**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"} qui fournit des réponses détaillées sur :

* Prise en main de Campaign
* Profils et audiences
* Conception et diffusion de messages
* Workflows et automatisation
* Rapports et analyses
* Paramètres et configuration de Campaign
* Ressources pour les développeurs
* Confidentialité et conformité

**Communauté et soutien :**

* [Forums de la communauté Campaign](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community?profile.language=fr){target="_blank"}
* [Assistance Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}
* [Panneau de Contrôle (clients hébergés)](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=fr){target="_blank"}

### Dois-je migrer de Campaign Classic v7 vers Campaign v8 ? {#should-i-migrate-to-v8}

Campaign v8 est une plateforme stratégique d’Adobe idéale pour les organisations qui ont besoin de campagnes volumineuses, d’une interface utilisateur web moderne, d’avantages natifs au cloud et d’une prise en charge à long terme. La prise en charge de Campaign Classic v7 prendra fin dans les années à venir.

**Envisagez de migrer vers Campaign v8 si vous :**

* Gérer des volumes de données importants ou rencontrer des problèmes de performances
* Vous souhaitez réduire les frais généraux informatiques et la gestion de l’infrastructure (la version v8 est Managed Cloud Services uniquement).
* Nécessité d’une interface utilisateur et d’une intégration Adobe Experience Platform modernes
* Besoin d&#39;une technologie évolutive avec des mises à jour automatiques
* Se trouvent actuellement sur des services hébergés/gérés (chemin de migration plus facile)

**Considérations importantes :**

* Campaign v8 est exclusivement disponible en tant que Managed Cloud Services (aucune option on-premise/hybride)
* Nécessite une planification de la migration des personnalisations et des intégrations
* L’architecture FFDA offre des performances, mais nécessite certaines adaptations des workflows et des API

**Étapes suivantes :** contactez votre représentant Adobe pour évaluer la préparation à la migration et accéder aux outils de migration.

En savoir plus :

* [Présentation de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html){target="_blank"}
* [Transition de Campaign Classic v7 vers v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/v7-to-v8.html){target="_blank"}
* [FAQ complète sur Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}

**Pour obtenir des réponses détaillées aux questions courantes de Campaign sur les workflows, les diffusions, les audiences, le reporting, la personnalisation, etc**, consultez la [FAQ complète de Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}.
