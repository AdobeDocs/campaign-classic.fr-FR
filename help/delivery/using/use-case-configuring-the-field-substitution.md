---
product: campaign
title: 'Cas pratique : configuration de la substitution des champs'
description: 'Cas pratique : configuration de la substitution des champs'
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Seed Address
exl-id: 3f567b2d-6f98-4831-af84-7db17fd12c6e
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 100%

---

# Cas pratique : configuration de la substitution des champs{#use-case-configuring-the-field-substitution}



La substitution aléatoire des champs permet d&#39;attribuer une valeur issue de la liste des destinataires à des adresses de contrôle qui en sont dépourvues lorsque l&#39;utilisateur utilise cette valeur dans une diffusion (exemple : le nom, la ville, etc.).

Cette substitution permet de gagner du temps lors de la création de la diffusion : au lieu d&#39;ajouter manuellement la valeur souhaitée aux adresses de contrôle, la substitution récupère aléatoirement cette valeur dans la liste des destinataires visés par la diffusion et l&#39;applique aux adresses de contrôle.

## Contexte {#context}

Dans ce cas pratique, le site **Ma bibliothèque en ligne** souhaite envoyer une offre de remise à ses clients en fonction de leurs préférences littéraires.

Dans son e-mail, le chargé de diffusion a intégré un champ de personnalisation lié au genre littéraire favori. Le but est d’utiliser des adresses de contrôle : ces adresses de contrôle contiennent le champ de personnalisation dans leur table, mais aucune valeur n’y est enregistrée.

Pour utiliser la substitution aléatoire des champs vous devez disposer :

* d&#39;une diffusion utilisant un ou plusieurs champs de personnalisation,
* d&#39;adresses de contrôle dont le **schéma de données** est modifié en fonction des champs de personnalisation utilisés dans la diffusion.

## Création dʼune diffusion {#step-1---creating-a-delivery}

Les étapes de création dʼune diffusion sont détaillées dans la section [Création dʼune diffusion e-mail](creating-an-email-delivery.md).

Dans cet exemple, la newsletter a été créée par le chargé de diffusion.

![](assets/dlv_seeds_usecase_24.png)

## Modification du schéma de données des adresses de contrôle {#editing-the-seed-addresses-data-schema}

Les étapes de modification d&#39;un schéma de données sont présentées dans la section .

Dans cet exemple, le schéma de données des adresses de contrôle reprend une valeur créée dans le schéma de données des destinataires :

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

Cette énumération permet à l&#39;utilisateur de spécifier le genre littéraire préféré de ses clients.

Pour que cette modification du schéma de données soit visible dans le **Formulaire de saisie** des adresses de contrôle, il faut mettre à jour ce dernier. Pour plus dʼinformations, consultez la section [Mise à jour du formulaire de saisie](use-case-selecting-seed-addresses-on-criteria.md#updating-the-input-form).

## Configurer la personnalisation {#configuring-personalization}

1. Ouvrez votre diffusion.

   Dans cet exemple, la diffusion possède deux champs de personnalisation : le **prénom** et le **genre littéraire favori** du destinataire.

   ![](assets/dlv_seeds_usecase_25.png)

1. Paramétrez votre liste de diffusion et vos adresses de contrôle. Consultez la section [Identification des populations cibles](steps-defining-the-target-population.md).

   Dans cet exemple, l&#39;utilisateur choisit comme cible principale les clients dont le **genre littéraire préféré** est la Science-Fiction.

   ![](assets/dlv_seeds_usecase_26.png)

   Il ajoute des adresses de contrôle à la diffusion.

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >Pour plus d’informations sur le lien **[!UICONTROL Modification de la condition dynamique...]**, consultez la section [Cas dʼutilisation : sélection des adresses de contrôle selon des critères](use-case-selecting-seed-addresses-on-criteria.md).

1. Cliquez sur l&#39;onglet **[!UICONTROL Aperçu]** puis sélectionnez une adresse de contrôle pour tester la personnalisation.

   ![](assets/dlv_seeds_usecase_28.png)

   Vous pouvez constater qu&#39;un des champs de personnalisation est vide. Comme l&#39;adresse de contrôle ne possède pas de données pour ce champ, l&#39;aperçu du contenu HTML ne peut pas afficher de valeur.

   La subsitution aléatoire des champs s&#39;effectue **au moment de l&#39;envoi de la diffusion**.

1. Cliquez sur le bouton **[!UICONTROL Envoyer]**.
1. Analysez votre diffusion puis **confirmez l&#39;envoi**.

   Les adresses de contrôle reçoivent la diffusion dans leur boîte email.

   La personnalisation des champs est effective.

   ![](assets/dlv_seeds_usecase_08.png)
