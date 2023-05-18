---
product: campaign
title: Perte de mot de passe
description: Perte de mot de passe
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Perte de mot de passe{#lost-password}



Il est possible de changer ou de récupérer un mot de passe perdu.
Deux cas sont possibles :

* [Perte du mot de passe d&#39;un opérateur Adobe Campaign](#password-lost-by-campaign-operator)
* [Perte du mot de passe interne](#internal-password-lost) (clients on-premise uniquement)

## Mot de passe perdu par un opérateur Campaign {#password-lost-by-campaign-operator}

Si un opérateur Adobe Campaign perd son mot de passe, vous pouvez le changer.
Pour ce faire, procédez comme suit :

1. Connectez-vous via un opérateur disposant des droits d’administrateur.
1. Cliquez avec le bouton droit sur un opérateur.
1. Sélectionnez **[!UICONTROL Actions]** > **[!UICONTROL Réinitialiser le mot de passe]**.

   ![](assets/operator-passwd.png)

1. Définissez le nouveau mot de passe de l’opérateur. Nous recommandons aux opérateurs de modifier leur mot de passe lorsqu’ils se reconnectent pour la première fois.

## Mot de passe interne perdu {#internal-password-lost}

>[!NOTE]
>
>Cette section ne s&#39;applique qu&#39;aux clients on-premise.

En cas de perte du mot de passe interne, vous devez le réinitialiser. Pour cela, la procédure est la suivante :

1. Modifiez le fichier **/usr/local/neolane/nl6/conf/serverConf.xml**.

1. Positionnez-vous sur la ligne **internalPassword**.

   ```
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. Supprimez la chaîne entre guillemets, ici par exemple : **myPassword**

   Vous obtenez ainsi la ligne suivante :

   ```
   !-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/
   ```

1. Enregistrez les modifications et fermez le fichier.

1. Paramétrez ensuite le nouveau mot de passe. Pour cela, saisissez les commandes suivantes :

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
