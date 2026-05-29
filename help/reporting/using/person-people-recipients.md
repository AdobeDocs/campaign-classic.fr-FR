---
product: campaign
title: Personnes et destinataires
description: Personnes et destinataires
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Reporting, Monitoring
exl-id: 69b810f3-aa8b-4ab5-95c1-831257d7fcb9
TQID: https://experienceleague.adobe.com/ZvTALeh3LgGQxNwaQv-usFMAfVvyQFe-rmf6WQDHqTE
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
feature_v2:
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
  - id: cfda811a-e413-43a4-adf0-7370888f5cfc
  - id: afe938ea-bc18-44a4-a3fb-03e1031466cb
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 800
ht-degree: 56%

---

# Personnes et destinataires {#person-people-and-recipients}



Cet exemple vous aidera à comprendre la différence entre une ou plusieurs personnes et un destinataire dans Adobe Campaign. Nous allons envoyer une diffusion à plusieurs personnes afin de mettre en évidence la différence entre les personnes et les destinataires tout en détaillant la méthode de calcul des indicateurs suivants :

* **[!UICONTROL Clics]**
* **[!UICONTROL Clics distincts sur la population atteinte]**
* **[!UICONTROL Ouvertures distinctes sur la population atteinte]**
* **[!UICONTROL Estimation des transferts]**
* **[!UICONTROL Réactivité brute]**

>[!NOTE]
>
>Ces indicateurs sont utilisés dans le rapport relatif aux **[!UICONTROL Indicateurs de tracking]**. Pour plus d&#39;informations, consultez la section [Indicateurs de tracking](../../reporting/using/delivery-reports.md#tracking-indicators).

Trois liens sont ajoutés à une diffusion. Il est envoyé à 4 destinataires :

![](assets/s_ncs_user_indicators_example_1.png)

* **[!UICONTROL John Davis]** : ce destinataire n&#39;ouvre pas l&#39;email (il ne clique donc sur aucun lien).
* **[!UICONTROL Marie Stuart]** : elle ouvre l&#39;email mais ne clique sur aucun lien.
* **[!UICONTROL Florian David]** : il ouvre l&#39;email et clique à 9 reprises sur les liens. Il transfère également l’e-mail à une personne qui l’ouvre et clique deux fois.
* **[!UICONTROL Henry Macdonald]** : ce destinataire a configuré son navigateur Internet pour qu&#39;il n&#39;accepte aucun cookie. Il ouvre l’e-mail et clique 4 fois sur les liens.

Les logs de tracking suivants sont remontés :

![](assets/s_ncs_user_indicators_example_2.png)

Pour mieux comprendre le mécanisme de comptabilisation des personnes et des destinataires, nous allons analyser successivement les logs correspondant à chaque profil.

## Etape 1 : John {#step-1--john}

**[!UICONTROL John Davis]** n&#39;ouvre pas l&#39;email (il ne clique donc sur aucun lien).

![](assets/s_ncs_user_indicators_example_8.png)

Comme John n&#39;a ni ouvert ni cliqué dans l&#39;email, il n&#39;apparaît pas dans les logs.

**Calcul intermédiaire :**

|   | Destinataires ayant cliqué | Personnes ayant cliqué | Destinataires ayant ouvert |
|---|---|---|---|
| John | - | - | - |
| Total intermédiaire | 0 | 0 | 0 |

## Etape 2 : Marie {#step-2--marie}

**[!UICONTROL Marie Stuart]** ouvre l&#39;email mais ne clique sur aucun lien.

![](assets/s_ncs_user_indicators_example_7.png)

L’ouverture de Marie apparait dans le log suivant :

![](assets/s_ncs_user_indicators_example_4bis.png)

L&#39;ouverture est attribuée à un destinataire : Marie. Adobe Campaign comptabilise donc un nouveau destinataire.

**Calcul intermédiaire :**

|   | Destinataires ayant cliqué | Personnes ayant cliqué | Destinataires ayant ouvert |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Total intermédiaire | 0 | 0 | 1 |

## Etape 3 : Florian {#step-3--florian}

**[!UICONTROL Florian David]** ouvre l&#39;email et clique à 9 reprises sur les liens. Il transfère également l’e-mail à une personne qui l’ouvre et clique deux fois.

![](assets/s_ncs_user_indicators_example_9.png)

Les actions effectuées par Florian (une ouverture et 9 clics) apparaissent dans les logs suivants :

![](assets/s_ncs_user_indicators_example_3bis.png)

**Destinataires** : L&#39;ouverture et les clics sont attribués au même destinataire (Florian). Comme ce destinataire est différent du précédent (Marie), Adobe Campaign ajoute un nouveau destinataire au décompte.

Personnes : comme le navigateur de ce destinataire accepte les cookies, nous pouvons constater que le même identifiant (UUID) est attribué à tous les journaux de clics : **`fe37a503 [...]`**. Adobe Campaign identifie correctement ces clics comme appartenant à la même personne. Une nouvelle personne est ajoutée au décompte.

**Calcul intermédiaire :**

|   | Destinataires ayant cliqué | Personnes ayant cliqué | Destinataires ayant ouvert |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Florian | +1 | +1 | +1 |
| Total intermédiaire | 1 | 1 | 2 |

Les logs suivants correspondent à l&#39;ouverture et les 2 clics effectués par la personne à qui Florian a transféré l&#39;email :

![](assets/s_ncs_user_indicators_example_6bis.png)

**Destinataires** : Son ouverture et ses clics sont attribués au destinataire qui a transféré l&#39;email (Florian). Comme ce destinataire a déjà été comptabilisé, le nombre de destinataires reste le même.

![](assets/s_ncs_user_indicators_example_12.png)

**Personnes** : en ce qui concerne les clics, on constate que le même identifiant (UUID) est attribué à tous les logs : **`9ab648f9 [...]`**. Cet identifiant n&#39;a pas encore été comptabilisé. Une nouvelle personne est donc ajoutée au décompte.

![](assets/s_ncs_user_indicators_example_13.png)

**Calcul intermédiaire :**

|   | Destinataires ayant cliqué | Personnes ayant cliqué | Destinataires ayant ouvert |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Florian | +1 | +1 | +1 |
| Personne inconnue | - | +1 | - |
| Total intermédiaire | 1 | 2 | 2 |

## Etape 4 : Henry {#step-4--henry}

**[!UICONTROL Henry Macdonald]** a configuré son navigateur Internet pour refuser les cookies. Il ouvre l’e-mail et clique 4 fois sur les liens.

![](assets/s_ncs_user_indicators_example_10.png)

L&#39;ouverture et les 4 clics effectués par Henry apparaissent dans les logs suivants :

![](assets/s_ncs_user_indicators_example_5bis.png)

**Destinataires** : l&#39;ouverture et les clics sont attribués au même destinataire (Henry). Comme ce destinataire n&#39;a pas encore été comptabilisé, Adobe Campaign ajoute un destinataire.

**Personnes** : étant donné que le navigateur d’Henry n’accepte pas les cookies, un nouvel identifiant (UUID) est généré pour chaque clic. Chacun des 4 clics est interprété comme provenant d’une personne différente. Comme ces identifiants n’ont pas encore été comptabilisés, ils sont ajoutés au nombre.

**Calcul intermédiaire :**

|   | Destinataires ayant cliqué | Personnes ayant cliqué | Destinataires ayant ouvert |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Florian | +1 | +1 | +1 |
| Personne inconnue | - | +1 | - |
| Henry | +1 | +4 | +1 |
| Total intermédiaire | 2 | 6 | 3 |

## Synthèse {#summary}

Au niveau de la diffusion, les résultats sont donc les suivants :

![](assets/s_ncs_user_indicators_example.png)

* **[!UICONTROL Clics]** (destinataires ayant cliqué) : 2
* **[!UICONTROL Clics distincts sur la population atteinte]** (personnes ayant cliqué) : 6
* **[!UICONTROL Ouvertures distinctes sur la population atteinte]** (destinataires ayant ouvert) : 3

La réactivité brute et l&#39;estimation des transferts sont calculées de la manière suivante :

![](assets/s_ncs_user_indicators_example11.png)

* **[!UICONTROL Estimation des transferts]** = **B - A** (donc 6 - 2 = 4)
* **[!UICONTROL Réactivité brute]** = **A / C** (donc 2 / 3 = 66,67 %)

>[!NOTE]
>
>Dans les formules ci-dessus :
>
>* A représente l&#39;indicateur **[!UICONTROL Clics]** (destinataires ayant cliqués).
>* B représente l&#39;indicateur **[!UICONTROL Clics distincts sur la population atteinte]** (personnes ayant cliqué).
>* C représente l&#39;indicateur **[!UICONTROL Ouvertures distinctes sur la population atteinte]** (destinataires ayant ouvert).
