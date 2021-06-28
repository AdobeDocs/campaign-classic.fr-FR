---
product: campaign
title: Migration vers Adobe Analytics Connector
description: FAQ sur Campaign - Connecteur Analytics
hide: true
hidefromtoc: true
source-git-commit: 41478c656ffd4e113788149e6cca9ed00602789e
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 8%

---

# Comment migrer vers Adobe Analytics Connector {#acc-aa-faq}

À compter de la version 21.1.3 de Campaign Classic, le connecteur de données Adobe Analytics est obsolète. [En savoir plus](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

Le 1er août 2021, Adobe Campaign Classic sera supprimé de l’interface utilisateur des Data Connectors héritée. Toutefois, les intégrations Campaign existantes continueront à collecter et à transmettre des données à Adobe Analytics jusqu’au 1er mars 2022. Le 1er mars 2022, l’intégration cessera de collecter et de transmettre des données à Adobe Analytics.

Vous devez migrer vers la nouvelle intégration d’Adobe Analytics Connector sur Adobe Exchange qui remplace l’ancienne intégration des Data Connectors, comme indiqué dans [cette page](../platform/using/adobe-analytics-connector.md).


>[!NOTE]
>
>Pour toute question sur ces modifications, consultez la [FAQ](#faq-aa). Pour plus d’informations, contactez [l’ Assistance clientèle Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).


## Qu&#39;est-ce qui a changé ?

Une nouvelle intégration entre Campaign Classic v7 et Adobe Analytics est désormais disponible. Les modifications majeures sont répertoriées ci-dessous.

* L’intégration entre l’authentification Adobe Campaign Classic et Adobe Analytics est passée de l’utilisateur/mot de passe à Adobe Identity Management Service (IMS). Par conséquent, vous devez mettre en oeuvre Adobe IMS et vous connecter à Campaign [via un Adobe ID](../integrations/using/about-adobe-id.md), avant de démarrer l’implémentation d’Analytics Connector.

* La classification **Date de contact**, qui doit être de type date, a été abandonnée par Adobe Analytics. Pour les intégrations migrées, il restera du même type. Pour toute **Date de contact** créée par Campaign, le type sera **Chaîne**.

* **Les** règles de traitement sont créées par Adobe Campaign dans le cadre de nouvelles intégrations. Les **règles de traitement** doivent être créées manuellement à partir d’Adobe Analytics ou utiliser directement l’implémentation JavaScript côté client. **Les** règles de traitement resteront intactes pour les intégrations existantes.

* Les workflows techniques intégrés et leur comportement restent les mêmes. Seules les API principales utilisées par les workflows pour pousser/extraire des données vers/depuis Adobe Analytics ont été modifiées.

* Notez que le processus `nlserver` doit être configuré avec l’utilisateur du compte technique IMS pour que le nouveau connecteur fonctionne. Ce changement doit être effectué par Adobe. Pour que cela soit mis en oeuvre, contactez [l’Assistance clientèle Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* Si vous étiez des API Adobe Genesis dans des workflows personnalisés pour extraire et envoyer les données d’Adobe Analytics, vous devez maintenant utiliser les nouvelles API Adobe Analytics 1.4/2.0. [En savoir plus](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## Cela vous concerne-t-il ?

Si vous utilisez le connecteur de données Adobe Analytics existant (précédemment connu sous le nom d’intégration de Genesis) et que l’intégration a été implémentée sur une version inférieure à Campaign 21.1.3, cela vous impacte.

Découvrez comment vérifier votre version [dans cette section](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Comment effectuer la mise à jour ?

Vous devez effectuer la mise à niveau vers Campaign 21.1.3 (ou plus) **avant le 1er mars 2022**.

En tant que client hébergé, Adobe collaborera avec vous pour mettre à niveau votre ou vos instances vers la version la plus récente.

En tant que client on-premise/hybride, vous devez effectuer une mise à niveau vers l’une des versions les plus récentes pour bénéficier de la nouvelle intégration.

Une fois toutes les instances mises à niveau, vous pourrez [mettre en oeuvre la nouvelle intégration](../platform/using/adobe-analytics-connector.md) vers Adobe Analytics Connector, et assurer une transition transparente.


## FAQ{#faq-aa}

**Comment puis-je obtenir des logs ?**

La configuration et les workflows de l’interface utilisateur sont équipés de la journalisation **verbose**.

En mode verbeux, les en-têtes de requête et de réponse sont également imprimés pour chaque requête d’API envoyée à Adobe Analytics.

En tant qu&#39;utilisateur on-premise, vous pouvez mettre en oeuvre le mode verbeux comme suit :

* Pour activer le mode verbeux pour l’interface utilisateur, procédez comme suit : réexécutez le processus `web` en mode verbose.
* Pour activer le mode verbeux pour les workflows **webAnalytics** : sélectionnez l’option **Exécuter dans le moteur** dans les propriétés du workflow, puis relancez `wfserver` en mode verbeux.

**Que signifie l’erreur &quot;Propriétaire de l’intégration et non administrateur&quot; ?**

En savoir plus sur l’erreur des Data Connectors `Integration Owner Not Admin` dans [cette page](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Une fois la migration vers le nouveau connecteur terminée, qu’advient-il des anciennes données et suites de rapports ?**

Après la migration, un nouveau connecteur (migré depuis l’ancien connecteur) commence à transférer les données vers cette même suite de rapports et les données existantes ne seront pas affectées : il sera ajouté aux données existantes.

**Certaines eVar/événements/suites de rapports existantes présentes dans Analytics ne sont pas visibles dans Campaign. Que dois-je faire ?**

L’intégration repose sur les données du Jeton de compte technique pour le fonctionnement quotidien. S’il manque une autorisation d’accès à une suite de rapports/de dimensions du profil de produit associé à l’utilisateur du compte technique, les API que nous utilisons seront simplement abandonnées pour ces requêtes.

Si nous lisons les détails d’un composant Analytics (comme les mesures/dimensions/segments/suites de rapports), l’API ne renverra pas ces composants dans le résultat (qui peuvent sembler avoir été supprimé du côté Analytics ou n’être pas présent). L’API Analytics rejettera ces requêtes et fera une erreur.

La solution consiste à mettre à jour le **profil de produit** dans le contexte utilisateur d’Analytics du jeton d’utilisateur technique avec les composants nouvellement créés/manquants en ajoutant ces composants dans [Adobe Admin Console](https://adminconsole.adobe.com/). Pour plus d’informations, contactez [l’ Assistance clientèle Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Liens utiles

* [Mise à niveau de votre environnement](../production/using/build-upgrade.md)
* [FAQ sur l’upgrade de build](../platform/using/faq-build-upgrade.md)
* [Télécharger le build Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Mise à disposition de la nouvelle console cliente auprès des utilisateurs](../installation/using/client-console-availability-for-windows.md)
* [Installation de la console cliente Campaign](../installation/using/installing-the-client-console.md)
