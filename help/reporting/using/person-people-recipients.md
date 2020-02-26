---
title: Rapports sur les diffusions
seo-title: Rapports sur les diffusions
description: Rapports sur les diffusions
seo-description: null
page-status-flag: never-activated
uuid: 83ea834e-08f7-441b-8f15-a25ec07c4aab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
discoiquuid: cc832666-ad18-49ce-afcc-f9169b683ae8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 18309c190c351cc57f7af24f48b2a772c1840319

---


# Personnes et destinataires {#person-people-and-recipients}

Cet exemple va vous permettre de comprendre la différence entre une personne et un destinataire dans Adobe Campaign. Nous allons envoyer une diffusion à plusieurs personnes afin de mettre en évidence, au travers d&#39;un cas concret, la distinction entre les personnes et les destinataires. Cela va également nous permettre de voir plus en détails la méthode de calcul des indicateurs suivants :

* **[!UICONTROL Clicks]**
* **[!UICONTROL Distinct clicks for the population reached]**
* **[!UICONTROL Distinct opens for the population reached]**
* **[!UICONTROL Estimation of forwards]**
* **[!UICONTROL Raw reactivity]**

>[!NOTE]
>
>Ces indicateurs sont utilisés dans le **[!UICONTROL Tracking indicators]** rapport. For more on this, refer to [Tracking indicators](../../reporting/using/delivery-reports.md#tracking-indicators).

Trois liens sont ajoutés dans une diffusion. Celle-ci est envoyée à 4 destinataires :

![](assets/s_ncs_user_indicators_example_1.png)

* **[!UICONTROL John Davis]** : ce destinataire n&#39;ouvre pas l&#39;email (il ne clique donc sur aucun lien).
* **[!UICONTROL Marie Stuart]** : ouvre l&#39;email mais ne clique sur aucun lien.
* **[!UICONTROL Florian David]** : ouvre le courrier électronique et clique 9 fois sur les liens. Il transfère également le courrier électronique à une personne qui l’ouvre et clique deux fois.
* **[!UICONTROL Henry Macdonald]** : ce destinataire a configuré son navigateur Internet pour rejeter les cookies. Il ouvre le courriel et clique 4 fois sur les liens.

Les logs de tracking suivants sont remontés :

![](assets/s_ncs_user_indicators_example_2.png)

Pour mieux comprendre le mécanisme de comptabilisation des personnes et des destinataires, nous allons analyser successivement les logs correspondant à chaque profil.

## Etape 1 : John {#step-1--john}

**[!UICONTROL John Davis]** n&#39;ouvre pas l&#39;email (il ne clique donc sur aucun lien).

![](assets/s_ncs_user_indicators_example_8.png)

Comme John n&#39;a ni ouvert ni cliqué dans l&#39;email, il n&#39;apparaît pas dans les logs.

**Calcul intermédiaire :**

|  | Destinataires ayant cliqué | Personnes ayant cliqué | Destinataires ayant ouvert |
|---|---|---|---|
| John | - | - | - |
| Total intermédiaire | 0 | 0 | 0 |

## Etape 2 : Marie {#step-2--marie}

**[!UICONTROL Marie Stuart]** ouvre l&#39;email mais ne clique sur aucun lien.

![](assets/s_ncs_user_indicators_example_7.png)

L&#39;ouverture de Marie apparait dans le log suivant :

![](assets/s_ncs_user_indicators_example_4bis.png)

L&#39;ouverture est attribuée à un destinataire, Marie. Adobe Campaign comptabilise donc un nouveau destinataire.

**Calcul intermédiaire :**

|  | Destinataires ayant cliqué | Personnes ayant cliqué | Destinataires ayant ouvert |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Total intermédiaire | 0 | 0 | 1 |

## Etape 3 : Florian {#step-3--florian}

**[!UICONTROL Florian David]** ouvre le courrier électronique et clique 9 fois sur les liens. Il transfère également le courrier électronique à une personne qui l’ouvre et clique deux fois.

![](assets/s_ncs_user_indicators_example_9.png)

Les actions effectuées par Florian (une ouverture et 9 clics) apparaissent dans les logs suivants :

![](assets/s_ncs_user_indicators_example_3bis.png)

**Destinataires :** L&#39;ouverture et les clics sont attribués au même destinataire (Florian). Comme ce destinataire est différent du précédent (Marie), Adobe Campaign comptabilise un nouveau destinataire.

People: Since this recipient&#39;s browser accepts cookies, we can see that the same identifier (UUID) is assigned to all click logs: **`fe37a503 [...]`**. Adobe Campaign correctly identifies these clicks as belonging to the same person. Une nouvelle personne est ajoutée au décompte.

**Calcul intermédiaire :**

|  | Destinataires ayant cliqué | Personnes ayant cliqué | Destinataires ayant ouvert |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Florian | +1 | +1 | +1 |
| Total intermédiaire | 1 | 1 | 2 |

Les logs suivants correspondent à l&#39;ouverture et les 2 clics effectués par la personne à qui Florian a transféré l&#39;email :

![](assets/s_ncs_user_indicators_example_6bis.png)

**Destinataires :** Son ouverture et ses clics sont attribués au destinataire ayant transféré l&#39;email (Florian). Comme ce destinataire a déjà été comptabilisé, le nombre de destinataires reste le même.

![](assets/s_ncs_user_indicators_example_12.png)

**Personnes**: en ce qui concerne les clics, nous constatons que le même identifiant (UUID) est affecté à tous les journaux : **`9ab648f9 [...]`**. Cet identifiant n&#39;a pas encore été comptabilisé. Une nouvelle personne est donc ajoutée au décompte.

![](assets/s_ncs_user_indicators_example_13.png)

**Calcul intermédiaire :**

|  | Destinataires ayant cliqué | Personnes ayant cliqué | Destinataires ayant ouvert |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Florian | +1 | +1 | +1 |
| Personne inconnue | - | +1 | - |
| Total intermédiaire | 1 | 2 | 2 |

## Etape 4 : Henry {#step-4--henry}

**[!UICONTROL Henry Macdonald]** a configuré son navigateur Internet pour rejeter les cookies. Il ouvre le courriel et clique 4 fois sur les liens.

![](assets/s_ncs_user_indicators_example_10.png)

L&#39;ouverture et les 4 clics effectués par Henry apparaissent dans les logs suivants :

![](assets/s_ncs_user_indicators_example_5bis.png)

**Destinataires :** L&#39;ouverture et les clics sont attribués au même destinataire (Henry). Comme ce destinataire n&#39;a pas encore été comptabilisé, Adobe Campaign ajoute un destinataire.

**Personnes :** Comme le navigateur d&#39;Henry n&#39;accepte pas les cookies, un nouvel identifiant (UUID) est généré à chaque clic. Chacun de ses quatre clics est interprété comme étant effectué par une nouvelle personne. Ces identifiants n&#39;ayant pas encore été comptabilisés, quatre nouvelles personnes sont donc ajoutées.

**Calcul intermédiaire :**

|  | Destinataires ayant cliqué | Personnes ayant cliqué | Destinataires ayant ouvert |
|---|---|---|---|
| John | - | - | - |
| Marie | - | - | +1 |
| Florian | +1 | +1 | +1 |
| Personne inconnue | - | +1 | - |
| Henry | +1 | +4 | +1 |
| Total intermédiaire | 2 | 6 | 3 |

## Synthèse {#summary}

Au niveau de la diffusion, les résultats sont donc les suivants :

![](assets/s_ncs_user_indicators_example.png)

* **[!UICONTROL Clicks]** (destinataires ayant cliqué) : 2
* **[!UICONTROL Distinct clicks for the population reached]** (personnes ayant cliqué) : 6
* **[!UICONTROL Distinct opens for the population reached]** (destinataires qui ont ouvert) : 3

La réactivité brute et l&#39;estimation des transferts sont calculées de la manière suivante :

![](assets/s_ncs_user_indicators_example11.png)

* **[!UICONTROL Estimation of forwards]** = **B - A** (donc 6 - 2 = 4)
* **[!UICONTROL Raw reactivity]** = **A / C** (2 / 3 = 66,67 %)

>[!NOTE]
>
>Dans les formules ci-dessus :
>
>* A represents the **[!UICONTROL Clicks]** indicator (recipients who clicked).
>* B représente l’ **[!UICONTROL Distinct clicks for the population reached]** indicateur (personnes ayant cliqué).
>* C représente l’ **[!UICONTROL Distinct opens for the population reached]** indicateur (les destinataires qui ont ouvert).