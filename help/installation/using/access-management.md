---
product: campaign
title: Gestion des accès
description: En savoir plus sur les bonnes pratiques relatives à la gestion des accès
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Access Management, Permissions
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Gestion des accès {#access-management}



## Opérateur webApp

L’opérateur webApp par défaut est un administrateur. Pour améliorer la sécurité, suivez les instructions suivantes :

* Remplacez l’admin nommé à droite de cet opérateur par un nouvel admin (qui peut être nommé « webapp »). Pour plus d’informations, consultez [cette page](../../platform/using/access-management.md).

* Ajoutez l’opérateur webApp à des dossiers (principalement des dossiers de destinataires) afin d’octroyer un accès en lecture/écriture aux destinataires. Pour plus d’informations à ce sujet, consultez [cette page](../../platform/using/access-management.md).

* Si vous utilisez une instance multimarque (ou multizone), vous souhaiterez peut-être répartir l’accès aux applications web entre différents dossiers de destinataires. Pour ce faire :

   1. Dupliquez l’opérateur webApp.

   1. Saisissez un nom pour chaque duplicata. Par exemple : webapp_brand, webapp_brand2, etc.

   1. Dupliquez un modèle d’application web pour disposer d’un modèle par marque et modifiez les propriétés afin de changer l’opérateur en sélectionnant l’option Utiliser un compte spécifique.  En savoir plus sur [cette page](../../web/using/defining-web-forms-properties.md).

## Groupes de sécurité et opérateurs admin

Créez suffisamment de groupes de sécurité afin de donner aux opérateurs des droits suffisants pour qu’ils puissent effectuer les opérations nécessaires (et pas davantage).

N’utilisez pas l’opérateur admin (ou ne le partagez pas). Créez un opérateur par utilisateur physique (pour disposer d’une connexion/d’un audit précis). Ajoutez vos administrateurs nouvellement nommés au groupe admin. Si vous n’utilisez pas l’opérateur admin, ne le supprimez pas et ne le désactivez pas : cet opérateur est utilisé en interne pour exécuter le traitement. Mais vous pouvez interdire son [accès à la console client](../../platform/using/access-management.md) et restreindre sa zone de sécurité (à localhost).

Évitez d’ajouter trop d’opérateurs au groupe admin (ou avec des droits nommés admin). Il s’agit d’opérateurs très puissants (ils peuvent effectuer toutes les instructions SQL, exécuter des commandes sur le serveur et bien d’autres actions).

Adobe Campaign propose trois privilèges de niveau supérieur par le biais des [droits nommés](../../platform/using/access-management.md#named-rights) :

* **ADMINISTRATION** (admin) : donne accès à tout et permet d’effectuer toutes les tâches en contournant les contrôles des droits nommés. Il comprend donc les droits nommés EXÉCUTION DE PROGRAMMES (createProcess) et SQL.

* **EXÉCUTION DE PROGRAMMES** (createProcess) : permet d’exécuter des programmes externes (sur le serveur).

* **SQL** : permet d’exécuter des scripts SQL sur la base de données (ce privilège peut donc contourner le modèle de sécurité). Remarque : si vous devez effectuer des calculs complexes (des filtrages, par exemple), vous pouvez demander à l’administrateur de votre base de données de créer une fonction SQL et de l’ajouter à la liste autorisée. En savoir plus sur [cette page](../../installation/using/scripting-coding-guidelines.md).

* **Octroyez ces privilèges à un nombre très limité d’opérateurs (de confiance)**.
