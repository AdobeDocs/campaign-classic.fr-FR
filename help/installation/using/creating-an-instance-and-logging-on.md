---
title: Création et connexion à une instance
seo-title: Création et connexion à une instance
description: Création et connexion à une instance
seo-description: null
page-status-flag: never-activated
uuid: cb1620b3-f6e8-41dc-9142-ac0da65b6f8d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: c7395094-c635-45ab-8455-a050f7d16b64
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# Création et connexion à une instance{#creating-an-instance-and-logging-on}

Pour créer une nouvelle instance ainsi que la base de données Adobe Campaign, la procédure est la suivante :

1. Créer la connexion,
1. S&#39;y connecter pour créer l&#39;instance associée,
1. Créer et paramétrer la base de données.

>[!NOTE]
>
>Seul l’identifiant **interne** peut effectuer ces opérations. For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

Lorsque la console Adobe Campaign est démarrée, vous accédez à une page de connexion.

Pour créer une instance, procédez comme suit :

1. Pour accéder à la fenêtre de paramétrage des connexions, cliquez sur le lien situé en haut à droite des champs des identifiant et mot de passe. Ce lien peut être **[!UICONTROL Nouveau...]** ou le nom d&#39;une instance existante.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Cliquez sur le menu **[!UICONTROL Ajouter > Connexion]** et saisissez le libellé et l&#39;URL du serveur applicatif Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Définissez une connexion vers votre serveur applicatif Adobe Campaign à partir d&#39;une URL. Utilisez soit un DNS ou un alias de la machine, soit votre adresse IP.

   Par exemple, vous pouvez utiliser le [`https://<machine>.<domain>.com`](https://machine) type URL.

   >[!CAUTION]
   >
   >For the connection URL, only use the following characters: `[a-z]`, `[A-Z]`, `[0-9]` and dashes (-) or full stops.

1. Cliquez sur **[!UICONTROL OK]** pour valider ce paramétrage : vous pouvez alors démarrer le processus de création de l&#39;instance.
1. In the **[!UICONTROL Connection settings]** window, enter the **internal** login and its password to connect to the Adobe Campaign application server. Once connected, you access the instance creation wizard to declare a new instance
1. Dans le champ **[!UICONTROL Nom]** , saisissez le nom **de l’** instance. Ce nom étant utilisé pour générer un fichier de configuration **config-`<instance>`.xml** et dans les paramètres de ligne de commande pour identifier l’instance, veillez à choisir un nom court sans caractères spéciaux. Par exemple : **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   Le nom de l&#39;instance accolé au nom de domaine ne doit pas dépasser 40 caractères. Ceci permet de limiter la taille des en-têtes &quot;Message-ID&quot; et d&#39;éviter qu&#39;un message ne soit considéré comme un spam, par exemple par un outil comme SpamAssassin.

1. Dans les champs **[!UICONTROL Masques DNS]**, saisissez la **liste des masques DNS** auxquels l&#39;instance doit être attachée. Le serveur Adobe Campaign utilise le nom d&#39;hôte (hostname) qui apparaît dans les requêtes HTTP pour déterminer quelle instance atteindre.

   Le nom d’hôte est contenu entre la chaîne **https://** et la première barre oblique **/** de l’adresse du serveur.

   Vous pouvez définir ici une liste de valeurs séparées par des virgules.

   Les caractères ? et * peuvent être utilisés comme jokers pour remplacer un ou plusieurs caractères (DNS, port, etc.). Ainsi, la valeur **demo*** fonctionnera ainsi aussi bien avec &quot;https://demo&quot; que &quot;https://demo:8080&quot; ou encore &quot;https://demo2&quot;.

   Les noms utilisés doivent être définis dans votre DNS. Vous pouvez également informer la correspondance entre un nom DNS et une adresse IP dans le fichier **c:/windows/system32/drivers/etc/hosts** sous Windows et dans le fichier **/etc/hosts** sous Linux. Vous devez donc modifier les paramètres de connexion pour utiliser ce nom DNS afin de vous connecter à votre instance choisie.

   Le serveur doit être identifié par ce nom, notamment pour la mise en ligne des images dans les emails.

   En complément, le serveur doit pouvoir se connecter à lui-même par ce nom, et si possible via une adresse de bouclage (loopback) - 127.0.0.1 -, notamment pour permettre l&#39;export des rapports en PDF.

1. Dans la liste déroulante **[!UICONTROL Langue]**, sélectionnez la **langue de l&#39;instance** : anglais (US), anglais (UK) , français ou japonais.

   Les différences entre l’anglais américain et l’anglais britannique sont présentées dans [cette section](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >La langue de l&#39;instance ne peut plus être modifiée après cette étape. Les instances d&#39;Adobe Campaign ne sont pas multilingues : vous ne pouvez pas passer d&#39;une langue à une autre.

1. Cliquez sur **[!UICONTROL Ok]** pour valider la déclaration de l&#39;instance. Vous devez alors vous reconnecter pour procéder à la déclaration de la base de données.

   >[!NOTE]
   >
   >L’instance peut être créée à partir de la ligne de commande. For more on this, refer to [Command lines](../../installation/using/command-lines.md).

