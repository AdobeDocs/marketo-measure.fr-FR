---
description: Conseils sur les coûts des canaux marketing pour les utilisateurs de Marketo Measure
title: Coûts associés aux canaux marketing
exl-id: 36ccaff3-db55-47bd-a24e-4aa1894f13e0
feature: Channels, Spend Management
hidefromtoc: true
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '1327'
ht-degree: 1%

---

# Coûts associés aux canaux marketing {#marketing-channel-costs}

L’un des avantages les plus fondamentaux de l’utilisation de [!DNL Marketo Measure] est la possibilité de relier les efforts de marketing directement à l’impact sur le chiffre d’affaires, avec autant de granularité que souhaité. Il est possible de voir le retour sur investissement au niveau du point de contact. Pour tirer parti de cet avantage, les coûts de canal doivent être chargés sur l’application [!DNL Marketo Measure]. Les rapports sur le retour sur investissement sont automatiquement créés et disponibles dans le **tableau de bord du retour sur investissement marketing** dans [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}.

[Cliquez ici pour accéder directement aux instructions.](/help/marketing-channel-costs.md)

La fonctionnalité Dépenses de marketing [!DNL Marketo Measure] permet aux clients de charger leurs dépenses sur tous les canaux, sous-canaux et campagnes. Plus la quantité de données ajoutées par les clients est élevée, plus le compte rendu des performances sur investissement est affiché dans le tableau de bord d’attribution des revenus.

Les coûts signalés et importés à partir de connexions d’annonces directes sont automatiquement extraits au niveau le plus granulaire et n’ont pas besoin d’être chargés. Cela inclut nos intégrations actuelles à Google AdWords, Bing Ads, Doubleclick et Facebook.

[Cliquez ici pour accéder directement à la FAQ.](/help/marketing-channel-costs.md)

## Définitions {#definitions}

**Dépenses par campagne**

Au niveau le plus granulaire, les clients peuvent saisir les dépenses par campagne individuelle, regroupée dans leur canal respectif. Pour les campagnes CRM, [!DNL Marketo Measure] a intégré l’identifiant de campagne dans une colonne distincte qui vous permet de mapper les dépenses de campagne hors ligne de votre CRM dans ce tableau. Ajouter des dépenses à ce niveau permet aux clients d’afficher le retour sur investissement de la campagne et d’optimiser les performances par campagne.

Le total de toutes les campagnes ne doit pas nécessairement totaliser les valeurs saisies au niveau du sous-canal ou du canal, mais il ne peut pas être supérieur aux valeurs saisies au niveau du sous-canal ou du canal. Si la somme est inférieure à la valeur saisie au niveau du sous-canal ou du canal, [!DNL Marketo Measure] ajoutera automatiquement une ligne pour « Autre » pour couvrir la différence et remplir les trous.

**Dépenses par sous-canal**

À un niveau supérieur, les clients peuvent saisir les dépenses par sous-canal, regroupées sous son canal. Ajouter des dépenses à ce niveau permet aux clients d’afficher le retour sur investissement du sous-canal et d’optimiser les performances par sous-canal.

Le total de tous les sous-canaux n’a pas besoin de faire la somme des valeurs saisies dans le canal, mais il ne peut pas être supérieur à toutes les valeurs saisies dans le canal. Si la somme est inférieure à la valeur saisie dans le canal, [!DNL Marketo Measure] ajoutera automatiquement une ligne pour « Autre » pour couvrir la différence et remplir les trous.

**Dépenses par canal**

Au niveau le plus élevé, les clients peuvent saisir les dépenses par canal. Ajouter des dépenses à ce niveau permet aux clients d’afficher le retour sur investissement du canal et d’optimiser les performances par canal.

**Sélecteur de date**

La période par défaut commence à partir de votre date de début ([!DNL Marketo Measure] jusqu’au mois en cours). Pour vous assurer que les coûts restent corrects, vous ne pouvez pas entrer de coûts pour les mois à venir, mais vous pouvez entrer des coûts pour les mois précédant votre partenariat avec [!DNL Marketo Measure].

**Filtrer**

Pour affiner vos résultats dans le tableau Dépenses marketing , sélectionnez un canal en haut pour filtrer les autres canaux. Cela s’avère utile lorsque vous avez une équipe axée sur un seul canal.

**Recherche**

Utilisez la zone de recherche pour rechercher du texte correspondant à partir des canaux, sous-canaux ou campagnes.

**Télécharger les coûts actuels**

Le fichier CSV téléchargé extrait les résultats de votre écran actuel, ce qui signifie que toutes les dates, tous les filtres ou toutes les recherches appliqués seront téléchargés en l’état.

**Charger CSV**

Quelle que soit la vue du navigateur, s’il s’agit d’une vue filtrée ou de la vue par défaut avec toutes les dates et tous les canaux, vous pouvez charger n’importe quel fichier CSV.

L’erreur la plus courante est le format des colonnes de dates, qui se produit si le format de date est modifié et qui peut se produire intentionnellement en passant d’une feuille Excel à une feuille Google. N’oubliez pas que la date doit être MM-AAAA, donc le 12 septembre et non le 12 septembre, ou le 12 mai et non le 5-12 septembre.

## Avant de commencer {#before-you-begin}

[!DNL Marketo Measure] est fourni avec 13 canaux par défaut qui peuvent être utilisés ou développés. En outre, jusqu’à 40 canaux en ligne et hors ligne peuvent être créés pour s’adapter à votre structure marketing unique. Sur cette base, un total de 200 sous-canaux peut être créé pour prendre également en charge ces canaux en ligne et hors ligne.

[!DNL Marketo Measure] téléchargera automatiquement les coûts des canaux marketing à partir des plateformes avec lesquelles il dispose d’une intégration d’API, telles que Bing Ads et Google AdWords. Les coûts des plateformes qui ne sont pas intégrées avec [!DNL Marketo Measure] doivent être téléchargés manuellement. Les canaux marketing doivent être configurés avant le chargement des données de coût.

## Chargement des coûts marketing {#uploading-marketing-costs}

Une fois les canaux et les règles marketing configurés ou mis à jour, les coûts associés peuvent être chargés. Pour ce faire, procédez comme suit :

**Étape 1 : accédez à la page Dépenses de marketing dans l’application [!DNL Marketo Measure].**

Accédez au menu **[!UICONTROL Mon compte]**, cliquez sur **[!UICONTROL Paramètres]**, puis accédez à l’option **[!UICONTROL Dépenses marketing]** dans la barre latérale gauche sous la section **[!UICONTROL Reporting]**.

![Accédez au menu Mon compte, cliquez sur Paramètres, puis sur &#x200B;](assets/spend-management-4.png)

**Étape 2 : télécharger le fichier CSV des coûts actuels**

Accédez à la droite de l’écran et cliquez sur **[!UICONTROL Télécharger les coûts actuels &#x200B;].** Cette option permet de télécharger une feuille de calcul au format CSV.

![Accédez à la droite de l’écran, puis cliquez sur Télécharger la version actuelle](assets/spend-management-1.png)

**Étape 3 : ouvrir le fichier CSV et apporter des modifications**

Vous pouvez importer le fichier et l’ouvrir à l’aide de Google Sheets, d’Apple Numbers, de Microsoft Excel ou du logiciel de votre choix. [!DNL Marketo Measure] recommande d’utiliser Google Sheets.

Après avoir importé la feuille, apportez les modifications souhaitées, telles que l’ajout de coûts aux canaux et sous-canaux ou la mise à jour des informations existantes.

Vérifiez les règles logiques dans votre feuille. Chaque ligne doit contenir un canal et un de ses sous-canaux séparés par un point (.) à la fin. Il est important d’utiliser ce format de manière cohérente.

Par exemple, pour indiquer Facebook comme sous-canal et social comme canal, la règle doit être écrite comme suit : « Social.Facebook ». De même, pour effectuer le suivi d’un événement hors ligne, la syntaxe du canal doit être : « Events.Big Conference » (Événements.Grande conférence). Des exemples sont présentés dans l’image ci-dessous :

![Par exemple, pour indiquer Facebook comme sous-canal et social comme &#x200B;](assets/spend-management-2.png)

_Remarques supplémentaires_ :

Ne modifiez pas les dates de la feuille de calcul, car cela peut entraîner des problèmes lors du chargement du document.

Ne laissez aucun champ vide. Même s’il n’y a pas de valeur en dollars à ajouter, saisissez 0 $ comme montant en dollars.

Les coûts de Bing Ads et Google AdWords n’ont pas besoin d’être saisis ou mis à jour, car [!DNL Marketo Measure] extrait automatiquement ces données de sa connexion API avec ces plateformes.

**Étape 4 : enregistrer le fichier au format CSV**

Si vous travaillez dans Google Sheets, veillez d’abord à télécharger le fichier . N’excluez ou ne supprimez aucune donnée mensuelle, car cela entraîne des difficultés lors du téléchargement ultérieur du fichier CSV vers [!DNL Marketo Measure].

**Étape 5 : charger le fichier CSV**

Accédez à la section **[!UICONTROL Coût]** de l’application [!DNL Marketo Measure], puis cliquez sur **[!UICONTROL Charger.CSV]**. Le système actualisera et reflétera les nouvelles informations.

## Questions fréquentes {#faq}

**Pourquoi les nombres apparaissent-ils dans le fichier CSV**

Si aucune valeur n’est saisie à un niveau supérieur comme Canal ou Sous-canal, [!DNL Marketo Measure] additionne automatiquement les niveaux enfants pour vous, qui seront présentés une fois votre fichier chargé. En outre, si la somme des enfants est inférieure à une valeur saisie pour le parent, [!DNL Marketo Measure] ajoute une ligne « Autre » pour afficher la différence dans le total.

**Comment les campagnes sont-elles déterminées dans la liste que je vois ?**

Actuellement, nos résultats répertorient les campagnes qui ont été créditées d’un point de contact. Si une campagne a donné lieu à une activité, nous affichons cette campagne en fonction de la date de point de contact à laquelle elle s’est produite.

**Il y a trop de lignes et de colonnes à passer en revue. Puis-je consolider la vue ?**

La possibilité de modifier la période, de filtrer le canal ou de rechercher des valeurs vous permet de consolider les résultats du tableau pour mieux les adapter à vos besoins.

**Pourquoi ne puis-je pas charger un fichier ?**

Nous disposons de différents jeux d’autorisations dans l’application [!DNL Marketo Measure]. Pour charger un fichier, vous devez être un « administrateur de compte ». Pour contourner ce problème, demandez l’accès à votre administrateur de compte ou demandez à votre administrateur de compte de charger le fichier en votre nom. Vous trouverez une liste des utilisateurs et de leurs rôles sous **[!UICONTROL Mon compte]** > **[!UICONTROL Paramètres]** > **[!UICONTROL Afficher/Ajouter des utilisateurs de compte]**.
