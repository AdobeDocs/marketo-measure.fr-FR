---
description: Découvrez Account-Based Marketing (ABM) et comment Adobe Marketo Measure aide les équipes marketing et commerciales à mettre en œuvre des stratégies ABM efficaces.
title: Vue d’ensemble du marketing basé sur les comptes
exl-id: 2ead69c0-66da-439d-a0ba-25c73c4b308c
feature: Account-based Marketing
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: 96ef477f-0ffb-5375-8fca-6d27be6b7c00
    internal-label: Account-based Marketing
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 92%
---
# Vue d’ensemble du marketing basé sur les comptes {#account-based-marketing-overview}

Les sections suivantes fournissent une brève vue d’ensemble d’ABM, des composants de la fonctionnalité ABM de [!DNL Marketo Measure] et de la manière de l’ajouter à votre disposition de page [!DNL Salesforce]. Pour en savoir plus sur ABM, consultez le [blog ABM](https://business.adobe.com/fr/blog/basics/account-based-marketing){target="_blank"} d’Adobe.

Pour obtenir des instructions détaillées sur la configuration d’ABM dans votre instance [!DNL Salesforce], consultez [Configuration de la disposition de page d’ABM dans Salesforce](/help/channel-tracking-and-setup/account-based-marketing-overview.md){target="_blank"}.

## Présentation d’ABM {#what-is-abm}

Le marketing basé sur les comptes (ABM) est une stratégie marketing qui consiste à cibler et à vendre auprès d’entreprises et de comptes dans leur ensemble, et non pas seulement à des individus. [!DNL Marketo Measure] aide les équipes de marketing et de vente à exécuter des stratégies d’ABM réussies grâce à sa fonctionnalité de mappage prospect>compte et son score d’engagement prédictif.

Pour que notre modèle Account-Based Marketing commence à s’afficher dans votre CRM, [!DNL Marketo Measure] nécessite que les critères suivants soient remplis :

* Votre CRM a besoin d’au moins 25 comptes disposant d’au moins une opportunité conclue avec succès (« Closed Won »), afin de mieux identifier les caractéristiques communes d’un compte ou d’une opportunité ayant abouti à une vente.
* En contrepartie, votre CRM a besoin d’au moins 25 comptes sans aucune opportunité conclue avec succès (« Closed Won »). Toutes les opportunités doivent être soit à une étape appartenant à la catégorie « Open », soit à une étape appartenant à la catégorie « Closed Lost ». Cela nous permet d’identifier les caractéristiques d’un compte moins performant au sein de votre organisation

>[!NOTE]
>
>Les « mauvais » comptes mentionnés ci-dessus doivent être ouverts depuis au moins 12 mois sans avoir généré d’opportunité « Closed Won » ; il s’agit de la règle de base pour déterminer si une opportunité est devenue obsolète pour les besoins du modèle.

## Mappage prospect>compte {#lead-to-account-mapping}

Le mappage des leads aux comptes est un élément crucial d’une approche ABM efficace. Grâce au mappage prospect>compte, les prospects sont regroupés dans le même compte d’entreprise lorsqu’ils s’intéressent à votre marque. Cela vous permet de cibler et de vendre à des personnes d’une même entreprise de manière cohérente. Il n’y a pas d’autre configuration [!DNL Salesforce] nécessaire pour commencer à bénéficier de cette fonctionnalité. Le mappage prospect>compte [!DNL Marketo Measure] dispose de cinq méthodes de correspondance différentes :

* Site web du lead > site web du compte
* Domaine d’adresse e-mail du prospect > domaine du site Web du compte
* Nom de l’entreprise du prospect > nom du compte
* Entreprise du prospect > domaine du site Web du compte
* Site web du lead > domaine d’adresse e-mail des contacts du compte
* Domaine d’adresse e-mail du lead > domaine d’adresse e-mail des contacts du compte
* Site web du lead > domaine d’e-mail des leads du compte
* Domaine d’e-mail du lead > domaine d’e-mail des leads du compte

Les leads et contacts des comptes sont validés en fonction de leurs domaines d’e-mail et de site web, puis mis en correspondance avec le domaine ou le sous-domaine d’e-mail ou de site web du lead. Le compte avec le plus de correspondances est utilisé.

>[!NOTE]
>
>Chaque lead tente d’être associé à un compte dans l’ordre préférentiel des méthodes ci-dessus. Une fois qu’une correspondance est établie, l’ID de compte est immédiatement défini sur le lead et ne sera pas mis en correspondance à l’aide d’une autre méthode.

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
* Si le compte comporte une opportunité au statut « Closed Lost » ou « Closed Won ».
* Probabilité que l’opportunité soit clôturée comme gagnée ou perdue

>[!NOTE]
>
>Vous remarquerez peut-être la mention « S/O » ou « - » (symbole du tiret) dans votre score d’engagement prédictif pour certains comptes.

_La mention « S/O » signifie simplement qu’il n’y a pas de données suffisantes sur ce compte pour que le modèle génère un score réel. Lorsqu’il dispose de données supplémentaires, il lui attribue un score._
_Un grade de « - » (symbole tiret) signifie que ce compte doit encore être traité par le processus ABM, en raison de contraintes de temps, de processus parfois manqués, etc. Si vous pensez qu’un compte doit avoir un score, basé sur d’autres comptes ou périodes similaires, contactez et informez [!DNL Marketo Measure]._

## Configurer de la disposition de page ABM dans [!DNL Salesforce] {#setting-up-abm-page-layout-in-salesforce}

Pour commencer à utiliser le SEP, vous devez ajouter le champ SEP et la liste associée aux dispositions de page appropriées dans [!DNL Salesforce].

1. Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Personnaliser]** > **[!UICONTROL Comptes]** > **[!UICONTROL Disposition de page]**. Sélectionnez ensuite la disposition de page que vous souhaitez modifier.
1. Accédez à [!UICONTROL Champs] et déplacez le champ « Score d’engagement prédictif » dans la section Informations du compte.

   ![1. Accédez à Champs et déplacez le champ « Score prédictif de l’engagement »](assets/account-marketing-3.png)

1. Enfin, accédez à [!UICONTROL Listes associées] et déplacez la liste associée « Prospects » dans votre mise en page.

   ![1. Enfin, accédez à Listes liées et déplacez la section « Leads » liée](assets/account-marketing-4.jpg)

1. Ensuite, accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Personnaliser]** > **[!UICONTROL Prospect]** > **[!UICONTROL Mise de page]** et sélectionnez les mises en page appropriées que vous souhaitez modifier.
1. Cliquez sur **[!UICONTROL Champs]** et ajoutez le champ [!UICONTROL Compte] à l’endroit qui vous convient sur la page.

   ![1. Cliquez sur Champs et ajoutez le champ Compte où vous &#x200B;](assets/account-marketing-5.png)

Tout est prêt !

