---
unique-page-id: 18874730
description: Vue d’ensemble du marketing basé sur les comptes -  [!DNL Marketo Measure]  - Documentation produit
title: Vue d’ensemble du marketing basé sur les comptes
exl-id: 2ead69c0-66da-439d-a0ba-25c73c4b308c
feature: Account-based Marketing
source-git-commit: a2a7657e8377fd5c556d38f6eb815e39d2b8d15e
workflow-type: ht
source-wordcount: '782'
ht-degree: 100%

---

# Vue d’ensemble du marketing basé sur les comptes {#account-based-marketing-overview}

Vous trouverez ci-dessous une brève vue d’ensemble du marketing basé sur les comptes (ABM), les composants de la fonction ABM de [!DNL Marketo Measure] et de la manière de l’ajouter à votre mise en page [!DNL Salesforce]. Pour en savoir plus sur ABM, consultez [cette page](https://www.marketo.com/account-based-marketing/){target="_blank"}.

Pour accéder directement aux instructions de configuration d’ABM dans votre instance [!DNL Salesforce], veuillez [cliquer ici](/help/advanced-marketo-measure-features/account-based-marketing/account-based-marketing-overview.md#setting-up-abm-page-layout-in-salesforce){target="_blank"}.

## Présentation d’ABM {#what-is-abm}

Le marketing basé sur les comptes, ou ABM, est une stratégie marketing dans laquelle vous ciblez et vendez à des entreprises et des comptes dans leur ensemble, pas seulement en tant que particuliers. [!DNL Marketo Measure] aide les équipes de marketing et de vente à exécuter des stratégies d’ABM réussies grâce à sa fonctionnalité de mappage prospect>compte et son score d’engagement prédictif.

Pour que notre modèle de marketing basé sur les comptes commence à s’afficher dans votre CRM, [!DNL Marketo Measure] nécessite que les critères suivants soient remplis :

* Votre CRM a besoin d’au moins 25 comptes disposant d’au moins une opportunité gagnée fermée, afin que nous puissions mieux évaluer les fonctionnalités communes d’un compte ou d’une opportunité « réussi(e) » pour votre entreprise.
* D’autre part, votre CRM a besoin d’au moins 25 comptes sans opportunité gagnée fermée (toutes les options doivent être soit dans notre catégorie d’étape « Ouverte », soit dans une catégorie «Perdue fermée »), ce qui nous permet d’évaluer ce qu’est un compte moins intéressant dans votre entreprise.

>[!NOTE]
>
>Les « mauvais » comptes mentionnés ci-dessus doivent être ouverts pendant au moins 12 mois sans accumuler d’opportunité « Perdue gagnée » ; c’est la ligne directrice de base pour savoir si une opportunité est devenue obsolète ou non et améliorer le modèle.

## Mappage prospect>compte {#lead-to-account-mapping}

Le mappage prospect>compte est essentiel à l’efficacité de l’approche ABM. Grâce au mappage prospect>compte, les prospects sont regroupés dans le même compte d’entreprise lorsqu’ils s’intéressent à votre marque. Cela vous permet de cibler et de vendre à des personnes d’une même entreprise de manière cohérente. Il n’y a pas d’autre configuration [!DNL Salesforce] nécessaire pour commencer à bénéficier de cette fonctionnalité. Le mappage prospect>compte [!DNL Marketo Measure] dispose de cinq méthodes de correspondance différentes :

* Site web du prospect > site Web du compte
* Domaine d’adresse e-mail du prospect > domaine du site Web du compte
* Nom de l’entreprise du prospect > nom du compte
* Entreprise du prospect > domaine du site Web du compte
* Correspondance du domaine de l’adresse e-mail du prospect et le compte via l’adresse e-mail du contact

>[!NOTE]
>
>Chaque prospect est associé à un compte dans l’ordre préférentiel des méthodes ci-dessus. Une fois qu’une correspondance est établie, l’ID de compte est immédiatement défini sur le prospect et ne sera pas mis en correspondance à l’aide d’une autre méthode. Si le prospect dispose déjà d’un ID de compte valide, il est ignoré.

## Score d’engagement prédictif {#predictive-engagement-score}

Le score d’engagement prédictif [!DNL Marketo Measure], ou SEP, est une valeur dynamique qui illustre l’engagement d’un compte particulier vis-à-vis de vos actions marketing. Ce score est utile pour la segmentation des comptes à cibler. Il s’agit d’un outil précieux pour identifier les comptes à cibler de manière plus efficace.

De nombreux composants entrent dans l’algorithme qui calcule le SEP. La récence et l’âge ont une grande influence sur les changements de score, ainsi que sur les dernières activités de point de contact ou pages vues. L’ajout de nouveaux contacts à un compte a également un impact sur le SEP. Voici une liste de certains éléments du SEP :

* Nombre total de pages vues à partir du compte
* Nombre moyen de pages vues
* Nombre moyen de personnes dans le compte
* Âge de la dernière page vue
* Âge moyen des pages vues
* Nombre de personnes dans le compte
* Pages importantes spécifiques et s’il y a eu une visite au cours des 30/60/90 derniers jours
* Si le compte a une transaction perdue/gagnée fermée
* La probabilité qu’elle soit perdue/gagnée fermée

>[!NOTE]
>
>Vous remarquerez peut-être la mention « N/A » ou « - » (symbole du tiret) dans votre score d’engagement prédictif pour certains comptes.

_La mention « S/O » signifie simplement que nous ne disposons pas encore de données suffisantes sur ce compte pour que notre modèle génère un score réel. Lorsqu’il disposera de données supplémentaires, il lui attribuera un score._
_Un tiret « - » signifie que ce compte n’a pas encore été traité par notre processus ABM, en raison de contraintes de temps, de processus parfois manqués, etc. Si vous pensez qu’un compte doit avoir un score, basé sur d’autres comptes ou périodes similaires, contactez et informez [!DNL Marketo Measure]._

## Configuration de la mise en page ABM dans [!DNL Salesforce] {#setting-up-abm-page-layout-in-salesforce}

Pour commencer à utiliser le SEP, vous devez simplement ajouter le champ SEP et la liste associée aux mises en page appropriées dans [!DNL Salesforce].

1. Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Personnaliser]** > **[!UICONTROL Comptes]** > **[!UICONTROL Mise en page]**. Sélectionnez ensuite la mise en page que vous souhaitez modifier.
1. Accédez à [!UICONTROL Champs] et déplacez le champ « Score d’engagement prédictif » dans la section Informations du compte.

   ![](assets/1.png)

1. Enfin, accédez à [!UICONTROL Listes associées] et déplacez la liste associée « Prospects » dans votre mise en page.

   ![](assets/2.png)

1. Ensuite, accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Personnaliser]** > **[!UICONTROL Prospect]** > **[!UICONTROL Mise de page]** et sélectionnez les mises en page appropriées que vous souhaitez modifier.
1. Cliquez sur **[!UICONTROL Champs]** et ajoutez le champ [!UICONTROL Compte] à l’endroit qui vous convient sur la page.

   ![](assets/3.png)

Tout est prêt !

