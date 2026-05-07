---
product: campaign
title: Régénération des schémas
description: Découvrez comment régénérer les schémas Campaign
feature: Custom Resources
role: Developer
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 81%

---

# Régénération des schémas{#regenerating-schemas}

Lorsque vous modifiez un schéma et enregistrez les modifications, le schéma étendu est automatiquement généré. Néanmoins, vous devrez peut-être régénérer les schémas manuellement pour appliquer les modifications. Pour cela :

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
