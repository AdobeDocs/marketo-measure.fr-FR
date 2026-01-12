---
description: Intégration des activités [!DNL Marketo Engage] - [!DNL Marketo Measure]
title: Intégration des activités [!DNL Marketo Engage]
exl-id: 463ad9b2-e1bd-49dd-8bf5-0da7b7132f05
feature: Integration
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '1737'
ht-degree: 1%

---


# Intégration des activités [!DNL Marketo Engage] {#marketo-engage-activities-integration}

Dans le cadre de l’intégration globale des [!DNL Marketo Measure] et des [!DNL Marketo Engage], cet effort pour intégrer les activités Marketo joue un rôle considérable. Grâce aux activités Marketo, le système effectue le suivi d’événements tels que des `Click Email`, des `Change Score` ou des `Change Status in Progression`. Ces types d’activités peuvent être réduits et définis afin de sélectionner un sous-ensemble éligible pour les points de contact. Une fois les points de contact créés sur ces activités, ils sont suivis dans le parcours d’engagement et mesurés avec vos autres canaux marketing tels que le référencement payant ou le marketing partenaire.

## Exigences {#requirements}

* Instance de Marketo de production
* [!DNL Salesforce] de production ou instance de [!DNL Microsoft Dynamics]
* Tout abonnement [!DNL Marketo Measure] payant
* Synchronisation des personnes Marketo activée (paramètres [!DNL Marketo Measure])
* Programmes Marketo activés (paramètres [!DNL Marketo Measure])
* Activités Marketo activées (paramètres [!DNL Marketo Measure])

## Configuration {#setup}

1. Pour commencer à configurer les activités Marketo, accédez à **Mon compte** > **Paramètres** > **Activités**.

   ![Page des paramètres des activités dans le compte Marketo Measure](assets/one-1.png)

   ![Écran de configuration des activités avec sélection du type d’activité](assets/two-1.png)

   La première chose à faire est de sélectionner la liste des types d’activités sur lesquels vous prévoyez de créer des règles. Il n’y a pas un nombre fixe de types d’activité requis, mais il est recommandé de ne pas surcharger vos points de contact et de ne pas diluer l’importance des jalons importants. Cela dit, vous n’avez peut-être pas besoin de plus de cinq types d’activités pour effectuer le suivi des engagements pertinents.

1. Cliquez sur le menu déroulant sous [!UICONTROL Sélectionner les types d’activités] pour commencer à choisir les différents types.

   ![Menu déroulant affichant les types d’activité Marketo disponibles](assets/three-1.png)

1. Lorsque toutes les activités dont vous avez besoin sont sélectionnées, elles sont renseignées dans votre [!UICONTROL Liste des activités sélectionnées] et sous [!UICONTROL Définir des règles].

   ![Liste des activités sélectionnées affichant les types d’activités sélectionnés](assets/four-1.png)

1. Pour chaque type d’activité, vous devez définir une ou plusieurs règles qui déterminent les enregistrements éligibles aux points de contact. Dans cet exemple, nous ajoutons une règle pour le type d’activité « Modifier le score » afin que le système crée un point de contact lorsqu’une personne Marketo atteint un score de 90 ou plus.

1. Tout d’abord, en fonction du type d’activité, vous devrez peut-être configurer un nom de campagne [!DNL Marketo Measure] qui pourra être utilisé ultérieurement pour le mapping de canaux. [!DNL Marketo Measure] noms de campagne peuvent être réutilisés dans plusieurs règles. Cela permet d’avoir des noms plus larges qui peuvent être utilisés dans une règle de canal unique. Tous les types d’activités ne contiennent pas de programme Marketo, c’est pourquoi cette première étape nécessite un nom.

   Voici un exemple de ce à quoi cette étape supplémentaire ressemblerait :

   ![Champ de configuration du nom de la campagne pour la règle d’activité](assets/five-1.png)

1. Dans l’exemple « Modifier le score », il est nécessaire de saisir un nom de campagne, car ces informations sont extraites du programme Marketo. Créez maintenant l’expression de règle. En suivant cet exemple, sélectionnez le champ « [!UICONTROL Nouvelle valeur] » avec un opérateur « [!UICONTROL est supérieur à] » avec une valeur de 90.

   Vous pouvez développer les règles et ajouter des filtres ou des critères supplémentaires en ajoutant des instructions « and » ou « or » pour limiter les résultats.

   ![Créateur de règles pour l’activité Modifier le score avec la sélection de champs et d’opérateurs](assets/six-1.png)

   ![Expression de règle affichant la condition Nouvelle valeur supérieure à 90](assets/seven-1.png)

1. Enfin, choisissez les éléments à utiliser comme date de point de contact. Tous les champs de date ou date/heure disponibles apparaissent ici à partir de Marketo. À moins que vous ne disposiez de champs de date personnalisés, vous verrez « [!UICONTROL Date de l’activité] ».

   ![ Sélecteur de champ de date de point de contact affichant l’option Date de l’activité ](assets/eight-1.png)

1. Veillez à cliquer sur **[!UICONTROL Enregistrer comme brouillon]** tout au long du processus pour ne pas perdre vos modifications.

   ![Bouton Enregistrer comme brouillon dans la configuration des règles d’activité](assets/nine-1.png)

1. Accédez à l’onglet **[!UICONTROL Mappage des attributs]**.

   ![Onglet Mappage des attributs dans les paramètres des activités](assets/ten-1.png)

1. Pour chaque type d’activité sélectionné, vous avez la possibilité de mapper des attributs Marketo supplémentaires aux champs de point de contact afin de pouvoir afficher et générer des rapports sur ces valeurs dans [!DNL Marketo Measure Discover] ou dans le CRM.

   La plupart des champs ont été automatiquement mappés et ne peuvent pas être modifiés afin d’être cohérents avec nos autres intégrations. Consultez la section Mappages de champs ci-dessous pour trouver ces valeurs. Pour certains types d’activité, Marketo inclut des attributs pour une page de destination, une page de référent ou un navigateur que vous pouvez éventuellement mapper à un champ de point de contact. Dans l’exemple ci-dessous, nous avons fait quelques suggestions supplémentaires qui peuvent être supprimées.

1. Sélectionnez le champ Buyer Touchpoint de la colonne de gauche que vous souhaitez mapper. Choisissez ensuite l’attribut Marketo à renseigner dans le champ Buyer Touchpoint . N’oubliez pas qu’il s’agit de mappages supplémentaires facultatifs, en plus de ceux que [!DNL Marketo Measure] a déjà établis.

   Champs Mappables :

   * Ville
   * Pays
   * Région
   * Page de destination
   * Page du référent
   * Page du formulaire
   * Date du formulaire
   * Platform
   * Navigateur

   >[!NOTE]
   >Les champs d’annonce tels que Contenu de l’annonce ou Mot-clé ne sont pas disponibles dans cette liste, car ils sont réservés à nos intégrations de plateforme publicitaire.

## Types d’activité {#activity-types}

Certains types d’activités nous fournissent l’ID de programme et le nom du programme. Il est donc facile de les mapper à l’ID de campagne et au nom de campagne sur le Buyer Touchpoint. Pour les autres, il n’existe aucune association de programme, de sorte qu’une partie de la définition des règles exige que vous créiez un nom de campagne [!DNL Marketo Measure]. Voici les listes de chaque catégorie :

**Types d’activités avec ID de programme**

Envoyer un courrier électronique (6)\
E-mail diffusé (7)\
E-mail non remis (8)\
E-mail de désabonnement (9)\
Ouvrir un e-mail (10)\
E-mail de clic (11)\
Modifier la valeur des données (13)\
Modifier le score (22)\
Ajouter à la liste (24)\
Changement de statut en progression (104)\
Ajouter à la culture (113)\
Changer le rythme de maturation (115)

>[!NOTE]
>Parmi les types d’activité pour lesquels un ID de programme est attendu, si une activité est détectée sans programme, [!DNL Marketo Measure] ne l’acceptera pas comme point de contact éligible, car les valeurs de campagne ne peuvent pas être nulles.

**Types d’activités sans ID de programme**

Clic sur le lien (3)\
Nouveau prospect (12)\
Synchroniser le prospect avec SFDC (19)\
Convertir le lead (21)\
Changer de propriétaire (23)\
Retirer de la liste (25)\
Activité SFDC (26)\
E-mail non remis (27)\
Supprimer le lead de SFDC (29)\
Fusionner les leads (32)\
Ajouter à l’opportunité (34)\
Supprimer de l’opportunité (35)\
Mettre à jour l’opportunité (36)\
Supprimer le lead (37)\
Envoyer une alerte (38)\
Envoyer un e-mail commercial (39)\
Ouvrir l&#39;e-mail de vente (40)\
Cliquez sur E-mail de vente (41)\
Ajouter à SFDC Campaign (42)\
Supprimer de SFDC Campaign (43)\
Changement de statut dans SFDC Campaign (44)\
Recevoir un e-mail de vente (45)\
Campagne de demande (47)\
E-mail de rebond de vente (48)\
Étape Modifier le chiffre d’affaires (101)\
Modifier Manuellement L’Étape De Revenu (102)\
Modifier le segment (108)\
Appeler Webhook (110)\
E-mail transféré à un ami (111)\
E-mail de transfert à un ami reçu (112)\
Changer de piste de maturation (114)\
Intégrer le lead à Marketo (145)\
Synchroniser le prospect avec Microsoft (300)\
Partage de contenu (400)
Boîte de dialogue engagée (158)
Document Avec Lequel Nous Avons Interagi (159)
Rendez-Vous De Boîte De Dialogue Planifié (160)
Objectif De Dialogue Atteint (161)
Activité personnalisée (xxx)

## Mappage de canal {#channel-mapping}

Pour toutes les règles d’un type d’activité avec un ID de programme, le canal du programme Marketo est déterminé à partir du programme. Nous utilisons le canal de programme pour mapper vos canaux hors ligne personnalisés. Vous devez donc vous assurer que vos canaux sont configurés correctement [comme indiqué ici](/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/marketo-engage-programs-integration.md#channel-mapping){target="_blank"}.

Et pour n’importe quelle règle d’un type d’activité sans ID de programme, votre première étape a été de créer un nom de campagne. Utilisez ce nom de campagne pour configurer vos canaux en ligne personnalisés [présentés ici](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md){target="_blank"}.

Si les canaux de vos activités Marketo ne sont pas correctement configurés, il est probable que vos nouveaux points de contact se trouvent sous le canal « Autre ».

## Coûts du programme {#program-costs}

Grâce à l’importation des données des programmes Marketo, les coûts sont automatiquement téléchargés à partir des coûts de la période et les coûts signalés dans Marketo sont répartis tout au long du mois attribué. Par exemple, si 1 000 $ sont déclarés pour janvier 2021, les 1 000 $ sont répartis sur 31 jours. Les coûts se trouvent à [!DNL Marketo Measure Discover].

## Mappage des cookies {#cookie-mapping}

Suite à l’intégration d’[!DNL Marketo Measure] à Marketo, l’ID de cookie [!DNL Marketo Measure] est désormais également mappé et synchronisé avec le [!DNL Marketo Munchkin Id]. Cela permet de combler l’écart afin d’attribuer le premier contact anonyme à une session web plutôt que d’attribuer les contacts FT et LC à une activité Marketo. Imaginez ce scénario :

Mark clique sur une annonce Facebook et arrive sur wayneenterprises.com où il obtient un cookie avec les [!DNL Marketo Measure] ID 123 et [!DNL Marketo Munchkin Id] 456. Aucun remplissage de formulaire n’a lieu.

L’équipe marketing de Wayne Enterprises envoie une grosse quantité d’e-mails à des prospects ciblés spécifiques, dont l’un est `mark@email.com`.

`mark@email.com` reçoit l’e-mail et clique sur et accède à `wayneenterprises.com`. Cela devient `mark@email.com's` deuxième visite pour `wayneenterprise.com` avec les mêmes ID de cookie, mais il n’y avait pas de remplissage de formulaire, donc pour [!DNL Marketo Measure], ils sont toujours un visiteur anonyme.

L’équipe marketing Wayne Enterprises crée une règle d’activité Marketo pour générer des points de contact pour un type d’activité « Cliquer sur l’e-mail ».

L’implémentation d’aujourd’hui créerait un seul point de contact FT et LC pour les `mark@email.com` de l’activité Marketo à partir du type d’activité « Cliquer sur l’e-mail ».

Grâce à cette amélioration du mappage des cookies, le FT retournerait en arrière et serait crédité à la publicité Facebook et le LC serait crédité à l’e-mail.

>[!NOTE]
>Avec le comportement de mappage des cookies, vous pouvez trouver certains points de contact LC qui proviennent d’une visite web. Il est possible qu’un prospect se soit affiché dans Marketo sans activité associée, puis [!DNL Marketo Measure] téléchargé ce prospect, qu’il corresponde aux cookies associés, puis qu’il soit tracé jusqu’à la session web la plus récente, même s’il n’y avait aucune activité de formulaire à l’origine du prospect.

## Questions fréquentes {#faq}

**Comment savoir s’il faut créer une règle Programmes Marketo ou une règle Activités Marketo ?**

L’intégration des programmes [!DNL Marketo Engage] est un moyen simple de générer des points de contact en fonction du statut de membre de programme d’une personne. Si vous souhaitez définir une règle basée sur le moment où une personne passe à un statut de programme particulier, l’intégration des activités [!DNL Marketo Engage] correspond à la configuration souhaitée, en particulier le type d’activité « Changement de statut en cours » afin que la date du point de contact puisse être mise en correspondance avec la date de l’activité générée par le système.

**Pourquoi le nom de mon type de point de contact est-il tronqué ?**

Le champ Type de point de contact a été créé dans le package [!DNL Marketo Measure] avec 16 caractères. Malheureusement, la modification de la limite de caractères du champ nécessiterait l’obsolescence du champ existant et la création d’un champ. La valeur du type de point de contact est le type d’activité, qui est également défini dans le champ Medium .

**Pourquoi mon type d’activité personnalisé n’apparaît-il pas dans la liste des activités disponibles ?**

Nous affichons uniquement les types d’activité personnalisés « Approuvé », et non les activités Brouillon ou Approuvé avec brouillon.

**Comment puis-je déterminer pour quels types d’activités je souhaite générer un point de contact ?**

Bien qu’il n’y ait pas de limite au nombre de types d’activités que vous pouvez créer, nous vous recommandons généralement de ne pas en créer plus de cinq. Il faut du temps pour déterminer les activités marketing suffisamment pertinentes pour faire partie du parcours de points de contact. Par exemple, « Désabonner l’e-mail » peut ne pas être un point de contact important à suivre, mais « Cliquer sur l’e-mail » avec des filtres supplémentaires peut être un bon point de contact. Cela varie d&#39;une organisation à l&#39;autre et d&#39;une équipe à l&#39;autre. Nous vous suggérons donc de travailler avec votre équipe pour réfléchir à la meilleure approche.

**Pourquoi mon nom de navigateur est-il coupé ?**

Le nom du navigateur [!DNL Marketo Measure] est limité à 20 caractères, bien que la valeur de l’agent utilisateur que nous obtenons de Marketo ait tendance à être une chaîne plus longue.

BrowserInfo.Name\
BrowserInfo.Version\
PlatformInfo.Name\
PlatformInfo.Version
