---
title: A propos du tableau des destinataires personnalisés
seo-title: A propos du tableau des destinataires personnalisés
description: A propos du tableau des destinataires personnalisés
seo-description: null
page-status-flag: never-activated
uuid: 4b162da4-90d2-44ff-9f89-ff0275540359
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: c3ff8462-e47e-4637-8213-769fdeb86a57
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 668a0093616e1a2b49623b010ae5055f4d43d9b9

---


# A propos du tableau des destinataires personnalisés{#about-custom-recipient-table}

Cette section présente les principes d&#39;utilisation d&#39;une table de destinataires non standard.

Par défaut, Adobe Campaign propose une table de destinataires standard à laquelle sont liés des processus et fonctionnements d&#39;usine. La table des destinataires standard possède un nombre de champs prédéfinis et de tables liées qui peuvent être facilement étendues grâce à une table d&#39;extension.

Si cette méthode d&#39;extension offre une bonne flexibilité pour étendre une table, elle ne permet pas de réduire le nombre de champs ou de liens dans celle-ci. L&#39;utilisation d&#39;une table non standard, dite &#39;table de destinataires externe&#39;, permet une plus grande flexibilité, mais nécessite certaines précautions dans sa mise en œuvre.

## Spécificités {#precisions}

Cette fonctionnalité permet notamment à Adobe Campaign d&#39;exploiter des données provenant d&#39;une base de données externe : ces données seront utilisées comme ensemble de profils pour les diffusions. La mise en oeuvre de ce mode de fonctionnement implique plusieurs spécificités qui peuvent s&#39;avérer pertinentes selon les besoins du client. Ainsi :

* Pas de flux de mise à jour vers et depuis la base Adobe Campaign : les données de cette table peuvent être mises à jour directement via le moteur de base de données qui l&#39;héberge.
* Pas de changements dans les processus qui opèrent sur la base existante.
* Utilisation d&#39;une base de profils avec une structure différente de celle proposée en standard : possibilité de diffuser avec une même instance vers des profils enregistrés dans des tables différentes, avec des structures différentes.
* Pas de changements ou de maintenance requis lors des mises à jour de la base de données Adobe Campaign.
* La table des destinataires standard est inutile si vous n&#39;avez pas l&#39;utilité de la plupart des champs de la table ou si le modèle de données n&#39;est pas centré sur les destinataires.
* Un volume important de profils nécessite une table avec peu de champs pour être efficace. La table des destinataires standard possède trop de champs dans ce cas précis.

Cette section décrit les points essentiels permettant de réaliser le mapping de tables existantes dans Adobe Campaign puis le paramétrage à réaliser pour permettre l&#39;exécution de diffusions en se basant sur n&#39;importe quelle table. Enfin, elle présente le mode de mise à disposition pour les utilisateurs d&#39;interfaces de requêtage aussi pratiques que celles disponibles avec la table standard des destinataires. La connaissance des principes de conception de schémas et d&#39;écrans est requise pour aborder les éléments présentés dans cette section.

## Recommandations et limitations  {#recommendations-and-limitations}

L&#39;utilisation d&#39;une table de destinataires externe implique les limitations suivantes :

* Adobe Campaign ne prend pas en charge plusieurs schémas de destinataires, appelés schémas de ciblage, liés aux mêmes schémas de journal de diffusion et/ou de journal de suivi. Cela peut par ailleurs entraîner des anomalies dans la réconciliation des données par la suite.

   Le graphique ci-dessous décrit la structure relationnelle requise pour chaque schéma de destinataire personnalisé :
   ![](assets/custom_recipient_limitation.png)

   Nous vous recommandons :

   * Dédiant les schémas **[!UICONTROL nms:BroadLogRcp]** et **[!UICONTROL nms:TrackingLogRcp]** aux **[!UICONTROL nms:Recipientschema]** prêts à l&#39;emploi. Ces deux tables de journal ne doivent pas être liées à une autre table de destinataires personnalisée.
   * Définition de schémas de journal large et de journal de suivi personnalisés dédiés pour chaque nouveau schéma de destinataire personnalisé. Cela peut être fait automatiquement lors de la configuration du mappage de la cible, voir Mappage [de](../../configuration/using/target-mapping.md)Target.

* Il n&#39;est pas possible d&#39;utiliser les **[!UICONTROL Services et Abonnements]** standards proposés dans le produit.

   Ainsi, le fonctionnement présenté dans [cette section](../../delivery/using/managing-subscriptions.md) n&#39;est pas applicable.

* Le lien avec la table des **[!UICONTROL visiteurs]** n&#39;est pas opérationnel.

   Thus, to use the **[!UICONTROLSocial Marketing]** module you must configure the storage step to reference the correct table.

   De même, dans le cadre de l&#39;utilisation des fonctionnalités de parainage, le modèle standard de transfert du message initial doit être adapté.

* Il n&#39;est pas possible d&#39;ajouter manuellement des profils dans une liste.

   Ainsi, le fonctionnement présenté dans [cette section](../../platform/using/creating-and-managing-lists.md) n&#39;est pas applicable sans une configuration supplémentaire.

   >[!NOTE]
   >
   >Vous pouvez toujours créer des listes de destinataires à l’aide de processus. Pour plus d’informations, reportez-vous à [Création d’une liste de profils avec un flux de travail](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

Il est également recommandé de vérifier les valeurs par défaut utilisées dans les différents paramétrages d&#39;usine : plusieurs adaptations doivent être apportées, selon les fonctionnalités utilisées.

Par exemple :

* Certain standard reports, particularly those offered by **Interaction** and the **Mobile Applications** must be redeveloped. Reportez-vous à la section [Gestion des rapports](../../configuration/using/managing-reports.md) .
* The default configurations for certain workflow activities reference the standard recipients table (**[!UICONTROL nms:recipient]**): these configurations must be changed when used for an external recipients table. Reportez-vous à la section [Gestion des processus](../../configuration/using/managing-workflows.md) .
* Le bloc de personnalisation du **[!UICONTROL Lien de désinscription]** standard doit être adapté.
* Le mapping de ciblage des modèles de diffusion standard doit être modifié.
* Les formulaires v4 ne sont pas compatibles avec l&#39;utilisation d&#39;une table de destinataires externe : vous devez utiliser les applications Web.

