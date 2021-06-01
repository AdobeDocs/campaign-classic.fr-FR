---
product: campaign
title: Régénération des schémas
description: Régénération des schémas
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 100%

---

# Régénération des schémas{#regenerating-schemas}

Lors de la modification d&#39;un schéma et de l&#39;enregistrement des modifications, le schéma étendu est automatiquement généré. Vous devrez peut-être toutefois régénérer les schémas manuellement pour appliquer les modifications. Pour ce faire :

1. Sélectionnez le ou les schémas que vous devez régénérer.
1. Cliquez avec le bouton droit et sélectionnez **[!UICONTROL Actions > Régénérer les schémas sélectionnés...]** .
1. Cliquez sur **[!UICONTROL OK]** pour valider et lancer le processus.

Vous pouvez ensuite vérifier la structure du schéma généré dans les onglets Aperçu et Documentation. Voir à ce sujet la section [Principes](../../configuration/using/data-schemas.md#principles).

>[!NOTE]
>
>Si vous devez forcer la régénération de tous les schémas, pour résoudre, par exemple, certains problèmes de dépendances dans les liens inverses, vous pouvez lancer la commande suivante à partir du serveur applicatif Adobe Campaign :
>
>**nlserver config -postupgrade -instance:`&lt;nom_instance>&#39; -force**
>
>Vous devez ensuite redémarrer le serveur applicatif Adobe Campaign et vous déconnecter/reconnecter à la console cliente.
