---
product: campaign
title: Insertion d’un code-barres dans un e-mail
description: Insertion d’un code-barres dans un e-mail
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Email Design
role: User
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 59%

---

# Insertion d’un code-barres dans un e-mail{#insert-a-barcode-in-an-email}

Le module de génération de codes-barres permet de créer plusieurs types de codes-barres répondant aux normes les plus courantes, dans les formats 1D (unidimensionnel) et 2D (bidimensionnel).

Il est possible de générer dynamiquement un code à barres sous forme d’image bitmap à l’aide d’une valeur définie selon les critères du client. Des codes à barres personnalisés peuvent être inclus dans les campagnes par e-mail. Le destinataire peut imprimer le message et le montrer à la société émettrice pour qu&#39;elle le scanne (lors d&#39;une extraction, par exemple).

Pour insérer un code-barres dans un email, positionnez le curseur dans le contenu, là où vous souhaitez l&#39;afficher, et cliquez sur le bouton de personnalisation. Choisissez **[!UICONTROL Inclure > Code-barres...]**.

![](assets/barcode_insert_14.png)

Puis paramétrez les éléments suivants en fonction de vos besoins :

1. Choisissez le type de code-barres.

   * Pour le format 1D, Adobe Campaign propose les types suivants: Codabar, Code 128, GS1-128 (anciennement EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 of 5, POSTNET et Royal Mail (RM4SCC).

     Exemple de code-barres 1D :

     ![](assets/barcode_insert_08.png)

   * Les types DataMatrix et PDF417 concernent le format 2D.

     Exemple de code-barres 2D :

     ![](assets/barcode_insert_09.png)

   * Pour insérer un code QR, sélectionnez ce type et saisissez le taux de correction d&#39;erreur à appliquer. Ce taux définit la quantité d&#39;informations répétées et la tolérance à la détérioration.

     ![](assets/barcode_insert_06.png)

     Exemple de QR Code :

     ![](assets/barcode_insert_12.png)

1. Indiquez la taille du code-barres à insérer dans l&#39;email : le paramétrage de l&#39;échelle permet d&#39;augmenter ou de réduire la taille du code-barres, de x 1 à x 10.
1. Le champ **[!UICONTROL Valeur]** permet de définir la valeur du code à barres. Une valeur peut correspondre à une offre spéciale et peut être la fonction d&#39;un critère, elle peut être la valeur d&#39;un champ de base de données lié aux clients.

   L&#39;exemple ci-dessous montre un code-barres de type EAN-8 auquel a été ajouté le numéro de compte d&#39;un destinataire. Pour ajouter ce numéro de compte, cliquez sur le bouton de personnalisation situé à droite du champ **[!UICONTROL Valeur]** et sélectionnez **[!UICONTROL Destinataire > N° de compte]**.

   ![](assets/barcode_insert_15.png)

1. Le champ **[!UICONTROL Hauteur]** permet de paramétrer la hauteur du code-barres sans en modifier la largeur, soit l&#39;espacement entre chaque barre.

   Il n&#39;existe pas de contrôle restrictif de saisie en fonction du type de code-barres sélectionné. Si une valeur de code-barres est erronée, vous ne le saurez que lorsque vous passerez en vue **Aperçu** avec le code-barres marqué d&#39;une croix rouge.

   >[!NOTE]
   >
   >La valeur attribuée à un code-barres dépend de son type. Par exemple, un type EAN-8 doit avoir exactement 8 numéros.
   >
   >Le bouton de personnalisation situé à droite du champ **[!UICONTROL Valeur]** vous permet d’ajouter des données en plus de la valeur elle-même. Cela enrichit le code à barres, à condition que le standard de code à barres l’accepte.
   >
   >Par exemple, si vous utilisez un code-barres de type GS1-128 et que vous souhaitez saisir le numéro de compte d’un destinataire en plus de la valeur, cliquez sur le bouton de personnalisation et sélectionnez **[!UICONTROL Destinataire > Numéro de compte]**. Si le numéro de compte du destinataire sélectionné est correctement saisi, le code-barres en tient compte.

Une fois ces éléments paramétrés, vous pouvez finaliser votre email et l&#39;envoyer. Pour éviter toute erreur, vérifiez toujours avant une diffusion que votre contenu s&#39;affiche correctement en cliquant sur l&#39;onglet **[!UICONTROL Aperçu]**.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Si la valeur d&#39;un code-barres s&#39;avère incorrecte, le bitmap qui le représente s&#39;affiche barré d&#39;une croix rouge.

![](assets/barcode_insert_11.png)
