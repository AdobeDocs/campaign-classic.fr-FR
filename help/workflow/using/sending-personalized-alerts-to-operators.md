---
product: campaign
title: Envoi d’alertes personnalisées aux opérateurs
description: Découvrez comment envoyer des alertes personnalisées aux opérateurs
feature: Workflows
hide: true
exl-id: 21c97eb3-60cd-4d19-bc0f-5ba9ec17e70a
TQID: https://experienceleague.adobe.com/AhEp-fucKo-UN8M9kzPxqpbHU2ichyv1LHa-qeN9qRc
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 374
ht-degree: 78%

---

# Envoi d’alertes personnalisées aux opérateurs{#sending-personalized-alerts-to-operators}



Dans cet exemple, nous souhaitons envoyer à un opérateur une alerte qui contiendra le nom des profils qui ont ouvert une newsletter, sans toutefois cliquer sur le lien qu&#39;il contient.

Les champs de prénom et de nom des profils sont liés à la dimension de ciblage **[!UICONTROL Destinataires]**, tandis que l&#39;activité **[!UICONTROL Alerte]** est liée à la dimension de ciblage **[!UICONTROL Opérateur]**. Par conséquent, aucun champ n’est disponible entre les deux dimensions de ciblage pour effectuer une réconciliation et récupérer les champs de prénom et de nom, puis les afficher dans l’activité Alerte .

Le processus créé un workflow comme ci-dessous :

1. Utilisez une activité **[!UICONTROL Requête]** sur les données de la cible.
1. Ajoutez une activité **[!UICONTROL Code JavaScript]** dans le workflow afin d&#39;enregistrer la population de la requête dans la variable d&#39;instance.
1. Utilisez une activité **[!UICONTROL Test]** pour vérifier la population.
1. Utilisez une activité **[!UICONTROL Alerte]** pour envoyer une alerte à un opérateur, selon le résultat de l&#39;activité **[!UICONTROL Test]**.

![](assets/uc_operator_1.png)

## Enregistrer la population dans la variable d&#39;instance {#saving-the-population-to-the-instance-variable}

Ajoutez le code ci-dessous dans l&#39;activité **[!UICONTROL Code JavaScript]**.

```
var query = xtk.queryDef.create(  
    <queryDef schema="temp:query" operation="select">  
      <select>  
       <node expr="[target/recipient.@firstName]"/>  
       <node expr="[target/recipient.@lastName]"/>  
      </select>  
     </queryDef>  
  );  
  var items = query.ExecuteQuery();
```

Assurez-vous que le code JavaScript correspond à vos informations de workflow :

* La balise **[!UICONTROL queryDef schema]** devrait correspondre au nom de la dimension de ciblage utilisée dans l’activité de requête.
* Le tag **[!UICONTROL node expr]** devrait correspondre au nom des champs que vous voulez récupérer.

![](assets/uc_operator_3.png)

Pour récupérer ces informations, procédez comme suit :

1. Cliquez avec le bouton droit sur la transition sortante à partir de l’activité **[!UICONTROL Requête]**, puis sélectionnez **[!UICONTROL Afficher la cible]**.

   ![](assets/uc_operator_4.png)

1. Cliquez avec le bouton droit sur la liste, puis sélectionnez **[!UICONTROL Configurer la liste]**.

   ![](assets/uc_operator_5.png)

1. Les noms des champs et de la dimension de ciblage de la requête s&#39;affichent dans la liste

   ![](assets/uc_operator_6.png)

## Tester le comptage de la population {#testing-the-population-count}

Ajoutez le code ci-dessous dans l&#39;activité **[!UICONTROL Test]** pour vérifier si la population ciblée contient au moins 1 profil.

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## Configurer l&#39;alerte {#setting-up-the-alert}

Maintenant que la population a été ajoutée dans la variable d&#39;instance avec les champs souhaités, vous pouvez ajouter ces informations dans l&#39;activité **[!UICONTROL Alerte]**.

Pour ce faire, ajoutez le code ci-dessous dans l&#39;onglet **[!UICONTROL Source]** :

```
<ul>
<%
var items = new XML(instance.vars.items)
for each (var item in items){
%>
<li><%= item.target.@firstName %> <%= item.target.@lastName %></li>
<%
} %></ul>
```

>[!NOTE]
>
>La commande **[!UICONTROL &lt;%= item.target.recipient.@fieldName %>]** permet d&#39;ajouter un des champs qui a été enregistré dans la variable d&#39;instance via l&#39;activité **[!UICONTROL Code JavaScript]**.\
>Vous pouvez ajouter autant de champs que vous le souhaitez, dès lors qu&#39;ils ont été insérés dans le code JavaScript.

![](assets/uc_operator_8.png)
