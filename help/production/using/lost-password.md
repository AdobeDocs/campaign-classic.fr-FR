---
product: campaign
title: Perte de mot de passe
description: Perte de mot de passe
feature: Monitoring, Access Management
badge-v7-only: label="v7" type="Informative" tooltip="S’applique uniquement à Campaign Classic v7"
badge-v7-prem: label="On-premise et hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '199'
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
