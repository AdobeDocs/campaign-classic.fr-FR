---
product: campaign
title: Contenu conditionnel
description: Découvrez comment ajouter du contenu conditionnel
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Personalization, Multilingual Messages
role: User
hide: true
exl-id: 12595ee4-6a52-4e06-b80d-85fe633a5a11
TQID: https://experienceleague.adobe.com/S8pQz1eOVkbkBKFzhPwzEfj50cPnBBOeYNGFg-R6EZ4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 517
ht-degree: 88%

---

# Contenu conditionnel{#conditional-content}

En configurant des champs de contenu conditionnel, vous pouvez créer une personnalisation dynamique basée sur le profil du ou de la destinataire, par exemple. Les blocs de texte et/ou les images sont remplacés lorsqu’une condition particulière est remplie.

![](assets/do-not-localize/how-to-video.png) [Découvrez cette fonctionnalité en vidéo](#conditionnal-content-video)


## Utilisation de conditions dans un e-mail {#using-conditions-in-an-email}

Dans l&#39;exemple ci-dessous, vous allez découvrir comment créer de manière dynamique un message personnalisé selon le genre et les centres d&#39;intérêt du destinataire.

* Affichage affichant « M. » ou « Mme » suivant la valeur du champ **[!UICONTROL Genre]** (M ou F) dans la source de données.
* Assemblage personnalisé d&#39;une newsletter ou d&#39;offres promotionnelles en fonction des centres d&#39;intérêt renseignés ou détectés :

   * Centre d&#39;intérêt 1 -- > Bloc 1
   * Centre d&#39;intérêt 2 -- > Bloc 2
   * Centre d&#39;intérêt 3 -- > Bloc 3
   * Centre d&#39;intérêt 4 -- > Bloc 4

Pour créer un contenu conditionnel en fonction de la valeur d&#39;un champ, respectez les étapes suivantes :

1. Cliquez sur l&#39;icône de personnalisation et choisissez **[!UICONTROL Contenu conditionnel > Si]**.

   ![](assets/s_ncs_user_conditional_content02.png)

   Les éléments de personnalisation sont insérés dans le corps du message. Vous devez maintenant les configurer.

1. Renseignez ensuite les paramètres de l&#39;expression **if**.

   Pour cela :

   * Sélectionnez le premier élément de l’expression **`<field>`** (par défaut, cet élément est en surbrillance lors de l’insertion de l’expression **if**) et cliquez sur l’icône de personnalisation pour le remplacer par le champ sur lequel porte le test.

     ![](assets/s_ncs_user_conditional_content03.png)

   * Remplacez **`<value>`** par la valeur du champ pour lequel la condition sera remplie. Cette valeur doit être entre guillemets.
   * Indiquez le contenu à insérer lorsque la condition est remplie. Il peut s’agir de texte, d’une image, d’un formulaire, d’un lien hypertexte, etc.

     ![](assets/s_ncs_user_conditional_content04.png)

1. Cliquez sur l&#39;onglet **[!UICONTROL Aperçu]** pour visualiser le contenu du message en fonction du destinataire de la diffusion :

   * Sélection d&#39;un destinataire pour lequel la condition est vérifiée :

     ![](assets/s_ncs_user_conditional_content05.png)

   * Sélection d&#39;un destinataire pour lequel la condition n&#39;est pas vérifiée :

     ![](assets/s_ncs_user_conditional_content06.png)

Vous pouvez ajouter d’autres cas et définir un contenu différent en fonction des valeurs d’un ou plusieurs champs. Utilisez pour cela les options **[!UICONTROL Contenu conditionnel > Sinon]** et **[!UICONTROL Contenu conditionnel > Sinon si]**. La configuration de ces expressions est la même que pour l’expression **if**.

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>Pour respecter la syntaxe du JavaScript, les caractères **%> &lt;%** doivent être supprimés après l&#39;ajout de conditions de type **Sinon** et **Sinon si**.

Cliquez sur l&#39;onglet **[!UICONTROL Aperçu]** et sélectionnez un destinataire pour visualiser le contenu conditionnel.

![](assets/s_ncs_user_conditional_content08.png)

## Création dʼun e-mail multilingue {#creating-multilingual-email}

Dans l’exemple ci-dessous, vous allez découvrir comment créer un email multilingue. Le contenu s’affiche dans une langue ou une autre, selon la préférence linguistique du destinataire.

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

1. Testez le contenu de l&#39;email dans l&#39;onglet **[!UICONTROL Aperçu]** en sélectionnant des destinataires avec des préférences linguistiques différentes.

   >[!NOTE]
   >
   >Comme aucune autre version n&#39;a été définie dans le contenu de l&#39;email, veillez à filtrer la population cible avant d&#39;envoyer l&#39;email.

## Tutoriel vidéo {#conditionnal-content-video}

Découvrez comment ajouter du contenu conditionnel à une diffusion en prenant pour exemple une newsletter multilingue.

>[!VIDEO](https://video.tv.adobe.com/v/24926?quality=12)

D’autres vidéos pratiques sur Campaign Classic sont disponibles [ici](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=fr).
