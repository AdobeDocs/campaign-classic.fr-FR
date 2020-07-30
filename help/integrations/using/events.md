---
title: Configuration de l'intégration
seo-title: Configuration de l'intégration
description: Configuration de l'intégration
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f70468e3dd7003a18812d07669f10c561e8bef7
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 2%

---


# Événements Triggers {#events}

## événements de traitement dans JavaScript {#events-javascript}

### Fichier JavaScript {#file-js}

Pipeline utilise une fonction JavaScript pour traiter chaque message. Cette fonction est définie par l’utilisateur.

Il est configuré dans l&#39;option **[!UICONTROL NmsPipeline_Config]** sous l&#39;attribut &quot;JSConnector&quot;. Ce javascript est appelé chaque fois qu&#39;un événement est reçu. Il est géré par le [!DNL pipelined] processus.

L&#39;exemple de fichier JS est cus:triggers.js.

### JavaScript, fonction {#function-js}

Le [!DNL pipelined] code JavaScript doit être début avec une fonction spécifique.

Cette fonction est appelée une fois pour chaque événement :

```
function processPipelineMessage(xmlTrigger) {}
```

Il doit retourner comme

```
<undefined/>
```

Redémarrez [!DNL pipelined] après avoir modifié le fichier JS.

### Format de données de déclenchement {#trigger-format}

Les [!DNL trigger] données sont transmises à la fonction JS. Il est au format XML.

* L&#39;attribut **[!UICONTROL @triggerId]** contient le nom du [!DNL trigger].
* L’élément **enrichissements** au format JSON contient les données générées par Analytics et est associé au déclencheur.
* **[!UICONTROL @offset]** est le &quot;pointeur&quot; vers le message. Il indique l’ordre du message dans la file d’attente.
* **[!UICONTROL @partitio]**n est un conteneur de messages dans la file d&#39;attente. Le décalage est relatif à une partition. <br>Il y a environ 15 partitions dans la file d&#39;attente.

Exemple :

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### Format de données d&#39;Enrichissement {#enrichment-format}

>[!NOTE]
>
>Il s&#39;agit d&#39;un exemple spécifique de différentes implémentations possibles.

Le contenu est défini dans Analytics pour chaque déclencheur. Il est au format JSON.
Par exemple, dans un déclencheur LogoUpload_uploading_Visits :

* **[!UICONTROL eVar01]** peut contenir l&#39;identifiant Shopper utilisé pour la conciliation avec les destinataires Campaign. Il est au format Chaîne. <br>Il doit être rapproché pour trouver l&#39;identifiant Shopper, qui est la clé principale.

* **[!UICONTROL timeGMT]** peut contenir l’heure du déclencheur côté Analytics. Il est au format Epoque UTC (secondes depuis le 01/01/1970 UTC).

Exemple :

```
{
 "analyticsHitSummary": {
 "dimensions": {
 "eVar01": {
 "type": "string",
 "data": ["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],
 "name": " eVar01",
 "source": "session summary"
 },
 "timeGMT": {
 "type": "int",
 "data": [1469164186, 1469164195],
 "name": "timeGMT",
 "source": "session summary"
 }
 },
 "products": {}
 }
 }
```

### Ordre de traitement des événements {#order-events}

Les événements sont traités un par un, par ordre de décalage. Chaque thread du [!DNL pipelined] processus traite une partition différente.

Le &quot;décalage&quot; du dernier événement récupéré est stocké dans la base de données. Par conséquent, si le processus est arrêté, il redémarre à partir du dernier message. Ces données sont stockées dans le schéma intégré xtk:pipelineOffset.

Ce pointeur est spécifique à chaque instance et à chaque consommateur. Par conséquent, lorsque de nombreux utilisateurs accèdent au même pipeline avec des consommateurs différents, ils reçoivent tous les messages et dans le même ordre.

Le paramètre &quot;consommateur&quot; de l’option de pipeline identifie l’instance appelante.

Actuellement, il n&#39;existe aucun moyen d&#39;avoir des files d&#39;attente différentes pour des environnements distincts tels que &quot;test&quot; ou &quot;dev&quot;.

### Journalisation et gestion des erreurs {#logging-error-handling}

Les journaux tels que logInfo() sont dirigés vers le [!DNL pipelined] journal. Des erreurs telles que logError() sont consignées dans le [!DNL pipelined] journal et entraînent le placement du événement dans une file d&#39;attente de nouvelle tentative. Vérifier le journal en pipeline.
Les messages en erreur sont répétés plusieurs fois dans la durée définie dans les [!DNL pipelined] options.

À des fins de débogage et de surveillance, les données de déclenchement complètes sont écrites dans la table de déclenchement. Il se trouve dans le champ &quot;données&quot; au format XML. Une autre solution consiste à utiliser un logInfo() contenant les données de déclenchement dans le même but.

### Analyse des données {#data-parsing}

Cet exemple de code JS analyse l&#39;eVar01 dans les enrichissements.

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var shopper_id = ""
 if (xmlTrigger.enrichments.length() > 0)
 {
 if (xmlTrigger.enrichments.toString().match(/eVar01/) != undefined)
 {
 var enrichments = JSON.parse(xmlTrigger.enrichments.toString())
 shopper_id = enrichments.analyticsHitSummary.dimensions. eVar01.data[0]
 }
 }
 (…)
 }
```

Soyez prudent lors de l’analyse pour éviter les erreurs.
Puisque ce code est utilisé pour tous les déclencheurs, la plupart des données ne sont pas requises. Par conséquent, il peut être laissé vide lorsqu’il n’est pas présent.

### Stockage du déclencheur {#storing-triggers-js}

>[!NOTE]
>
>Il s&#39;agit d&#39;un exemple spécifique de différentes implémentations possibles.

Cet exemple de code JS enregistre le déclencheur dans la base de données.

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var event = 
 <pipelineEvent
 xtkschema = "cus:pipelineEvent"
 _operation = "insert"
 created = {timeNow}
 lastModified = {timeNow}
 triggerType = {triggerType}
 timeGMT = {timeGMT}
 shopper_id = {shopper_id}
 data = {xmlTrigger.toXMLString()}
 />
 xtk.session.Write(event)
 return <undef/>; 
 }
```

### Contraintes {#constraints}

Les performances de ce code doivent être optimales puisqu&#39;il s&#39;exécute à des fréquences élevées. D&#39;autres activités marketing peuvent avoir des effets négatifs. Surtout si vous traitez plus d’un million de événements de déclenchement par heure sur le serveur Marketing. Ou s&#39;il n&#39;est pas correctement réglé.

Le contexte de ce JavaScript est limité. Toutes les fonctions de l’API ne sont pas disponibles. Par exemple, getOption() ou getCurrent() ne fonctionnent pas.

Pour accélérer le traitement, plusieurs threads de ce script sont exécutés en même temps. Le code doit être thread-safe.

## Stockage des événements {#store-events}

>[!NOTE]
>
>Il s&#39;agit d&#39;un exemple spécifique de différentes implémentations possibles.

### schéma de événement de tuyau {#pipeline-event-schema}

Les Événements sont stockés dans une table de base de données. Il est utilisé par les campagnes marketing pour cible des clients et pour enrichir les courriers électroniques à l’aide de déclencheurs.
Bien que chaque déclencheur puisse avoir une structure de données distincte, tous les déclencheurs peuvent être conservés dans un seul tableau.
Le champ triggerType identifie à partir duquel les données sont déclenchées.

Voici un exemple de code de schéma pour ce tableau :

| Attribut | Type | Libellé | Description |
|:-:|:-:|:-:|:-:|
| pipelineEventId | Long | Clé primaire | Clé primaire interne du déclencheur. |
| data | Memo | Données de déclenchement | Contenu complet des données de déclenchement au format XML. À des fins de débogage et d’audit. |
| triggerType | Chaîne 50 | TriggerType | Nom du déclencheur. Identifie le comportement du client sur le site Web. |
| shopper_id | Chaîne 32 | shopper_id | Identifiant interne du commerçant. Défini par le processus de réconciliation. Si la valeur est nulle, cela signifie que le client est inconnu à Campaign. |
| shopper_key | Long | shopper_key | L&#39;Identifiant externe du commerçant capturé par Analytics. |
| created | Datetime | Created | Heure à laquelle le événement a été créé dans Campaign. |
| lastModified | Datetime | Dernière modification | Dernière modification du événement en Adobe. |
| timeGMT | Datetime | Horodatage | Heure à laquelle le événement a été généré dans Analytics. |

### Affichage des événements {#display-events}

Les événements peuvent être affichés avec un formulaire simple basé sur le schéma des événements.

>[!NOTE]
>
>Le noeud de Événement Pipeline n’est pas intégré et doit être ajouté, de même que le formulaire associé doit être créé dans Campaign. Ces opérations sont limitées aux utilisateurs experts uniquement. Pour plus d’informations à ce sujet, reportez-vous aux sections suivantes : [Hiérarchie](../../configuration/using/about-navigation-hierarchy.md) de navigation et [Modification de formulaires](../../configuration/using/editing-forms.md).

![](assets/triggers_7.png)

## Traitement des événements {#processing-the-events}

### Processus de rapprochement {#reconciliation-workflow}

La réconciliation est le processus de mise en correspondance du client d’Analytics avec la base de données Campaign. Par exemple, les critères de correspondance peuvent être shopper_id.

Pour des raisons de performances, la correspondance doit être effectuée en mode batch par un processus.
La fréquence doit être définie à 15 minutes pour optimiser la charge de travail. Par conséquent, le délai entre la réception d’un événement dans l’Adobe Campaign et son traitement par un processus marketing est de 15 minutes maximum.

### Options de réconciliation des unités dans JavaScript {#options-unit-reconciliation}

En théorie, il est possible d&#39;exécuter la requête de réconciliation pour chaque déclencheur dans le code JavaScript. Il a un impact sur les performances plus élevé et donne des résultats plus rapides. Il peut être nécessaire pour des cas d’utilisation spécifiques lorsque la réactivité est nécessaire.

Il peut être difficile de le faire si aucun index n&#39;est défini sur shopper_id. Si les critères se trouvent sur un serveur de base de données distinct de celui du serveur marketing, il utilise un lien de base de données, qui présente de faibles performances.

### Processus de purge {#purge-workflow}

Les déclencheurs sont traités dans l’heure, il n’y a donc aucune raison de les conserver longtemps. Le volume peut être d&#39;environ 1 million de déclencheurs par heure. Il explique pourquoi un processus de purge doit être mis en place. La purge supprime tous les déclencheurs qui ont plus de trois jours et s’exécute une fois par jour.

### Processus Campaign {#campaign-workflow}

Le processus de déclenchement d’une campagne est souvent similaire aux autres campagnes récurrentes qui ont été utilisées.
Par exemple, il peut début avec une requête sur les déclencheurs à la recherche de événements spécifiques au cours de la dernière journée. Cette cible est utilisée pour envoyer le courriel. Les Enrichissements ou les données peuvent provenir du déclencheur. Il peut être utilisé en toute sécurité par Marketing car il ne nécessite aucune configuration.
