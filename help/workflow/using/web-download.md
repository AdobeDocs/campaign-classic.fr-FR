---
product: campaign
title: Téléchargement Web
description: En savoir plus sur l'activité de workflow de téléchargement Web
feature: Workflows
hide: true
hidefromtoc: true
exl-id: b6005eae-5fbc-4e22-ab3a-c9b7ed6506f6
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: ht
source-wordcount: '538'
ht-degree: 100%

---

# Téléchargement Web{#web-download}



L&#39;activité de type **Téléchargement Web** permet de lancer le téléchargement d&#39;un fichier sur une URL explicite, un compte externe ou une instance Adobe Campaign. Le protocole utilisé est le HTTP. Il peut s&#39;agir d&#39;un téléchargement de type GET ou POST.

## Propriétés {#properties}

1. **Sélection du fichier web**

   Pour indiquer le fichier à télécharger, vous pouvez saisir directement l&#39;URL du fichier à télécharger, utiliser un compte HTTP externe où le fichier est stocké ou télécharger le fichier à partir d&#39;une instance Adobe Campaign. Les paramètres disponibles sont présentés ci-dessous :

   * Pour saisir directement l&#39;URL du fichier à télécharger, sélectionnez l&#39;option **[!UICONTROL URL explicite]** et indiquez l&#39;URL dans le champ correspondant. Cette URL peut être construite avec des données variables.

     ![](assets/download_web_edit.png)

   * Pour utiliser un **[!UICONTROL Compte externe]**, sélectionnez le compte dans la liste déroulante et indiquez le fichier à télécharger.

     Les comptes externes sont configurés à partir du nœud **[!UICONTROL Administration > Plateforme > Comptes externes]** de l’arborescence d’Adobe Campaign. Les paramètres du compte peuvent être modifiés à l’aide de l’icône **[!UICONTROL Modifier le lien]**.

     ![](assets/download_web_edit_external.png)

   * Pour télécharger le fichier depuis l&#39;instance Adobe Campaign, choisissez l&#39;option **[!UICONTROL Instance Adobe Campaign]**.

     ![](assets/download_web_edit_instance.png)

1. **Historisation des fichiers**

   Le lien **[!UICONTROL Paramètres d&#39;historisation des fichiers...]** permet d&#39;indiquer le répertoire de stockage des fichiers et la fréquence de purge de ce répertoire.

   ![](assets/download_web_edit_hist.png)

   Les options disponibles sont les suivantes :

   * **[!UICONTROL Utiliser un répertoire de stockage par défaut]** : le fichier est toujours déplacé avant d’être traité. Si cette option est cochée, le fichier est déplacé dans le répertoire de stockage par défaut (le répertoire **vars** du dossier d’installation d’Adobe Campaign). Pour spécifier un répertoire de stockage, décochez la case et saisissez le chemin de celui-ci dans le champ **[!UICONTROL Répertoire de stockage]**.
   * **[!UICONTROL Nombre de fichiers]** : saisissez le nombre maximal de fichiers à conserver dans le répertoire de stockage.
   * **[!UICONTROL Taille maximale (en Mo)]** : saisissez la capacité maximale du répertoire de stockage (en méga octets).

   Chaque fichier est toujours conservé 24 heures avant d’être soumis aux règles de purge définies. La purge a lieu juste avant le début du traitement de l’activité et ne prend donc pas en compte les fichiers du workflow en cours.

   Les fichiers sont toujours supprimés du plus ancien au plus récent. Les fichiers les plus anciens sont supprimés jusqu&#39;à ce que les deux règles de purge soient vérifiées. Ainsi, si une limite de 100 fichiers est définie, cela signifie que le répertoire de stockage contiendra toujours les 100 fichiers les plus récents avant le début du workflow, en plus des fichiers traités dans le workflow en cours.

   Si vous ne souhaitez pas définir de limite pour les options **[!UICONTROL Nombre de fichiers]** et **[!UICONTROL Taille maximale (en Mo)]**, saisissez la valeur 0.

1. **Paramètres avancés**

   Le lien **[!UICONTROL Paramètres avancés...]** permet d&#39;indiquer les options supplémentaires ci-dessous :

   * **[!UICONTROL Suivre les redirections]** : la redirection de fichier permet d’utiliser des remplacements pour diriger les entrées ou les sorties de données vers un périphérique d’un différent type.
   * **[!UICONTROL Ajouter des en-têtes HTTP au fichier]** : dans certains cas, vous pouvez ajouter des en-têtes HTTP supplémentaires à un fichier. Le plus souvent, ces en-têtes sont utilisés pour fournir des informations supplémentaires à des fins de résolution de problèmes, pour le [partage de ressources entre origines multiples (CORS)](https://developer.mozilla.org/fr/docs/Web/HTTP/CORS) ou pour définir des directives de mise en cache spécifiques.
   * **[!UICONTROL Ignorer le code de retour HTTP]** : les codes de retour HTTP, également appelés codes d’état HTTP, indiquent le résultat d’une requête HTTP.

   ![](assets/download_web_edit_advanced.png)

   L&#39;option **[!UICONTROL Traiter les erreurs]** est présentée dans la section [Traiter les erreurs](monitoring-workflow-execution.md#processing-errors).

## Paramètres de sortie {#output-parameters}

* filename : Nom complet du fichier téléchargé.
