---
solution: Campaign Classic
product: campaign
title: Confidentialité et consentement
description: En savoir plus sur la confidentialité et le consentement
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: ht
source-git-commit: 9e31f69fde38dcdc7f4e6d3ba3fb17911f96ded8
workflow-type: ht
source-wordcount: '808'
ht-degree: 100%

---


# FAQ sur la confidentialité {#privacy-faq}

Voici quelques-unes des questions fréquentes sur la confidentialité et le consentement lors de l’utilisation d’Adobe Campaign.

## Termes clés {#key-terms}

**Quels sont les termes clés relatifs à la confidentialité ?**

Les éléments répertoriés ci-dessous renvoient aux termes et concepts clés relatifs à la confidentialité et au consentement dans Adobe Campaign :

* [Règlements relatifs à la gestion de la confidentialité](../../platform/using/privacy-management.md#privacy-management-regulations)
* [Données personnelles et acteurs impliqués](../../platform/using/privacy-and-recommendations.md#personal-data)
* [Droit d&#39;accès et droit à l&#39;oubli](../../platform/using/privacy-management.md#right-access-forgotten)
* [Consentement, conservation des données et rôles](../../platform/using/privacy-management.md#consent-retention-roles)

## Préparation aux règlements relatifs à la confidentialité {#privacy-regulations-readiness}

**Que suggère Adobe Campaign pour se conformer aux règlements les plus récents en matière de confidentialité ?**

Adobe ne fournit pas de conseils juridiques. Nous vous conseillons de faire appel à votre propre service juridique pour vous assurer qu’il prend toutes les mesures nécessaires à la préparation de l&#39;application des règlements RGPD, CCPA, PDPA, LGPD ou tout autre règlement applicable.

**Préparation pour les demandes d’accès et de suppression des données**

* Définissez un processus pour recevoir les demandes formulées par les titulaires des données et y répondre, en désignant un point de contact en charge de la protection des données.

* Examinez les différents types de données client stockées dans Adobe Campaign et définissez des identifiants uniques (il en faudra certainement plusieurs).

* Définissez des règles et procédures d’authentification et de validation pour la confirmation de l’identité des titulaires des données.

* Penchez-vous sur la réponse adressée au titulaire des données et assurez-vous qu&#39;elle est parfaitement compréhensible.

**Obtention du consentement**

* Faites l&#39;inventaire de tous les points de contact utilisés pour la capture des données et actualisez-les pour garantir votre conformité au RGPD (tenez compte de la langue, du mécanisme d&#39;obtention du consentement et des logs de consentement, par exemple).

* Vérifiez que tous les emails marketing comprennent un lien de désabonnement.

* Evaluez la stratégie globale d&#39;email marketing pour définir des mises en œuvre propres à chaque zone géographique.

**Contrôle des données**

* Passez en revue toutes les sources de capture et d’import des données transitant par Adobe Campaign, et documentez les champs utilisés dans le cadre de vos actions marketing.

* Supprimez tout attribut de données non utilisé de votre base de données Adobe Campaign.

* Utilisez les données disponibles dans Adobe Campaign aux fins pour lesquelles elles ont été collectées, et offrez aux destinataires une expérience plus personnalisée.

* Passez en revue les autorisations d&#39;accès aux données et mettez-les à jour pour que les utilisateurs d&#39;Adobe Campaign puissent exploiter uniquement les données nécessaires à l&#39;exécution de leurs campagnes, sans accéder aux autres données.

* Vérifiez que chaque utilisateur d’Adobe Campaign dispose des droits d’accès nécessaires pour exécuter ses tâches, mais qu’il ne dispose d’aucun autre droit pour effectuer d’autres tâches.

## Conserver l’engagement de l&#39;utilisateur {#preserve-user-engagement}

**Comment les contrôleurs de données peuvent-ils obtenir le consentement avec un minimum d&#39;impact sur l&#39;expérience utilisateur ?**

Dans les cas où le consentement est nécessaire pour certaines activités de marketing, le consentement du client doit être actif (c’est-à-dire pas d’acceptation tacite ou de cases pré-cochées), dégroupé, et ne peut pas être conditionnel à l’offre de services.

Il peut même arriver que certains consentements doivent être actualisés pour pouvoir continuer à utiliser les données.

Plutôt que de considérer ces exigences de consentement plus strictes comme un risque pour l’univers du commerce, les spécialistes du marketing pourraient les considérer comme un véritable indicateur de l’engagement des clients et de leur fidélité à la marque, outre la satisfaction et la confiance qu’ils lui accordent.

## Gérer le consentement {#manage-consent}

**Comment les contrôleurs de données peuvent-ils gérer le consentement dans Adobe Campaign ?**

Adobe Campaign offre déjà des fonctionnalités de gestion du consentement à des niveaux supérieurs à ceux qu’appliquent la plupart des spécialistes du marketing au moyen de champs de données personnalisés ou d’un ou plusieurs services.

Les spécialistes du marketing devraient consulter leur service juridique pour savoir comment procéder, puis tirer parti des fonctionnalités déjà intégrées à Adobe Campaign.

Par exemple, l’extension du modèle de données dans Adobe Campaign permet de suivre non seulement si les personnes ont choisi de s’inscrire, mais aussi la date et l&#39;heure de l&#39;inscription, et un certain type d’indicateur contenant la portée précise du consentement.

## Suppression de données {#data-deletion}

**Quelles données les contrôleurs de données peuvent-ils supprimer dans Adobe Campaign en réponse à une demande client par un titulaire des données ?**

Toutes les données associées au titulaire de données seront supprimées, y compris les tables d&#39;usine et personnalisées.

Techniquement, toutes les données liées au titulaire de données `integrity="own"` seront supprimées.

En tant que contrôleur de données, vous avez la possibilité de personnaliser le processus en modifiant l’intégrité des liens définis dans les schémas de données (par exemple, si vous avez une justification commerciale de ne pas supprimer certaines données).

**Quel est l&#39;impact sur les rapports de la suppression des logs de tracking et de diffusion ?**

Dans Adobe Campaign, les rapports reposent sur des indicateurs calculés grâce aux données agrégées issues des logs de diffusion et de tracking. Par conséquent, la suppression de ces logs ne doit pas avoir d&#39;incidence sur les mesures affichées dans les rapports.

## Réimport des données {#re-import-data}

**Souvent dans Adobe Campaign, un enregistrement est téléchargé à partir d’une source de données externe. Dois-je être attentif à la possibilité de réimporter les données ultérieurement ?**

Lorsque vous recevez une demande de suppression, vous devez vérifier, en tant que contrôleur de données, que vous supprimez de tous vos systèmes toutes les données nécessaires concernant le titulaire des données.

## Nouvel Opt-in {#opt-in-again}

**Est-ce qu&#39;un titulaire de données dont les données ont été effacées d&#39;Adobe Campaign peut donner son accord à nouveau plus tard ?**

Il est possible qu&#39;un titulaire de données utilise à nouveau l&#39;Opt-in ou qu&#39;il soit ajouté en tant que nouveau destinataire après l&#39;effacement de ses données dans Adobe Campaign.

Vous pouvez utiliser le journal d’audit qui détaille la date de suppression précédente et la date de création du nouveau destinataire.