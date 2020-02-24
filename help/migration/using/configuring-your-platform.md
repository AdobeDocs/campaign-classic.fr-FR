---
title: Configurer votre plateforme
seo-title: Configurer votre plateforme
description: Configurer votre plateforme
seo-description: null
page-status-flag: never-activated
uuid: e6255e4b-c9c8-4ac9-9ee3-aaa4dc9e5ecf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: 4d2e765b-750b-457f-ad55-8bd6faaa86af
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 40391fbea53757decb48fd937f5e74e8ba6fb207

---


# Configurer votre plateforme{#configuring-your-platform}

Certaines évolutions majeures d&#39;Adobe Campaign v7 nécessitent un paramétrage pour en assurer le bon fonctionnement. Ces paramètres peuvent être nécessaires avant ou après l&#39;exécution de la migration. Les évolutions concernées et leur mode de paramétrage sont présentés dans cette section.

Lors de la migration, la table **NmsRecipient** est reconstruite à partir de la définition des schémas. Toute modification de la structure SQL de cette table effectuée en dehors d&#39;Adobe Campaign sera perdue.

Exemples d&#39;éléments à vérifier :

* Si vous avez ajouté une colonne (ou un index) dans la table **NmsRecipient** mais que vous ne l&#39;avez pas décrite dans le schéma, celle-ci ne sera pas conservée.
* L&#39;attribut **tablespace** reprend ses valeurs par défaut, c&#39;est-à-dire celles définies dans l&#39;assistant de déploiement.
* Si vous avez ajouté une vue qui référence la table NmsRecipient, vous devez la supprimer avant la migration.

This warning also concerns Oracle users: if you have added the **usetimestamptz:1** option during a postupgrade (see [Time zones](../../migration/using/general-configurations.md#time-zones)), all tables containing at least one **date+time** field are rebuilt.

## Avant la migration {#before-the-migration}

Dans le cadre d&#39;une migration vers Adobe Campaign v7, les éléments suivants doivent être paramétrés. Ces paramétrages impliquent une prise en compte avant le lancement du **postupgrade**.

* Fuseaux horaires

   Dans le cadre d&#39;une migration depuis une plateforme v5.11, vous devez indiquer le fuseau horaire à utiliser lors du postupgrade.

   If you wish to use the &quot;multi timezone&quot; mode, refer to the [Time zones](../../migration/using/general-configurations.md#time-zones) section.

   Si vous utilisez Oracle comme base de données, vérifiez que les fichiers de fuseau horaire Oracle ont été correctement synchronisés entre le serveur d’applications et le serveur de base de données. For more on this, refer to the [Oracle](../../migration/using/general-configurations.md#oracle) section.

* Zones de sécurité

   Pour des raisons de sécurité, la plateforme Adobe Campaign n&#39;est plus accessible par défaut : vous devez configurer les zones de sécurité, et pour cela collecter, avant la migration, les adresses IP des utilisateurs.

   For more information, refer to the [Security](../../migration/using/general-configurations.md#security) section.

* Syntaxe

   Certaines syntaxes dans JavaScript peuvent être acceptées dans les versions 5.11 et 6.02 et ne sont plus acceptées dans la version v7, en raison de l’utilisation d’un nouvel interprète. For more information, refer to the [JavaScript](../../migration/using/general-configurations.md#javascript) section.

   De même, une nouvelle syntaxe est introduite dans Adobe Campaign v7 pour remplacer la syntaxe basée sur SQLData. Si vous utilisez des éléments de code avec cette syntaxe, vous devez les adapter. For more information, refer to the [SQLData](../../migration/using/general-configurations.md#sqldata) section.

* Mots de passe

   Vous devez configurer les mots de passe **Admin** et **Interne** . For more information, refer to the [User passwords](../../migration/using/before-starting-migration.md#user-passwords) section.

* Arborescence

   Si vous effectuez une migration à partir d’une plateforme v5.11, vous devez réorganiser les dossiers de structure en arborescence conformément aux normes Adobe Campaign v6. Pour plus d’informations, reportez-vous à la section Structure [de l’arborescence d’](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) Adobe Campaign v7.

* Interaction

   Si vous utilisez **Interaction**, vous devez supprimer toutes les références de schéma 6.02 qui n’existent plus dans v7. For more information, refer to the [Interaction](../../migration/using/general-configurations.md#interaction) section.

## Après la migration {#after-the-migration}

Après l&#39;exécution du **postupgrade**, les éléments suivants doivent être pris en compte et les paramétrages correspondants doivent être réalisés :

* Pages miroir

   Dans la version v6.x, le bloc de personnalisation des pages miroir a changé. Cette nouvelle version renforce la sécurité lors de l&#39;accès à ces pages.

   Si vous utilisez le bloc de personnalisation de la version v5 dans vos messages, les pages miroir ne s&#39;affichent pas. Adobe recommande vivement d&#39;utiliser le nouveau bloc de personnalisation lors de l&#39;insertion d&#39;une page miroir dans vos messages.

   A titre de solution temporaire (et pendant que les pages miroir sont toujours en ligne), vous pouvez revenir à l&#39;ancien bloc de personnalisation pour éviter ce problème en définissant l&#39;option **[!UICONTROL XtkAcceptOldPasswords]** sur **[!UICONTROL 1]**. Ce paramétrage n&#39;a aucun impact sur l&#39;utilisation du nouveau bloc de personnalisation de la version v6.x.

* Syntaxe

   If you encounter any errors related to the syntax, during the postupgrade, you must temporarily activate the **allowSQLInjection** option in the **serverConf.xml** file, as this gives you time to rewrite the code. Once the code is adapted, be sure to reactivate the security. For more on this, refer to the [SQLData](../../migration/using/general-configurations.md#sqldata) section.

* Conflits

   La migration étant effectuée au travers d&#39;un postupgrade, des conflits peuvent apparaître au niveau des rapports, formulaires ou applications web. Ces conflits peuvent être résolus manuellement depuis la console.

   See the [Conflicts](../../migration/using/general-configurations.md#conflicts) section.

* Tomcat

   Si vous avez personnalisé le dossier d’installation, vérifiez qu’il est correctement mis à jour après la migration. Pour plus de détails, reportez-vous à la section [Tomcat](../../migration/using/general-configurations.md#tomcat) .

* Rapports 

   Tous les rapports d&#39;usine utilisent à présent le moteur de rendu v6.x. Si vous aviez ajouté du code javascript dans ces rapports, certains éléments peuvent être altérés.

   Consult the [Reports](../../migration/using/general-configurations.md#reports) section.

* Applications Web

   After the postupgrade, if you have any problems connecting to your identified Web applications, you must activate the **allowUserPassword** and **sessionTokenOnly** options in the **serverConf.xml** file. Remember to then deactivate these two options. Pour plus d&#39;informations, consultez la section Applications [Web](../../migration/using/general-configurations.md#identified-web-applications) identifiées.

   Selon le type d&#39;applications Web et leur configuration, vous devez effectuer des manipulations complémentaires pour en assurer le bon fonctionnement.

   Voir la section Applications [](../../migration/using/general-configurations.md#web-applications) Web.

   If migrating from a v5.11 platform, additional configurations must be carried out: for more information, refer to the [Web applications](../../migration/using/specific-configurations-in-v5-11.md#web-applications) section.

* Zones de sécurité

   Avant de démarrer le serveur, vous devez configurer les zones de sécurité. Pour plus d&#39;informations, consultez [cette section](../../installation/using/configuring-campaign-server.md#defining-security-zones) et la section [Sécurité](../../migration/using/general-configurations.md#security) .

* Schémas

   Dans Red Hat, vous pouvez rencontrer des erreurs lors de la modification de certains schémas. For more on this, refer to the [Red-Hat](../../migration/using/general-configurations.md#red-hat) section.

* Workflows

   Si vous effectuez une migration à partir d’une plateforme v5.11, vous devez contrôler le répertoire d’exécution des processus. For more on this, refer to the [Workflows](../../migration/using/specific-configurations-in-v5-11.md#workflows) section.

* Effectuer un tracking

   Si vous effectuez une migration depuis une plateforme v5.11, vous devez configurer le mode de suivi. Voir à ce sujet la section [Suivre les ](../../migration/using/specific-configurations-in-v5-11.md#tracking).

* Page d&#39;accueil 

   If migrating from a v6.02 platform, you may define additional parameters to keep your old home page from v6.02. For more on this, refer to the [User friendliness: Home page and navigation](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation) section.

* Interaction

   Si vous utilisez **Interaction**, vous devez ajuster les paramètres après la migration. For more on this, refer to the [Interaction](../../migration/using/general-configurations.md#interaction) section.

