---
title: Blocs de personnalisation
seo-title: Blocs de personnalisation
description: Blocs de personnalisation
seo-description: null
page-status-flag: never-activated
uuid: f9867f8d-f6ce-4a5f-b6b4-fd8056d28576
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: e68d1435-70e6-479e-a347-9ff9f9f11b92
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Blocs de personnalisation{#personalization-blocks}

Les blocs de personnalisation sont dynamiques, personnalisés et contiennent un rendu spécifique que vous pouvez insérer dans vos remises. Par exemple, vous pouvez ajouter un logo, un message de bienvenue ou un lien vers une page miroir. Voir [Insertion de blocs](#inserting-personalization-blocks)de personnalisation.

>[!NOTE]
>
>Personalization blocks are also available from the **[!UICONTROL Digital Content Editor (DCE)]** . For more on this, refer to [this page](../../web/using/editing-content.md#inserting-a-personalization-block).

Les blocs de personnalisation sont accessibles via le **[!UICONTROL Resources > Campaign Management > Personalization blocks]** noeud de l’explorateur Adobe Campaign. Plusieurs blocs sont disponibles par défaut (voir Blocs [](#out-of-the-box-personalization-blocks)de personnalisation prêts à l’emploi).

Vous pouvez définir de nouveaux blocs qui vous permettront d&#39;optimiser la personnalisation de vos livraisons. Pour plus d’informations, reportez-vous à la section [Définition de blocs](#defining-custom-personalization-blocks)de personnalisation personnalisée.

## Insérer des blocs de personnalisation {#inserting-personalization-blocks}

Pour insérer un bloc de personnalisation dans un message, procédez comme suit :

1. In the content editor of the delivery wizard, click the personalized field icon and select the **[!UICONTROL Include]** menu.
1. Select a personalization block from the list (the list displays the 10 last used blocks), or click the **[!UICONTROL Other...]** menu to access the full list.

   ![](assets/s_ncs_user_personalized_block01.png)

1. Le **[!UICONTROL Other...]** menu donne accès à tous les blocs de personnalisation prêts à l’emploi et personnalisés (voir les blocs [de personnalisation prêts à l’emploi et](#out-of-the-box-personalization-blocks) Définition des blocs [](#defining-custom-personalization-blocks)de personnalisation personnalisée).

   ![](assets/s_ncs_user_personalized_block02.png)

1. Le bloc de personnalisation est alors inséré sous forme de script. Il sera automatiquement adapté au profil du destinataire lors de la génération de la personnalisation.

   ![](assets/s_ncs_user_personalized_block03.png)

1. Click the **[!UICONTROL Preview]** tab and select a recipient to view the personalization.

   ![](assets/s_ncs_user_personalized_block04.png)

Vous pouvez inclure le code source d’un bloc de personnalisation dans le contenu de diffusion. Pour ce faire, sélectionnez-la **[!UICONTROL Include the HTML source code of the block]** lors de sa sélection.

![](assets/s_ncs_user_personalized_block05.png)

Le code source HTML est inséré dans le contenu de diffusion. Par exemple, le bloc **[!UICONTROL Greetings]** de personnalisation s’affiche comme suit :

![](assets/s_ncs_user_personalized_block06.png)

## Exemple de blocs de personnalisation {#personalization-blocks-example}

Dans cet exemple, nous créons un email dans lequel nous utilisons les blocs de personnalisation pour permettre au destinataire d&#39;afficher la page miroir, de partager la newsletter sur les réseaux sociaux et de se désabonner des diffusions futures.

Pour ce faire, nous devons insérer les blocs de personnalisation suivants :

* **[!UICONTROL Link to mirror page]** .
* **[!UICONTROL Social network sharing links]** .
* **[!UICONTROL Unsubscription link]** .

>[!NOTE]
>
>Pour plus d’informations sur la génération de la page miroir, voir [Génération de la page](../../delivery/using/sending-messages.md#generating-the-mirror-page)miroir.

1. Créez une nouvelle diffusion ou ouvrez une diffusion existante de type email.
1. In the delivery wizard, click **[!UICONTROL Subject]** to edit the subject of the message and enter a subject.
1. Insérez les blocs de personnalisation dans le corps du message. Pour ce faire, cliquez sur dans le contenu du message, cliquez sur l’icône de champ personnalisé et sélectionnez le **[!UICONTROL Include]** menu.
1. Sélectionnez le premier bloc à insérer. Renouvelez la procédure pour inclure les deux autres blocs.

   ![](assets/s_ncs_user_personalized_block_example.png)

1. Cliquez sur l’ **[!UICONTROL Preview]** onglet pour afficher le résultat de la personnalisation. Vous devez sélectionner un destinataire pour afficher son message.

   ![](assets/s_ncs_user_personalized_block_example2.png)

1. Confirmez que le contenu des blocs est affiché correctement.

## Blocs de personnalisation d&#39;usine {#out-of-the-box-personalization-blocks}

Une liste des blocs de personnalisation est disponible par défaut pour vous aider à personnaliser le contenu de votre message.

>[!NOTE]
>
>Cette liste dépend des modules et options installés sur votre instance.

![](assets/s_ncs_user_personalized_block_list.png)

* **[!UICONTROL Greetings]** : insère les salutations avec le nom du destinataire. Exemple : &quot;Bonjour John Doe&quot;.
* **[!UICONTROL Insert logo]** : insère un logo prêt à l’emploi qui a été défini lors de la configuration de l’instance.
* **[!UICONTROL Powered by Adobe Campaign]** : insère le logo &quot;Optimisé par Adobe Campaign&quot;.
* **[!UICONTROL Mirror page URL]** : insère l’URL de la page miroir, ce qui permet aux concepteurs de distribution de vérifier le lien.

   >[!NOTE]
   >
   >Pour plus d’informations sur la génération de la page miroir, voir [Génération de la page](../../delivery/using/sending-messages.md#generating-the-mirror-page)miroir.

* **[!UICONTROL Link to mirror page]** : insère un lien vers la page miroir : &quot;Si vous ne parvenez pas à afficher ce message correctement, cliquez ici&quot;.
* **[!UICONTROL Unsubscription link]** : insère un lien permettant de se désabonner de toutes les livraisons (liste noire).
* **[!UICONTROL Formatting function for proper nouns]** : génère la fonction **[!UICONTROL toSmartCase]** JavaScript, qui modifie la première lettre de chaque mot en majuscules. Ce bloc doit être inséré dans le code source de la remise, dans les **`<script>...</script>`** balises.

   Dans l’exemple ci-dessous, la fonction est utilisée pour remplacer l’élément &quot;Mon en-tête&quot; par &quot;Mon nouvel en-tête&quot; par des lettres majuscules à chaque mot :

   ```
   <h1 id="sample">My header</h1>
   <script><%@ include view='toSmartCase'%>;
   document.getElementById("sample").innerHTML = toSmartCase("My new header");
   </script>
   ```

   ![](assets/s_ncs_user_personalized_block_uppercasefunction.png)

* **[!UICONTROL Registration page URL]** : insère une URL d’abonnement (voir [A propos des services et des abonnements](../../delivery/using/about-services-and-subscriptions.md)).
* **[!UICONTROL Registration link]** : insère un lien d’abonnement. qui a été définie lors de la configuration de l’instance.
* **[!UICONTROL Registration link (with referrer)]** : insère un lien d’abonnement permettant d’identifier le visiteur et la diffusion. Le lien a été défini lors de la configuration de l’instance.

   >[!NOTE]
   >
   >Ce bloc peut être utilisé dans les diffusions qui ciblent uniquement les visiteurs.

* **[!UICONTROL Registration confirmation]** : insère un lien permettant de confirmer l’abonnement.
* **[!UICONTROL Social network sharing links]** : insère des boutons qui permettent au destinataire de partager un lien vers le contenu de la page miroir avec le client de messagerie, Facebook, Twitter, Google + et LinkedIn (voir [Marketing Viral : à un ami](../../delivery/using/viral-and-social-marketing.md#viral-marketing--forward-to-a-friend)).
* **[!UICONTROL Style of content emails]** et **[!UICONTROL Notification style]** : générer du code qui formate un courrier électronique avec des styles HTML prédéfinis. Ces blocs doivent être insérés dans le code source de la remise, dans la **[!UICONTROL ...]** section, en **`<style>...</style>`** balises.
* **[!UICONTROL Offer acceptance URL in unitary mode]** : insère une URL permettant de définir une offre d’interaction **[!UICONTROL Accepted]** (voir [cette section](../../interaction/using/offer-analysis-report.md)).

## Définir des blocs de personnalisation personnalisés {#defining-custom-personalization-blocks}

Vous pouvez définir de nouveaux champs de personnalisation à insérer à partir de l’icône de champ personnalisé via le **[!UICONTROL Include...]** menu. Ces champs sont définis dans des blocs de personnalisation.

Pour créer un bloc de personnalisation, ouvrez l&#39;Explorateur et respectez les étapes suivantes :

1. Cliquez sur le **[!UICONTROL Resources > Campaign Management > Personalization blocks]** noeud.
1. Right-click the list of blocks and select **[!UICONTROL New]** .
1. Renseignez le paramétrage du bloc de personnalisation :

   ![](assets/s_ncs_user_personalized_block.png)

   * Saisissez le libellé du bloc. Ce libellé sera affiché dans la fenêtre d&#39;insertion de champs de personnalisation.
   * Sélectionnez **[!UICONTROL Visible in the customization menus]** pour rendre ce bloc accessible à partir de l’icône d’insertion du champ de personnalisation.
   * Si nécessaire, sélectionnez **[!UICONTROL The content of the personalization block depends upon the format]** pour définir deux blocs distincts pour les courriers électroniques au format HTML et ceux au format texte.

      Deux onglets seront alors affichés dans la section inférieure de cet éditeur (Contenu HTML et Contenu Texte) pour définir les contenus correspondants.

      ![](assets/s_ncs_user_personalized_block_b.png)

   * Enter the content (in HTML, text, JavaScript, etc.) of the personalization block(s) and click **[!UICONTROL Save]** .
