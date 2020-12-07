---
solution: Campaign Classic
product: campaign
title: Amélioration de votre réputation lors de l'utilisation d'Adobe Campaign Classic
description: En savoir plus sur l'amélioration de votre réputation lors de l'utilisation d'Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '550'
ht-degree: 100%

---


# Amélioration de votre réputation{#improve-reputation}

Pour éviter d’excéder vos destinataires, supprimez les adresses email dupliquées de votre cible. Cette étape protège votre réputation d’expéditeur et assure une bonne gestion des quarantaines. Adobe Campaign dispose des outils nécessaires pour mettre en œuvre ces recommandations et éviter le risque d&#39;être ajouté à une liste bloquée par les FAI.

Pour éviter le plus possible l’existence de doublons, les éléments suivants doivent être impérativement vérifiés :

* Les imports doivent être soigneusement paramétrés
* Attention aux modifications d’adresses email
* Attention aux imports automatiques
* Le rangement des profils dans des dossiers différents

La gestion des quarantaines est présentée dans [cette section](../../delivery/using/understanding-quarantine-management.md).

Vous trouverez ci-dessous des informations sur la gestion des doublons et des quarantaines.

Vous avez la possibilité de suivre le volume d&#39;emails envoyés par adresse IP. Pour cela, une extension de schéma est nécessaire. Vous devez étendre la table des broadlogs afin d&#39;ajouter l&#39;&#39;&#39;identifiant public&quot; et créer un workflow pour extraire et afficher les données. Si vous avez besoin de cette extension, contactez Adobe.

## Doublons {#duplicates}

L’existence de doublons pour une adresse email peut avoir plusieurs conséquences :

* Envois multiples du même message. Même si Adobe Campaign applique par défaut une déduplication sur l’adresse email avant chaque envoi, rien n’empêche d’envoyer plusieurs fois le même message par des actions différentes qui ont un même contenu lorsqu’on effectue un partage de cible.
* Non-respect de la désinscription. Si une personne se désinscrit suite à la réception d’un message, son profil en doublon sera quant à lui toujours éligible aux envois.

Outre le non-respect de l’opt-in, cette situation amènera probablement les utilisateurs à considérer les messages comme du spam et déclencher une action de placement sur liste bloquée de la part du FAI.

Il faut être particulièrement prudent lors d&#39;opérations sur la base :

* Les imports doivent être soigneusement paramétrés, en particulier dans le choix de la clé de réconciliation.
* Les modifications d’adresses email peuvent être source de doublons. En particulier, il peut arriver que deux adresses qui ne diffèrent que par le domaine soient routées vers la même boîte mail, par exemple dans le cas d’une société qui change de nom et qui garde un certain temps le fonctionnement des deux types d’adresse : marie.dupont@anciennesociete.com et marie.dupont@nouvellesociete.com.
* Les imports automatiques, qu&#39;ils soient issus de fichiers ou d&#39;autres bases de données sont des éléments à prendre en compte dans les manipulations de profils. Que se passe-t-il si on supprime ou on déplace un profil dans une autre partition ? Il risque d’être recréé dans la partition initiale par un import automatique, par exemple suite au passage d’une commande.
* Le rangement des profils dans des dossiers différents peut être mise en oeuvre à l&#39;aide de vues plutôt que de partitions. Ainsi on s&#39;assure que les profils sont physiquement dans la même partition tout en permettant un affichage et une gestion des droits adéquats.

Il existe tout de même des cas où la présence de doublons entre différentes partitions est normale. Par exemple, lorsqu’on opère des envois pour le compte de sociétés ou d’entités différentes, il est logique qu’une même personne puisse être adressée à des titres différents. Il est cependant rarement normal de trouver des doublons dans une même partition.

## Les quarantaines {#quarantines}

Adobe Campaign gère une liste d’adresses en quarantaine. Les destinataires dont l’adresse est en quarantaine sont par défaut exclus lors de l’analyse d’une diffusion : ils ne seront pas ciblés. Une adresse email peut être mise en quarantaine par exemple lorsque la boîte de messagerie est pleine ou si l’adresse n’existe pas. Dans tous les cas, la mise en quarantaine répond à des règles précises qui sont décrites ci-après.

La gestion des quarantaines est présentée dans [cette section](../../delivery/using/understanding-quarantine-management.md).