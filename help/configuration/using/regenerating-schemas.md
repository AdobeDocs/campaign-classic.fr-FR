---
product: campaign
title: Régénération des schémas
description: Découvrez comment régénérer les schémas Campaign
feature: Custom Resources
role: Developer
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
TQID: https://experienceleague.adobe.com/gkWtbp4Vw-wY5yHsd4xJbDx04u3aPhdg-8kB5OXZu94
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2: id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: ht
source-wordcount: 136
ht-degree: 100%

---

# Régénération des schémas{#regenerating-schemas}

Lorsque vous modifiez un schéma et enregistrez les modifications, le schéma étendu est automatiquement généré.Néanmoins, vous devrez peut-être générer à nouveau les schémas manuellement pour appliquer les modifications.Pour cela :

1. Sélectionnez le ou les schémas que vous devez régénérer.
1. Cliquez avec le bouton droit et sélectionnez **[!UICONTROL Actions > Régénérer les schémas sélectionnés...]** .
1. Cliquez sur **[!UICONTROL OK]** pour valider et lancer le processus.

Vous pouvez ensuite vérifier la structure du schéma généré dans les onglets Aperçu et Documentation. Voir à ce sujet la section [Principes](../../configuration/using/data-schemas.md#principles).

>[!NOTE]
>
>Si vous devez forcer la régénération de tous les schémas, pour résoudre, par exemple, certains problèmes de dépendances dans les liens inverses, vous pouvez lancer la commande suivante à partir du serveur applicatif Adobe Campaign :
>
> `nlserver config -postupgrade -instance:`&lt;nom_instance>` -force`
>
>Vous devez ensuite redémarrer le serveur applicatif Adobe Campaign et vous déconnecter/reconnecter à la console cliente.
