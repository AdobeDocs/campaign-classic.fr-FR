---
title: Mettre à jour l’interface de Campaign après la migration IMS
description: En savoir plus sur les impacts de l’interface de migration d’Adobe Identity Management System
exl-id: 8b13fe4d-d8d3-43b3-bbe4-c8c5574f585a
TQID: https://experienceleague.adobe.com/RkgX2M0BnO5pjgI7oAp7NlycXY551manwFHhcA1LMjw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2:
  - id: a39dbcf0-89cb-4765-9bcb-cf9dfbe2875f
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 463
ht-degree: 100%

---

# Mettre à jour l’interface de Campaign après la migration IMS {#impact-ims-migration}

Une fois que vous avez [migré vos opérateurs et opératrices techniques Campaign vers Developer Console](ims-migration.md) et [effectué la transition vers IMS pour l’authentification des utilisateurs et utilisatrices finaux](migrate-users-to-ims.md), la dernière étape consiste à activer les restrictions de l’interface d’utilisation et de l’API pour supprimer les options et fonctionnalités spécifiques à l’authentification native. Cette mise à jour est disponible à partir de Campaign v7.4.1.

## Activer des restrictions IMS {#ims-restrictions}

Pour finaliser votre migration vers Adobe Identity Management System (IMS), vous devez bloquer la création d’utilisateurs et utilisatrices natifs, la connexion d’utilisateurs et utilisatrices natifs et l’accès à l’API pour les opérateurs et opératrices natifs. Votre environnement est ensuite sécurisé et normalisé.

En tant qu’utilisateur ou utilisatrice Cloud Service/hébergé, contactez Adobe pour activer cette restriction et les mises à jour associées dans l’interface d’utilisation du produit.

En tant qu’utilisateur ou utilisatrice on-premise/hybride, procédez comme suit :

1. Accédez à la section `<imsConfig>` de votre fichier de configuration d’instance.
1. Pour activer les restrictions de l’interface d’utilisation, mettez à jour l’option `nonIMSOperatorMgmtInClientConsoleRestricted`, dans l’élément `nonIMSOperatorMgmtInClientConsole`, sur `true`, comme ci-dessous :


   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSOperatorMgmtInClientConsole nonIMSOperatorMgmtInClientConsoleRestricted="true"/>
       </imsConfig>
   </shared>
   </serverConf>
   ```

1. Pour activer les restrictions de l’API, mettez à jour l’option `disableAPI`, dans l’élément `nonIMSAuthnAPI`, sur `true`, comme ci-dessous :

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

Notez que certains opérateurs et opératrices sont autorisés à se connecter à Adobe Campaign avec une authentification native. Ces opérateurs et opératrices techniques sont activés par défaut et ne doivent pas être modifiés. Pour autoriser cette exception, ces opérateurs et opératrices techniques sont ajoutés par défaut à la liste autorisée. Cette liste figure dans la section `<imsConfig>` de votre fichier de configuration d’instance, dans l’option `allowOperator` de l’élément `nonIMSAuthnAPI`.

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

Si vous devez ajouter un opérateur ou une opératrice à la liste autorisée, ajoutez un nouvel élément `allowOperator` avec le nom de l’opérateur ou opératrice. Par exemple, si vous souhaitez ajouter un nouvel opérateur ou une nouvelle opératrice nommé `test`, mettez à jour cette section comme suit :

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

## Impacts dans l’interface d’utilisation {#ims-impacts}

Une fois la migration terminée et les restrictions appliquées comme décrit ci-dessous, les modifications suivantes sont appliquées au produit et à son interface d’utilisation.

### Gestion des opérateurs et opératrices {#manage-admin}

Vous ne pouvez plus créer, modifier, mettre à jour ou supprimer des opérateurs et opératrices avec une authentification native à partir de la console cliente.

Par conséquent, ces actions ont été désactivées dans la console cliente.

L’administration des opérateurs et opératrices est centralisée dans Adobe Admin Console et les tâches suivantes sont désormais gérées exclusivement via cette console. Découvrez comment créer des utilisateurs et utilisatrices et attribuer des autorisations dans la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/admin/permissions/manage-permissions){target="_blank"}.

### Options non disponibles {#unavailable-migration}

Après la migration, les tâches suivantes ne sont plus disponibles dans la console cliente :

* Utilisez l’[option Fusionner les lignes sélectionnées](../../platform/using/updating-data.md#merge-data) pour fusionner les opérateurs et les opératrices.

* Mettez à jour les champs suivants pour vos opérateurs et opératrices :
   * Nom
   * Mot de passe
   * Libellé
   * E-mail

* [Réinitialiser votre mot de passe Campaign](../../production/using/lost-password.md)

* Modifier la source XML des opérateurs et opératrices

* Dupliquez les opérateurs et opératrices.


>[!MORELIKETHIS]
>
>* [Migration des utilisateurs et utilisatrices finaux vers IMS](migrate-users-to-ims.md)
>* [Migration des opérateurs et opératrices techniques vers Adobe Developer Console](ims-migration.md)
>* [Dernières notes de mise à jour d’Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [Présentation du système de gestion des identités (IMS) d’Adobe](https://helpx.adobe.com/fr/enterprise/using/identity.html){target="_blank"}
