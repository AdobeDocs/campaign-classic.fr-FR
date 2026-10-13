---
product: campaign
title: Détection des URL de tracking
description: En savoir plus sur le modèle recommandé pour suivre les URL
feature: Monitoring
role: User, Developer
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
TQID: 'https://experienceleague.adobe.com/F63e0G1uyp-tXDiBk9cau5P-HBHttCkiFD2yw657RBw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 76%
---
# Détection des URL de tracking

Adobe Campaign détecte les URL à suivre dans votre contenu lors de l’analyse de la diffusion.

Dans le cadre de la transition de Campaign v7 vers v8, le jeu de documentation de Campaign Classic a été rationalisé et réorganisé. Les fonctionnalités communes sont désormais disponibles exclusivement dans le jeu de documentation de Campaign v8. Pour découvrir comment les URL sont détectées et les modèles à utiliser, consultez la [documentation de Campaign v8](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/analytics/tracking/personalized-links#url-detection){target=_blank}.

[![Image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/fr/docs/campaign/campaign-v8/analytics/tracking/personalized-links#url-detection){target=_blank}

## Modèle non sécurisé

Lorsque vous ajoutez des liens personnalisés à votre contenu, évitez toujours toute personnalisation dans la partie de nom d’hôte de l’URL afin d’éviter des failles de sécurité potentielles. En savoir plus sur [cette page](../../installation/using/privacy.md#url-personalization).

Par exemple, la syntaxe `<a href="http://<%=myURL%>">` n’est **pas sécurisée** et doit être évitée.

* L’utilisation de cette syntaxe peut entraîner des problèmes de sécurité si le lien généré par Adobe Campaign contient un ou plusieurs paramètres.
* Tidy peut incorrectement corriger certains liens, ce qui peut se produire de manière aléatoire. Le symptôme typique est une portion de code HTML visible dans les BAT d&#39;email mais pas dans la prévisualisation.
* L’échappement de l’URL est problématique, certains caractères de l’URL peuvent poser des problèmes.
* Un paramètre nommé ID ne peut pas entrer en conflit avec un paramètre dans l’URL de redirection.
* L’intérêt du tracking est alors limité aux statistiques de la diffusion, car Adobe Campaign tracke indifféremment toutes les valeurs possibles de « myURL ».
