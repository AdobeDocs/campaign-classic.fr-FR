---
product: campaign
title: Perte de mot de passe
description: Perte de mot de passe
feature: Monitoring, Access Management
badge-v7-prem: label="On-Premise/hybride uniquement" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=fr" tooltip="S’applique uniquement aux déploiements on-premise et hybrides"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
TQID: https://experienceleague.adobe.com/MaAtheK2WnozPDuEO-qPq2l9u-AOGj5aGu2TgKslgLc
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 250
ht-degree: 92%

---

# Perte de mot de passe{#lost-password}

>[!NOTE]
>
>Cette page ne s’applique qu’aux opérateurs et aux opératrices qui se connectent à Campaign avec une authentification native.

Vous pouvez modifier ou récupérer un mot de passe perdu.
Deux scénarios sont possibles :

* [Perte du mot de passe d&#39;un opérateur Adobe Campaign](#password-lost-by-campaign-operator)
* [Perte du mot de passe interne](#internal-password-lost) (clients on-premise uniquement)

## Mot de passe perdu par un opérateur Campaign {#password-lost-by-campaign-operator}

Si un opérateur ou une opératrice Adobe Campaign perd son mot de passe, vous pouvez le modifier.

>[!NOTE]
>
>Cette procédure ne s’applique qu’aux opérateurs et aux opératrices qui se connectent à Campaign avec une authentification native. Pour l’authentification Adobe IMS, consultez [cette documentation](https://helpx.adobe.com/ie/manage-account/using/change-or-reset-password.html){target="_blank"}.

Pour réinitialiser un mot de passe Campaign, suivez les étapes ci-dessous :

1. Connectez-vous via un opérateur ou une opératrice disposant des droits d’administrateur.
1. Cliquez avec le bouton droit sur un opérateur.
1. Sélectionnez **[!UICONTROL Actions]** > **[!UICONTROL Réinitialiser le mot de passe]**.

   ![](assets/operator-passwd.png)

1. Définissez le nouveau mot de passe de l’opérateur. Nous recommandons aux opérateurs de modifier leur mot de passe lorsqu’ils se reconnectent pour la première fois.

## Mot de passe interne perdu {#internal-password-lost}

>[!NOTE]
>
>Cette section ne s’applique qu’aux clientes et clients on-premise.

Si le mot de passe interne est perdu, vous devez le réinitialiser.

Pour cela, respectez la procédure suivante :

1. Modifiez le fichier **/usr/local/neolane/nl6/conf/serverConf.xml**.

1. Positionnez-vous sur la ligne **internalPassword**.

   ```xml
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. Supprimez la chaîne entre guillemets. Dans ce cas : `myPassword`. Vous obtenez la ligne suivante :

   ```xml
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/>
   ```

1. Enregistrez les modifications et fermez le fichier.

1. Arrêtez le processus `nlserver`.

1. Configurez le nouveau mot de passe. Pour cela, saisissez les commandes suivantes :

   ```javascript
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. Démarrez le processus `nlserver`.

1. Vous pouvez maintenant vous connecter en mode **Interne** avec votre nouveau mot de passe.
