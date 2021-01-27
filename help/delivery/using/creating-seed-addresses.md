---
solution: Campaign Classic
product: campaign
title: Créer des adresses de contrôle
description: Découvrez comment créer et utiliser des adresses de contrôle
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 100%

---


# Créer des adresses de contrôle{#creating-seed-addresses}

Les adresses de contrôle ne sont pas gérées via les profils et cibles standards, mais dans un nœud dédié de l&#39;arborescence Adobe Campaign, sous **[!UICONTROL Ressources > Gestion de campagne > Adresses de contrôle]**.

Vous pouvez créer des sous-dossiers afin d&#39;organiser les adresses de contrôle. Pour cela, cliquez avec le bouton droit sur le nœud **[!UICONTROL Adresses de contrôle]** et sélectionnez **[!UICONTROL Ajouter un dossier « Adresses de contrôle »]**. Nommez le sous-dossier et validez par la touche **[!UICONTROL Entrée]** du clavier. Vous pouvez ensuite créer ou copier des adresses de contrôle dans ce sous-dossier. Voir à ce sujet la section [Définir des adresses](#defining-addresses).

Adobe Campaign permet également de créer des modèles d&#39;adresses de contrôle qui sont importées au niveau des diffusions ou des campagnes et sont ensuite adaptées selon les besoins spécifiques aux diffusions et campagnes concernées. Voir [Créer des modèles d&#39;adresses de contrôle](#creating-seed-address-templates).

## Définir des adresses {#defining-addresses}

Pour créer des adresses de contrôle, procédez comme suit :

1. Cliquez sur le bouton **[!UICONTROL Nouveau]** situé au-dessus de la liste des adresses de contrôle.
1. Saisissez les données associées à l&#39;adresse dans les champs correspondants de l&#39;onglet **[!UICONTROL Destinataire]**. Les champs disponibles correspondent aux champs standards dans les profils des destinataires de la diffusion (nms:recipient table) : nom, prénom, email, etc.

   >[!NOTE]
   >
   >Le libellé de l&#39;adresse reprend automatiquement le nom et le prénom saisis.
   >
   >Pour chaque adresse de contrôle, il n&#39;est pas nécessaire de renseigner tous les champs des différents onglets. Les éléments de personnalisation manquants sont renseignés aléatoirement lors de la diffusion.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. Indiquez dans l&#39;onglet **[!UICONTROL Champs de l&#39;adresse]** les valeurs qui seront insérées dans les logs de la diffusion lors de la phase d&#39;analyse (dans la table **[!UICONTROL nms:broadLog]**).

1. Dans l&#39;onglet **[!UICONTROL Données additionnelles]**, renseignez les données de personnalisation utilisées pour les diffusions créées dans les workflows Data management et auxquelles vous souhaitez affecter une valeur spécifique.

   >[!NOTE]
   >
   >Assurez-vous que les données additionnelles de la cible ont été définies avec un alias commençant par &#39;@&#39; dans l&#39;activité **[!UICONTROL Enrichissement]**. Sinon, vous ne pourrez pas les utiliser correctement avec vos adresses de contrôle dans votre activité de diffusion.

## Créer des modèles d&#39;adresses de contrôle {#creating-seed-address-templates}

Pour créer des modèles d&#39;adresses, qui seront importées et pourront être modifiées pour chaque diffusion, la procédure est la même que celle permettant de définir une nouvelle adresse de contrôle, mais les adresses des modèles doivent être stockées dans un dossier de type &#39;Modèle&#39;.

Pour définir un dossier de modèle, la procédure est la suivante :

1. Créez un dossier de type **[!UICONTROL Adresses de contrôle]**, cliquez avec le bouton droit dessus et sélectionnez **[!UICONTROL Propriétés...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Cliquez sur l’onglet **[!UICONTROL Restriction]** et ajoutez la condition de filtrage suivante : **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Les adresses stockées dans ce dossier pourront ainsi être utilisées comme des modèles d&#39;adresses. Vous pouvez les importer dans des diffusions ou des campagnes et les adapter en fonction des besoins spécifiques des livraisons et campagnes concernées (voir [Ajouter des adresses de contrôle](../../delivery/using/adding-seed-addresses.md)).
