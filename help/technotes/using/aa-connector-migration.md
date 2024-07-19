---
product: campaign
title: Migration vers le connecteur Adobe Analytics
description: FAQ sur Campaign - Connecteur Analytics
feature: Technote, Analytics Integration
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements On-Premise et hybrides."
exl-id: 5bf61654-3d68-4560-a93f-7a768a2c5be4
hide: true
hidefromtoc: true
source-git-commit: a1dbef3e1feca1e3347de013db8bd7809d315016
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 100%

---

# Procédure de migration des intégrations Genesis existantes vers le connecteur Adobe Analytics {#acc-aa-faq}

À compter de la version 21.1.3 de Campaign Classic v7, le connecteur de données Adobe Analytics est obsolète. [En savoir plus](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html?lang=fr)

Le 1er août 2021, Adobe Campaign Classic a été supprimé de l’interface utilisateur des connecteurs de données héritée. Toutefois, les intégrations Campaign existantes continueront à collecter et à transmettre des données à Adobe Analytics jusqu’au 17 août 2022. Passée cette date, l’intégration cessera de collecter et de transmettre des données à Adobe Analytics.

Vous **devez implémenter** la nouvelle intégration du connecteur Adobe Analytics sur Adobe Exchange. Elle remplace l’ancienne intégration des connecteurs de données. Pour en savoir plus sur le connecteur Adobe Analytics, reportez-vous à [cette page](../../integrations/using/gs-aa.md).

Pour toute question sur ces modifications, consultez le [FAQ](#faq-aa). Pour plus d&#39;informations, contactez l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

>[!NOTE]
>
>Si vous effectuez une migration à partir d’un connecteur de données Adobe Analytics existant (anciennement connu sous le nom d’intégration Genesis) et que vous utilisez la nouvelle architecture de classification dans Adobe Analytics, vous avez besoin de versions de build commençant à 7.3.1 ou 8.4.1 pour pouvoir migrer vers le nouveau connecteur Adobe Analytics.

## Qu&#39;est-ce qui a changé ?

Une nouvelle intégration entre Campaign Classic v7 et Adobe Analytics est désormais disponible. Les modifications majeures sont répertoriées ci-dessous.

* La classification **Date de contact**, qui doit être de type date, a été abandonnée par Adobe Analytics. Pour les intégrations migrées, elle restera du même type. Pour toute **Date de contact** créée par Campaign, le type sera **Chaîne**.

* Les **règles de traitement** sont créées par Adobe Campaign dans le cadre de nouvelles intégrations. Les **règles de traitement** doivent être créées manuellement à partir d&#39;Adobe Analytics ou l&#39;implémentation JavaScript côté client doit être directement utilisée. Les **règles de traitement** resteront intactes pour les intégrations existantes.

* Les workflows techniques natifs et leur comportement restent les mêmes. Seules les API principales utilisées par les workflows pour transmettre/extraire des données vers/depuis Adobe Analytics ont été modifiées.

* Veuillez noter que le processus `nlserver` doit être configuré avec l&#39;utilisateur du compte technique IMS pour que le nouveau connecteur fonctionne. Ce changement doit être effectué par Adobe. Pour que celui-ci soit mis en œuvre, contactez l&#39;[Assistance clientèle Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* Si vous utilisiez des API Adobe Genesis dans des workflows personnalisés pour extraire et envoyer les données d’Adobe Analytics, vous devez désormais utiliser les nouvelles API Adobe Analytics 1.4/2.0. [En savoir plus](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## Cela vous concerne-t-il ?

Si vous utilisez le connecteur de données Adobe Analytics existant (précédemment connu sous le nom d&#39;intégration Genesis) et que l&#39;intégration a été implémentée sur un build inférieur à Campaign 21.1.3, cela vous impacte.

Découvrez comment vérifier votre version [dans cette section](../../integrations/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Comment effectuer la mise à jour ?

Vous devez effectuer la mise à niveau vers Campaign 21.1.3 (ou version ultérieure) **avant le 17 août 2022**.

Parce que vous êtes un client hébergé, Adobe collaborera avec vous afin de mettre à niveau votre ou vos instance(s) vers la nouvelle version. Vous pourrez ensuite utiliser le [connecteur Adobe Analytics](../../platform/using/gs-aa.md).

En tant que client On-premise/hybride, vous devez effectuer la mise à niveau vers l’une des versions les plus récentes pour bénéficier de la nouvelle intégration.
Une fois toutes les instances mises à niveau, vous pourrez [mettre en œuvre la nouvelle intégration](../../integrations/using/adobe-analytics-provisioning.md) vers le connecteur Adobe Analytics, et assurer une transition transparente.

## FAQ{#faq-aa}

**Comment puis-je obtenir des logs ?**

La configuration et les workflows de l&#39;interface utilisateur sont dotés de la journalisation **verbeuse**.

En mode verbeux, les en-têtes de requête et de réponse sont également imprimés pour chaque requête d&#39;API envoyée à Adobe Analytics.

En tant qu&#39;utilisateur On-premise, vous pouvez mettre en œuvre le mode verbeux comme suit :

* Pour activer le mode verbeux pour l&#39;interface utilisateur, procédez comme suit : réexécutez le processus `web` en mode verbeux.
* Pour activer le mode verbeux pour les workflows **webAnalytics** : sélectionnez l&#39;option **Exécuter dans le moteur** dans les propriétés du workflow, puis relancez `wfserver` en mode verbeux.

**Que signifie l&#39;erreur &quot;Le propriétaire de l&#39;intégration n&#39;est pas un administrateur&quot; ?**

En savoir plus sur l’erreur des connecteurs de données `Integration Owner Not Admin` dans [cette page](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Une fois la migration vers le nouveau connecteur terminée, qu&#39;advient-il des anciennes données et suites de rapports ?**

Après la migration, un nouveau connecteur (migré depuis l&#39;ancien connecteur) commence à transférer les données vers cette même suite de rapports et les données existantes ne sont pas affectées : il est ajouté aux données existantes.

**Certains eVar/événements/suites de rapports existants présents dans Analytics ne sont pas visibles dans Campaign. Que dois-je faire ?**

L&#39;intégration repose sur les données du jeton de compte technique pour le fonctionnement quotidien. S&#39;il manque une autorisation d&#39;accès à une dimension/mesure/suite de rapports du profil de produit associé à l&#39;utilisateur du compte technique, les API que nous utilisons seront simplement abandonnées pour ces requêtes.

Si nous lisons les détails d&#39;un composant Analytics (comme les mesures/dimensions/segments/suites de rapports), l&#39;API ne renverra pas ces composants dans le résultat (il peut alors sembler que quelque chose a été supprimé du côté Analytics ou est absent). L&#39;API Analytics rejettera ces requêtes et génèrera une erreur.

La solution consiste à mettre à jour le **profil de produit** dans le contexte utilisateur d’Analytics du jeton d’utilisateur technique avec les composants nouvellement créés/manquants en ajoutant ces composants dans [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}. Pour d&#39;autres conseils, contactez l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Liens utiles

* [Mise à niveau de votre environnement](../../production/using/build-upgrade.md)
* [FAQ sur la mise à niveau des builds](../../platform/using/faq-build-upgrade.md)
* [Télécharger le build Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Mettre à disposition la nouvelle console cliente auprès des utilisateurs et des utilisatrices](../../installation/using/client-console-availability-for-windows.md)
* [Installation de la console cliente Campaign](../../installation/using/installing-the-client-console.md)
