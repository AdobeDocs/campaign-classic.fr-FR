---
solution: Campaign Classic
product: campaign
title: Perte de mot de passe
description: Perte de mot de passe
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: b7f44f4c18bef4cc412af878846b2c4305a17787
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 72%

---


# Perte de mot de passe{#lost-password}

Il est possible de changer ou de récupérer un mot de passe perdu.
Deux cas sont possibles :

* **Perte du mot de passe d&#39;un opérateur Adobe Campaign**

Dans ce cas, vous pouvez modifier le mot de passe de l’opérateur concerné.
Pour ce faire, procédez comme suit :

1. Connectez-vous via un opérateur disposant des droits d’administrateur.
1. Cliquez avec le bouton droit sur un opérateur.
1. Sélectionnez **[!UICONTROL Actions]** > **[!UICONTROL Réinitialiser le mot de passe]**.

   ![](assets/operator-passwd.png)

1. Définissez le nouveau mot de passe de l’opérateur. Nous recommandons aux opérateurs de modifier leur mot de passe lorsqu’ils se reconnectent pour la première fois.

* Perte du mot de passe **internal (clients on-premise uniquement)**

En cas de perte du mot de passe internal, vous devez le réinitialiser. Pour cela, la procédure est la suivante :

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
