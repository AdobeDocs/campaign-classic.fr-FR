---
product: campaign
title: Nouvel assistant d’ajout de champs
description: Nouvel assistant d’ajout de champs
feature: Schema Extension
role: Developer
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: ht
source-wordcount: '205'
ht-degree: 100%

---

# Nouvel assistant d’ajout de champs{#new-field-wizard}


Un assistant accessible à partir du menu **[!UICONTROL Outils >Avancé >Ajout de champs]** permet d’ajouter un ou plusieurs champs dans un tableau de la base de données.

La validation de l’assistant met à jour le schéma d’extension dutableau à étendre et lance le script SQL pour modifier la structure physique de la base de données.

Cet assistant à l&#39;avantage d&#39;ajouter rapidement un champ sans avoir à connaître la structure d&#39;un schéma de données.

L&#39;inconvénient principal est la limitation des données et des propriétés à étendre.

Les écrans de l’assistant contiennent les étapes suivantes :

1. La première page permet de renseigner le nom du schéma à étendre et l&#39;espace de noms du schéma d&#39;extension où seront enregistrées les modifications :

   ![](assets/d_ncs_integration_schema_addfield.png)

1. La page suivante renseigne les propriétés du champ à ajouter.

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. Pour valider les modifications, cliquez sur le bouton **[!UICONTROL Terminer]**.

Un fichier d’extension, « cus:recipient » dans notre exemple, est automatiquement créé et le script SQL correspondant exécuté :

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>Par défaut, les champs ajoutés sont déclarés avec la propriété **user** (avec la valeur « true »). Celle-ci permet d’afficher et de modifier le champ dans le formulaire de saisie du schéma étendu avec l’utilisation d’un contrôle de type « treeEdit » (consultez à ce sujet le chapitre Formulaires de saisie).
