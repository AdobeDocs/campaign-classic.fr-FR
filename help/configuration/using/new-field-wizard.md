---
product: campaign
title: Assistant d'ajout de champs
description: Assistant d'ajout de champs
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Schema Extension
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '206'
ht-degree: 100%

---

# Assistant d&#39;ajout de champs{#new-field-wizard}


Un assistant accessible à partir du menu **[!UICONTROL Outils > Avancé > Ajout de champs]** permet d&#39;ajouter un ou plusieurs champs dans une table de la base de données.

La validation de l&#39;assistant met à jour le schéma d&#39;extension de la table à étendre et lance le script SQL pour modifier la structure physique de la base de données.

Cet assistant à l&#39;avantage d&#39;ajouter rapidement un champ sans avoir à connaître la structure d&#39;un schéma de données.

L&#39;inconvénient principal est la limitation des données et des propriétés à étendre.

Les écrans de l&#39;assistant contiennent les étapes suivantes :

1. La première page permet de renseigner le nom du schéma à étendre et l&#39;espace de noms du schéma d&#39;extension où seront enregistrées les modifications :

   ![](assets/d_ncs_integration_schema_addfield.png)

1. La page suivante renseigne les propriétés du champ à ajouter.

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. Pour valider les modifications, cliquez sur le bouton **[!UICONTROL Terminer]**.

Un fichier d&#39;extension de nom &quot;cus:recipient&quot; dans notre exemple, est automatiquement créé et le script SQL correspondant exécuté :

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>Par défaut, les champs ajoutés sont déclarés avec la propriété **user** (avec la valeur &quot;true&quot;). Celle-ci permet d&#39;afficher et d&#39;éditer le champ dans le formulaire de saisie du schéma étendu avec l&#39;utilisation d&#39;un contrôle de type &quot;treeEdit&quot; (voir à ce sujet le chapitre Formulaires de saisie).
