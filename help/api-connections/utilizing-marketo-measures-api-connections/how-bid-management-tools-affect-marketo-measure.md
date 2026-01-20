---
unique-page-id: 18874720
description: Impact Des Outils De Gestion Des Offres  [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: Incidence des outils de gestion des offres sur [!DNL Marketo Measure]
exl-id: 67c00ad9-8b12-4238-8a1f-2d2f5ed04423
feature: APIs, Integration, UTM Parameters
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---

# Comment les outils de gestion des enchères affectent-ils [!DNL Marketo Measure] {#how-bid-management-tools-affect-marketo-measure}

Découvrez comment les plateformes de gestion des enchères affectent la capacité des [!DNL Marketo Measure] à suivre AdWords et BingAds, ainsi que la manière de configurer des modèles de suivi avec nos paramètres pour s’assurer que tout est suivi correctement.

Kenshoo et Marin sont d’excellents outils qui permettent aux marketeurs de suivre, de gérer et d’optimiser leurs campagnes publicitaires avec différents moteurs de recherche. Pour que [!DNL Marketo Measure] paramètres soient ajoutés à ces URL d’annonces, vous devez configurer un modèle de tracking avec nos paramètres de [!DNL Marketo Measure]. Il n’est pas possible de connecter vos plateformes publicitaires à votre compte [!DNL Marketo Measure] et d’activer le balisage automatique, car cela entraîne la concurrence du système de balisage [!DNL Marketo Measure] avec celui de Kenshoo/Marin. Cela entraîne la modification de nos paramètres et leur ajout incorrect. Pour contourner ce problème, des modèles de tracking avec des paramètres [!DNL Marketo Measure] doivent être configurés dans Kenshoo et Marin.

## Pour les comptes [!DNL Adwords] {#for-adwords-accounts}

Paramétrez un modèle de tracking comme suit :

* Cliquez sur l’onglet **[!UICONTROL Campagnes]**.
* Cliquez sur le lien **[!UICONTROL Bibliothèque partagée]** dans la barre de navigation latérale.
* Cliquez sur **Options d’URL**.
* En regard de « Modèle de tracking », cliquez sur **Modifier**.
* Renseignez l’URL :

   * Si TOUTES les URL de vos publicités comportent un « ? » dans ces pages, utilisez cette URL :
      * `{lpurl}&_bk={keyword}&_bt={creative}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`
   * Si AUCUNE de vos URL d’annonces publicitaires ne comporte de « ? » dans ces pages, utilisez cette URL :
      * `{lpurl}?_bk={keyword}&_bt={creative}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`


## Pour les comptes [!DNL Bing Ads] {#for-bing-ads-accounts}

Paramétrez un modèle de tracking comme suit :

* Cliquez sur l’onglet **[!UICONTROL Campagnes]**.
* Cliquez sur le lien **[!UICONTROL Bibliothèque partagée]** dans la barre de navigation latérale.
* Cliquez sur **Options d’URL**.
* En regard de « Modèle de tracking », cliquez sur **Modifier**.
* Renseignez l’URL :

   * Si TOUTES les URL de vos publicités comportent un « ? » dans ces pages, utilisez cette URL :
      * `{lpurl}&_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`
   * Si AUCUNE de vos URL d’annonces publicitaires ne comporte de « ? » dans ces pages, utilisez cette URL :
      * `{lpurl}?_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`
