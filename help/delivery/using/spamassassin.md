---
product: campaign
title: SpamAssassin
description: Découvrez comment configurer la détection des messages indésirables avec SpamAssassin
badge-v8: label="S’applique également à la v8." type="Positive" tooltip="S’applique également à Campaign v8."
feature: Email, Deliverability
role: User
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
TQID: https://experienceleague.adobe.com/nZB19N90xSjDCNnibtwcPBm75SSyxkq1hQxICXCOg2A
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 284
ht-degree: 100%

---

# SpamAssassin{#spamassassin}

Adobe Campaign peut être configuré pour fonctionner avec [SpamAssassin](https://spamassassin.apache.org), service tiers destiné à filtrer les e-mails indésirables.Cela permet d’attribuer un score aux e-mails afin de déterminer si un message risque d’être considéré comme indésirable par les outils anti-spams utilisés à sa réception.

SpamAssassin utilise diverses techniques de détection des emails indésirables, notamment :

* la détection des emails indésirables basée sur une somme de contrôle approximative et DNS,
* le filtrage bayésien,
* les programmes externes,
* Listes bloquées
* les bases de données en ligne.

>[!NOTE]
>
>SpamAssassin doit être installé et configuré sur le serveur d&#39;application d&#39;Adobe Campaign. Pour plus d’informations, consultez [cette section](../../installation/using/configuring-spamassassin.md).
>
>Les règles qui déterminent si un élément est indésirable ou non sont gérées par SpamAssassin et peuvent être éditées par un administrateur disposant de privilèges.

## Utilisation de SpamAssassin dans Campaign {#using-spamassassin}

Une fois que vous avez créé votre email et défini son contenu, suivez les étapes ci-après pour évaluer les risques.

Pour plus d&#39;informations sur la conception d&#39;une diffusion, consultez [cette section](about-email-channel.md).

1. Accédez à l&#39;onglet **[!UICONTROL Aperçu]**.
1. Sélectionnez un destinataire pour prévisualiser votre diffusion.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >Si vous ne sélectionnez pas de destinataire, la vérification anti-spam ne peut pas être effectuée.

1. Un message d’avertissement fournit le résultat du test.Si un risque élevé est détecté, le message d’avertissement suivant est affiché :

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. Cliquez sur le lien **[!UICONTROL Détail...]** situé en regard de l&#39;avertissement.
1. Sélectionnez l&#39;onglet **[!UICONTROL Vérification anti-spam]**.
1. Accédez à la section **[!UICONTROL Points / Règle / Description]** pour découvrir les raisons de ce risque.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>Chaque fois que vous cliquez sur **[!UICONTROL Vérification anti-spam]**, le service SpamAssassin est appelé et le message est réanalysé pour la détection des e-mails indésirables.Veillez à modifier votre contenu avant de réexécuter l’analyse anti-spam.
