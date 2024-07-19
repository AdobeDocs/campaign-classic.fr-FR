---
product: campaign
title: À propos des adresses de contrôle
description: Prise en main des adresses de contrôle
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Seed Address
role: User
exl-id: 1f55eda8-c393-4f86-9118-01bcd981c6df
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 100%

---

# À propos des adresses de contrôle{#about-seed-addresses}

Les adresses de contrôle permettent de cibler des destinataires qui ne correspondent pas aux critères de ciblage définis. Ainsi, les destinataires qui n’entrent pas dans le cadre de la diffusion peuvent la recevoir, comme tout autre destinataire cible.

**La protection de votre liste de diffusion** représente l’une des principales raisons de les utiliser. L’insertion d’adresses de contrôle dans votre liste de diffusion vous permet de savoir si elle est utilisée par un tiers. Les adresses de contrôle qu’elle contient recevront en effet les diffusions envoyées à votre liste de diffusion.

De plus, les adresses de contrôle vous permettent de **prévisualiser et de tester la personnalisation et le rendu des diffusions** avant leur envoi grâce à l’envoi de BAT (voir la section [Utilisation d’adresses de contrôle en tant que BAT](steps-defining-the-target-population.md#using-seed-addresses-as-proof)).

![](assets/do-not-localize/how-to-video.png) [Découvrez cette fonctionnalité en vidéo](steps-defining-the-target-population.md#seeds-and-proofs-video)

Les avantages des adresses de contrôle sont les suivants :

* Substitution aléatoire des champs avec des données issues des profils des destinataires : on peut ainsi renseigner seulement l’adresse email par exemple au niveau des adresses de contrôle et laisser Campaign renseigner automatiquement les autres champs du profil (voir [Cas pratique : configuration de la substitution des champs](use-case-configuring-the-field-substitution.md)).
* Dans un contexte de workflow avec utilisation des fonctionnalités de Datamanagement, les données additionnelles exploitées dans les diffusions peuvent être renseignées au niveau des adresses de contrôle afin d&#39;en forcer la valeur : on s&#39;affranchit ainsi de la substitution aléatoire des valeurs.
* Les adresses de contrôle sont automatiquement exclues des rapports sur les statistiques de diffusions suivants : **[!UICONTROL Clics]**, **[!UICONTROL Ouvertures]**, **[!UICONTROL Désinscriptions]**.

Les adresses de contrôle sont ajoutées à la cible de diffusions en étant importées ou créées directement au niveau de la diffusion ou de la campagne.

>[!NOTE]
>
>Les adresses de contrôle ne font pas partie de la table des destinataires. Elles sont créées dans une table distincte. Si vous étendez la table des destinataires avec de nouvelles données, vous devez également étendre la table des adresses de contrôle avec les mêmes données. Sinon, les champs étendus ne seront pas pris en compte pour les adresses de contrôle.
>
>Vous trouverez un exemple d’extension de table d’adresses de contrôle dans la section suivante : [Cas d’utilisation : sélection des adresses de contrôle selon des critères](use-case-selecting-seed-addresses-on-criteria.md).

Dans le cadre des diffusions courrier, les adresses de contrôle sont ajoutées pendant l&#39;extraction et mélangées dans le document de sortie.

>[!IMPORTANT]
>
>Pour les diffusions courrier, le format du fichier d&#39;extraction doit respecter les limitations suivantes :
>
>* Il ne doit pas utiliser l&#39;option **[!UICONTROL Gérer les groupements (GROUP BY+HAVING)]**.
>* Si des collections d’éléments sont extraites, ces champs auront une valeur vide pour les adresses de contrôle, sauf si l’option **[!UICONTROL Ligne unique (mode expert)]** est cochée. Pour plus d’informations, consultez [cette section](../../platform/using/executing-export-jobs.md#step-7---data-formatting).
>
