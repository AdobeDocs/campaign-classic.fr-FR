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
source-git-commit: 9957dabca4c63d504a3d06cf527a97b79fee46d5
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 2%

---


# Pipeline, option NmsPipeline_Config {#nmspipeline_config}

Une fois l&#39;authentification effectuée, l&#39;oléoduc peut récupérer les événements et les traiter. Il traite uniquement les déclencheurs configurés dans l’Adobe Campaign, en ignorant les autres. Le déclencheur doit avoir été généré à partir d&#39;Analytics et envoyé au pipeline avant.
L’option peut également être configurée avec un caractère générique pour capturer tous les déclencheurs, quel que soit leur nom.

La configuration des déclencheurs est effectuée dans une option, sous **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. Le nom de l&#39;option est **[!UICONTROL NmsPipeline_Config]**. Le type de données est &quot;texte long&quot; au format JSON.

Cet exemple montre comment spécifier deux déclencheurs.

Collez le code JSON de ce modèle dans la valeur de l’option. Veillez à supprimer les commentaires.

```
{
    "topics": [ // list of "topics" that the pipelined is listening to.
        {
            "name": "triggers", // Name of the first topic: triggers.
            "consumer": "customer_dev", // Name of the instance that listens. 
            "triggers": [ // Array of triggers. 
                {
                    "name": "3e8a2ba7-fccc-49bb-bdac-33ee33cf02bf", // TriggerType ID from Analytics 
                    "jsConnector": "cus:triggers.js" // Javascript library holding the processing function.
                }, {
                    "name": "2da3fdff-13af-4c51-8ed0-05802a572e94", // Second TriggerType ID 
                    "jsConnector": "cus:triggers.js" // Can use the same JS for all.
                },
            ]
        }
    ]
}
```

Ce deuxième exemple capture tous les déclencheurs.

```
{
 "topics": [
    {
      "name": "triggers",
      "consumer":  "customer_dev",
      "triggers": [
        {
          "name": "*",
          "jsConnector": "cus:pipeline.js"
        }
      ]
    }
 ]
 }
```

>[!NOTE]
>
>La valeur [!DNL Trigger] UID d’un nom de déclencheur spécifique dans l’interface Analytics fait partie des paramètres de chaîne de requête d’URL de l’interface Triggers. L&#39;UID de type de trigger est transmis dans le flux de données du pipeline et le code peut être écrit dans le pipeline.JS pour mapper l&#39;UID du déclencheur à une étiquette conviviale qui peut être stockée dans une colonne Nom du déclencheur dans le schéma pipelineEvents.

## Le paramètre consommateur {#consumer-parameter}

Le pipeline fonctionne avec un modèle &quot;fournisseur et consommateur&quot;. Il peut y avoir beaucoup de consommateurs sur la même file d&#39;attente. Les messages sont &quot;consommés&quot; uniquement pour un consommateur individuel. Chaque consommateur reçoit sa propre &quot;copie&quot; des messages.

Le paramètre &quot;consommateur&quot; identifie l’instance comme l’un de ces consommateurs. Il s&#39;agit de l&#39;identité de l&#39;instance qui appelle le pipeline. Vous pouvez le remplir avec le nom de l’instance. Le service de pipeline effectue le suivi des messages récupérés par chaque client. L’utilisation de différents consommateurs pour différentes instances garantit que chaque message est envoyé à chaque instance.

## Configuration de l’option Pipeline {#configure-pipeline-option}

Ajouter ou modifier les déclencheurs Experience Cloud sous le tableau &quot;triggers&quot;; ne modifiez pas le reste.
Assurez-vous que le fichier JSON est valide avec l’aide de ce [site Web](http://jsonlint.com/).

* &quot;name&quot; est l’identifiant du déclencheur. Un caractère générique &quot;*&quot; capture tous les déclencheurs.
* &quot;Consumer&quot; est toute chaîne unique qui identifie de manière unique l’instance nlserver. Il peut généralement s’agir du nom d’instance lui-même. Pour plusieurs environnements (dev/stage/prod), veillez à ce qu’il soit unique pour chacun d’eux afin que chaque instance reçoive une copie du message.
* Pipelin prend également en charge la rubrique &quot;alias&quot;.

Redémarrez l’oléoduc après avoir apporté des modifications.
