---
product: campaign
title: Gestion des accès
description: En savoir plus sur les bonnes pratiques relatives à la gestion des accès
feature: Installation, Access Management, Permissions
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
TQID: https://experienceleague.adobe.com/dbC74X04V5SFr7fWOl1b0-Br-x-jjHFNvMSX9Y6M-JQ
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: ht
source-wordcount: 377
ht-degree: 100%

---

# Gestion des accès {#access-management}



## Opérateur webApp

L’opérateur webApp par défaut est un administrateur. Pour améliorer la sécurité, suivez les instructions suivantes :

* Remplacez l’admin nommé à droite de cet opérateur par un nouvel admin (qui peut être nommé « webapp »). Pour plus d’informations, consultez [cette page](../../platform/using/access-management.md).

* Ajoutez l’opérateur webApp à des dossiers (principalement des dossiers de destinataires) afin d’octroyer un accès en lecture/écriture aux destinataires. Pour plus d’informations à ce sujet, consultez [cette page](../../platform/using/access-management.md).

* Si vous utilisez une instance multimarque (ou multizone), vous souhaiterez peut-être répartir l’accès aux applications web entre différents dossiers de destinataires. Pour ce faire :

   1. Dupliquez l’opérateur webApp.

   1. Saisissez un nom pour chaque doublon. Par exemple : webapp_brand, webapp_brand2, etc.

   1. Dupliquez un modèle d’application web pour disposer d’un modèle par marque et modifiez les propriétés afin de changer l’opérateur en sélectionnant l’option Utiliser un compte spécifique.  En savoir plus sur [cette page](../../web/using/defining-web-forms-properties.md).

## Groupes de sécurité et opérateurs admin

Créez suffisamment de groupes de sécurité afin de donner aux opérateurs des droits suffisants pour qu’ils puissent effectuer les opérations nécessaires (et pas davantage).

N’utilisez pas l’opérateur admin (ou ne le partagez pas).Créez un opérateur par personne physique (pour un audit/un enregistrement précis).Ajoutez les administrateurs et administratrices que vous venez de nommer au groupe d’administrateurs et d’administratrices.Si vous n’utilisez pas l’opérateur admin, ne le supprimez pas et ne le désactivez pas : cet opérateur est utilisé en interne pour exécuter le traitement.Mais vous pouvez interdire son [accès à la console client](../../platform/using/access-management.md) et restreindre sa zone de sécurité (à localhost).

Évitez d’ajouter trop d’opérateurs dans le groupe d’administrateurs et d’administratrices (ou avec des droits nommés d’administration).Il s’agit d’opérateurs très puissants (ils peuvent effectuer toutes les instructions SQL, exécuter des commandes sur le serveur et bien d’autres actions).

Adobe Campaign propose trois privilèges de niveau supérieur par le biais des [droits nommés](../../platform/using/access-management.md#named-rights) :

* **ADMINISTRATION** (admin) : donne accès à tout et permet d’effectuer toutes les tâches en contournant les contrôles des droits nommés. Il comprend donc les droits nommés EXÉCUTION DE PROGRAMMES (createProcess) et SQL.

* **EXÉCUTION DE PROGRAMMES** (createProcess) : permet d’exécuter des programmes externes (sur le serveur).

* **SQL** : permet d’exécuter des scripts SQL sur la base de données (ce privilège peut donc contourner le modèle de sécurité). Remarque : si vous devez effectuer des calculs complexes (des filtrages, par exemple), vous pouvez demander à l’administrateur de votre base de données de créer une fonction SQL et de l’ajouter à la liste autorisée. En savoir plus sur [cette page](../../installation/using/scripting-coding-guidelines.md).

* **Octroyez ces privilèges à un nombre très limité d’opérateurs (de confiance)**.
