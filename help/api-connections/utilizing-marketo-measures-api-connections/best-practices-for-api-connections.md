---
description: Bonnes pratiques relatives aux connexions aux API - [!DNL Marketo Measure] - Documentation du produit
title: Bonnes pratiques pour les connexions d’API
exl-id: b8550e4e-a567-427f-b5d3-50232553a066
feature: APIs, Integration
source-git-commit: a2a7657e8377fd5c556d38f6eb815e39d2b8d15e
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 2%

---

# Bonnes pratiques pour les connexions d’API {#best-practices-for-api-connections}

## Vue d’ensemble {#overview}

[!DNL Marketo Measure] offre des connexions API avec [!DNL Google AdWords], [!DNL Microsoft Bing Ads], [!DNL Facebook Ads]et LinkedIn. Ces connexions API activent [!DNL Marketo Measure] pour extraire diverses données de vos plateformes publicitaires qui peuvent ensuite faire l’objet de rapports dans vos données de point de contact d’achat. L’une des principales fonctionnalités de ces connexions d’API est leur capacité à extraire automatiquement des données relatives aux dépenses, ce qui vous permet de gagner du temps et d’économiser le temps et les efforts nécessaires au chargement manuel des données pour la création de rapports de retour sur investissement. La configuration de ces connexions API n’est pas obligatoire pour [!DNL Marketo Measure] pour effectuer le suivi de ces canaux, mais ils fournissent des détails granulaires précieux qui améliorent vos rapports.

La variable [!DNL Marketo Measure] Les connexions API constituent un aspect inestimable de votre compte. Nos recommandations de bonnes pratiques vous aideront, ainsi qu’à votre équipe, à utiliser pleinement nos connexions.

## Bonne pratique {#best-practice}

Quelle que soit la plate-forme publicitaire que vous connectez, les instructions suivantes sont importantes à garder à l’esprit.

* Utilisation d’un administrateur pour se connecter
* Vous pouvez connecter plusieurs comptes de publicité pour une seule plateforme.
* Connectez tous les comptes publicitaires possibles pour automatiser autant que possible les rapports de dépenses.
* Si possible, implémentez toujours un modèle de suivi. Le modèle garantit que même si le compte publicitaire est déconnecté, [!DNL Marketo Measure] peut toujours extraire des détails de publicité granulaires

Pour optimiser chaque [!DNL Marketo Measure] API, veuillez respecter les bonnes pratiques suivantes.

**[!DNL Facebook]**: connexion avec le balisage automatique

Avant d’activer le balisage automatique, exportez votre historique d’annonces vers un fichier csv. L’activation du balisage automatique réinitialise l’historique de conversion et le BAT social de toutes les publicités balisées par [!DNL Marketo Measure].

En suivant notre recommandation, la variable [!DNL Marketo Measure] [!DNL Facebook] API pourra :

* Balisage automatique de toutes les [!DNL Facebook] Les publicités avec les [!DNL Marketo Measure] parameter `_bf ={creative}`
* Télécharger les informations sur les coûts publicitaires dans toutes les principales [!DNL Facebook] publicités

>[!NOTE]
>
>Il n’existe aucun modèle de suivi pour [!DNL Facebook], l’API repose sur le paramètre de balisage automatique (_bf) pour rassembler les détails de la publicité.

**AdWords**: implémentation d’un modèle de suivi au niveau du compte et activation du balisage automatique

[!DNL Marketo Measure] recommande d’utiliser un modèle de suivi au niveau du compte, de la campagne ou du groupe publicitaire, car il permet l’ajout et la soustraction de paramètres pour toutes les publicités sans risque d’interruption ou de suppression de l’historique des publicités.

En suivant notre recommandation, la variable [!DNL Marketo Measure] L’API AdWords pourra :

* Balisez automatiquement toutes les publicités AdWords à l’aide du [!DNL Marketo Measure] paramètres de `_bk={keyword}, _bt={creative}, _bm={matchtype}, _bn={network}, _bg={adgroupID}`
* Télécharger les informations de coût de la publicité dans toutes les publicités AdWords principales

**Bing**: implémentation d’un modèle de suivi au niveau du compte et activation du balisage automatique

Il n’y a aucun risque de perte d’historique publicitaire lors de la configuration de votre [!DNL Bing] La connexion à l’API, contrairement à certaines de nos autres connexions à l’API.

En suivant notre recommandation, la variable [!DNL Marketo Measure] L’API Bing pourra :
* Balisez automatiquement toutes les publicités Bing avec les paramètres suivants de `_bt={adid}, utm_medium=cpc, utm_source=bing, utm_term={keyword}`
* Téléchargement des informations de coût des publicités sur toutes les publicités Bing principales

**LinkedIn**: connexion avec le balisage automatique

L’activation du balisage automatique recrée un partage et le place dans un nouveau créatif, l’ancien créatif est archivé.

En suivant notre recommandation, la variable [!DNL Marketo Measure] L’API linkedIn pourra :

* Balisez automatiquement toutes les publicités LinkedIn qui sont de type publicitaire Contenu sponsorisé avec les [!DNL Marketo Measure] parameter_bl={creativeId}. Ce paramètre extrait l’ID de création permettant [!DNL Marketo Measure] pour résoudre la campagne et les informations créatives.
* Télécharger les informations sur les coûts publicitaires dans tous les principaux et pris en charge [!DNL LinkedIn] publicités

>[!NOTE]
>
>Il n’existe aucun modèle de suivi pour [!DNL LinkedIn], l’API repose sur le paramètre de balisage automatique (_bl) pour rassembler tous les détails de publicité possibles.

## Bonne pratique de maintenance {#best-practice-for-maintenance}

Bien que nos bonnes pratiques vous protègent de la perte de données si vous êtes déconnecté, nous vous recommandons tout de même de revoir votre connexion de manière régulière, mensuelle si possible. Ceci est une simple vérification visuelle de la variable [!UICONTROL Connexions] dans votre section [!DNL Marketo Measure] pour s’assurer qu’il n’y a pas d’icônes de clé rouge, signalant un compte déconnecté.

Lorsqu’un compte connecté à une API est déconnecté, [!DNL Marketo Measure] ne peut pas extraire des données de dépenses dans ou baliser de nouvelles publicités. C&#39;est pourquoi nous vous recommandons de toujours mettre en oeuvre, si possible, un modèle de tracking. Le modèle garantit que même si le compte publicitaire est déconnecté, [!DNL Marketo Measure] peut toujours baliser les publicités et extraire des détails de publicité granulaires. Une fois la reconnexion effectuée, les données de dépenses sont conservées et les perturbations de vos rapports Canal payant sont minimes.

Les raisons de la déconnexion et de la réautorisation incluent...

* Modification du mot de passe du compte de la personne connectée
* Cette personne n&#39;est plus dans l&#39;entreprise
* Mises à jour des API

Si votre équipe a fait l’expérience de l’un des scénarios ci-dessus, vérifiez vos connexions API dans la variable [!DNL Marketo Measure] pour s’assurer qu’elles n’ont pas besoin d’être réautorisées.

>[!MORELIKETHIS]
>
>* [Plateformes d’annonces intégrées (API)](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md)
>* [Incidence des outils de gestion des offres sur [!DNL Marketo Measure]](/help/api-connections/utilizing-marketo-measures-api-connections/how-bid-management-tools-affect-marketo-measure.md)
>* [[!DNL Marketo Measure] Explication des paramètres d’API](/help/api-connections/utilizing-marketo-measures-api-connections/marketo-measure-parameters.md)
>* [Présentation de l’API facebook](/help/api-connections/utilizing-marketo-measures-api-connections/facebook-api.md)
>* [[!DNL LinkedIn] Présentation de l’intégration](/help/api-connections/utilizing-marketo-measures-api-connections/linkedin-integration.md)
>* [Présentation de l’intégration AdWords](/help/api-connections/utilizing-marketo-measures-api-connections/understanding-marketo-measure-adwords-tagging.md)
>* [Réautorisation des comptes API connectés](/help/api-connections/utilizing-marketo-measures-api-connections/reauthorizing-connected-accounts.md)
