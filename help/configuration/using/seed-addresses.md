---
title: Adresses de contrôle
seo-title: Adresses de contrôle
description: Adresses de contrôle
seo-description: null
page-status-flag: never-activated
uuid: 0ebdeb73-be67-4c34-9f59-9fd4fb5241ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 41338d32-b95c-45ae-bee6-17b2af5bd837
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Adresses de contrôle{#seed-addresses}

Si la table des destinataires est une table personnalisée, vous devez effectuer des paramétrages complémentaires. Le schéma **[!UICONTROL nms:seedMember]** doit être étendu. Un onglet supplémentaire est alors ajouté au niveau des adresses de contrôle afin de définir les champs adéquats, comme dans l&#39;exemple ci-dessous :

![](assets/s_ncs_user_seedlist_new_tab.png)

Pour plus d&#39;informations sur l&#39;utilisation des adresses de contrôle, consultez [cette section](../../delivery/using/about-seed-addresses.md).

## Mise en oeuvre {#implementation}

Le schéma **nms:seedMember** et le formulaire éponyme livrés d&#39;usine ont vocation à être étendus pour un paramètrage client afin de référencer tous les champs nécessaires. La définition du schéma contient des commentaires expliquant son mode de paramétrage.

Définition du schéma étendu de la table des destinataires :

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

1. Créez une extension du schéma **nms:seedMember** . Pour plus d’informations, reportez-vous à la section [Extension d’un schéma](../../configuration/using/extending-a-schema.md).
1. Dans cette extension, ajoutez un nouvel élément à la racine de l&#39;élément **[!UICONTROL seedMember]**, avec les paramètres suivants :

   ```
   name="custom_customNamespace_customSchema"
   ```

   Cet élément doit contenir les champs nécessaires à l&#39;export de campagnes. Ces champs doivent porter le même nom que le champ correspondant dans le schéma externe. Par exemple, si le schéma est **[!UICONTROL cus:person]**, le schéma **[!UICONTROL nms:seedMember]** devra être étendu comme dans l&#39;exemple suivant :

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
   >L&#39;extension du schéma **nms:seedMember** doit respecter les structures types d&#39;une opération et d&#39;une diffusion dans Adobe Campaign.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * Lors de l&#39;extension, vous devez obligatoirement préciser **un nom SQL (@sqlname)** pour le champ &#39;email&#39;. Le nom SQL doit être différent de &#39;sEmail&#39; qui est réservé pour le schéma des destinataires.
   >    * Vous devez impérativement mettre à jour la structure de la base avec le schéma créé lors de l&#39;extension de **nms:seedMember**.
   >    * In the **nms:seedMember** extension, the field containing the email address must have **name=&quot;email&quot;** as an attribute. The SQL name must be different from &#39;sEmail&#39; which is already used for the recipient schema. This attribute must be immediately declared under the **`<element name="custom_cus_person" />`** element.


1. Modifiez le formulaire **[!UICONTROL seedMember]** en conséquence pour définir un nouvel onglet &quot;Destinataire interne&quot; dans la fenêtre des adresses **[!UICONTROL de]** démarrage. For more on this, refer to [Form structure](../../configuration/using/form-structure.md).

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

Si tous les attributs de l&#39;adresse de contrôle ne sont pas renseignés, Adobe Campaign procède automatiquement à la substitution de profils : ils seront alimentés automatiquement, lors de la personnalisation, par les données d&#39;un profil existant.
