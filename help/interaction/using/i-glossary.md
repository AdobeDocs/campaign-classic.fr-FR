---
product: campaign
title: Glossaire d’Interaction de Campaign
description: Glossaire d’Interaction de Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: interaction-overview
exl-id: 9e199b7c-9307-4797-bf86-7940388555bc
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1122'
ht-degree: 100%

---

# Glossaire d’Interaction de Campaign{#i-glossary}



Voici la définition des éléments principaux d&#39;Interaction.

* **Environnement** : ensemble regroupant un Catalogue d&#39;offres et des points d&#39;intégration (emplacements). Vous devez créer un environnement par dimension de ciblage. Il existe deux types d&#39;environnements :

   * **Environnement en édition** : environnement dans lequel sont créées les offres et où sont définies les règles de typologie qui vont déterminer les offres à présenter ou non à une personne ciblée. La table des individus qui seront ciblés par les offres et la table destinée à stocker toutes les propositions d&#39;offres y sont également définies. Le nœud **[!UICONTROL Environnement en édition]** contient les sous-dossiers des emplacements, des filtres prédéfinis et des catégories d&#39;offres. À chaque **[!UICONTROL Environnement en édition]** correspond un **[!UICONTROL Environnement en ligne]** en lecture seule, généré à partir de ce même **[!UICONTROL Environnement en édition]**.
   * **Environnement en ligne** : environnement associé à un **[!UICONTROL Environnement en édition]**. Il contient des offres en lecture seule dont le contenu et l&#39;éligibilité ont été validés à partir de l&#39;**[!UICONTROL Environnement en édition]**. Elles sont destinées à être sélectionnées pour être présentées sur un site web ou insérées dans un message.

* **Emplacement** : dossier définissant les lieux d&#39;exposition de l&#39;offre. La définition d&#39;un emplacement permet à la fois d&#39;indiquer le canal utilisé, de spécifier s&#39;il est possible ou non de l&#39;utiliser en mode unitaire (par défaut : uniquement en mode batch), de construire le contenu de l&#39;offre par l&#39;intermédiaire de fonctions de rendu et de spécifier le thème des offres présentées. Un emplacement est une interface entre le canal et le moteur d&#39;offres.

   >[!IMPORTANT]
   >
   >Un emplacement n&#39;est pas égal à un canal de communication, il correspond à un lieu d&#39;exposition sur un canal. Par exemple, des offres exposées sur un site web peuvent occuper deux emplacements dans une même page. Dans ce cas, on aura donc deux emplacements pour le même canal.
   >
   >Les emplacements doivent être définis dans le cahier des charges et ne doivent pas être modifiés en cours de projet.

* **Catalogue d&#39;offres** : ensemble des offres définies dans Adobe Campaign pouvant être sélectionnées lors d&#39;une interaction. Le catalogue a une organisation hiérarchique dont chaque noeud est une catégorie.
* **Catégorie** : dossier relié au Catalogue d&#39;offres d&#39;un environnement, destiné à organiser les offres selon leur nature, leurs dates d&#39;éligibilité et leurs thèmes d&#39;application. Une catégorie peut contenir d&#39;autres sous-catégories qui hériteront de toutes les caractéristiques définies au niveau de la catégorie parent. Des règles d&#39;éligibilité peuvent être définies au niveau d&#39;une catégorie, afin notamment de les mutualiser pour plusieurs offres.

* **Thèmes d&#39;application** : mots-clés définis au niveau de la catégorie qui permettent de filtrer les offres au moment de leur présentation sur un canal sortant ou entrant en restreignant la sélection des offres à une ou plusieurs catégorie(s).

   >[!NOTE]
   >
   >Les catégories enfants héritent des thèmes définis au niveau de la catégorie parent.

* **Règles d&#39;éligibilité** : contraintes appliquées à un environnement, à une catégorie ou à une offre, portant sur la période de validité, les personnes à cibler et le poids. Elles permettent de s&#39;assurer qu&#39;une offre est en adéquation avec un contact ciblé.

   Au niveau des environnements, les règles d&#39;éligibilité comprennent les règles de présentation appliquées aux offres et les personnes à cibler.

   Au niveau des catégories, les règles d&#39;éligibilité permettent de limiter la validité de la catégorie dans le temps, de définir des thèmes d&#39;application et de déterminer les personnes à cibler. Elles peuvent également recevoir un poids multiplicateur pendant une période donnée. Cela permet de mutualiser les règles pour les offres d&#39;une même catégorie et ainsi d&#39;en simplifier la gestion.

   Au niveau des offres, les règles d&#39;éligibilité permettent de limiter la validité des offres dans le temps et de déterminer les personnes à cibler.

* **Arbitrage** : étape de sélection des offres qui seront présentées sur un emplacement (offres éligibles). Le principe d&#39;arbitrage est de classer les offres par priorité, en prenant en compte les poids définis au niveau des offres et des catégories.
* **Contact** : contact à l&#39;origine d&#39;une interaction entrante. Lors du traitement de l&#39;appel au moteur, le contact est associé à une dimension de ciblage. On distingue deux types de contacts :

   * **[!UICONTROL Contact identifié]** : contact s&#39;étant volontairement identifié sur le canal. Dans les interactions sortantes, le contact est systématiquement identifié.
   * **[!UICONTROL Contact anonyme]** : contact qui ne s&#39;est pas volontairement inscrit sur le canal mais qui peut être identifié implicitement au moyen d&#39;un cookie. Cette terminologie n&#39;a lieu d&#39;être que dans le cadre d&#39;interactions entrantes.

      >[!NOTE]
      >
      >Les contacts anonymes non identifiés sont rattachés à la dimension de ciblage des visiteurs.

* **Interaction sortante** : appel du moteur d&#39;interaction à partir d&#39;une liste de contacts (mails, courrier, etc.). Les mêmes règles et processus sont appliqués à chaque contact. Ce type d&#39;interaction est généralement traité en mode batch.
* **Interaction entrante** : interaction faisant suite à un appel entrant généré par une action d&#39;un contact sur le canal. Ce type d&#39;interaction est généralement traité en mode unitaire.
* **Mode batch** : le mode batch permet de sélectionner la meilleure offre pour un ensemble de contacts. Les règles d&#39;éligibilité/priorisation sont appliquées à l&#39;ensemble des contacts. Ce mode est généralement utilisé pour les interactions sortantes.
* **Mode unitaire** : un seul contact est traité à la fois. Ce mode est généralement utilisé pour les interactions entrantes et pour les messages transactionnels.
* **Mode d&#39;identification** : il se réfère au statut d&#39;un contact.

   * **[!UICONTROL explicite]** : le contact est identifié, il s’est authentifié sur l’interface du canal.
   * **[!UICONTROL implicite]** : le contact a été identifié par un cookie (de session ou permanent). Il peut être traité comme un contact anonyme ou comme un contact identifié.
   * **[!UICONTROL anonyme]** : le contact n&#39;a pas pu être identifié.

* **Offre éligible** : offre répondant à des contraintes définies en amont pouvant être proposée de façon cohérente à une cible.
* **Règles de présentation** : règles de typologie référencées au niveau de l&#39;environnement d&#39;offres permettant d&#39;exclure certaines offres en tenant compte de l&#39;historique des propositions.
* **Poids** : formules permettant de calculer précisément la pertinence d&#39;une offre pour une personne afin de départager plusieurs offres auxquelles cette personne est éligible. Les poids sont définis au niveau des offres. La sélection prend en compte les offres éligibles par ordre de poids décroissant.
* **Fonction de rendu** : fonction définie au niveau de l&#39;emplacement permettant de construire la représentation de l&#39;offre pour ce même emplacement à partir d&#39;attributs définis au niveau de l&#39;offre. Trois modes de fonctions de rendu existent : HTML, XML et texte.
* **Proposition d&#39;offre** : résultat de l&#39;action qui consiste à présenter une ou plusieurs offres à un contact sur un emplacement donné (une bannière sur un site web, un email ou un SMS par exemple). Ce résultat est stocké dans la table des propositions d&#39;offre. Il n&#39;est cependant pas obligatoire de stocker les propositions.
* **Simulation** : module permettant de tester la présentation d&#39;offres auprès des personnes à cibler avant de procéder à la véritable présentation.
* **Prévisualisation** : aperçu de l&#39;offre telle qu&#39;elle apparaîtra dans son emplacement. La prévisualisation d&#39;une offre est accessible depuis la fenêtre de paramétrage des offres ou le profil d&#39;un contact.
* **Filtres prédéfinis** : règles de filtrage prédéfinis pouvant prendre en compte des paramètres d&#39;une offre (par exemple le code de l&#39;offre). Ils peuvent être réutilisés lors de la création des offres.
* **Représentation d&#39;offre** : information exploitée par le canal afin d&#39;afficher l&#39;offre. La représentation d&#39;une offre peut être construite à partir de la fonction de rendu de l&#39;emplacement sur lequel l&#39;offre est représentée ou saisie directement dans l&#39;interface (par exemple : dans le bloc HTML). Une offre peut avoir une représentation par emplacement.
* **Processus de basculement** : processus activé dans un environnement identifié, chargé de diriger l&#39;appel vers un environnement anonyme si le contact n&#39;a pas pu être identifié explicitement et/ou implicitement.
