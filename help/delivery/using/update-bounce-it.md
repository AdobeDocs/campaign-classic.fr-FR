---
product: campaign
title: Mise à jour de la qualification des bounces après une interruption de service en ligne Italia
description: Découvrez comment mettre à jour la qualification des bounces après une panne Italia Online
feature: Deliverability
hide: true
hidefromtoc: true
source-git-commit: 3fa54f83ee6a119a4566866933aaee20ec378e91
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 19%

---

# Mise à jour de hard bounces incorrects après une panne d&#39;Italia Online {#update-bounce-italia}

![](../../assets/common.svg)

## Contexte{#outage-context}

Depuis le 22 janvier (heure locale), Italia Online a subi une panne qui a entraîné plusieurs retards et refusé les emails. Le service a commencé à reprendre avec une capacité limitée le 26 janvier.

Les domaines concernés sont les suivants : **libero.it**, **virgilio.it**, **inwind.it**, **iol.it**, et **blu.it**.

Ce problème est survenu du 1/22/2023 au 1/26/2023, mais la plupart des quarantaines incorrectes ont eu lieu le 26 janvier.

En savoir plus dans la communication officielle [here](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}.


## Impact{#outage-impact}

Comme dans la plupart des cas, lorsqu’un FAI est en panne, certains emails envoyés via Campaign sont marqués à tort comme des bounces. Cela n&#39;a pas seulement eu un impact sur l&#39;Adobe, mais tout le monde essayant de se faire livrer des emails à Italia Online pendant la durée de la panne.

Les symptômes étaient les suivants :

* **Rebonds au report** avec le message `452 requested action aborted: try again later` - ont été automatiquement relancés et aucune action n’est nécessaire.

* **Hard bounces** avec le message `550 <email address> recipient rejected` ont été renvoyés par le FAI le 26 janvier, de 8h00 à 14h00, heure locale, pour empêcher les expéditeurs de continuer à surcharger leurs serveurs. Comme le confirme le Postmaster en ligne Italia, il ne s&#39;agit pas de vrais hard bounces, nous vous recommandons donc de mettre en quarantaine toutes les adresses email qui ont été exclues le 26 janvier 2023 en raison de ce message.

## Processus de mise à jour{#outage-update}

Selon la logique standard de gestion des bounces, Adobe Campaign a automatiquement ajouté ces destinataires à la liste de quarantaine avec un **[!UICONTROL Statut]** de **[!UICONTROL Quarantaine]**. Pour corriger ce problème, vous devez mettre à jour votre table de quarantaines dans Campaign en recherchant et en supprimant ces destinataires ou en basculant leur **[!UICONTROL Statut]** sur **[!UICONTROL Valide]** afin que le processus de nettoyage de nuit les supprime.

Pour trouver les destinataires qui ont été affectés par ce problème, ou au cas où cela se reproduirait avec un autre FAI, veuillez consulter les instructions . [dans cette page](../../delivery/using/understanding-quarantine-management.md#unquarantine-bulk).
