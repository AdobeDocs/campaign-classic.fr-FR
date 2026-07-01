---
product: campaign
title: Architectures réparties
description: Architectures réparties
feature: Interaction, Offers, Architecture
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 083be073-aad4-4c81-aff2-77f5ef3e80db
TQID: https://experienceleague.adobe.com/UYcZcSX8pLO0mCB8OW6WWx9qQ4vg13FAel6R7moeMA8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
feature_v2:
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
subfeature_v2: []
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 1030
ht-degree: 100%

---

# Architectures réparties{#distributed-architectures}



## Principe {#principle}

Pour pouvoir assurer l’évolutivité et offrir un service 24h/24, 7j/7 sur le canal entrant, vous pouvez utiliser Interaction avec une architecture distribuée.Ce type d’architecture est déjà utilisé avec Message Center et est constitué de plusieurs instances :

* une ou plusieurs instances de pilotage dédiées au canal sortant et contenant la base marketing et l&#39;environnement en édition
* une ou plusieurs instances d&#39;exécution dédiées au canal entrant

![](assets/interaction_powerbooster_schema.png)

>[!NOTE]
>
>Les instances de pilotage sont dédiées au canal entrant et contiennent la version en ligne du catalogue.Chaque instance d’exécution est indépendante et dédiée à un segment de contact (par exemple, une instance d’exécution par pays).Les appels au moteur d’offre doivent être effectués directement sur l’instance d’exécution (une URL spécifique par instance d’exécution).Étant donné que la synchronisation entre les instances n&#39;est pas automatique, les interactions d&#39;un même contact doivent être envoyées à travers la même instance.

## Synchronisation des propositions {#proposition-synchronization}

La synchronisation des offres s’effectue par le biais de packages.Sur les instances d’exécution, tous les objets de catalogue sont précédés du nom du compte externe.Cela signifie que plusieurs instances de pilotage (instances de développement et de production, par exemple) peuvent être prises en charge sur une même instance d’exécution.

>[!IMPORTANT]
>
>Nous vous recommandons fortement d&#39;utiliser des noms internes courts et explicites.

Les offres sont automatiquement déployées puis publiées sur les instances d&#39;exécution et l&#39;instance de pilotage.

Les offres supprimées dans l&#39;environnement en édition sont désactivées sur toutes les instances en ligne. Les propositions et les offres obsolètes sont automatiquement supprimées de toutes les instances lorsque la période de purge (définie dans l’assistant de déploiement sur chaque instance) et la période glissante (définie dans les règles de typologie des propositions entrantes) sont dépassées.

![](assets/interaction_powerbooster_schema2.png)

Un workflow est créé pour chaque environnement et compte externe pour la synchronisation des propositions.La fréquence de synchronisation peut être ajustée pour chaque environnement et compte externe.

## Limites {#limitations}

* Si vous utilisez la fonction de basculement (fall back) d&#39;un environnement anonyme vers un environnement identifié, ces deux environnements doivent être sur la même instance d&#39;exécution.
* La synchronisation entre plusieurs instances d’exécution n’est pas effectuée en temps réel.Les interactions d’une même personne contact doivent être envoyées à la même instance.L’instance de pilotage doit être dédiée au canal sortant (pas en temps réel).
* La base de données marketing n’est pas synchronisée automatiquement.Les données marketing utilisées dans les règles de poids et d’éligibilité doivent être dupliquées sur les instances d’exécution.Ce processus n’est pas fourni en standard, vous devez le développer pendant la période d’intégration.
* La synchronisation des propositions s&#39;effectue exclusivement par connexion FDA.
* Si vous utilisez Interaction et Message Center sur une même instance, la synchronisation s&#39;effectuera par protocole FDA dans les deux cas.

## Configuration des packages {#packages-configuration}

Les éventuelles extensions de schémas directement liées à **Interaction** (offres, propositions, personnes destinataires, etc.)doivent être déployées sur les instances d’exécution.

Le package Interaction doit être installé sur toutes les instances (pilotage et exécution).Deux packages supplémentaires sont disponibles : un package à installer sur les instances de pilotage, et un package à installer sur chaque instance d’exécution.

>[!NOTE]
>
>Lors de l’installation du package, les champs de type **long** de la table **nms:proposition** comme l’identifiant de la proposition, deviennent des champs de type **int64**.Les types de données sont décrits dans [cette section](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data).

La durée de conservation des données doit être configurée sur chaque instance (via la fenêtre **[!UICONTROL Purge des données]** dans l’assistant de déploiement).Sur les instances d&#39;exécution, cette période doit correspondre à la profondeur historique nécessaire au calcul des règles de typologie (période glissante) et d&#39;éligibilité.

Sur les instances de pilotage :

1. Créez un compte externe par instance d&#39;exécution :

   ![](assets/interaction_powerbooster1.png)

   * Renseignez le libellé et un nom interne court et explicite.
   * Sélectionnez le type **[!UICONTROL Instance d&#39;exécution]**.
   * Cochez l&#39;option **[!UICONTROL Activé]**.
   * Renseignez les paramètres de connexion à l&#39;instance d&#39;exécution.
   * Chaque instance d&#39;exécution doit être associée à un identifiant. Cet identifiant est attribué lorsque vous cliquez sur le bouton **[!UICONTROL Initialiser la connexion]**.
   * Cochez le type d&#39;application utilisée : **[!UICONTROL Message Center]**, **[!UICONTROL Interaction]**, ou les deux.
   * Saisissez le compte FDA utilisé.Un profil d’opérateur ou d’opératrice doit être créé sur les instances d’exécution et doit disposer des droits de lecture et d’écriture suivants sur la base de données de l’instance concernée :

     ```
     grant SELECT ON nmspropositionrcp, nmsoffer, nmsofferspace, xtkoption, xtkfolder TO user;
     grant DELETE, INSERT, UPDATE ON nmspropositionrcp TO user;
     ```

   >[!NOTE]
   >
   >L&#39;adresse IP de l&#39;instance de pilotage doit être autorisée sur les instances d&#39;exécution.

1. Configurez l&#39;environnement :

   ![](assets/interaction_powerbooster2.png)

   * Ajoutez la liste des instances d&#39;exécutions.
   * Définissez pour chacune la fréquence de synchronisation et les critères de filtrage (par exemple par pays).

     >[!NOTE]
     >
     >En cas d’erreur, vous pouvez consulter les workflows de synchronisation et les notifications d’offres.Ils se trouvent dans les workflows techniques de l’application.

Si, pour des raisons d’optimisation, seule une partie de la base de données marketing est dupliquée sur les instances d’exécution, vous pouvez définir un schéma restreint lié à l’environnement afin de permettre aux utilisateurs et utilisatrices de n’utiliser que les données disponibles sur les instances d’exécution.Vous pouvez créer une offre utilisant des données non disponibles sur les instances d’exécution.Pour cela, vous devez désactiver la règle sur les autres canaux en limitant cette règle au canal sortant (champ **[!UICONTROL Pris en compte si]**).

![](assets/ita_filtering.png)

## Options de maintenance {#maintenance-options}

Voici la liste des options de maintenance disponibles sur l&#39;instance de pilotage :

>[!IMPORTANT]
>
>Ces options ne doivent être utilisées que dans des cas de maintenance spécifiques.

* **`NmsInteraction_LastOfferEnvSynch_<offerEnvId>_<executionInstanceId>`** : date de dernière synchronisation d&#39;un environnement sur une instance donnée.
* **`NmsInteraction_LastPropositionSynch_<propositionSchema>_<executionInstanceIdSource>_<executionInstanceIdTarget>`** : date de dernière synchronisation des propositions d&#39;un schéma donné d&#39;une instance vers une autre.
* **`NmsInteraction_MapWorkflowId`** : option contenant la liste de tous les workflows de synchronisation générés.

L&#39;option suivante est disponible sur les instances d&#39;exécution :

**NmsExecutionInstanceId** : option contenant l&#39;identifiant de l&#39;instance.

## Installation des packages {#packages-installation}

Si votre instance ne disposait pas précédemment du package Interaction, aucune migration n’est nécessaire.Par défaut, la table des propositions sera en 64 bits une fois les packages installés.

>[!IMPORTANT]
>
>Selon le volume de propositions existantes dans votre instance, cette opération peut être très longue.

* Si votre instance ne comporte pas ou peu de propositions, aucune modification manuelle de la table des propositions n’est nécessaire.La modification sera effectuée lors de l’installation des packages.
* Si votre instance comporte un grand nombre de propositions, il est préférable de changer la structure de la table des propositions avant l’installation des packages de pilotage et d’exécution.Nous vous recommandons d’exécuter les requêtes pendant une période de faible activité.

>[!NOTE]
>
>Si vous avez effectué des paramétrages spécifiques dans la table des propositions, adaptez les requêtes en conséquence.

### PostgreSQL {#postgresql}

Deux méthodes sont disponibles.La première (utilisation d’une table de travail) est un peu plus rapide.

**Table de travail**

```
CREATE TABLE NmsPropositionRcp_tmp AS SELECT * FROM nmspropositionrcp WHERE 0=1;
ALTER TABLE nmspropositionrcp_tmp
  ALTER COLUMN ipropositionid TYPE bigint,
  ALTER COLUMN iinteractionid TYPE bigint;
INSERT INTO nmspropositionrcp_tmp SELECT * FROM nmspropositionrcp;
DROP TABLE nmspropositionrcp;
CREATE INDEX proposition_id ON NmsPropositionRcp (ipropositionid);
CREATE INDEX nmspropositionrcp_deliveryid ON NmsPropositionRcp (ideliveryid);
CREATE INDEX nmspropositionrcp_lastmodified ON NmsPropositionRcp (tslastmodified);
CREATE INDEX nmspropositionrcp_offerid ON NmsPropositionRcp (iofferid);
CREATE INDEX nmspropositionrcp_offerspaceid ON NmsPropositionRcp (iofferspaceid);
CREATE INDEX nmspropositionrcp_recipientidid ON NmsPropositionRcp (irecipientid);
ALTER TABLE nmspropositionrcp_tmp RENAME TO nmspropositionrcp;
```

**Alter Table**

```
ALTER TABLE nmspropositionrcp
  ALTER COLUMN ipropositionid TYPE bigint,
  ALTER COLUMN iinteractionid TYPE bigint;
```

### Oracle {#oracle}

La modification de la taille d’un type **Number** n’entraîne pas la réécriture des valeurs ou de l’index.Elle est donc immédiate.

La requête à exécuter est la suivante :

```
ALTER TABLE nmspropositionrcp MODIFY (
ipropositionid NUMBER(19, 0),
iinteractionid NUMBER(19, 0)
);
```

### MSSQL {#mssql}

Les requêtes à exécuter sont les suivantes :

```
SELECT * INTO NmsPropositionRcp_tmp FROM NmsPropositionRcp WHERE 1 = 0;
GO
ALTER TABLE NmsPropositionRcp_tmp ALTER COLUMN ipropositionid BIGINT;
GO
ALTER TABLE NmsPropositionRcp_tmp ALTER COLUMN iinteractionid BIGINT;
GO
INSERT INTO NmsPropositionRcp_tmp SELECT * FROM NmsPropositionRcp;
GO
DROP TABLE NmsPropositionRcp;
GO
sp_rename 'NmsPropositionRcp_tmp', NmsPropositionRcp
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR dWeight
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iDeliveryId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iEngineType
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iInteractionId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iOfferId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iOfferSpaceId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iPropositionId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iRank
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iRecipientId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iStatus
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_deliveryId ON NmsPropositionRcp (iDeliveryId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_eventDate ON NmsPropositionRcp (tsEvent)
GO
CREATE UNIQUE NONCLUSTERED INDEX NmsPropositionRcp_id ON NmsPropositionRcp (iPropositionId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_lastModified ON NmsPropositionRcp (tsLastModified)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_offerId ON NmsPropositionRcp (iOfferId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_offerSpaceI ON NmsPropositionRcp (iOfferSpaceId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_recipientId ON NmsPropositionRcp (iRecipientId)
GO
```
