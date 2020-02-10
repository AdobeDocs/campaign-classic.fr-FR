---
title: Contenu conditionnel
seo-title: Contenu conditionnel
description: Contenu conditionnel
seo-description: null
page-status-flag: never-activated
uuid: d1c38263-a163-448c-8822-8b3e776e45cf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 167cc61a-fbc7-48cb-89ff-fbdbf9321c01
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Contenu conditionnel{#conditional-content}

En configurant des champs de contenu conditionnel, vous pouvez créer une personnalisation dynamique basée sur le profil du destinataire, par exemple. Les blocs de texte et/ou les images sont remplacés lorsqu&#39;une condition particulière est remplie.

## Utiliser des conditions dans un email {#using-conditions-in-an-email}

Dans l&#39;exemple ci-dessous, vous allez découvrir comment créer de manière dynamique un message personnalisé selon le genre et les centres d&#39;intérêt du destinataire.

* Affichage de &quot;M.&quot; ou &quot;Mme&quot; selon la valeur du **[!UICONTROL Gender]** champ (M ou F) dans la source de données,
* Assemblage personnalisé d&#39;une newsletter ou d&#39;offres promotionnelles en fonction des centres d&#39;intérêt renseignés ou détectés :

   * Centre d&#39;intérêt 1 -- > Bloc 1
   * Centre d&#39;intérêt 2 -- > Bloc 2
   * Centre d&#39;intérêt 3 -- > Bloc 3
   * Centre d&#39;intérêt 4 -- > Bloc 4

Pour créer un contenu conditionnel en fonction de la valeur d&#39;un champ, respectez les étapes suivantes :

1. Cliquez sur l’icône de personnalisation et sélectionnez **[!UICONTROL Conditional content > If]**.

   ![](assets/s_ncs_user_conditional_content02.png)

   Les éléments de personnalisation sont insérés dans le corps du message : vous devez maintenant les paramétrer.

1. Renseignez ensuite les paramètres de l&#39;expression **if**.

   Pour cela :

   * Select the first element of the expression, **`<field>`**, (by default, this element is highlighted during insertion of the **if** expression) and click the personalization icon to replace it with the test field.

      ![](assets/s_ncs_user_conditional_content03.png)

   * Remplacez **`<value>`** par la valeur du champ pour lequel la condition sera remplie. Cette valeur doit être entre guillemets.
   * Spécifiez ensuite le contenu à insérer lorsque la condition est vérifiée. Ce contenu peut être du texte, une image, un formulaire, un lien hypertexte, etc.

      ![](assets/s_ncs_user_conditional_content04.png)

1. Click the **[!UICONTROL Preview]** tab to view the content of the message according to the delivery recipient:

   * Sélection d&#39;un destinataire pour lequel la condition est vérifiée :

      ![](assets/s_ncs_user_conditional_content05.png)

   * Sélection d&#39;un destinataire pour lequel la condition n&#39;est pas vérifiée :

      ![](assets/s_ncs_user_conditional_content06.png)

Vous pouvez ajouter d’autres cas et définir un contenu différent selon les valeurs d’un ou de plusieurs champs. Pour ce faire, utilisez **[!UICONTROL Conditional content > Else]** et **[!UICONTROL Conditional content > Else if]**. Ces expressions sont configurées de la même manière que l’expression **if** .

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>Pour respecter la syntaxe du JavaScript, les caractères **%> &lt;%** doivent être supprimés après l&#39;ajout de conditions de type **Sinon** et **Sinon si**.

Click **[!UICONTROL Preview]** and select a recipient to view the conditional content.

![](assets/s_ncs_user_conditional_content08.png)

## Créer un email multilingue {#creating-multilingual-email}

Dans l&#39;exemple ci-dessous, vous allez découvrir comment créer un email multilingue. Le contenu s&#39;affichera dans une langue ou une autre en fonction de la préférence linguistique du destinataire.

1. Créez un email et sélectionnez la population cible. Dans cet exemple, la condition d&#39;affichage d&#39;une version ou d&#39;une autre sera basée sur la valeur **Langue** du profil du destinataire. Dans cet exemple, ces valeurs sont définies sur **EN**, **FR**, **ES**.
1. Dans le contenu HTML de l&#39;email, cliquez sur l&#39;onglet **[!UICONTROL Source]** et collez le code suivant :

   ```
   <% if (language == "EN" ) { %>
   <DIV id=en-version>Hello <%= recipient.firstName %>,</DIV>
   <DIV>Discover your new offers!</DIV>
   <DIV><a href="https://www.adobe.com/products/en">www.adobe.com/products/en</A></FONT></DIV><%
    } %>
   <% if (language == "FR" ) { %>
   <DIV id=fr-version>Bonjour <%= recipient.firstName %>,</DIV>
   <DIV>Découvrez nos nouvelles offres !</DIV>
   <DIV><a href="https://www.adobe.com/products/fr">www.adobe.com/products/fr</A></DIV><%
    } %>
    <% if (language == "ES" ) { %>
   <DIV id=es-version><FONT face=Arial>
   <DIV>Olà <%= recipient.firstName %>,</DIV>
   <DIV>Descubra nuestros nuevas ofertas !</DIV>
   <DIV><a href="https://www.adobe.com/products/es">www.adobe.com/products/es</A></DIV>
   <% } %>
   ```

1. Test email content in the **[!UICONTROL Preview]** tab by selecting recipients with different preferred languages.

   >[!NOTE]
   >
   >Comme aucune autre version n&#39;a été définie dans le contenu de l&#39;email, veillez à filtrer la population cible avant d&#39;envoyer l&#39;email.
