---
product: campaign
title: Effectuer une mise à jour vers le nouveau serveur de délivrabilité
description: Découvrez comment mettre à jour le nouveau serveur de délivrabilité de Campaign
feature: Technote, Deliverability
hide: true
hidefromtoc: true
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: 8d15a5666b5768bc0f17a4391061c4fcb9f76811
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Effectuer une mise à jour vers le nouveau serveur de délivrabilité {#acc-deliverability}

Depuis la [version 7.2.2](../../rn/using/latest-release.md#release-7-2-2), Adobe Campaign s’appuie sur un nouveau serveur de délivrabilité qui assure une haute disponibilité et résout les problèmes de conformité en matière de sécurité. Campaign Classic synchronise désormais les règles de délivrabilité, les broadlogs, ainsi que l’adresse de suppression depuis et vers le nouveau serveur de délivrabilité. L’ancien serveur de délivrabilité sera désactivé le 31 août 2022.

En tant que client Campaign Classic, vous devez implémenter le nouveau serveur de délivrabilité **avant le 31 août 2022**.

>[!NOTE]
>
>Pour plus d’informations sur ces modifications, reportez-vous à la section [FAQ](#faq) ou contactez [l’Assistance clientèle d’Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}.
>

## Qu’est-ce qui a changé ?{#acc-deliverability-changes}

Adobe désactive les anciens centres de données pour des raisons de conformité en matière de sécurité. Les clients Adobe Campaign Classic doivent effectuer une migration vers le nouveau serveur de délivrabilité, hébergé sur Amazon Web Service (AWS).

Ce nouveau serveur garantit une haute disponibilité (99,9) et fournit des points d’entrée sécurisés et authentifiés permettant aux serveurs de campagne de récupérer les données requises. Ainsi, plutôt que de se connecter à la base de données pour chaque demande, le nouveau serveur de délivrabilité met en cache les données afin de répondre aux demandes, dans la mesure du possible. Ce mécanisme améliore le temps de réponse.

## Cela vous concerne-t-il ?{#acc-deliverability-impacts}

Tous les clients sont concernés et doivent effectuer la mise à niveau vers [la version 7.2.2 de Campaign](../../rn/using/latest-release.md#release-7-2-2) (ou une version ultérieure) et implémenter leur environnement pour bénéficier du nouveau serveur de délivrabilité.

## Comment effectuer la mise à jour ?{#acc-deliverability-update}

En tant que **client hébergé**, Adobe collaborera avec vous pour mettre à niveau votre ou vos instances vers la version la plus récente et créer le projet dans la console Adobe Developer.

En tant que **client on-premise/hybride**, vous devez effectuer la mise à niveau vers [la version 7.2.2 de Campaign](../../rn/using/latest-release.md#release-7-2-2) (ou une version ultérieure) pour bénéficier du nouveau serveur de délivrabilité. Une fois toutes les instances mises à niveau, vous devez [implémenter la nouvelle intégration](#implementation-steps) vers le serveur de délivrabilité d’Adobe, et assurer ainsi une transition transparente.

## Étapes dʼimplémentation {#implementation-steps}

>[!WARNING]
>
>Ces étapes ne doivent être effectuées que pour les implémentations hybrides et On-Premise.

Dans le cadre de la nouvelle intégration du serveur de délivrabilité, Campaign doit communiquer avec les services partagés d’Adobe via une authentification basée sur Identity Management Service (IMS). Il est préférable d’utiliser le jeton de passerelle basé sur Adobe Developer (également appelé Jeton de compte technique ou JWT Adobe IO).

>[!AVAILABILITY]
>
> Les informations d’identification de compte de service (JWT) étant abandonnées par Adobe, les intégrations de Campaign aux solutions et aux applications Adobe doivent désormais utiliser des informations d’identification OAuth serveur à serveur.</br>
>
> * Si vous avez implémenté des intégrations entrantes pour Campaign, vous devez migrer votre compte technique comme décrit dans [cette documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). Les [informations d’identification de compte de service (JWT)](oauth-technical-account.md) existantes continueront à fonctionner jusqu’au 27 janvier 2025. </br>
>
> * Si vous avez implémenté des intégrations sortantes, telles qu’une intégration Campaign-Analytics ou une intégration Experience Cloud Triggers, celles-ci continueront de fonctionner jusqu’au 27 janvier 2025. Toutefois, avant cette date, vous devez mettre à niveau votre environnement Campaign vers la version 7.4.1 et migrer votre compte technique vers OAuth.

### Conditions préalables{#prerequisites}

Avant de commencer l’implémentation, vérifiez la configuration de votre instance.

1. Ouvrez la console cliente Campaign et connectez-vous à Adobe Campaign en tant qu’administrateur.
1. Accédez à **Administration > Plateforme > Options**.
1. Vérifiez que la valeur de l’option `DmRendering_cuid` est renseignée.

   * Si vous avez renseigné cette option, vous pouvez lancer l’implémentation.
   * Si aucune valeur n’est renseignée, contactez l’[Assistance clientèle d’Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} pour obtenir votre CUID.

   Cette option doit être renseignée sur toutes vos instances Campaign (MKT, MID, RT, EXEC) avec la valeur correcte. En tant que client hybride, contactez Adobe pour que l’option soit définie sur vos instances MID, RT et EXEC.

En tant que client On-Premise, vous devez également vérifier qu’un **[!UICONTROL profil de produit]** Campaign est disponible pour votre organisation. Pour ce faire, suivez les étapes ci-après :

1. En tant qu’administrateur, connectez-vous à [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}.
1. Accédez à la section **Produit et services** et vérifiez qu’**Adobe Campaign** est répertorié.
Si vous ne pouvez pas voir **Adobe Campaign**, contactez l’[Assistance clientèle d’Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} pour l’ajouter.
1. Cliquez sur **Adobe Campaign** et sélectionnez votre organisation.
   **Attention** : si vous avez plusieurs organisations, veillez à choisir la bonne. En savoir plus sur les organisations [sur cette page](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=fr#ims-org-id){_blank}.

1. Vérifiez qu’il existe un **[!UICONTROL profil de produit]**. Dans le cas contraire, créez-le. Aucune autorisation n’est requise pour ce **[!UICONTROL profil de produit]**.


>[!CAUTION]
>
>En tant que client On-Premise, si un pare-feu est implémenté de votre côté, vous devez ajouter cette URL `https://deliverability-service.adobe.io` à votre liste autorisée. [En savoir plus](../../installation/using/url-permissions.md).


### Étape 1 : créer/mettre à jour votre projet Adobe Developer {#adobe-io-project}

Pour poursuivre la configuration de votre connecteur Adobe Analytics, accédez à Adobe Developer Console et créez votre projet OAuth serveur à serveur.

Consultez [cette page](../../integrations/using/oauth-technical-account.md#oauth-service) pour accéder à la documentation détaillée.

### Étape 2 : ajouter les informations d’identification du projet dans Adobe Campaign {#add-credentials-campaign}

Suivez les étapes décrites sur [cette page](../../integrations/using/oauth-technical-account.md#add-credentials) pour ajouter vos informations d’identification de projet OAuth dans Adobe Campaign.

### Étape 3 : valider votre configuration

Pour vérifier que l’intégration a réussi, procédez comme suit :

1. Ouvrez la console cliente et connectez-vous à Adobe Campaign.
1. Accédez à **Administration > Production > Workflows techniques**.
1. Redémarrez le workflow **Actualiser la délivrabilité** (deliverabilityUpdate). Cette opération doit être réalisée sur toutes vos instances Campaign (MKT, MID, RT, EXEC). En tant que client hybride, contactez Adobe pour redémarrer le workflow sur vos instances MID, RT et EXEC.
1. Vérifier les logs : le workflow doit s’exécuter sans erreur.

>[!CAUTION]
>
>Après la mise à jour, le workflow **Mettre à jour le réseau de test pour l’Inbox Rendering (updateRenderingSeeds)** doit être arrêté, car il ne s’appliquera plus et échouera.

## Forum aux questions {#faq}

### Quelle est le planning de la mise à jour ?

La transition vers le nouveau serveur de délivrabilité, permettant l’ajout de ces fonctionnalités améliorées et le renforcement de la sécurité, commencera le 22 juillet pour les clients hébergés (Campaign Managed Services). Tous les clients hébergés seront mis à jour avant la fin du mois d’août.

Les clients on-premise et hybrides doivent effectuer une transition à la même période.

### Que se passe-t-il si je ne mets pas à niveau mon environnement ?

Toute instance de Campaign non mise à niveau d’ici le 31 août ne pourra plus se connecter au serveur de délivrabilité de Campaign. Par conséquent, le workflow **Actualiser la délivrabilité** (deliverabilityUpdate) échouera, ce qui affectera votre délivrabilité.

Si vous ne mettez pas à niveau votre environnement, les paramètres d’e-mail ne seront plus synchronisés (règles de gestion MX, règles relatives aux e-mails entrants, règles de gestion des domaines et règles de qualification des rebonds). Cela peut affecter votre délivrabilité au fil du temps. Si une modification importante est apportée à ces règles, celles-ci doivent être appliquées manuellement à partir de ce point.

Pour les instances MKT, seule la [Liste de suppression globale](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules) est affectée.
