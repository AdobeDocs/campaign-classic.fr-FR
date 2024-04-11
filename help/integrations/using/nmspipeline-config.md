---
product: campaign
title: Option de pipeline NmsPipeline_Config
description: Option de pipeline NmsPipeline_Config
feature: Triggers
badge-v8: label="S’applique également à la version 8" type="Positive" tooltip="S’applique également à Campaign v8"
audience: integrations
content-type: reference
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 98%

---


# Option de pipeline NmsPipeline_Config {#nmspipeline_config}



Une fois l&#39;authentification effectuée, [!DNL pipelined] peut récupérer les événements et les traiter. Il traite uniquement les déclencheurs configurés dans Adobe Campaign, en ignorant les autres. Le déclencheur doit avoir été généré à partir d&#39;Analytics et envoyé au pipeline avant.
L&#39;option peut également être configurée avec un caractère générique pour capturer tous les déclencheurs, quel que soit leur nom.

La configuration des déclencheurs s&#39;effectue dans une option, sous **[!UICONTROL Administration]** > **[!UICONTROL Plateforme]** > **[!UICONTROL Options]**. Le nom de l&#39;option est **[!UICONTROL NmsPipeline_Config]**. Le type de données est &quot;texte long&quot; au format JSON.

Cet exemple montre comment spécifier deux déclencheurs.

Collez le code JSON de ce modèle dans la valeur de l&#39;option. Veillez à supprimer les commentaires.

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
>La valeur UID [!DNL Trigger] d&#39;un nom de déclencheur spécifique dans l&#39;interface Analytics fait partie des paramètres de chaîne de requête d&#39;URL de l&#39;interface Triggers. L&#39;UID triggerType est transmis dans le flux de données du pipeline et le code peut être écrit dans le pipeline .JS pour mapper l&#39;UID du déclencheur avec un libellé convivial qui peut être stocké dans une colonne Nom du déclencheur du schéma pipelineEvents.

## Le paramètre consommateur {#consumer-parameter}

Le pipeline fonctionne avec un modèle &quot;fournisseur et consommateur&quot;. Il peut y avoir de nombreux consommateurs sur la même file d&#39;attente. Les messages sont &quot;consommés&quot; uniquement pour un consommateur individuel. Chaque consommateur reçoit sa propre &quot;copie&quot; des messages.

Le paramètre &quot;consommateur&quot; identifie l&#39;instance comme l&#39;un de ces consommateurs. Il s&#39;agit de l&#39;identité de l&#39;instance qui appelle le pipeline. Vous pouvez le remplir avec le nom de l&#39;instance. Le service de pipeline effectue le suivi des messages récupérés par chaque consommateur. L&#39;utilisation de différents consommateurs pour différentes instances garantit que chaque message est envoyé à chaque instance.

## Configuration de l&#39;option Pipeline {#configure-pipeline-option}

Ajoutez ou modifiez les Triggers Experience Cloud sous le tableau « triggers » ; ne modifiez pas le reste.
Assurez-vous que le fichier JSON est valide à l’aide de ce [site Web](https://jsonlint.com/).

* &quot;name&quot; est l&#39;identifiant du déclencheur. Un caractère générique &quot;*&quot; capture tous les déclencheurs.
* &quot;Consumer&quot; est formé de toute chaîne unique qui identifie de manière unique l&#39;instance nlserver. Il peut s&#39;agir généralement du nom de l&#39;instance lui-même. Pour plusieurs environnements (dev/stage/prod), veillez à ce qu&#39;il soit unique pour chacun d&#39;eux afin que chaque instance reçoive une copie du message.
* [!DNL Pipelined] prend également en charge le topic « alias ».

Redémarrez [!DNL pipelined] après avoir apporté des modifications. 
