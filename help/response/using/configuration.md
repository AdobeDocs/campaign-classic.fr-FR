---
product: campaign
title: Configuration de la gestion de la réaction (Response Manager) de Campaign
description: Découvrez comment configurer la gestion de la réaction (Response Manager) de Campaign
feature: Campaigns
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1a115ca9-2532-4bd3-be77-814e43250c51
TQID: https://experienceleague.adobe.com/P89PBe23uuRmGX5vb6lCNd8kTd24peaZcKsTRAj2pnw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
  - id: d72afaa0-c842-48c8-9a3c-51b7911edc1b
topic_v2:
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 796
ht-degree: 100%

---

# Configuration de la gestion de la réaction (Response Manager) de Campaign{#configuration}



Cette section est destinée aux personnes responsables de la configuration de la gestion des réponses.Elle suppose une certaine connaissance de l’extension des schémas, de la définition des workflows et de la programmation SQL.

Elle permet de comprendre comment adapter le modèle de données standard aux spécificités d’une table de transactions externe à Adobe Campaign avec la table des personnes individuelles.Cette table des personnes individuelles peut coïncider avec la table des individus disponibles dans Adobe Campaign ou avec une table différente.

L’hypothèse de mesure est lancée par le workflow de processus d’opération (**[!UICONTROL operationMgt]**).Chaque hypothèse représente un processus distinct exécuté de manière asynchrone avec un statut d’exécution (En édition, En attente, Terminé, En échec, etc.)et contrôlée par un planificateur qui gère les contraintes de priorité, la limitation du nombre de processus simultanés, la page de faible activité et l’exécution automatique avec fréquence.

## Configuration de schémas {#configuring-schemas}

>[!CAUTION]
>
>Ne modifiez pas les schémas natifs de l’application. Utilisez plutôt le mécanisme d’extension de schéma. Sinon, les schémas modifiés ne seront pas mis à jour au moment des futures mises à niveau de l’application. Cela peut entraîner des dysfonctionnements lors de l’utilisation d’Adobe Campaign.

Avant toute utilisation du module de la réaction, vous devez définir les différentes tables (transactions, détails des transactions) et leur relation avec les diffusions, les offres et les individus.

### Schémas standards {#standard-schemas}

Le schéma d’usine **[!UICONTROL nms:remaMatch]** contient la table des logs de réaction, c’est-à-dire la relation entre les personnes individuelles, les hypothèses et la table des transactions.Ce schéma doit être utilisé comme schéma d’héritage pour la table de destination finale des logs de réponses.

Le schéma **[!UICONTROL nms:remaMatchRcp]** est également fourni en standard. Il contient le stockage des logs de réaction pour les destinataires Adobe Campaign (**[!UICONTROL nms:recipient]**).Pour l’utiliser, il devra être étendu pour lui associer la table des transactions (contenant les achats, etc.).

### Tables des transactions et des détails des transactions {#transaction-tables-and-transaction-details}

La table des transactions doit comporter un lien direct vers les individus.

Vous pouvez également ajouter une table contenant les détails de la transaction.Ce n’est pas directement lié aux personnes individuelles.

Par exemple dans le cas d’un ticket de caisse, une table des transactions est liée au contact (la table des tickets) et une table des lignes de tickets n’est reliée qu’à la table des tickets (la table des détails).Vous pouvez ainsi paramétrer l’hypothèse directement au niveau de la table des lignes de tickets associée à la table des tickets.

>[!NOTE]
>
>Si vous souhaitez conserver l’identifiant de ticket de caisse qui décrit le comportement attendu dans les hypothèses, vous pouvez étendre le modèle de table nms:remaMatchRcp afin de lui ajouter l’identifiant (dans ce cas, aucun calcul de retour sur investissement n’est associé à ces champs).

L&#39;ajout d&#39;une date d&#39;évènement est également fortement recommandée.

Le schéma suivant représente les jointures entre les différentes tables une fois le paramétrage effectué :

![](assets/response_data_model.png)

### Gestion de la réaction et destinataires {#response-management-with-adobe-campaign-recipients}

Dans cet exemple, vous allez intégrer une table d’achats dans votre module de gestion des réponses en utilisant une table des destinataires **[!UICONTROL nms:recipient]** disponible dans Adobe Campaign.

La table des logs de réponse de la personne destinataire **[!UICONTROL nms:remaMatchRcp]** est étendue pour ajouter un lien vers le schéma de la table des achats.Dans l’exemple suivant, la table des achats est appelée **demo:purchase**.

1. Via l&#39;explorateur Adobe Campaign, sélectionnez le noeud **[!UICONTROL Administration]** > **[!UICONTROL Gestion de campagne]** > **[!UICONTROL Mappings de ciblage]**.
1. Cliquez-droit sur **Destinataires** puis sélectionnez **[!UICONTROL Actions]** et **[!UICONTROL Modifier les options de la dimension de ciblage]**.

   ![](assets/delivery_mapping1.png)

1. Dans la fenêtre qui s&#39;affiche, personnalisez éventuellement l&#39;**[!UICONTROL Espace de noms d&#39;extension]** puis cliquez sur **[!UICONTROL Suivant]**.

   ![](assets/delivery_mapping2.png)

1. Dans la catégorie **[!UICONTROL Gestion de la réaction]**, assurez-vous que la case **[!UICONTROL Générer un schéma de stockage pour les réactions]** est cochée.

   Cliquez ensuite sur **[!UICONTROL Définir des champs supplémentaires…]** pour sélectionner les tables de transactions associées et ajouter les champs souhaités à l’extension du schéma nms:remaMatchRcp.

   ![](assets/delivery_mapping3.png)

Le schéma alors créé se présente comme suit :

```
<srcSchema _cs="Reactions (Recipients) (cus)" entitySchema="xtk:srcSchema" extendedSchema="nms:remaMatchRcp" 
img="nms:remaMatch.png" implements="xtk:persist" label="Reactions (Recipients)" mappingType="sql"
name="remaMatchRcp" namespace="cus">  
 <element label="Reactions (Recipients)" name="remaMatchRcp">    
  <key internal="true" name="match">      
   <keyfield xlink="hypothesis"/>      
   <keyfield xlink="broadLog"/>      
   <keyfield xlink="proposition"/>    
  </key>    
  <attribute label="Quantity" name="quantity" type="long"/>    
  <element name="purchase" target="demo:purchase" type="link"/>    
  <element name="hypothesis" revLabel="Reactions (Recipients)" revLink="remaMatchRcp"/>    
  <element applicableIf="HasPackage('nms:coreInteraction')" label="Proposition" name="proposition" target="nms:propositionRcp" type="link"/>   
  <element desc="Message (Delivery log)" label="Message" name="broadLog" target="nms:broadLogRcp" type="link"/>    
  <element label="Respondent" name="responder" target="nms:recipient" type="link"/>  
 </element>  
 <createdBy _cs="Administrator (admin)"/>  
 <modifiedBy _cs="Administrator (admin)"/>
</srcSchema>
```

### Gestion de la réaction avec une table des destinataires personnalisée {#response-management-with-a-personalized-recipient-table}

Dans cet exemple, vous allez intégrer une table d&#39;achats dans votre module de gestion de la réaction en utilisant une table d&#39;individus autre que la table des destinataires disponible dans Adobe Campaign.

* Créez un schéma de logs de réponses dérivé du schéma **[!UICONTROL nms:remaMatch]**.

  La table des personnes individuelles étant différente de la table des destinataires Adobe Campaign, il est nécessaire de créer un nouveau schéma des logs de réponses basé sur le schéma **[!UICONTROL nms:remaMatch]**.Il faut ensuite le compléter avec les liens vers les logs de diffusion et la table des actes d&#39;achats.

  Dans l’exemple suivant, nous utiliserons le schéma **demo:broadLogPers** et la table des transactions **demo:purchase** :

  ```
  <srcSchema desc="Linking of a recipient transaction to a hypothesis"    
  img="nms:remaMatch.png" label="Responses on persons" labelSingular="Responses on a person" name="remaMatchPers" namespace="nms">
    <element name="remaMatchPers" template="nms:remaMatch">
      <key internal="true" name="match">
        <keyfield xlink="hypothesis"/>
       <keyfield xlink="purchase"/>
      </key>
  
      <element name="hypothesis" revLabel="Response logs for persons" revLink="remaMatchPers"/>
      <element applicableIf="HasPackage('nms:interaction')" label="Proposition" name="proposition"
               target="demo:propositionPers" type="link"/>
      <element label="Delivery log" name="broadLog" target="demo:broadLogPers" type="link"/>
    </element>
  </srcSchema>
  ```

* Modifiez le formulaire des hypothèses dans le schéma **[!UICONTROL nms:remaHypothesis]**.

  Par défaut, la liste des logs de réponses est visible dans les logs des destinataires.Il faut donc modifier la forme des hypothèses pour pouvoir visualiser les nouveaux logs de réponses créés à l’étape précédente.

  Par exemple :

  ```
   <container type="visibleGroup" visibleIf="[context/@remaMatchStorage]= 'demo:remaMatchPers'">
                <input hideEditButtons="true" img="nms:remaMatch.png" nolabel="true" refresh="true"
                 toolbarCaption="Responses generated by the hypothesis" type="linklist"
                 xpath="remaMatchPers">
            <input xpath="[.]"/>
            <input xpath="@controlGroup"/>
          </input>
     </container> 
  ```

## Gestion des indicateurs {#managing-indicators}

Le module Response Manager est fourni avec une liste d’indicateurs prédéfinis.Vous pouvez cependant ajouter d’autres indicateurs de mesure personnalisés.

Pour cela, vous devez étendre la table des hypothèses en insérant deux champs pour chaque nouvel indicateur :

* le premier pour la population ciblée ;
* le second pour la population témoin.

Par exemple :

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:remaHypothesis" label="Measurement hypothesis" 
md5="1D4DED54FF8EC2432AED6736EDE6F547" name="remaHypothesis" namespace="demo" xtkschema="xtk:srcSchema">  
    <element name="remaHypothesis">    
        <element name="indicators">      
            <!-- Quantity -->      
            <attribute label="Total contacted" name="contactReactedTotalQuantity" type="long"/>
            <attribute label="Total number of people in the control group" name="proofReactedTotalquantity" type="long"/> 
        </element> 
    </element>
</srcSchema>
```
