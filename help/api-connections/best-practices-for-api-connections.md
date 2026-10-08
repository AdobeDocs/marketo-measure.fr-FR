---
description: Conseils sur les bonnes pratiques pour les connexions API pour les utilisateurs de Marketo Measure
title: Bonnes pratiques relatives aux connexions API
exl-id: b8550e4e-a567-427f-b5d3-50232553a066
feature: APIs, Integration
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: fb43f4c1-87d9-4081-8df1-6fe7e6e5cdc8
    internal-label: APIs
  - id: 7da342c5-06ee-5869-b3e8-b73d5bf75a9d
    internal-label: Integration
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 96%
---
# Bonnes pratiques relatives aux connexions API {#best-practices-for-api-connections}

## Vue d’ensemble {#overview}

[!DNL Marketo Measure] fournit des connexions API avec [!DNL Google AdWords], [!DNL Microsoft Bing Ads], [!DNL Facebook Ads] et LinkedIn. Ces connexions API activent [!DNL Marketo Measure] pour extraire diverses données depuis vos plateformes publicitaires qui peuvent ensuite faire l’object d’un rapport dans vos données Buyer Touchpoint. L’un des principaux avantages de ces connexions API est leur capacité à extraire automatiquement les données de dépenses, ce qui vous évite, à vous et à votre équipe, de charger manuellement les données pour les rapports sur le ROI. La mise en place de ces connexions API n’est pas obligatoire dans [!DNL Marketo Measure] pour effectuer un suivi de ces canaux, mais celles-ci fournissent de précieuses informations détaillées qui améliorent vos rapports.

Les connexions API [!DNL Marketo Measure] constituent un aspect inestimable de votre compte. Nos recommandations de bonnes pratiques vous aideront, ainsi que votre équipe, à utiliser pleinement nos connexions.

## Bonne pratique {#best-practice}

Quelle que soit la plateforme publicitaire que vous connectez, il est important de garder à l’esprit les instructions ci-après.

* Utilisez un compte d’administration pour vous connecter.
* Vous pouvez connecter plusieurs comptes publicitaires pour une même plateforme.
* Connectez tous les comptes publicitaires possibles pour automatiser autant que possible les rapports de dépenses.
* Si possible, mettez toujours en œuvre un modèle de suivi. Le modèle garantit que même si le compte publicitaire est déconnecté, [!DNL Marketo Measure] peut toujours extraire des informations publicitaires détaillées.

Pour optimiser chaque API [!DNL Marketo Measure], respectez les bonnes pratiques suivantes.

**[!DNL Facebook]** : connexion avec le balisage automatique

Avant d’activer le balisage automatique, exportez votre historique d’annonces publicitaires au format CSV. L’activation du balisage automatique réinitialise l’historique de conversion et la preuve sociale de toutes les publicités balisées par [!DNL Marketo Measure].

En suivant notre recommandation de bonne pratique, l’API [!DNL Facebook] de [!DNL Marketo Measure] est capable de :

* baliser automatiquement toutes les publicités [!DNL Facebook] avec le paramètre [!DNL Marketo Measure] requis : `_bf ={creative}` ;
* télécharger les informations de coût des publicités de toutes les publicités [!DNL Facebook] actives.

>[!NOTE]
>
>Il n’existe aucun modèle de suivi pour [!DNL Facebook], l’API utilise le paramètre de balisage automatique (_bf) pour rassembler les détails des publicités.

**AdWords** : implémentation d’un modèle de suivi au niveau du compte et activation du balisage automatique

[!DNL Marketo Measure] recommande d’utiliser un modèle de suivi au niveau du compte, de la campagne, ou du groupe de publicités, car cela permet d’ajouter et de soustraire des paramètres pour toutes les publicités sans risque d’interruption ou de suppression de l’historique des publicités.

En suivant notre recommandation de bonne pratique, l’API AdWords [!DNL Marketo Measure] est capable de :

* baliser automatiquement toutes les publicités AdWords à l’aide des paramètres [!DNL Marketo Measure] de `_bk={keyword}, _bt={creative}, _bm={matchtype}, _bn={network}, _bg={adgroupID}` ;
* télécharger les informations de coût des publicités de toutes les publicités AdWords actives.

**Bing** : implémentation d’un modèle de suivi au niveau du compte et activation du balisage automatique

Il n’y a aucun risque de perte de l’historique des publicités lors de la configuration de votre connexion API [!DNL Bing], contrairement à certaines de nos autres connexions API.

En suivant notre recommandation de bonne pratique, l’API Bing [!DNL Marketo Measure] est capable de :
* baliser automatiquement toutes les publicités Bing avec les paramètres suivants de `_bt={adid}, utm_medium=cpc, utm_source=bing, utm_term={keyword}` ;
* Téléchargez les informations sur les coûts publicitaires de toutes les publicités Bing actives.

**LinkedIn** : connexion avec le balisage automatique

L’activation du balisage automatique crée un nouveau Partage et le place dans une nouvelle Création. L’ancienne Création est archivée.

En suivant notre recommandation de bonne pratique, l’API LinkedIn [!DNL Marketo Measure] est capable de :

* Balisage automatique de toutes les publicités LinkedIn qui sont du contenu sponsorisé de type publicité avec le paramètre de [!DNL Marketo Measure] nécessaire _bl={creativeId}. Ce paramètre extrait l’ID de création permettant à [!DNL Marketo Measure] de traiter la campagne et les informations de création ;
* télécharger des informations de coût des publicités de toutes les publicités [!DNL LinkedIn] actives et prises en charge.

>[!NOTE]
>
>Il n’existe aucun modèle de suivi pour [!DNL LinkedIn], l’API utilise le paramètre de balisage automatique (_bl) pour collecter toutes les informations possibles des publicités.

## Bonne pratique de maintenance {#best-practice-for-maintenance}

Bien que le respect de nos bonnes pratiques vous protège d’une perte de données en cas de déconnexion, nous vous recommandons tout de même de vérifier régulièrement votre connexion, chaque mois si cela est possible. Il s’agit d’une simple vérification visuelle de la section [!UICONTROL Connexions] dans votre application [!DNL Marketo Measure] pour vous assurer qu’il n’y a pas d’icônes de clés rouges qui indiquent un compte déconnecté.

Lorsqu’un compte connecté à une API est déconnecté, [!DNL Marketo Measure] ne peut pas extraire de données de dépenses ou baliser de nouvelles publicités. C’est pourquoi nous vous recommandons toujours, dans la mesure du possible, de mettre en œuvre un modèle de suivi. Le modèle garantit que même si le compte publicitaire est déconnecté, [!DNL Marketo Measure] peut toujours baliser les publicités et extraire les informations de publicité détaillées. Une fois la reconnexion effectuée, les données de dépenses sont automatiquement récupérées et les perturbations dans vos rapports de Canal payant sont minimes.

Les raisons d’une déconnexion et d’une réautorisation incluent les éléments suivants :

* Une modification du mot de passe du compte de la personne connectée.
* Cette personne n’est plus dans l’entreprise.
* Des mises à jour des API.

Si votre équipe a fait l’expérience de l’un des scénarios ci-dessus, vérifiez vos connexions API dans l’application [!DNL Marketo Measure] pour vous assurer qu’elles n’ont pas besoin d’être réautorisées.

>[!MORELIKETHIS]
>
>* [Plateformes publicitaires intégrées (API)](/help/api-connections/integrated-ad-platforms.md)
>* [Incidence des outils de gestion des offres [!DNL Marketo Measure]](/help/api-connections/how-bid-management-tools-affect-marketo-measure.md)
>* [[!DNL Marketo Measure] Explication des paramètres d’API](/help/api-connections/marketo-measure-parameters.md)
>* [Vue d’ensemble de l’API Facebook](/help/api-connections/facebook-api.md)
>* [[!DNL LinkedIn] Vue d’ensemble de l’intégration](/help/api-connections/linkedin-integration.md)
>* [Vue d’ensemble de l’intégration AdWords](/help/api-connections/understanding-marketo-measure-adwords-tagging.md)
>* [Réautoriser des comptes d’API connectés](/help/api-connections/reauthorizing-connected-accounts.md)
