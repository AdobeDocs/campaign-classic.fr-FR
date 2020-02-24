---
title: Perte de mot de passe
seo-title: Perte de mot de passe
description: Perte de mot de passe
seo-description: null
page-status-flag: never-activated
uuid: caac68bf-abdc-45da-9697-b689ebd37002
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: d52eeadc-19c6-4d48-995a-1c1f2ca3b5ec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5f3ceab5ee82587d9f1829792bdabf2209f793cd

---


# Perte de mot de passe{#lost-password}

Il est possible de changer ou de récupérer un mot de passe perdu.

Deux cas sont possibles :

* Perte du mot de passe d&#39;un opérateur Adobe Campaign.

   Dans ce cas, vous pouvez modifier le mot de passe de l&#39;opérateur concerné. Pour cela, connectez-vous avec un opérateur ayant les droits administrateurs, cliquez avec le bouton droit sur un opérateur, sélectionnez **[!UICONTROL Actions]** > **[!UICONTROL Réinitialiser le mot de passe]**, puis définissez le nouveau mot de passe de l&#39;opérateur. Nous recommandons aux opérateurs de changer leur mot de passe lors de leur première reconnexion.

   ![](assets/operator-passwd.png)

* Perte du mot de passe **internal** (clients on-premise uniquement).

   En cas de perte du mot de passe **internal**, vous devez le réinitialiser. Pour cela, la procédure est la suivante :

   1. Edit the **/usr/local/neolane/nl6/conf/serverConf.xml** file.
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

