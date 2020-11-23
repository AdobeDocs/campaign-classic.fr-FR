---
solution: Campaign Classic
product: campaign
title: Perte de mot de passe
description: Perte de mot de passe
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 100%

---


# Perte de mot de passe{#lost-password}

Il est possible de changer ou de récupérer un mot de passe perdu.

Deux cas sont possibles :

* Perte du mot de passe d&#39;un opérateur Adobe Campaign.

   Dans ce cas, vous pouvez modifier le mot de passe de l&#39;opérateur concerné. Pour cela, connectez-vous avec un opérateur ayant les droits administrateurs, cliquez avec le bouton droit sur un opérateur, sélectionnez **[!UICONTROL Actions]** > **[!UICONTROL Réinitialiser le mot de passe]**, puis définissez le nouveau mot de passe de l&#39;opérateur. Nous recommandons aux opérateurs de changer leur mot de passe lors de leur première reconnexion.

   ![](assets/operator-passwd.png)

* Perte du mot de passe **internal** (clients on-premise uniquement).

   En cas de perte du mot de passe **internal**, vous devez le réinitialiser. Pour cela, la procédure est la suivante :

   1. Modifiez le fichier **/usr/local/neolane/nl6/conf/serverConf.xml**.
   1. Positionnez-vous sur la ligne **internalPassword**.

      ```
      <!-- XTK authentication mode internalPassword : Password of internal account -->
       <xtk internalPassword="myPassword"/>
      ```

   1. Supprimez la chaîne entre guillemets, ici par exemple : **myPassword**

      Vous obtenez ainsi la ligne suivante :

      ```
      !-- XTK authentication mode internalPassword : Password of internal account -->
      <xtk internalPassword=""/
      ```

   1. Enregistrez les modifications et fermez le fichier.
   1. Paramétrez ensuite le nouveau mot de passe. Pour cela, saisissez les commandes suivantes :

      ```
      nlserver config -internalpassword
      HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
      Enter current password.
      Password: (empty)
      Enter the new password.
      Password: 
      Confirmation 
      ```

   1. Vous pouvez maintenant vous connecter en **Internal** avec votre nouveau mot de passe.

