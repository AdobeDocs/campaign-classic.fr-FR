---
title: Insérer un code-barres dans un email
seo-title: Insérer un code-barres dans un email
description: Insérer un code-barres dans un email
seo-description: null
page-status-flag: never-activated
uuid: 61f9d8ea-38b0-46a5-8085-b6f34f8559f7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 679b9ae2-362c-483d-acb8-47bc01928541
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Insérer un code-barres dans un email{#inserting-a-barcode-in-an-email}

Le module de génération de codes-barres permet de créer plusieurs types de codes-barres répondant aux normes les plus courantes, dans les formats 1D (unidimensionnel) et 2D (bidimensionnel).

Il est possible de générer dynamiquement un code-barres sous la forme d&#39;un bitmap au moyen d&#39;une valeur définie grâce à des critères client. Un code-barres personnalisé peut être intégré à des communications émises par email dans le cadre d&#39;une campagne marketing. Le destinataire pourra imprimer ce message et le présenter à la société émettrice qui le scannera (lors d&#39;un passage en caisse par exemple).

To insert a barcode into an email, place the cursor in the content where you want to display it, then click the personalization button. Select **[!UICONTROL Include > Barcode...]**.

![](assets/barcode_insert_14.png)

Puis paramétrez les éléments suivants en fonction de vos besoins :

1. Choisissez le type de code-barres.

   * Pour le format 1D, Adobe Campaign propose les types suivants: Codabar, Code 128, GS1-128 (anciennement EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 of 5, POSTNET et Royal Mail (RM4SCC).

      Exemple de code-barres 1D :

      ![](assets/barcode_insert_08.png)

   * Les types DataMatrix et PDF417 concernent le format 2D.

      Exemple de code-barres 2D :

      ![](assets/barcode_insert_09.png)

   * Pour insérer un QR Code, sélectionnez ce type et indiquez le taux de correction d&#39;erreur à appliquer. Ce taux définit la quantité d&#39;informations répétées et donc une tolérance plus ou moins importante aux dégradations.

      ![](assets/barcode_insert_06.png)

      Exemple de QR Code :

      ![](assets/barcode_insert_12.png)

1. Indiquez la taille du code-barres à insérer dans l&#39;email : le paramétrage de l&#39;échelle permet d&#39;augmenter ou de réduire la taille du code-barres, de x 1 à x 10.
1. Le **[!UICONTROL Value]** champ vous permet de définir la valeur du code à barres. Une valeur peut correspondre à une offre spéciale et peut être fonction d’un critère ; elle peut être la valeur d’un champ de base de données lié aux clients.

   Cet exemple montre un code à barres de type EAN-8 auquel a été ajouté le numéro de compte d’un destinataire. Pour ajouter ce numéro de compte, cliquez sur le bouton de personnalisation à droite du **[!UICONTROL Value]** champ et sélectionnez **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. The **[!UICONTROL Height]** field lets you configure the height of the barcode without changing its width, by altering the amount of space between each bar.

   Il n&#39;existe pas de contrôle restrictif de saisie en fonction du type de code-barres sélectionné. Si une valeur de code-barres est erronée, vous ne le saurez que lorsque vous passerez en vue **Aperçu** avec le code-barres marqué d&#39;une croix rouge.

   >[!NOTE]
   >
   >La valeur donnée à un code-barres dépend du type choisi. Par exemple, un type EAN-8 devra comporter exactement huit chiffres.
   >
   >Le bouton de personnalisation à droite du **[!UICONTROL Value]** champ vous permet d’ajouter des données en plus de la valeur elle-même. Cela enrichit le code à barres, à condition que la norme de code à barres l’accepte.
   >
   >For example, if you are using a GS1-128 type barcode and want to enter the account number of a recipient in addition to the value, click the personalization button and select **[!UICONTROL Recipient > Account number]**. If the account number of the selected recipient is entered correctly, the barcode takes it into account.

Une fois ces éléments configurés, vous pouvez finaliser votre courrier électronique et l’envoyer. Pour éviter les erreurs, assurez-vous toujours que votre contenu s’affiche correctement avant d’effectuer une diffusion en cliquant sur l’ **[!UICONTROL Preview]** onglet.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Si la valeur d&#39;un code-barres s&#39;avère incorrecte, le bitmap qui le représente s&#39;affiche barré d&#39;une croix rouge.

![](assets/barcode_insert_11.png)
