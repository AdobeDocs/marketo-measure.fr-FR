---
unique-page-id: 18874730
description: Présentation marketing basée sur les comptes - [!DNL Marketo Measure] - Documentation du produit
title: Vue d’ensemble du marketing basé sur les comptes
exl-id: 2ead69c0-66da-439d-a0ba-25c73c4b308c
feature: Account-based Marketing
source-git-commit: a2a7657e8377fd5c556d38f6eb815e39d2b8d15e
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 1%

---

# Vue d’ensemble du marketing basé sur les comptes {#account-based-marketing-overview}

Vous trouverez ci-dessous un bref aperçu d’ABM, les composants de [!DNL Marketo Measure] fonction ABM et comment l’ajouter à votre [!DNL Salesforce] mise en page. Pour en savoir plus sur ABM, consultez la rubrique [cette page](https://www.marketo.com/account-based-marketing/){target="_blank"}.

Pour accéder directement aux instructions de configuration d’ABM dans votre [!DNL Salesforce] instance, s’il vous plaît [cliquez ici](/help/advanced-marketo-measure-features/account-based-marketing/account-based-marketing-overview.md#setting-up-abm-page-layout-in-salesforce){target="_blank"}.

## Présentation d’ABM {#what-is-abm}

Le marketing basé sur les comptes, ABM, est une stratégie marketing dans laquelle vous ciblez et vendez des données aux entreprises et aux comptes dans leur ensemble, pas seulement en tant qu&#39;individus. [!DNL Marketo Measure] aide les équipes de marketing et de vente à exécuter des stratégies ABM réussies avec sa fonctionnalité de mappage prospect à compte et son score d’engagement prédictif.

Pour que notre modèle de marketing basé sur les comptes commence à apparaître dans votre CRM, [!DNL Marketo Measure] nécessite que les critères suivants soient remplis :

* Votre service de gestion de la relation client a besoin d’au moins 25 comptes disposant d’au moins une opportunité de gestion de la relation client fermée, afin que nous puissions mieux jauger les fonctionnalités communes d’un compte/opportunité &quot;réussi&quot; pour votre entreprise.
* De l’autre côté de la pièce, votre CRM a besoin d’au moins 25 comptes sans opportunité de gain fermée (toutes les options doivent être soit dans notre catégorie d’étape &quot;Ouverture&quot;, soit dans une catégorie &quot;Perte fermée&quot; - ce qui nous permet de jauger ce qui fait qu’un compte de qualité inférieure dans votre organisation.

>[!NOTE]
>
>Les &quot;mauvais&quot; comptes ci-dessus doivent être ouverts pendant au moins 12 mois sans accumuler une valeur d’opt-in &quot;Closed Won&quot; ; c’est la ligne directrice de base pour savoir si une valeur d’opt-in est ou non devenue obsolète aux fins du modèle.

## Mappage de piste à compte {#lead-to-account-mapping}

La mise en correspondance des pistes et des comptes est essentielle à l&#39;efficacité de l&#39;approche ABM. Grâce au mappage de piste sur compte, les prospects ou les prospects sont regroupés dans le même compte d’entreprise que celui auquel ils s’engagent auprès de votre marque. Cela vous permet de cibler et de vendre des données à des personnes d’une même société de manière cohérente. Il n’y a pas d’autres [!DNL Salesforce] configuration nécessaire pour commencer à bénéficier de cette fonctionnalité. La variable [!DNL Marketo Measure] Mappage de compte de cinq méthodes de correspondance différentes :

* Diriger le site web vers le site web du compte
* Domaine de courriel de piste vers le domaine du site web du compte
* Nom de la société de piste dans le nom du compte
* Société responsable dans le domaine du site web du compte
* Correspondance du domaine de l’adresse électronique du prospect avec le compte via l’adresse électronique du contact.

>[!NOTE]
>
>Chaque prospect est associé à un compte dans l’ordre préférentiel des méthodes ci-dessus. Une fois qu’une correspondance est établie, le AccountId est immédiatement défini sur le prospect et ne sera pas mis en correspondance à l’aide d’une autre méthode. Si le prospect dispose déjà d’un ID de compte valide, il est ignoré.

## Score prédictif de l’engagement {#predictive-engagement-score}

La variable [!DNL Marketo Measure] Score d’engagement prédictif, ou SPE, est une valeur dynamique qui illustre l’engagement d’un compte particulier dans vos efforts marketing. Ce score est utile pour la segmentation des comptes à cibler. Il s’agit d’un outil précieux pour identifier les comptes à cibler de manière plus efficace et plus efficace.

De nombreux composants entrent dans l’algorithme qui calcule le SPE. La récence et l’âge ont une grande influence sur les changements de score, ainsi que sur les dernières activités de point de contact ou pages vues. L&#39;ajout de nouveaux contacts à un compte a également un impact sur le SPE. Ci-dessous, une liste de quelques éléments du rapport :

* Nombre total de pages vues du compte
* Nombre moyen de pages vues
* Nombre moyen de personnes dans le compte
* Âge de la dernière page vue
* Âge moyen des pages vues
* Nombre de personnes dans le compte
* Pages importantes spécifiques et s’il y a eu une visite au cours des 30/60/90 derniers jours
* Si le compte a une transaction perdue/gagnée fermée
* La probabilité qu’il soit fermé est perdue/gagnée

>[!NOTE]
>
>Vous remarquerez peut-être une note de &quot;S/O&quot; ou &quot;-&quot; (symbole du tiret) dans votre note d’engagement prédictive pour certains comptes.

_Une note &quot;S/O&quot; signifie simplement que nous ne disposons pas encore de données suffisantes sur ce compte pour que notre modèle génère une note réelle - avec plus de données, une note sera finalement donnée._
_Une note de &quot;-&quot; signifie que ce compte doit encore être traité par notre processus ABM, en raison de contraintes de temps, de processus parfois manqués, etc. Si vous pensez qu’un compte doit avoir une note, basée sur d’autres comptes ou périodes similaires, contactez et laissez [!DNL Marketo Measure] Je sais._

## Configuration de la mise en page ABM dans [!DNL Salesforce] {#setting-up-abm-page-layout-in-salesforce}

Pour commencer à utiliser les PES, vous devez simplement ajouter le champ PES et la liste associée aux mises en page appropriées dans [!DNL Salesforce].

1. Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Personnaliser]** > **[!UICONTROL Comptes]** > **[!UICONTROL Disposition de page]**. Sélectionnez ensuite la mise en page que vous souhaitez modifier.
1. Accédez à [!UICONTROL Champs] et déplacez le champ &quot;Score d’engagement prédictif&quot; dans la section Informations du compte.

   ![](assets/1.png)

1. Enfin, accédez à [!UICONTROL Listes connexes] et déplacez la liste liée &quot;Leads&quot; dans votre mise en page.

   ![](assets/2.png)

1. Ensuite, accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Personnaliser]** > **[!UICONTROL Pistes]** > **[!UICONTROL Disposition de page]** et sélectionnez les mises en page appropriées que vous souhaitez modifier.
1. Cliquez sur **[!UICONTROL Champs]** et ajoutez le [!UICONTROL Compte] champ où vous voyez l’ajustement sur la page.

   ![](assets/3.png)

Tout est prêt!

