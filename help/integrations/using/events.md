---
product: campaign
title: Configuration des événements
description: Découvrez comment configurer des événements pour une implémentation personnalisée
feature: Triggers
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
audience: integrations
content-type: reference
exl-id: 13717b3b-d34a-40bc-9c9e-dcf578fc516e
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '1212'
ht-degree: 100%

---

# Configuration des événements pour une implémentation personnalisée {#events}



Une partie de cette configuration est un travail de développement personnalisé qui requiert les connaissances suivantes :

* connaissances opérationnelles de l’analyse JSON, XML et Javascript dans Adobe Campaign,
* connaissances opérationnelles des API QueryDef et Writer,
* notions de chiffrement et d&#39;authentification à l’aide de clés privées.

Étant donné que la modification du code JavaScript nécessite des compétences techniques, veuillez ne pas la modifier pas si vous ne le maîtrisez pas.

## Événements de traitement dans JavaScript {#events-javascript}

### Fichier JavaScript {#file-js}

Pipeline utilise une fonction JavaScript pour traiter chaque message. Cette fonction est définie par l’utilisateur.

Elle est configurée dans l’option **[!UICONTROL NmsPipeline_Config]** sous l’attribut « JSConnector ». Ce JavaScript est appelé chaque fois qu’un événement est reçu. Il est exécuté par le processus [!DNL pipelined].

L’exemple de fichier JavaScript est cus:triggers.js.

### Fonction JavaScript {#function-js}

Le JavaScript [!DNL pipelined] doit commencer avec une fonction spécifique.

Cette fonction est appelée une fois pour chaque événement :

```
function processPipelineMessage(xmlTrigger) {}
```

Elle doit être renvoyée comme

```
<undefined/>
```

Vous devez redémarrer [!DNL pipelined] après avoir modifié le fichier JavaScript.

### Format des données Trigger {#trigger-format}

Les données [!DNL trigger] sont transmises à la fonction JS au format XML.

* L’attribut **[!UICONTROL @triggerId]** contient le nom du [!DNL trigger].
* L&#39;élément **enrichments** au format JSON contient les données générées par Adobe Analytics et est attaché au déclencheur.
* **[!UICONTROL @offset]** est le « pointeur » vers le message. Il indique l’ordre du message dans la file d’attente.
* **[!UICONTROL @partition]** est un conteneur de messages dans la file d&#39;attente. Le décalage est relatif à une partition. <br>Il y a environ 15 partitions dans la file d&#39;attente.

Exemple :

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### Enrichissement du format de données {#enrichment-format}

>[!NOTE]
>
>Il s&#39;agit d&#39;un exemple spécifique parmi plusieurs implémentations possibles.

Le contenu est défini au format JSON dans Adobe Analytics pour chaque déclencheur.
Par exemple, dans un déclencheur LogoUpload_uploading_Visits :

* **[!UICONTROL eVar01]** peut contenir l&#39;identifiant de nouvel acheteur au format Chaîne utilisé pour la réconciliation avec les destinataires Campaign. <br>Il doit être réconcilié pour trouver l&#39;identifiant de nouvel acheteur, qui est la clé principale.

* **[!UICONTROL timeGMT]** peut contenir l&#39;heure du déclencheur côté Adobe Analytics au format UTC Epoch (secondes depuis le 01/01/1970 UTC).

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

### Ordre de traitement des événements{#order-events}

Les événements sont traités un par un, par ordre de décalage. Chaque thread du [!DNL pipelined] traite une partition différente.

Le « décalage » du dernier événement récupéré est stocké dans la base de données. Par conséquent, si le processus est arrêté, il redémarre à partir du dernier message. Ces données sont stockées dans le schéma intégré xtk:pipelineOffset.

Ce pointeur est spécifique à chaque instance et à chaque consommateur. Par conséquent, lorsque de nombreuses instances accèdent au même pipeline avec des consommateurs différents, ils reçoivent tous les messages et dans le même ordre.

Le paramètre **consumer** de l&#39;option de pipeline identifie l&#39;instance appelante.

Actuellement, il n&#39;existe aucun moyen d&#39;avoir des files d&#39;attente différentes pour des environnements distincts tels que &#39;staging&#39; ou &#39;dev&#39;.

### Journalisation et gestion des erreurs {#logging-error-handling}

Les logs tels que logInfo() sont dirigés vers le log [!DNL pipelined]. Des erreurs telles que logError() sont écrites dans le log [!DNL pipelined] et entraînent le placement de l’événement dans une file d’attente de reprise. Dans ce cas, vous devez vérifier le log en pipeline.
Les messages en erreur sont repris plusieurs fois dans la durée définie dans les options [!DNL pipelined].

À des fins de débogage et de surveillance, l&#39;intégralité des données de déclenchement est écrite dans le tableau de déclenchement dans le champ &quot;données&quot; au format XML. Une autre solution consiste à utiliser un logInfo() contenant les données de déclenchement dans le même but.

### Analyse des données {#data-parsing}

Cet exemple de code JavaScript analyse l’eVar01 dans les enrichissements.

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

Faites attention lors de l’analyse pour éviter toute erreur.
Puisque ce code est utilisé pour tous les déclencheurs, la plupart des données ne sont pas requises. Par conséquent, il peut être laissé vide lorsqu’il n’est pas présent.

### Stockage du déclencheur {#storing-triggers-js}

>[!NOTE]
>
>Il s&#39;agit d&#39;un exemple spécifique parmi plusieurs implémentations possibles.

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

Les performances de ce code doivent être optimales, car il s&#39;exécute à des fréquences élevées et peut avoir des effets négatifs potentiels pour d&#39;autres activités marketing. Surtout en cas de traitement de plus d&#39;un million d&#39;événements de déclenchement par heure sur le serveur Marketing ou s&#39;il n&#39;est pas correctement réglé.

Le contexte de ce JavaScript est limité. Toutes les fonctions de l’API ne sont pas disponibles. Par exemple, getOption() ou getCurrentdate() ne fonctionnent pas.

Pour accélérer le traitement, plusieurs threads de ce script sont exécutés en même temps. Le code doit être sécurisé par rapport aux threads.

## Stockage des événements {#store-events}

>[!NOTE]
>
>Il s&#39;agit d&#39;un exemple spécifique parmi plusieurs implémentations possibles.

### Schéma d’événement de pipeline {#pipeline-event-schema}

Les événements sont stockés dans une table de base de données. Elle est utilisée par les campagnes marketing pour cibler des clients et pour enrichir les emails à l&#39;aide de déclencheurs.
Bien que chaque déclencheur puisse avoir une structure de données distincte, tous les déclencheurs peuvent être conservés dans une seule table.
Le champ triggerType identifie à partir duquel les données sont déclenchées.

Voici un exemple de code de schéma pour cette table :

| Attribut | Type | Libellé | Description |
|:-:|:-:|:-:|:-:|
| pipelineEventId | Long | Clé primaire | Clé primaire interne du déclencheur. |
| data | Memo | Données de déclenchement | Contenu complet des données de déclenchement au format XML. À des fins de débogage et d’audit. |
| triggerType | Chaîne 50 | TriggerType | Nom du déclencheur. Identifie le comportement du client sur le site web. |
| shopper_id | Chaîne 32 | shopper_id | Identifiant interne du nouvel acheteur Défini par le workflow de réconciliation. Si la valeur est nulle, cela signifie que le client est inconnu dans Campaign. |
| shopper_key | Long | shopper_key | Identifiant externe du nouvel acheteur capturé par Analytics. |
| created | Datetime | Created | Heure à laquelle l’événement a été créé dans Campaign. |
| lastModified | Datetime | Dernière modification | Dernière modification de l’événement dans Adobe. |
| timeGMT | Datetime | Date et heure | Heure à laquelle l’événement a été généré dans Analytics. |

### Affichage des événements {#display-events}

Les événements peuvent être affichés avec un formulaire simple basé sur le schéma des événements.

>[!NOTE]
>
>Le nœud d’événement de pipeline n’est pas natif et doit être ajouté, de même que le formulaire associé doit être créé dans Campaign. Ces opérations sont limitées aux utilisateurs experts uniquement. Pour plus d’informations, consultez les sections suivantes : [Arborescence de navigation](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy) et [Éditer les formulaires](../../configuration/using/editing-forms.md).

![](assets/triggers_7.png)

## Traitement des événements {#processing-the-events}

### Workflow de réconciliation {#reconciliation-workflow}

La réconciliation est le processus de mise en correspondance du client d&#39;Adobe Analytics dans la base de données Campaign. Par exemple, les critères de correspondance peuvent être shopper_id.

Pour des raisons de performances, la correspondance doit être effectuée en mode batch par un workflow.
La fréquence doit être définie sur 15 minutes pour optimiser la charge de travail. Par conséquent, le délai entre la réception d’un événement dans Adobe Campaign et son traitement par un workflow marketing est de 15 minutes maximum.

### Options de réconciliation des unités dans JavaScript {#options-unit-reconciliation}

Il est possible d&#39;exécuter la requête de réconciliation pour chaque déclencheur dans le JavaScript. Les performances sont ainsi supérieures et les résultats sont plus rapides. Cela peut être nécessaire pour des cas pratiques spécifiques lorsqu’une grande réactivité est requise.

Il peut être difficile de l&#39;implémenter si aucun index n&#39;est défini sur shopper_id. Si les critères se trouvent sur un serveur de base de données distinct de celui du serveur marketing, il utilise un lien de base de données, qui offre de faibles performances.

### Workflow de purge {#purge-workflow}

Les déclencheurs sont traités dans l&#39;heure. Le volume peut être d’environ 1 million de déclencheurs par heure. Cela explique pourquoi un workflow de purge doit être mis en place. La purge s&#39;exécute une fois par jour et supprime tous les déclencheurs dont la date est antérieure à trois jours.

### Workflow de campagne {#campaign-workflow}

Le workflow de campagne de déclenchement est souvent similaire aux autres campagnes récurrentes qui ont été utilisées.
Par exemple, il peut débuter avec une requête sur les déclencheurs à la recherche d’événements spécifiques au cours de la dernière journée. Cette cible est utilisée pour envoyer l’email. Les enrichissements ou les données peuvent provenir du déclencheur. Il peut être utilisé en toute sécurité par Marketing car il ne nécessite aucune configuration.
