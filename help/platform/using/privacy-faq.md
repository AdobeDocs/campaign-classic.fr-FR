---
product: campaign
title: Questions fréquentes sur la confidentialité et le consentement
description: Questions fréquentes sur la confidentialité et le consentement
feature: Privacy, Privacy Tools
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: ce2c90cd-46d9-4365-8013-5c1273b6c176
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 100%

---

# FAQ sur la confidentialité {#privacy-faq}



Voici quelques-unes des questions fréquentes sur la confidentialité et le consentement lors de l’utilisation d’Adobe Campaign.

## Termes clés {#key-terms}

### Quels sont les termes clés de la protection des données personnelles ?

Les éléments répertoriés ci-dessous renvoient aux termes et concepts clés relatifs à la protection des informations personnelles et au consentement dans Adobe Campaign :

* [Règlements relatifs à la gestion de la confidentialité](../../platform/using/privacy-management.md#privacy-management-regulations)
* [Données personnelles et personnes concernées](../../platform/using/privacy-and-recommendations.md#personal-data)
* [Droit d’accès et droit à l’oubli](../../platform/using/privacy-management.md#right-access-forgotten)
* [Consentement, conservation des données et rôles](../../platform/using/privacy-management.md#consent-retention-roles)

## Préparation à la réglementation en matière de confidentialité {#privacy-regulations-readiness}

### Que suggère Adobe Campaign pour se conformer aux dernières réglementations en matière de protection des données personnelles ?

Adobe ne fournit pas de conseils juridiques. Nous vous recommandons donc de vous rapprocher de votre propre service juridique pour vous assurer qu’il prend toutes les mesures nécessaires pour le respect du RGPD, de l’ACPCP, de PDPA, du LGPD ou de toute autre disposition réglementaire applicable.

**Préparation aux demandes d’accès et de suppression des données**

* Identifiez un processus pour recevoir les demandes formulées par les titulaires des données et y répondre, en désignant notamment un point de contact en charge de la protection des données.

* Examinez les différents types de données client stockées dans Adobe Campaign et définissez des identifiants uniques (il en faudra certainement plusieurs).

* Définissez des règles et procédures d’authentification et de validation pour la confirmation de l’identité des titulaires des données.

* Assurez-vous que la réponse adressée au titulaire de données est parfaitement compréhensible.

**Obtention du consentement**

* Établissez régulièrement la liste de tous les points de contact utilisés pour la capture des données afin de garantir votre conformité avec le RGPD (tenez compte de la langue, du mécanisme d’obtention du consentement et des journaux de consentements, par exemple).

* Vérifiez que tous les emails marketing comprennent un lien de désabonnement.

* Évaluez la stratégie globale du marketing email pour définir des mises en œuvre propres à chaque zone géographique.

**Compréhension des données**

* Passez en revue toutes les sources de capture et d’import des données transitant par Adobe Campaign, et documentez les champs utilisés dans le cadre de vos actions marketing.

* Supprimez tout attribut de données non utilisé de votre base de données Adobe Campaign.

* Utilisez les données disponibles dans Adobe Campaign aux fins pour lesquelles elles ont été collectées, et offrez aux destinataires une expérience plus personnalisée.

* Passez en revue les autorisations d’accès aux données et mettez-les à jour pour que les utilisateurs d’Adobe Campaign puissent exploiter uniquement les données nécessaires à l’exécution de leurs campagnes, sans accéder aux autres données.

* Vérifiez que chaque utilisateur d’Adobe Campaign dispose des droits d’accès nécessaires pour exécuter ses tâches, mais qu’il ne dispose d’aucun autre droit pour effectuer d’autres tâches.

## Préserver l’interaction client {#preserve-user-engagement}

### Comment les contrôleurs de données peuvent-ils obtenir le consentement avec un minimum d’impact sur l’interaction client ?

Dans les cas où le consentement est nécessaire pour certaines activités de commercialisation, le consentement du consommateur doit être actif (l’absence de réponse ne peut valoir consentement, pas d’utilisation de cases pré-cochées). Le consentement ne doit pas non plus être groupé, ni être conditionné à l’offre de services.

Certains consentements doivent même parfois être réactualisés pour que les données puissent continuer à être utilisées.

Les spécialistes marketing devraient considérer ces exigences de consentement améliorées comme un véritable indicateur de la fidélité et de l’interaction avec la marque, ainsi que de la satisfaction et de la confiance des clients.

## Gestion du consentement {#manage-consent}

### Comment les contrôleurs de données peuvent-ils gérer le consentement dans Adobe Campaign ?

Adobe Campaign offre déjà des capacités de gestion du consentement à plus de niveaux que la plupart des spécialistes marketing ne tirent parti des champs de données personnalisés ou d’un ou plusieurs services.

Il est conseillé aux spécialistes marketing de consulter leur service juridique pour savoir comment procéder, puis tirer parti des capacités déjà intégrées à Adobe Campaign.

Par exemple, il est possible d’étendre le modèle de données dans Adobe Campaign pour suivre non seulement si les personnes ont choisi de s’inscrire, mais aussi l’horodatage de l’opt-in et un type d’indicateur qui capture la portée précise du consentement.

## Suppression de données {#data-deletion}

### Quelles données les contrôleurs de données peuvent-ils supprimer dans Adobe Campaign en réponse à une requête d’un client (titulaire des données) ?

Toutes les données associées au titulaire de données seront supprimées, y compris les tables d’usine et personnalisées.

Techniquement, toutes les données liées au titulaire de données avec `integrity="own"` seront supprimées.

En tant que contrôleur de données, vous avez la possibilité de personnaliser cela en modifiant l’intégrité des liens définis dans les schémas de données (par exemple, si vous avez une justification commerciale pour ne pas supprimer certaines données).

### Quel est l’impact de la suppression des logs de tracking et de diffusion sur les rapports ?

Dans Adobe Campaign, les rapports reposent sur des indicateurs calculés grâce aux données agrégées issues des logs de diffusion et de tracking. Par conséquent, la suppression de ces logs ne doit pas avoir d’incidence sur les mesures affichées dans les rapports.

## Réimporter les données {#re-import-data}

### Dois-je garder à l’esprit la possibilité de réimporter les données ultérieurement ?

Souvent dans Adobe Campaign, l’enregistrement est téléchargé à partir d’une source de données externe.

Lorsque vous recevez une demande de suppression, vous devez vérifier, en tant que contrôleur de données, que vous supprimez de tous vos systèmes toutes les données nécessaires concernant le titulaire de données.

## Renouvellement d’opt-in {#opt-in-again}

### Est-ce qu’un ou une titulaire de données, dont les données ont été effacées d’Adobe Campaign, peut à nouveau donner son opt-in plus tard ?

Il est possible pour un titulaire de données de donner à nouveau son accord ou d’être ajouté en tant que nouveau destinataire après l’effacement de ses données d’Adobe Campaign.

Vous pouvez utiliser le journal d’audit qui détaille la date de suppression précédente et la date de création du nouveau destinataire.
