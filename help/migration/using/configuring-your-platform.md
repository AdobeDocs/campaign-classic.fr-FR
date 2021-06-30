---
product: campaign
title: Configurer votre plateforme
description: Configurer votre plateforme
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: ht
source-wordcount: '941'
ht-degree: 100%

---

# Configurer votre plateforme{#configuring-your-platform}

Certaines évolutions majeures d&#39;Adobe Campaign v7 nécessitent un paramétrage pour en assurer le bon fonctionnement. Ces paramètres peuvent être nécessaires avant ou après l&#39;exécution de la migration. Les évolutions concernées et leur mode de paramétrage sont présentés dans cette section.

Lors de la migration, la table **NmsRecipient** est reconstruite à partir de la définition des schémas. Toute modification de la structure SQL de cette table effectuée en dehors d&#39;Adobe Campaign sera perdue.

Exemples d&#39;éléments à vérifier :

* Si vous avez ajouté une colonne (ou un index) dans la table **NmsRecipient** mais que vous ne l&#39;avez pas décrite dans le schéma, celle-ci ne sera pas conservée.
* L&#39;attribut **tablespace** reprend ses valeurs par défaut, c&#39;est-à-dire celles définies dans l&#39;assistant de déploiement.
* Si vous avez ajouté une vue qui référence la table NmsRecipient, vous devez la supprimer avant la migration.

Cet avertissement concerne également les utilisateurs d&#39;Oracle : si vous ajoutez l&#39;option **-usetimestamptz:1** lors du postupgrade (voir la section [Fuseaux horaires](../../migration/using/general-configurations.md#time-zones)), toutes les tables contenant au moins un champ **date+time** sont reconstruites.

## Avant la migration {#before-the-migration}

Dans le cadre d&#39;une migration vers Adobe Campaign v7, les éléments suivants doivent être paramétrés. Ces paramétrages impliquent une prise en compte avant le lancement du **postupgrade**.

* Fuseaux horaires

   Dans le cadre d&#39;une migration depuis une plateforme v5.11, vous devez indiquer le fuseau horaire à utiliser lors du postupgrade.

   Si vous souhaitez utiliser le mode « multi timezone », consultez la section [Fuseaux horaires](../../migration/using/general-configurations.md#time-zones).

   Si vous utilisez Oracle comme moteur de base de données, vérifiez que les fichiers de fuseaux horaires Oracle sont bien synchronisés entre le serveur applicatif et le serveur de base. Voir à ce propos la section [Oracle](../../migration/using/general-configurations.md#oracle).

* Zones de sécurité

   Pour des raisons de sécurité, la plateforme Adobe Campaign n&#39;est plus accessible par défaut : vous devez configurer les zones de sécurité, et pour cela collecter, avant la migration, les adresses IP des utilisateurs.

   Voir à ce sujet la section [Sécurité](../../migration/using/general-configurations.md#security).

* Syntaxe

   Certaines syntaxes en JavaScript pouvaient être tolérées dans les versions 5.11 et 6.02 et ne le seront plus dans la v7 du fait de l&#39;utilisation d&#39;un nouvel interpréteur. Voir à ce sujet la section [JavaScript](../../migration/using/general-configurations.md#javascript).

   Parallèlement, une nouvelle syntaxe est introduite dans Adobe Campaign v7 pour remplacer celle basée sur SQLData. Si vous utilisez des éléments de code avec cette syntaxe, vous devez les adapter. Voir à ce sujet la section [SQLData](../../migration/using/general-configurations.md#sqldata).

* Mots de passe

   Vous devez configurer les mots de passe **Admin** et **Interne**. Pour plus d&#39;informations, consultez la section [Mots de passe des opérateurs](../../migration/using/before-starting-migration.md#user-passwords).

* Arborescence

   Si vous effectuez une migration à partir d&#39;une plateforme v5.11, vous devez réorganiser les dossiers de l&#39;arborescence conformément aux normes Adobe Campaign v6. Pour plus d&#39;informations, voir la section [Arborescence Adobe Campaign v7](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure).

* Interaction

   Si vous utilisez **Interaction**, vous devez supprimer toutes les références au schéma 6.02 qui n&#39;existent plus dans v7. Voir à ce sujet la section [Interaction](../../migration/using/general-configurations.md#interaction).

## Après la migration {#after-the-migration}

Après l&#39;exécution du **postupgrade**, les éléments suivants doivent être pris en compte et les paramétrages correspondants doivent être réalisés :

* Pages miroir

   Dans la version v6.x, le bloc de personnalisation des pages miroir a changé. Cette nouvelle version renforce la sécurité lors de l&#39;accès à ces pages.

   Si vous utilisez le bloc de personnalisation de la version v5 dans vos messages, les pages miroir ne s&#39;affichent pas. Adobe recommande vivement d&#39;utiliser le nouveau bloc de personnalisation lors de l&#39;insertion d&#39;une page miroir dans vos messages.

   A titre de solution temporaire (et pendant que les pages miroir sont toujours en ligne), vous pouvez revenir à l&#39;ancien bloc de personnalisation pour éviter ce problème en définissant l&#39;option **[!UICONTROL XtkAcceptOldPasswords]** sur **[!UICONTROL 1]**. Ce paramétrage n&#39;a aucun impact sur l&#39;utilisation du nouveau bloc de personnalisation de la version v6.x.

* Syntaxe

   Si vous rencontrez des erreurs, lors du postupgrade, liées à la syntaxe SQLData, vous devez temporairement activer l&#39;option **allowSQLInjection** dans le fichier **serverConf.xml**, le temps de réécrire le code. Une fois le code adapté, n&#39;oubliez pas de réactiver la sécurité. Voir à ce propos la section [SQLData](../../migration/using/general-configurations.md#sqldata).

* Conflits

   La migration étant effectuée au travers d&#39;un postupgrade, des conflits peuvent apparaître au niveau des rapports, formulaires ou applications web. Ces conflits peuvent être résolus manuellement depuis la console.

   Consultez la section [Conflits](../../migration/using/general-configurations.md#conflicts).

* Tomcat

   Si vous avez personnalisé le dossier d&#39;installation, vérifiez qu&#39;il est correctement mis à jour après la migration. Pour plus de détails, voir la section [Tomcat](../../migration/using/general-configurations.md#tomcat).

* Rapports 

   Tous les rapports d&#39;usine utilisent à présent le moteur de rendu v6.x. Si vous aviez ajouté du code javascript dans ces rapports, certains éléments peuvent être altérés.

   Consultez la section [Rapports](../../migration/using/general-configurations.md#reports).

* Applications Web

   Après le postupgrade, si vous rencontrez des problèmes de connexion à vos applications Web identifiées, vous devez activer les options **allowUserPassword** et **sessionTokenOnly** dans le fichier **serverConf.xml**. N&#39;oubliez pas de désactiver ensuite ces deux options. Pour plus d&#39;informations, consultez la section [Applications Web identifiées](../../migration/using/general-configurations.md#identified-web-applications).

   Selon le type d&#39;applications Web et leur configuration, vous devez effectuer des manipulations complémentaires pour en assurer le bon fonctionnement.

   Voir la section [Applications Web](../../migration/using/general-configurations.md#web-applications).

   Dans le cadre d&#39;une migration depuis une plateforme v5.11, des paramétrages additionnels doivent être réalisés. Voir à ce propos la section [Applications Web](../../migration/using/specific-configurations-in-v5-11.md#web-applications).

* Zones de sécurité

   Avant de démarrer le serveur, vous devez configurer les zones de sécurité. Pour plus d&#39;informations, consultez [cette section](../../installation/using/security-zones.md) et la section [Sécurité](../../migration/using/general-configurations.md#security).

* Schémas

   Dans Red Hat, vous pouvez rencontrer des erreurs lors de l&#39;édition de certains schémas. Voir à ce propos la section [Red Hat](../../migration/using/general-configurations.md#red-hat).

* Workflows

   Si vous effectuez une migration à partir d&#39;une plateforme v5.11, vous devez contrôler le répertoire d&#39;exécution des workflows. Voir à ce propos la section [Workflows](../../migration/using/specific-configurations-in-v5-11.md#workflows).

* Effectuer un tracking

   Si vous effectuez une migration à partir d&#39;une plateforme v5.11, vous devez configurer le mode de tracking. Voir à ce sujet la section [Suivre les ](../../migration/using/specific-configurations-in-v5-11.md#tracking).

* Page d&#39;accueil 

   Dans le cadre d&#39;une migration depuis une plateforme v6.02, vous pouvez définir des paramètres additionnels afin de conserver votre ancienne page d&#39;accueil v6.02. Voir à ce propos la section [Ergonomie : page d&#39;accueil et navigation](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation).

* Interaction

   Si vous utilisez **Interaction**, vous devez ajuster les paramètres après la migration. Voir à ce propos la section [Interaction](../../migration/using/general-configurations.md#interaction).
