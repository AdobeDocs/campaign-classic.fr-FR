---
solution: Campaign Classic
product: campaign
title: Migration du connecteur SMS non prise en charge
description: Migration du connecteur SMS non pris en charge vers le connecteur SMPP générique étendu
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 6a856c95f21b52c66a9b7359133227394fae05a5
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 11%

---


# Migration du connecteur SMS non pris en charge vers le connecteur SMPP générique étendu{#unsupported-connector-migration}

A compter de la version 20.2, les connecteurs hérités sont obsolètes. Ce document vous aidera à migrer les connecteurs qui s&#39;exécutent toujours sur l&#39;ancien système vers le connecteur SMPP recommandé.

>[!CAUTION]
>
>Cette migration n&#39;est pas obligatoire, mais recommandée par l&#39;Adobe. Elle vous permettra de vous assurer que vous utilisez la dernière version du logiciel prise en charge.

## À propos des connecteurs SMS {#about-sms-connectors}

Les connecteurs suivants sont obsolètes à compter de la version 20.2 :

* **[!UICONTROL SMPP]**  générique (SMPP version 3.4 prenant en charge le mode binaire)
* **[!UICONTROL Sybase365]**  (SAP SMS 365)
* **[!UICONTROL CLX Communications]**
* **[!UICONTROL Tele2]**
* **[!UICONTROL O2]**
* **[!UICONTROL iOS]**

Les capacités obsolètes sont toujours disponibles et prises en charge, mais elles ne seront pas encore améliorées. Nous vous recommandons d’utiliser le connecteur **[!UICONTROL SMPP générique étendu.]**

Pour plus d’informations sur les fonctionnalités obsolètes et supprimées, consultez cette [page](../../rn/using/deprecated-features.md).

Les anciens connecteurs SMS utilisent le connecteur SMS Java qui surcharge le processus Web. La migration vers le nouveau connecteur **[!UICONTROL SMPP générique étendu]** déplacera cette charge vers le MTA qui peut la prendre en charge.

## Migration vers le connecteur SMPP générique étendu {#migrating-extended-generic-smpp}

>[!CAUTION]
>
>Même si vous pouvez transposer les paramètres, la configuration du connecteur **[!UICONTROL SMPP générique étendu]** nécessite que vous discutiez avec votre fournisseur qui vous fournira les informations nécessaires pour remplir le reste des paramètres. Pour plus d’informations à ce sujet, consultez cette [page](../../delivery/using/sms-protocol.md).

Tout d&#39;abord, vous devrez créer un nouveau compte externe **[!UICONTROL SMPP générique étendu]**, puis vous pourrez peut-être transposer certains des paramètres. Vous trouverez les étapes détaillées dans cette [page](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account).

Vous devez maintenant remplir les paramètres de l&#39;onglet **[!UICONTROL Mobile]** de votre nouveau compte externe **[!UICONTROL SMPP générique étendu]** en fonction de votre connecteur précédent.

### À partir du connecteur générique {#from-generic-connector}

Lorsque vous sélectionnez le connecteur **[!UICONTROL générique]**, vous devez disposer d’un connecteur JavaScript personnalisé qui s’adaptera à chaque situation.

Si vous savez que ce connecteur utilise déjà le protocole SMPP, vous pouvez migrer vers le connecteur **[!UICONTROL SMPP générique étendu]**. Dans le cas contraire, vérifiez auprès de votre fournisseur s’il prend en charge le protocole SMPP et configurez un nouveau connecteur avec l’aide d’un consultant.

À partir de votre connecteur **[!UICONTROL générique]**, vous pouvez effectuer une transposition vers votre compte **[!UICONTROL SMPP étendu]** nouvellement créé :

![](assets/smpp_generic.png)

Dans l&#39;onglet **[!UICONTROL Paramètres de connexion]** :

* **[!UICONTROL Compte]**
* **[!UICONTROL Mot de passe]**
* **[!UICONTROL Serveur]**
* **[!UICONTROL Port]**

### À partir du connecteur SMPP générique {#from-generic-smpp-connector}

À partir de votre connecteur **[!UICONTROL SMPP générique]**, vous pouvez effectuer une transposition vers votre compte **[!UICONTROL SMPP étendu]** nouvellement créé :

![](assets/smpp_generic_2.png)

Dans l&#39;onglet **[!UICONTROL Paramètres de connexion]** :

* **[!UICONTROL Compte]**
* **[!UICONTROL Mot de passe]**
* **[!UICONTROL Serveur]**
* **[!UICONTROL Port]**
* **[!UICONTROL Type de système]**

Dans l&#39;onglet **[!UICONTROL Paramètres du Canal SMPP]** :

* **[!UICONTROL Numéro source]**
* **[!UICONTROL NPI source]**
* **[!UICONTROL NPI destination]**
* **[!UICONTROL TON source]**
* **[!UICONTROL TON destination]**

Dans l&#39;onglet **[!UICONTROL Mappage de l&#39;encodage]** :

* **[!UICONTROL Codage SMS sortant]**

Dans l&#39;onglet **[!UICONTROL Spécifications SMSC]** :

* **[!UICONTROL Le codage lors de l’]** envoi correspond au format  **[!UICONTROL d’ID dans l’accusé de réception MT.]**
* **[!UICONTROL Le codage lors de la]** réception correspond au format  **[!UICONTROL d&#39;ID dans la SR]**

### À partir du connecteur Sybase365 {#from-sybase}

À partir de votre connecteur **[!UICONTROL Sybase365]**, vous pouvez effectuer une transposition vers votre compte **[!UICONTROL SMPP étendu]** nouvellement créé :

![](assets/smpp_3.png)

Dans l&#39;onglet **[!UICONTROL Paramètres de connexion]** :

* **[!UICONTROL Compte]**
* **[!UICONTROL Mot de passe]**
* **[!UICONTROL Serveur]**
* **[!UICONTROL Port]**
* **[!UICONTROL Type de système]**

### À partir du connecteur CLX {#from-clx}

À partir de votre connecteur **[!UICONTROL CLX]**, vous pouvez effectuer une transposition vers votre compte **[!UICONTROL SMPP étendu]** nouvellement créé :

![](assets/smpp_4.png)

Dans l&#39;onglet **[!UICONTROL Paramètres de connexion]** :

* **[!UICONTROL Compte]**
* **[!UICONTROL Mot de passe]**
* **[!UICONTROL Serveur]**
* **[!UICONTROL Port]**
* **[!UICONTROL Type de système]**

Dans l&#39;onglet **[!UICONTROL Paramètres du Canal SMPP]** :

* **[!UICONTROL Numéro source]**

Dans l&#39;onglet **[!UICONTROL Spécifications SMSC]** :

* **[!UICONTROL Le codage lors de l’]** envoi correspond au format  **[!UICONTROL d’ID dans l’accusé de réception MT.]**
* **[!UICONTROL Le codage lors de la]** réception correspond au format  **[!UICONTROL d&#39;ID dans la SR]**

### À partir du connecteur Tele2 {#from-tele2}

À partir de votre connecteur **[!UICONTROL Télé2]**, vous pouvez effectuer une transposition vers votre compte **[!UICONTROL SMPP étendu]** nouvellement créé :

![](assets/smpp_6.png)

Dans l&#39;onglet **[!UICONTROL Paramètres de connexion]** :

* **[!UICONTROL Compte]**
* **[!UICONTROL Mot de passe]**
* **[!UICONTROL Serveur]**
* **[!UICONTROL Port]**
* **[!UICONTROL Type de système]**

Dans l&#39;onglet **[!UICONTROL Paramètres du Canal SMPP]** :

* **[!UICONTROL Numéro source]**
* **[!UICONTROL NPI source]**
* **[!UICONTROL NPI destination]**
* **[!UICONTROL TON source]**

Dans l&#39;onglet **[!UICONTROL Mappage de l&#39;encodage]** :

* **[!UICONTROL Codage SMS sortant]**

### À partir du connecteur O2 {#from-O2}

À partir de votre connecteur **[!UICONTROL O2]**, vous pouvez effectuer une transposition vers votre compte **[!UICONTROL SMPP étendu]** nouvellement créé :

![](assets/smpp_5.png)

Dans l&#39;onglet **[!UICONTROL Paramètres de connexion]** :

* **[!UICONTROL Compte]**
* **[!UICONTROL Mot de passe]**
* **[!UICONTROL Serveur]**
* **[!UICONTROL Port]**
* **[!UICONTROL Type de système]**

Dans l&#39;onglet **[!UICONTROL Paramètres du Canal SMPP]** :

* **[!UICONTROL Numéro source]**
* **[!UICONTROL NPI source]**
* **[!UICONTROL NPI destination]**
* **[!UICONTROL TON source]**
* **[!UICONTROL TON destination]**