---
unique-page-id: 18874720
description: Incidence des outils de gestion des offres [!DNL Marketo Measure] - [!DNL Marketo Measure] - Documentation du produit
title: Incidence des outils de gestion des offres [!DNL Marketo Measure]
exl-id: 67c00ad9-8b12-4238-8a1f-2d2f5ed04423
source-git-commit: 65e7f8bc198ceba2f873ded23c94601080ad0546
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Incidence des outils de gestion des offres [!DNL Marketo Measure] {#how-bid-management-tools-affect-marketo-measure}

Découvrez comment les plateformes de gestion des offres affectent les [!DNL Marketo Measure] la possibilité d’effectuer le suivi d’AdWords et de BingAds, ainsi que de configurer des modèles de suivi avec nos paramètres pour garantir un suivi correct de tout.

Kenshoo et Marin sont de bons outils qui permettent aux marketeurs de suivre, gérer et optimiser leurs campagnes publicitaires avec différents moteurs de recherche. Pour [!DNL Marketo Measure] à ajouter à ces URL de publicité, vous devez configurer un modèle de suivi avec nos [!DNL Marketo Measure] paramètres. Il n’est pas possible de connecter vos plateformes publicitaires à vos [!DNL Marketo Measure] compte et activer le balisage automatique, car cela entraîne la création de la variable [!DNL Marketo Measure] système de balisage pour concurrencer le système de balisage de Kenshoo/Marin. Cela entraîne la modification et l’ajout incorrect de nos paramètres. Pour contourner ce problème, effectuez le suivi des modèles avec [!DNL Marketo Measure] doivent être configurés dans Kenshoo et Marin.

## Pour [!DNL Adwords] Comptes {#for-adwords-accounts}

Configurez un modèle de suivi comme suit :

* Cliquez sur le bouton **[!UICONTROL Campagnes]** .
* Cliquez sur le bouton **[!UICONTROL Bibliothèque partagée]** dans la barre de navigation latérale.
* Cliquez sur **Options d’URL**.
* En regard de &quot;Modèle de suivi&quot;, cliquez sur **Modifier**.
* Renseignez l’URL :

   * Si TOUTES vos URL de publicité comportent un &quot;?&quot; dans , utilisez cette URL :
      * `{lpurl}&_bk={keyword}&_bt={creative}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`
   * Si AUCUNE de vos URL de publicité n’a de &quot;?&quot; dans , utilisez cette URL :
      * `{lpurl}?_bk={keyword}&_bt={creative}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`


## Pour [!DNL Bing Ads] Comptes {#for-bing-ads-accounts}

Configurez un modèle de suivi comme suit :

* Cliquez sur le bouton **[!UICONTROL Campagnes]** .
* Cliquez sur le bouton **[!UICONTROL Bibliothèque partagée]** dans la barre de navigation latérale.
* Cliquez sur **Options d’URL**.
* En regard de &quot;Modèle de suivi&quot;, cliquez sur **Modifier**.
* Renseignez l’URL :

   * Si TOUTES vos URL de publicité comportent un &quot;?&quot; dans , utilisez cette URL :
      * `{lpurl}&_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`
   * Si AUCUNE de vos URL de publicité n’a de &quot;?&quot; dans , utilisez cette URL :
      * `{lpurl}?_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`
