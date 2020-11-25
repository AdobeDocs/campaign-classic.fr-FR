---
solution: Campaign Classic
product: campaign
title: Confidentialité et consentement
description: En savoir plus sur la confidentialité et le consentement
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 9e31f69fde38dcdc7f4e6d3ba3fb17911f96ded8
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 29%

---


# FAQ sur la confidentialité {#privacy-faq}

Voici quelques-unes des questions fréquentes sur la confidentialité et le consentement lors de l’utilisation d’Adobe Campaign.

## Termes clés {#key-terms}

**Quels sont les termes clés de la protection des renseignements personnels ?**

Les éléments répertoriés ci-dessous renvoient aux termes et concepts clés relatifs à la protection des renseignements personnels et au consentement en Adobe Campaign :

* [Règlement sur la gestion de la confidentialité](../../platform/using/privacy-management.md#privacy-management-regulations)
* [Données personnelles et acteurs impliqués](../../platform/using/privacy-and-recommendations.md#personal-data)
* [Droit d&#39;accès et droit à l&#39;oubli](../../platform/using/privacy-management.md#right-access-forgotten)
* [Consentement, conservation des données et rôles](../../platform/using/privacy-management.md#consent-retention-roles)

## Préparation aux règles de confidentialité {#privacy-regulations-readiness}

**Que suggère Adobe Campaign pour se conformer aux plus récentes réglementations en matière de protection des renseignements personnels ?**

L&#39;Adobe ne fournit pas de conseils juridiques. Vous devriez travailler avec votre propre conseiller juridique pour vous assurer qu&#39;il prend toutes les mesures nécessaires pour que le RGPD, l&#39;ACPCP, le PDPA, la LGPD ou toute autre disposition réglementaire applicable soit prêt.

**Préparation des requêtes d’accès aux données et de suppression**

* Identifier un processus pour recevoir ou répondre aux demandes des sujets de données, y compris la nomination d&#39;un point de contact pour la protection des renseignements personnels.

* Examinez les différents types de données client stockées dans Adobe Campaign et définissez des identifiants uniques (il en faudra certainement plusieurs).

* Déterminez une stratégie de validation/authentification et un processus pour la confirmation de l&#39;identité du sujet de données.

* Penchez-vous sur la réponse adressée au titulaire des données et assurez-vous qu&#39;elle est parfaitement compréhensible.

**Considérer le consentement**

* Liste et mise à jour, le cas échéant, de tous les points de contact pour la capture de données pour le RGMD (c.-à-d. prendre en compte la langue, le mécanisme de consentement et les journaux de consentement).

* Vérifiez que tous les emails marketing comprennent un lien de désabonnement.

* Evaluez la stratégie globale d&#39;email marketing pour définir des mises en œuvre propres à chaque zone géographique.

**Contrôle des données**

* Examinez toutes les sources d’importation et de capture de données dans Adobe Campaign et document les champs utilisés pour vos actions marketing.

* Supprimez tout attribut de données non utilisé de votre base de données Adobe Campaign.

* Utilisez les données disponibles dans Adobe Campaign aux fins pour lesquelles elles ont été collectées, et offrez aux destinataires une expérience plus personnalisée.

* Passez en revue les autorisations d&#39;accès aux données et mettez-les à jour pour que les utilisateurs d&#39;Adobe Campaign puissent exploiter uniquement les données nécessaires à l&#39;exécution de leurs campagnes, sans accéder aux autres données.

* Assurez-vous que chaque utilisateur d’Adobe Campaign dispose des droits d’accès appropriés pour exécuter les tâches requises, mais n’a pas d’autres droits pour effectuer des tâches supplémentaires.

## Conserver l’engagement des utilisateurs {#preserve-user-engagement}

**Comment les contrôleurs de données peuvent-ils obtenir le consentement avec un minimum d&#39;impact sur l&#39;expérience utilisateur ?**

Dans les cas où le consentement est nécessaire pour certaines activités de commercialisation, le consentement du consommateur doit être principal (c&#39;est-à-dire qu&#39;il n&#39;y a pas de silence en tant qu&#39;avis conforme ou cases pré-cochées), dégroupé, et il ne peut pas être conditionnel à l&#39;offre de services.

Il peut même arriver que certains consentements doivent être actualisés pour pouvoir continuer à utiliser les données.

Plutôt que de considérer ces exigences accrues de consentement comme un risque pour l&#39;univers commercialisable, les spécialistes du marketing pourraient les considérer comme un véritable indicateur de l&#39;engagement et de la fidélité de la marque, ainsi que de la satisfaction et de la confiance des clients.

## Gérer le consentement {#manage-consent}

**Comment les contrôleurs de données peuvent-ils gérer le consentement en Adobe Campaign ?**

Adobe Campaign offre déjà des capacités de gestion du consentement à plus de niveaux que la plupart des spécialistes du marketing ne tirent parti des champs de données personnalisés ou d’un ou plusieurs services.

Les spécialistes du marketing devraient consulter leur conseiller juridique pour savoir comment procéder, puis tirer parti des capacités déjà intégrées à Adobe Campaign.

Par exemple, l’extension du modèle de données en Adobe Campaign pour suivre non seulement si les personnes ont choisi de s’inscrire, mais aussi l’horodatage de l’inclusion et un type d’indicateur qui capture la portée précise du consentement.

## Suppression de données {#data-deletion}

**Quelles données les contrôleurs de données peuvent-ils supprimer en Adobe Campaign en réponse à une demande du client par une personne concernée ?**

Toutes les données associées à la personne concernée seront supprimées, y compris les tableaux prêts à l&#39;emploi et personnalisés.

Techniquement, toutes les données liées à la personne concernée `integrity="own"` seront supprimées.

En tant que contrôleur de données, vous avez la possibilité de personnaliser cela en modifiant l’intégrité des liens définis dans les schémas de données (par exemple, si vous avez une justification commerciale pour ne pas supprimer certaines données).

**Quel est l&#39;impact sur les rapports de la suppression des logs de tracking et de diffusion ?**

Dans Adobe Campaign, les rapports reposent sur des indicateurs calculés grâce aux données agrégées issues des logs de diffusion et de tracking. Par conséquent, la suppression de ces logs ne doit pas avoir d&#39;incidence sur les mesures affichées dans les rapports.

## Réimportation des données {#re-import-data}

**Souvent en Adobe Campaign, l’enregistrement est téléchargé à partir d’une source de données externe. Dois-je garder à l’esprit la possibilité de réimporter les données ultérieurement ?**

Lorsque vous recevez une demande de suppression, vous devez vérifier, en tant que contrôleur de données, que vous supprimez de tous vos systèmes toutes les données nécessaires concernant le titulaire des données.

## opt-in à nouveau {#opt-in-again}

**Est-ce qu&#39;un titulaire de données dont les données ont été effacées d&#39;Adobe Campaign peut donner son accord à nouveau plus tard ?**

Il est possible qu&#39;une personne soumise à l&#39;obligation de s&#39;inscrire à nouveau ou qu&#39;elle soit ajoutée en tant que nouveau destinataire après l&#39;effacement de ses données de Adobe Campaign.

Vous pouvez utiliser le journal d’audit qui détaille la date de suppression précédente et la date de création du nouveau destinataire.