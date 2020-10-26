---
title: Profils d'opérateurs
seo-title: Profils d'opérateurs
description: Profils d'opérateurs
seo-description: null
page-status-flag: never-activated
uuid: cd718d20-79cb-40ed-b2ae-23186387e2db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 9a3f1dc9-71ef-4039-94b4-a217996f6a80
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '412'
ht-degree: 100%

---


# Profils d&#39;opérateurs{#operator-profiles}

Deux types d&#39;opérateurs sont amenés à utiliser Interaction : un chargé d&#39;offres et un chargé de diffusion. Chacun dispose de droits spécifiques qui ne leur donnent accès qu&#39;à certaines parties de l&#39;arborescence de la plateforme.

* **[!UICONTROL Chargé d&#39;offres]** : crée et maintient les offres. Notez que si des offres sont utilisées dans le workflow, l’opérateur doit se trouver dans le groupe d’opérateurs **[!UICONTROL Administrateur]** ou **[!UICONTROL Chargés d’offres]** pour l’exécuter.
* **[!UICONTROL Chargé de diffusion]** : valide et utilise les offres

Les étapes de création des opérateurs propres à Interaction sont identiques à celles utilisées pour créer n&#39;importe quel opérateur dans la plate-forme. Reportez-vous à [cette section](../../platform/using/access-management.md#creating-an-operator) pour plus d&#39;informations. Les droits sont configurés lors de la création de l&#39;opérateur.

## Chargé d&#39;offres {#offer-manager}

1. Créez votre nouvel opérateur.
1. Dans la fenêtre **[!UICONTROL Groupes et droits nommés]**, cliquez sur **[!UICONTROL Ajouter]** et sélectionnez le groupe **[!UICONTROL Chargé d&#39;offres]**.

   ![](assets/offer_operators_create_001.png)

Les droits attribués au chargé d&#39;offres lui permettent d&#39;effectuer les opérations suivantes :

* Modifier des environnements **[!UICONTROL En édition]**.
* Consulter des environnements **[!UICONTROL En ligne]**.
* Paramétrer des fonctions d&#39;administration (emplacements et filtres prédéfinis).
* Créer et modifier des catégories.
* Créer des offres.
* Paramétrer l&#39;éligibilité des offres.
* Valider des offres.

   >[!NOTE]
   >
   >Le chargé d&#39;offre ne peut valider une offre que si aucun validant n&#39;est spécifié pour l&#39;offre ou qu&#39;il a été défini comme validant dans le modèle d&#39;offre sur lequel se base l&#39;offre en cours par l&#39;administrateur en charge de la création des modèles (et disposant du droit nommé d&#39;administration des validants).

## Chargé de diffusion {#delivery-manager}

1. Créez votre nouvel opérateur.
1. Dans la fenêtre **[!UICONTROL Groupes et droits nommés]**, cliquez sur **[!UICONTROL Ajouter]** et sélectionnez le groupe **[!UICONTROL Chargé de diffusion]**.

   ![](assets/offer_operators_create_002.png)

Les droits attribués au chargé de diffusion sont les suivants/lui permettent d&#39;effectuer les opérations suivantes :

* Afficher les environnements **[!UICONTROL En ligne]**.
* Afficher et modifier des catégories d&#39;offres.
* Valider des offres s&#39;il y est spécifié comme validant.

   >[!NOTE]
   >
   >Le chargé de diffusion ne peut valider une offre que s&#39;il a été défini comme validant lors du paramétrage de l&#39;offre.

## Récapitulatif des droits selon le type d&#39;opérateur {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Chargé d'offres (en édition)</strong><br /> </td> 
   <td> <strong>Chargé d'offres (en ligne)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Niveau de l'arborescence</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Offres en édition / Offres en ligne<br /> </td> 
   <td> Lecture / Ecriture<br /> </td> 
   <td> Lecture<br /> </td> 
  </tr> 
  <tr> 
   <td> Environnement - Destinataire<br /> </td> 
   <td> Lecture / Ecriture<br /> </td> 
   <td> Lecture<br /> </td> 
  </tr> 
  <tr> 
   <td> Administration<br /> </td> 
   <td> Lecture / Ecriture<br /> </td> 
   <td> Lecture<br /> </td> 
  </tr> 
  <tr> 
   <td> Emplacements<br /> </td> 
   <td> Lecture / Ecriture<br /> </td> 
   <td> Lecture<br /> </td> 
  </tr> 
  <tr> 
   <td> Filtres prédéfinis d'offres<br /> </td> 
   <td> Lecture / Ecriture<br /> </td> 
   <td> Lecture<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologie<br /> </td> 
   <td> Lecture / Ecriture<br /> </td> 
   <td> Lecture<br /> </td> 
  </tr> 
  <tr> 
   <td> Règles de typologie<br /> </td> 
   <td> Lecture / Ecriture<br /> </td> 
   <td> Lecture<br /> </td> 
  </tr> 
  <tr> 
   <td> Catalogue d'offres<br /> </td> 
   <td> Lecture / Ecriture<br /> </td> 
   <td> Lecture<br /> </td> 
  </tr> 
  <tr> 
   <td> Catégorie d'offres<br /> </td> 
   <td> Lecture / Ecriture<br /> </td> 
   <td> Lecture<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Chargé de diffusion (en édition)</strong><br /> </td> 
   <td> <strong>Chargé de diffusion (en ligne)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Niveau de l'arborescence</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Offres en édition / Offres en ligne<br /> </td> 
   <td> </td> 
   <td> Lecture<br /> </td> 
  </tr> 
  <tr> 
   <td> Environnement - Destinataire<br /> </td> 
   <td> </td> 
   <td> Lecture<br /> </td> 
  </tr> 
  <tr> 
   <td> Administration<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Emplacements<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Filtres prédéfinis d'offres<br /> </td> 
   <td> Lecture<br /> </td> 
   <td> Lecture<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologie<br /> </td> 
   <td> Lecture<br /> </td> 
   <td> Lecture<br /> </td> 
  </tr> 
  <tr> 
   <td> Règles de typologie<br /> </td> 
   <td> </td> 
   <td> Lecture<br /> </td> 
  </tr> 
  <tr> 
   <td> Catalogue d'offres<br /> </td> 
   <td> Lecture<br /> </td> 
   <td> Lecture<br /> </td> 
  </tr> 
  <tr> 
   <td> Catégorie d'offres<br /> </td> 
   <td> </td> 
   <td> Lecture<br /> </td> 
  </tr> 
 </tbody> 
</table>

