---
product: campaign
title: Configuration de l’interface
description: Découvrez comment configurer lʼinterface de Campaign
feature: Application Settings
role: Data Engineer, Developer
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: d56038fc8baf766667d89bb73747c20ec041124c
workflow-type: ht
source-wordcount: '304'
ht-degree: 100%

---

# Configuration de l’interface{#configuring-the-interface}

Afin de visualiser et de dialoguer avec la nouvelle table des destinataires dans l&#39;interface d&#39;Adobe Campaign, il faut suivre les étapes suivantes :

* Créer un nouveau formulaire pour éditer le contenu de la nouvelle table des destinataires.
* Renseigner un nouveau type de dossier dans l&#39;arborescence de l&#39;explorateur.
* Créer une nouvelle application web pour accéder à la table personnalisée depuis la page d&#39;accueil d&#39;Adobe Campaign.

Adobe Campaign utilise une variable globale « Nms_DefaultRcpSchema » pour communiquer avec la base de données de personnes destinataires par défaut (nms:recipient). Il convient donc de modifier cette variable.

1. Accédez au nœud **[!UICONTROL Administration > Plateforme > Options]** dans l’explorateur.
1. Modifiez la valeur de la variable **Nms_DefaultRcpSchema** avec le nom du schéma correspondant à la table externe des personnes destinataires (dans ce cas : cus:individual).
1. Enregistrez les modifications.

## Créer un nouveau formulaire {#creating-a-new-form-}

La création d&#39;un nouveau formulaire va permettre de visualiser et d&#39;éditer les données de la table externe des destinataires.

>[!IMPORTANT]
>
>Le nom du formulaire doit être identique au nom du schéma auquel il se rapporte.

1. Ouvrez le nœud **Administration > Paramétrage > Formulaires de saisie** dans l&#39;explorateur.
1. Créez un fichier **form:form** de type **xtk**.
1. Décrivez tous les contrôles et champs dont vous avez besoin en fonction de votre modèle de table.

   >[!NOTE]
   >
   >Pour en savoir plus sur les fichiers de type **form**, reportez-vous à [cette page](../../configuration/using/identifying-a-form.md).

   Dans cet exemple, le fichier **form** doit être basé sur le schéma **cus:individual** et donc posséder la mise en page suivante :

   ```
   <container colspan="2">
       <input xpath="@id"/>
       <static type="separator"/>
   </container>
   <container colcount="2">
       <input xpath="@lastName"/>
       <input xpath="@firstName"/>
       <input xpath="@email"/>
       <input xpath="@mobile"/>
   </container> 
   ```

1. Enregistrez la création.

## Créer un nouveau type de dossier dans l&#39;arborescence de navigation {#creating-a-new-type-of-folder-in-the-navigation-hierarchy}

1. Accédez au nœud **[!UICONTROL Administration > Configuration > Arborescences de navigation]** dans l’explorateur.
1. Créez un document **navtree** de type **xtk:navtree**.
1. Décrivez tous les contrôles et champs dont vous avez besoin en fonction de votre modèle de table.

   Dans cet exemple, le fichier **navtree** doit être basé sur le schéma **cus:individual** et donc utiliser le formulaire suivant :

   ```
    <model name="root">
       <nodeModel img="nms:usergrp.png" label="My recipient table" name="cusindividual">
         <view name="listdet" schema="cus:individual" type="listdet">
           <columns>
             <node xpath="@id"/>
             <node xpath="@lastName"/>
             <node xpath="@firstName"/>
             <node xpath="@email"/>
             <node xpath="@mobile"/>
           </columns>
         </view>
       </nodeModel>
   </model>
   ```

1. Enregistrez la création.
