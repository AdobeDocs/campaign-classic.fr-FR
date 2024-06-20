---
title: Mise à jour de l’interface de Campaign après la migration IMS
description: Découvrez comment activer les impacts de l’interface de migration d’Adobe Identity Management System
source-git-commit: ab1bb91bdbc9961b4f3f0feba7cfd354b02b6511
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 4%

---

# Mise à jour de l’interface de Campaign après la migration IMS {#impact-ims-migration}

Une fois que vous avez [migration des opérateurs techniques Campaign vers Developer Console](ims-migration.md) et [transition vers IMS pour l’authentification des utilisateurs finaux](migrate-users-to-ims.md), la dernière étape consiste à activer l’interface utilisateur et les restrictions de l’API pour supprimer les options et fonctionnalités spécifiques à l’authentification native. Cette mise à jour est disponible à partir de Campaign v7.4.1.

## Activation des restrictions IMS {#ims-restrictions}

Pour finaliser votre migration vers Adobe Identity Management System (IMS), vous devez bloquer la création d’utilisateurs natifs, la connexion d’utilisateurs natifs et l’accès aux API pour les opérateurs natifs. Votre environnement est ensuite sécurisé et normalisé.

En tant qu’utilisateur Cloud Service/hébergé, contactez l’Adobe pour activer cette restriction et les mises à jour associées dans l’interface utilisateur du produit.

En tant qu’utilisateur on-premise/hybride, procédez comme suit :

1. Accédez au `<imsConfig>` de votre fichier de configuration d’instance.
1. Pour activer les restrictions de l’interface utilisateur, mettez à jour la variable `nonIMSOperatorMgmtInClientConsoleRestricted` , à l’intérieur de la propriété `nonIMSOperatorMgmtInClientConsole` élément, à `true`, comme ci-dessous :


   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSOperatorMgmtInClientConsole nonIMSOperatorMgmtInClientConsoleRestricted="true"/>
       </imsConfig>
   </shared>
   </serverConf>
   ```

1. Pour activer les restrictions de l’API, mettez à jour la variable `disableAPI` , à l’intérieur de la propriété `nonIMSAuthnAPI` élément, à `true`, comme ci-dessous :

   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSAuthnAPI disableAPI="true">
               ...
           </nonIMSAuthnAPI>
       </imsConfig>
   </shared>
   </serverConf>
   ```

Notez que certains opérateurs sont autorisés à se connecter à Adobe Campaign avec une authentification native. Ces opérateurs techniques sont activés par défaut et ne doivent pas être modifiés. Pour autoriser cette exception, ces opérateurs techniques sont ajoutés par défaut à la liste autorisée. Cette liste figure dans la `<imsConfig>` de votre fichier de configuration d’instance, dans la section `allowOperator` à l’intérieur de la fonction `nonIMSAuthnAPI` élément .

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

Si vous devez ajouter un opérateur à la liste autorisée, ajoutez une nouvelle `allowOperator` avec le nom de l&#39;opérateur. Par exemple, si vous souhaitez ajouter un nouvel opérateur nommé `test`, mettez à jour cette section comme suit :

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
            <allowOperator name="test"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

## Impacts dans l’interface utilisateur {#ims-impacts}

Une fois la migration terminée et les restrictions appliquées comme décrit ci-dessous, les modifications suivantes sont appliquées au produit et à son interface utilisateur.

### Gestion des opérateurs {#manage-admin}

Vous ne pouvez plus créer, modifier, mettre à jour ou supprimer des opérateurs avec une authentification native à partir de la console cliente.

Par conséquent, ces actions ont été désactivées dans la console cliente.

L’administration des opérateurs est centralisée dans Adobe Admin Console et les tâches suivantes sont désormais gérées exclusivement via cette console. Découvrez comment créer des utilisateurs et attribuer des autorisations dans [Documentation de Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/manage-permissions){target="_blank"}.

### Options non disponibles {#unavailable-migration}

Après la migration, les tâches suivantes ne sont plus disponibles dans la console cliente :

* Utilisez la variable [Option Fusionner les lignes sélectionnées](../../platform/using/updating-data.md#merge-data) pour fusionner des opérateurs.

* Mettez à jour les champs suivants pour vos opérateurs :
   * Nom
   * Mot de passe
   * Libellé
   * E-mail

* [Réinitialisation du mot de passe Campaign](../../production/using/lost-password.md)

* Editer la source XML des opérateurs

* Dupliquez les opérateurs.


>[!MORELIKETHIS]
>
>* [Migration des utilisateurs finaux vers IMS](migrate-users-to-ims.md)
>* [Migration des opérateurs techniques vers la console Adobe Developer](ims-migration.md)
>* [Notes de mise à jour les plus récentes de Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [Présentation d’Adobe Identity Management System (IMS)](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"}

