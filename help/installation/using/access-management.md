---
solution: Campaign Classic
product: campaign
title: Gestion des accès
description: En savoir plus sur les meilleures pratiques de gestion des accès.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 51%

---


# Gestion des accès {#access-management}

## Opérateur web

L’opérateur webApp par défaut est un administrateur. Pour améliorer la sécurité, suivez les consignes suivantes :

* Remplacez l’administrateur nommé à droite de cet opérateur par un nouvel administrateur (qui peut être nommé &quot;webapp&quot;). Pour plus d’informations, consultez [cette page](../../platform/using/access-management.md).

* Ajoutez l’opérateur webApp à des dossiers (principalement des dossiers de destinataires) afin d’accorder un accès en lecture/écriture aux destinataires. Consultez [cette page](../../platform/using/access-management.md) pour plus d&#39;informations.

* Si vous utilisez une instance multimarque (ou multizone), vous souhaiterez peut-être répartir l’accès aux applications web entre différents dossiers de destinataires. Pour ce faire :

   1. Dupliquez l’opérateur webApp.

   1. Entrez un nom pour chaque duplicata. Par exemple : webapp_brand, webapp_brand2, etc.

   1. Dupliquez un modèle d’application web pour disposer d’un modèle par marque et éditez les propriétés pour changer l’opérateur en sélectionnant l’option Utiliser un compte spécifique.  En savoir plus sur [cette page](../../web/using/defining-web-forms-properties.md).

## Groupes de sécurité et opérateurs d’administration

Créez suffisamment de groupes de sécurité afin de donner aux opérateurs des droits suffisants pour qu’ils puissent effectuer les opérations nécessaires (et pas davantage).

N’utilisez pas l’opérateur d’administration (ou ne le partagez pas). Créez un opérateur par utilisateur physique (pour disposer d’un audit/d’une journalisation précis). Ajoutez vos administrateurs nouvellement nommés au groupe d’administrateurs. Si vous n’utilisez pas l’opérateur administrateur, ne le supprimez pas et ne le désactivez pas : cet opérateur est utilisé en interne pour exécuter le traitement. Mais vous pouvez interdire son [accès à la console client](../../platform/using/access-management.md) et limiter sa zone de sécurité (à localhost).

Evitez d&#39;ajouter trop d&#39;opérateurs au groupe admin (ou avec des droits nommés admin). Il s&#39;agit d&#39;opérateurs très puissants (ils peuvent effectuer toutes les instructions SQL, exécuter des commandes sur le serveur, etc.).

Adobe Campaign fournit trois privilèges de haut niveau par le biais de [droits nommés](../../platform/using/access-management.md#named-rights) :

* **ADMINISTRATION** (admin) : donne accès à tout et permet de tout faire, en contournant toutes les vérifications de droits nommées, de sorte qu&#39;il inclut le PROGRAMME EXECUTION (createProcess) et les droits nommés SQL

* **PROGRAMME EXECUTION** (createProcess) : permet d’exécuter des programmes externes (sur le serveur).

* **SQL** : permet d&#39;exécuter des scripts SQL sur la base de données (afin de contourner le modèle de sécurité). Remarque : si vous devez effectuer des calculs complexes (des filtrages, par exemple), vous pouvez demander à l’administrateur de la base de données de créer une fonction SQL et de l’ajouter à la liste autorisée. En savoir plus sur [cette page](../../installation/using/scripting-coding-guidelines.md).

* **Accordez ces privilèges à un nombre très limité d&#39;opérateurs (de confiance).**
