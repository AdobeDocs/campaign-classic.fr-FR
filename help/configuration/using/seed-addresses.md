---
product: campaign
title: Adresses de contrôle
description: Adresses de contrôle
role: Data Engineer, Developer
badge-v7: label="v7" type="Informative" tooltip="S’applique à Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="S’applique également à Campaign v8"
feature: Seed Address
exl-id: a16103bf-0498-4f59-ad96-8bfdeea26577
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 75%

---

# Adresses de contrôle{#seed-addresses}



Si la table des destinataires est une table personnalisée, vous devez effectuer des paramétrages complémentaires. Le schéma **[!UICONTROL nms:seedMember]** doit être étendu. Un onglet supplémentaire est alors ajouté au niveau des adresses de contrôle afin de définir les champs adéquats, comme dans l&#39;exemple ci-dessous :

![](assets/s_ncs_user_seedlist_new_tab.png)

Pour plus d&#39;informations sur l&#39;utilisation des adresses de contrôle, consultez [cette section](../../delivery/using/about-seed-addresses.md).

## Mise en œuvre {#implementation}

Le schéma **nms:seedMember** et le formulaire éponyme livrés d&#39;usine ont vocation à être étendus pour un paramètrage client afin de référencer tous les champs nécessaires. La définition du schéma contient des commentaires expliquant son mode de paramétrage.

Définition du schéma étendu de la table des destinataires :

```
<srcSchema label="Person" name="person" namespace="cus">
  <element autopk="true" label="Person" name="person">
      <attribute label="LastName" name="lastname" type="string"/>
      <attribute label="FirstName" name="firstname" type="string"/>
    <element label="Address" name="address">
      <attribute label="Email" name="addrEnv" type="string"/>
    </element>
    <attribute label="Code Offer" name="codeOffer" type="string"/>
  </element>
</srcSchema>
```

Les étapes sont les suivantes :

1. Créez une extension du schéma **nms:seedMember**. Pour plus d’informations, consultez [cette section](../../configuration/using/extending-a-schema.md).
1. Dans cette extension, ajoutez un nouvel élément à la racine de l&#39;élément **[!UICONTROL seedMember]**, avec les paramètres suivants :

   ```
   name="custom_customNamespace_customSchema"
   ```

   Cet élément doit contenir les champs nécessaires à l&#39;export des campagnes. Ces champs doivent porter le même nom que les champs correspondants du schéma externe. Par exemple, si le schéma est **[!UICONTROL cus:person]** , la variable **[!UICONTROL nms:seedMember]** schéma doit être étendu comme suit :

   ```
     <srcSchema extendedSchema="nms:seedMember" label="Seed addresses" labelSingular="Seed address" name="seedMember" namespace="cus">
     <element name="common">
       <element name="custom_cus_person">
         <attribute name="lastname" template="cus:person:person/@lastname"/>
         <attribute name="firstname" template="cus:person:person/@firstname"/>
         <attribute name="email" sqlname="myEmailField" template="cus:person:person/address/@addrEnv" xml="false"/>
       </element>
     </element>
     <element name="seedMember">
      <element aggregate="cus:seedMember:common"/>
     </element>
   </srcSchema>
   ```

   >[!NOTE]
   >
   >L&#39;extension du schéma **nms:seedMember** doit respecter les structures types d&#39;une opération et d&#39;une diffusion dans Adobe Campaign.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * Lors de l&#39;extension, vous devez obligatoirement préciser **un nom SQL (@sqlname)** pour le champ &#39;email&#39;. Le nom SQL doit être différent de &#39;sEmail&#39; qui est réservé pour le schéma des destinataires.
   >    * Vous devez impérativement mettre à jour la structure de la base avec le schéma créé lors de l&#39;extension de **nms:seedMember**.
   >    * Dans le **nms:seedMember** , le champ contenant l’adresse électronique doit avoir la valeur **name=&quot;email&quot;** comme attribut. Le nom SQL doit être différent de &#39;sEmail&#39; qui est déjà utilisé pour le schéma des destinataires. Cet attribut doit être immédiatement déclaré sous la variable **`<element name="custom_cus_person" />`** élément .
   >    
   >

1. Modifiez le formulaire **[!UICONTROL seedMember]** en conséquence pour définir un nouvel onglet « Destinataire interne » dans la fenêtre **[!UICONTROL Adresses de contrôle]**. Pour plus dʼinformations, consultez [cette page](../../configuration/using/form-structure.md).

   ```
   <container colcount="2" label="Internal recipient" name="internal"
                xpath="custom_cus_person">
       <input colspan="2" editable="true" nolabel="true" type="treeEdit">
         <container label="Recipient (cus:person)">
           <input xpath="@last name"/>
           <input xpath="@first name"/>
           <input xpath="@email"/>
         </container>
       </input>
     </container>
   ```

Si tous les attributs de lʼadresse de contrôle ne sont pas renseignés, Adobe Campaign procède automatiquement à la substitution de profils : ils seront alimentés automatiquement, lors de la personnalisation, par les données dʼun profil existant.
