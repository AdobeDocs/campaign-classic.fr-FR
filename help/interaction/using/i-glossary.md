---
product: campaign
title: Glossaire d’Interaction de Campaign
description: Glossaire d’Interaction de Campaign
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: interaction-overview
exl-id: 9e199b7c-9307-4797-bf86-7940388555bc
TQID: https://experienceleague.adobe.com/d6fevvmNur-4TC1KFM-09o68GnPFEM6S6SaFICwyCsw
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
subfeature_v2: []
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 1128
ht-degree: 56%

---

# Glossaire d’Interaction de Campaign{#i-glossary}



Voici la définition des éléments principaux d&#39;Interaction.

* **Environnement** : ensemble comprenant un catalogue d&#39;offres et des points d&#39;extension (emplacements). Vous devez créer un environnement par dimension de ciblage. Il existe deux types d’environnements :

   * **Environnement en édition** : environnement dans lequel les offres sont créées et/ou les règles de typologie sont définies (règles qui déterminent les offres à présenter ou non à une personne ciblée). La table des individus qui seront ciblés par les offres et la table destinée à stocker toutes les propositions d&#39;offres y sont également définies. Le nœud **[!UICONTROL Environnement en édition]** contient des sous-dossiers d&#39;emplacements, des filtres prédéfinis et des catégories d&#39;offres. Pour chaque **[!UICONTROL Environnement en édition]**, il existe un **[!UICONTROL Environnement en ligne]** correspondant, généré à partir de ce même **[!UICONTROL Environnement en édition]**.
   * **Environnement en ligne** : environnement associé à un **[!UICONTROL Environnement en édition]**. Il contient des offres en lecture seule dont le contenu et l’éligibilité ont été approuvés via l’**[!UICONTROL Environnement en édition]**. Elles sont destinées à être sélectionnées pour être présentées sur un site web ou insérées dans un message.

* Un **emplacement** désigne un dossier définissant l’emplacement d’exposition de l’offre. La définition d&#39;un emplacement permet à la fois d&#39;indiquer le canal utilisé, de spécifier s&#39;il est possible ou non de l&#39;utiliser en mode unitaire (par défaut : uniquement en mode batch), de construire le contenu de l&#39;offre par l&#39;intermédiaire de fonctions de rendu et de spécifier le thème des offres présentées. Un emplacement est une interface entre le canal et le moteur d&#39;offres.

  >[!IMPORTANT]
  >
  >Un emplacement n&#39;est pas un canal de communication, il correspond à un lieu d&#39;exposition spécifique sur le canal. Par exemple, les offres exposées sur un site web peuvent occuper deux emplacements sur la même page. Dans ce cas, nous aurons alors deux espaces pour le même canal.
  >
  >Les emplacements doivent être définis dans le cahier des charges et ne doivent pas être modifiés en cours de projet.

* **Catalogue d&#39;offres** : ensemble des offres définies dans Adobe Campaign pouvant être sélectionnées lors d&#39;une interaction. Le catalogue est organisé de manière hiérarchique avec chaque nœud correspondant à une catégorie.
* **Catégorie** : dossier lié au catalogue d&#39;offres dans un environnement, qui organise les offres en fonction de la nature, de la date d&#39;éligibilité et du thème de l&#39;application. Une catégorie peut contenir des sous-catégories qui héritent de toutes les caractéristiques de la catégorie parente. Les règles d&#39;éligibilité peuvent être définies pour une catégorie, de manière à les partager avec plusieurs offres.
* **Thèmes d&#39;application** : mots-clés définis au niveau de la catégorie qui permettent de filtrer les offres au moment de leur présentation sur un canal sortant ou entrant en restreignant la sélection des offres à une ou plusieurs catégorie(s).

  >[!NOTE]
  >
  >Les catégories enfants héritent des thèmes définis au niveau de la catégorie parent.

* **Règles d&#39;éligibilité** : contraintes appliquées à un environnement, à une catégorie ou à une offre, portant sur la période de validité, la cible et le poids. Elles permettent de s’assurer qu’une offre est en phase avec le contact ciblé.

  Au niveau des environnements, les règles d&#39;éligibilité comprennent les règles de présentation appliquées aux offres et les personnes à cibler.

  Dans les catégories, les règles d&#39;éligibilité permettent de limiter la validité de la catégorie dans le temps, de définir des thèmes d&#39;application et de déterminer les personnes à cibler. Ils peuvent également recevoir un poids multiplicateur pour une période donnée. Ainsi, les opérateurs peuvent partager les règles relatives aux offres d’autres catégories et ainsi simplifier leur gestion.

  Au niveau des offres, les règles d&#39;éligibilité permettent de limiter la validité des offres dans le temps et de déterminer les personnes à cibler.

* **Arbitrage** : sélection des offres qui seront présentées sur un emplacement (offres éligibles). Le principe de l’arbitrage permet de classer les offres par priorité en fonction des critères définis dans les catégories, les offres et les offres contextuelles.
* **Contact** : contact provenant d’une interaction entrante. Lors du traitement des appels au moteur, le contact est associé à une dimension de ciblage. Il existe deux types de contacts :

   * **[!UICONTROL Contact identifié]** : contact s’étant volontairement identifié sur le canal. Dans les interactions sortantes, le contact est automatiquement identifié.
   * **[!UICONTROL Contact anonyme]** : contact qui ne s’est pas volontairement inscrit sur le canal mais qui peut être identifié implicitement au moyen d’un cookie. Cette terminologie n’est utilisée que pour les interactions entrantes.

     >[!NOTE]
     >
     >Les contacts anonymes non identifiés sont rattachés à la dimension de ciblage des visiteurs.

* **Interaction sortante** : appel du moteur d&#39;interaction à partir d&#39;une liste de contacts (utilisée pour la diffusion d&#39;emails, de courrier, etc.). Les mêmes règles et processus sont appliqués à chaque contact. Ce type d&#39;interaction est généralement traité en mode batch.
* **Interaction entrante** : interaction faisant suite à un appel entrant généré par l’action d’un contact sur le canal. Ce type d&#39;interaction est généralement traité en mode unitaire.
* **Mode Lot** : le mode Lot permet de sélectionner la meilleure offre pour un ensemble de contacts. Les règles d&#39;éligibilité/priorisation sont appliquées à tous les contacts de l&#39;ensemble. Ce mode est généralement utilisé pour les interactions sortantes.
* **Mode unitaire** : un seul contact est traité à la fois. Ce mode est généralement utilisé pour les interactions entrantes et les messages transactionnels.
* **Mode d&#39;identification** : il se réfère au statut d&#39;un contact.

   * **[!UICONTROL explicite]** : le contact est identifié, il s’est authentifié sur l’interface du canal.
   * **[!UICONTROL implicite]** : le contact a été identifié par un cookie (de session ou permanent). Ils peuvent être traités comme des contacts anonymes ou identifiés.
   * **[!UICONTROL anonyme]** : le contact n&#39;a pas pu être identifié.

* **Offre éligible** : offre répondant à des contraintes définies en amont pouvant être proposée de façon cohérente à une cible.
* **Règles de présentation** : règles de typologie référencées au niveau de l&#39;environnement d&#39;offres permettant d&#39;exclure certaines offres en tenant compte de l&#39;historique des propositions.
* **Poids** : formules permettant de calculer précisément la pertinence d&#39;une offre, afin de sélectionner l&#39;offre la plus pertinente. Les poids sont définis dans les offres. Les offres éligibles sont prises en compte dans l’ordre de poids décroissant.
* **Fonction de rendu** : fonction définie au niveau de l&#39;emplacement permettant de construire la représentation de l&#39;offre pour ce même emplacement à partir d&#39;attributs définis au niveau de l&#39;offre. Il existe trois modes de fonction de rendu différents : HTML, XML et texte.
* **Proposition d&#39;offre** : résultat de l&#39;action qui consiste à présenter une ou plusieurs offres à un contact sur un emplacement donné (une bannière sur un site web, un email ou un SMS par exemple). Ce résultat est stocké dans la table des propositions d&#39;offre. Toutefois, il n’est pas obligatoire d’enregistrer les propositions.
* **Simulation** : module permettant de tester la présentation d&#39;offres auprès des personnes à cibler avant de procéder à la véritable présentation.
* **Aperçu** : aperçu de l&#39;offre telle qu&#39;elle est affichée dans son dossier. Il est accessible à partir de la fenêtre de paramétrage des offres ou du profil du contact.
* **Filtres prédéfinis** : règles de filtrage prédéfinis pouvant prendre en compte des paramètres d&#39;une offre (par exemple le code de l&#39;offre). Ils peuvent être réutilisés après la création des offres.
* **Représentation de l’offre** : informations utilisées par le canal pour afficher l’offre. La représentation de l’offre peut être construite à partir de la fonction de rendu de l’emplacement sur lequel l’offre est représentée ou saisie directement dans l’interface (par exemple, dans le bloc HTML). Une offre peut être représentée par un emplacement.
* **Processus de basculement** : processus activé dans un environnement identifié, chargé de diriger l&#39;appel vers un environnement anonyme si le contact n&#39;a pas pu être identifié explicitement et/ou implicitement.
