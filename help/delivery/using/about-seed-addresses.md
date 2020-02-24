---
title: A propos des adresses de contrôle
seo-title: A propos des adresses de contrôle
description: A propos des adresses de contrôle
seo-description: null
page-status-flag: never-activated
uuid: 80ab5abc-3ae0-484d-88c0-be039aac360d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: b49acfd0-b601-4694-88e3-cc0a169cb866
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0ce6e5277c32bc18c20dca62e5b276f654d1ace5

---


# A propos des adresses de contrôle{#about-seed-addresses}

Les adresses de contrôle permettent de cibler des destinataires qui ne correspondent pas aux critères de ciblage définis. Ainsi, les destinataires qui n&#39;entrent pas dans le cadre de la diffusion peuvent la recevoir, comme tout autre destinataire cible.

L&#39;une des principales raisons est la **protection de votre liste de messagerie**. L&#39;insertion d&#39;adresses de contrôle dans votre liste de diffusion vous permet de savoir si elle est utilisée par une tierce partie, car les adresses de contrôle qu&#39;elle contient recevront les diffusions envoyées à la liste de diffusion.

Moreover, seed addresses let you **preview and test the deliveries personalization and rendering** before their sending, by sending them proofs (see [Using seed addresses as proof](../../delivery/using/steps-validating-the-delivery.md#using-seed-addresses-as-proof)).

Les avantages des adresses de contrôle sont les suivants :

* Random substitution of fields with data taken from recipient profiles: this lets you enter only the email address, for instance in the seed address section, and let Campaign automatically fill in the other fields form the profile (see [Use case: configuring the field substitution](../../delivery/using/use-case--configuring-the-field-substitution.md)).
* Dans un contexte de workflow avec utilisation des fonctionnalités de Datamanagement, les données additionnelles exploitées dans les diffusions peuvent être renseignées au niveau des adresses de contrôle afin d&#39;en forcer la valeur : on s&#39;affranchit ainsi de la substitution aléatoire des valeurs.
* Les adresses de contrôle sont automatiquement exclues des rapports sur les statistiques de diffusions suivants : **[!UICONTROL Clics]**, **[!UICONTROL Ouvertures]**, **[!UICONTROL Désinscriptions]**.

Les adresses de contrôle sont ajoutées à la cible de diffusions en étant importées ou créées directement au niveau de la diffusion ou de la campagne.

>[!NOTE]
>
>Les adresses de contrôle ne font pas partie de la table des destinataires. Elles sont créées dans une table distincte. Si vous étendez la table des destinataires avec de nouvelles données, vous devez également étendre la table des adresses de contrôle avec les mêmes données. Sinon, les champs étendus ne seront pas pris en compte pour les adresses de contrôle.
>
>Cette section présente un exemple d’extension du tableau des adresses de départ : Cas [d’utilisation : sélection des adresses de base sur des critères](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)

Dans le cadre des diffusions courrier, les adresses de contrôle sont ajoutées pendant l&#39;extraction et mélangées dans le document de sortie.

>[!CAUTION]
>
>Pour les diffusions courrier, le format du fichier d&#39;extraction doit respecter les limitations suivantes :
>
>* Il ne doit pas utiliser l&#39;option **[!UICONTROL Gérer les groupements (GROUP BY+HAVING)]**.
>* Si des collections d&#39;éléments sont extraites, ces champs auront une valeur vide pour les adresses de contrôle, sauf si l&#39;option **[!UICONTROL Ligne unique (mode expert)]** est cochée. Voir à ce sujet [cette section](../../platform/using/exporting-data.md#step-7---data-formatting).
>


