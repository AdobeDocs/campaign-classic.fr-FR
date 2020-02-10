---
title: Réception d'emails
seo-title: Réception d'emails
description: Réception d'emails
seo-description: null
page-status-flag: never-activated
uuid: 6bcc7952-f051-4e50-8833-95d49c7ed781
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: 4c0530b1-0292-45bc-8730-668bc5b8550b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Réception d&#39;emails{#inbound-emails}

L&#39;activité **Réception d&#39;emails** permet de récupérer et de traiter des emails depuis une messagerie accessible via le protocole POP3.

![](assets/email_rec_edit_1.png)

Le premier onglet de l&#39;activité **Réception d&#39;email** permet de renseigner les paramètres du serveur POP3 et de saisir le script à exécuter à la réception de chaque message. Le deuxième onglet permet d&#39;affecter un planning à l&#39;activité et le troisième onglet définit les conditions d&#39;expiration de l&#39;activité.

1. **[!UICONTROL Inbound Emails]**

   * **[!UICONTROL Use an external account]**

      Lorsque cette option est activée, vous pouvez sélectionner un compte POP3 externe au lieu de saisir les paramètres de connexion. Le **[!UICONTROL External account]** champ spécifie le compte POP3 externe à utiliser pour la connexion au service de messagerie. Ce champ n’est visible que si l’option &quot;Utiliser un compte externe&quot; est activée.

      Si cette option n&#39;est pas sélectionnée, vous devez indiquer les paramètres suivants :

      ![](assets/email_rec_edit_1b.png)

      * **[!UICONTROL POP3 server]**

         Nom du serveur POP3.

      * **[!UICONTROL POP3 account]**

         Nom de l&#39;utilisateur.

      * **[!UICONTROL Password]**

         Mot de passe du compte de l&#39;utilisateur.

      * **[!UICONTROL Port]**

         Numéro de port de la connexion POP3. Le port par défaut est 110.
   * **[!UICONTROL Stop as soon as email is processed]**

      Cette option permet de traiter les emails un par un. L&#39;activité n&#39;active sa transition qu&#39;une seule fois puis termine le traitement en laissant les messages non traités sur le serveur.


1. **[!UICONTROL Script]**

   Le script permet de traiter le message et d&#39;effectuer différentes opérations dépendantes du contenu du message. Le script est exécuté pour chaque message et peut décider de l&#39;opération à effectuer sur la messagerie (laisser ou supprimer le message) et de l&#39;activation de la transition sortante.

   Le code retour doit être une des valeurs suivantes :

   * 1 - Supprime le message sur le serveur et active la transition sortante.
   * 2 - Laisse le message sur le serveur et active la transition sortante.
   * 3 - Supprime le message sur le serveur.
   * 4 - Laisse le message sur le serveur.
   Le contenu du message est accessible depuis la variable globale **[!UICONTROL mailMessage]**.

1. **[!UICONTROL Schedule]**

   Pour définir un calendrier pour l’activité, cliquez sur l’ **[!UICONTROL Scheduling]** onglet et cochez **[!UICONTROL Plan execution]**. Cliquez sur le **[!UICONTROL Change]** bouton pour configurer la planification.

   La configuration de planification est la même que pour l’activité de planification. Reportez-vous au [Planificateur](../../workflow/using/scheduler.md).

1. **[!UICONTROL Expiration]**

   Vous pouvez définir des délais d&#39;expiration à partir de l&#39;onglet **[!UICONTROL Expiration]**.

   ![](assets/email_rec_edit_3.png)

   La configuration est la même que pour l’activité de planification. Reportez-vous à [Expirations](../../workflow/using/executing-a-workflow.md#expirations).

