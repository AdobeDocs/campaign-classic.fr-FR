---
product: campaign
title: A propos des adresses de contrôle
description: A propos des adresses de contrôle
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: 1f55eda8-c393-4f86-9118-01bcd981c6df
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 100%

---

# A propos des adresses de contrôle{#about-seed-addresses}

Les adresses de contrôle permettent de cibler des destinataires qui ne correspondent pas aux critères de ciblage définis. Ainsi, les destinataires qui n&#39;entrent pas dans le cadre de la diffusion peuvent la recevoir, comme tout autre destinataire cible.

L&#39;une des principales raisons est la **protection de votre liste de messagerie**. L&#39;insertion d&#39;adresses de contrôle dans votre liste de diffusion vous permet de savoir si elle est utilisée par une tierce partie, car les adresses de contrôle qu&#39;elle contient recevront les diffusions envoyées à la liste de diffusion.

De plus, les adresses de contrôle vous permettent de **prévisualiser et de tester la personnalisation et le rendu des diffusions** avant leur envoi, en leur envoyant des BAT (voir la section [Utiliser des adresses de contrôle en tant que BAT](../../delivery/using/steps-defining-the-target-population.md#using-seed-addresses-as-proof)).

![](assets/do-not-localize/how-to-video.png) [Découvrez cette fonctionnalité en vidéo](../../delivery/using/steps-defining-the-target-population.md#seeds-and-proofs-video)

Les avantages des adresses de contrôle sont les suivants :

* Substitution aléatoire des champs avec des données issues des profils des destinataires : on peut ainsi renseigner seulement l’adresse email par exemple au niveau des adresses de contrôle et laisser Campaign renseigner automatiquement les autres champs du profil (voir [Cas pratique : configuration de la substitution des champs](../../delivery/using/use-case--configuring-the-field-substitution.md)).
* Dans un contexte de workflow avec utilisation des fonctionnalités de Datamanagement, les données additionnelles exploitées dans les diffusions peuvent être renseignées au niveau des adresses de contrôle afin d&#39;en forcer la valeur : on s&#39;affranchit ainsi de la substitution aléatoire des valeurs.
* Les adresses de contrôle sont automatiquement exclues des rapports sur les statistiques de diffusions suivants : **[!UICONTROL Clics]**, **[!UICONTROL Ouvertures]**, **[!UICONTROL Désinscriptions]**.

Les adresses de contrôle sont ajoutées à la cible de diffusions en étant importées ou créées directement au niveau de la diffusion ou de la campagne.

>[!NOTE]
>
>Les adresses de contrôle ne font pas partie de la table des destinataires. Elles sont créées dans une table distincte. Si vous étendez la table des destinataires avec de nouvelles données, vous devez également étendre la table des adresses de contrôle avec les mêmes données. Sinon, les champs étendus ne seront pas pris en compte pour les adresses de contrôle.
>
>Vous trouverez un exemple de cela dans la section : [Cas pratique : sélection des adresses de contrôle selon des critères](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

Dans le cadre des diffusions courrier, les adresses de contrôle sont ajoutées pendant l&#39;extraction et mélangées dans le document de sortie.

>[!IMPORTANT]
>
>Pour les diffusions courrier, le format du fichier d&#39;extraction doit respecter les limitations suivantes :
>
>* Il ne doit pas utiliser l&#39;option **[!UICONTROL Gérer les groupements (GROUP BY+HAVING)]**.
>* Si des collections d&#39;éléments sont extraites, ces champs auront une valeur vide pour les adresses de contrôle, sauf si l&#39;option **[!UICONTROL Ligne unique (mode expert)]** est cochée. Voir à ce sujet [cette section](../../platform/using/executing-export-jobs.md#step-7---data-formatting).

>


