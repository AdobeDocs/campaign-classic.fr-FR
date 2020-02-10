---
title: Collecteur de fichiers
seo-title: Collecteur de fichiers
description: Collecteur de fichiers
seo-description: null
page-status-flag: never-activated
uuid: 57ef7b2b-f257-4d76-970f-55aece719cec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: 9b937d4d-55ae-4bd4-8dc6-eea42f15b69f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Collecteur de fichiers{#file-collector}

Le collecteur **de** fichiers surveille l’arrivée d’un ou de plusieurs fichiers dans un répertoire et active sa transition pour chaque fichier reçu. Pour chaque événement, une **[!UICONTROL filename]** variable contient le nom complet du fichier reçu. Les fichiers collectés sont déplacés vers un autre répertoire à des fins d’archivage et pour être sûrs qu’ils ne sont comptabilisés qu’une seule fois.

Par défaut, le collecteur de fichiers est une tâche persistante testant la présence de fichiers aux heures spécifiées par le planning.

Les fichiers doivent se trouver sur le serveur sur lequel s&#39;exécute le module wfserver qui prend en charge ce workflow. Si plusieurs modules wfserver sont déployés sur une même instance, il faut spécifier soit l&#39;affinité des activités utilisant ces fichiers, soit l&#39;affinité globale du workflow.

## Propriétés {#properties}

Le premier onglet de l’ **[!UICONTROL File collector]** activité vous permet de sélectionner le répertoire source et, si nécessaire, de filtrer les fichiers collectés. Les autres onglets sont détaillés dans les Courriers électroniques [](../../workflow/using/inbound-emails.md) entrants (**[!UICONTROL Schedule]** et **[!UICONTROL Expiry]** ).

![](assets/file_collect_edit.png)

1. **Récupération des fichiers**

   * **[!UICONTROL Directory]**

      Répertoire contenant le ou les fichiers à récupérer. Ce répertoire doit être créé au préalable sur le serveur : s&#39;il n&#39;existe pas, une erreur est générée.

   * **[!UICONTROL Filter]**

      Seuls les fichiers correspondant à ce filtre sont pris en compte. Les autres fichiers du répertoire sont ignorés. Si le filtre est vide, tous les fichiers du répertoire sont pris en compte. Exemples de filtrage : ***.zip**, **import-*.txt**.

   * **[!UICONTROL Stop as soon as a file has been processed]**

      Si cette option est activée, la tâche se termine après réception du premier fichier. Si plusieurs fichiers correspondant au filtre sont présents dans le répertoire, un seul sera pris en compte. Cette option garantit qu&#39;un seul événement sera émis. Le fichier pris en compte est le premier de la liste dans l&#39;ordre alphabétique.

      For an unscheduled activity, if no file matching the filter is found in the specified directory, and if the **[!UICONTROL Process file nonexistence]** option is not enabled, an error will be raised.

   * **[!UICONTROL Execution schedule]**

      Determines the frequency of the file presence check via the parameters of the **[!UICONTROL Schedule]** tab.

1. **Traitement des erreurs**

   Les deux options suivantes sont disponibles :

   * **[!UICONTROL Process file nonexistence]**

      Cette option fait apparaître une transition particulière qui sera activée à chaque vérification de présence de fichier si aucun fichier correspondant au filtre n&#39;est trouvé dans le répertoire spécifié.

      Si la tâche n&#39;est pas planifiée, cette transition sera activée une seule fois.

   * **[!UICONTROL Processing errors]**

      Cette option fait apparaître une transition particulière qui sera activée si une erreur est générée. Dans ce cas, le workflow ne passe pas en état d&#39;erreur et continue son exécution.

      Les erreurs prises en compte sont les erreurs du système de fichiers (impossible de déplacer un fichier, impossible d&#39;accéder au répertoire, etc.).

      Cette option ne traite pas les erreurs liées au paramétrage de l&#39;activité, c&#39;est-à-dire des valeurs invalides.

1. **Historisation**

   Reportez-vous à l’ **[!UICONTROL File historization]** étape suivante : Téléchargement [Web](../../workflow/using/web-download.md).

Impossible de déterminer l&#39;ordre de traitement du fichier. Pour traiter un ensemble de fichiers de manière séquentielle, utilisez l’ **[!UICONTROL Stop as soon as a file has been processed]** option et créez une boucle. Dans ce cas, les fichiers seront traités par ordre alphabétique. L’ **[!UICONTROL Process file nonexistence]** option vous permet de terminer l’itération.

![](assets/file_collect_loop.png)

## Paramètres de sortie {#output-parameters}

* filename

Nom complet du fichier. C&#39;est le nom du fichier après son déplacement dans le répertoire d&#39;historique. Le chemin est donc différent, mais le nom est également différent s&#39;il existe déjà un autre fichier ayant le même nom dans le répertoire. L&#39;extension est conservée.
