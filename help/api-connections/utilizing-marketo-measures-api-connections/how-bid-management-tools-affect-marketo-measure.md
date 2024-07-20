---
unique-page-id: 18874720
description: Comment les outils de gestion des offres affectent-ils [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: Incidence des outils de gestion des offres sur [!DNL Marketo Measure]
exl-id: 67c00ad9-8b12-4238-8a1f-2d2f5ed04423
feature: APIs, Integration, UTM Parameters
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---

# Comment les outils de gestion des offres affectent [!DNL Marketo Measure] {#how-bid-management-tools-affect-marketo-measure}

Découvrez comment les plateformes de gestion des offres affectent la capacité [!DNL Marketo Measure] à effectuer le suivi d’AdWords et de BingAds, ainsi que comment configurer des modèles de suivi avec nos paramètres pour garantir un suivi correct de tout.

Kenshoo et Marin sont de bons outils qui permettent aux marketeurs de suivre, gérer et optimiser leurs campagnes publicitaires avec différents moteurs de recherche. Pour que [!DNL Marketo Measure] paramètres soient ajoutés à ces URL de publicité, vous devez configurer un modèle de suivi avec nos paramètres [!DNL Marketo Measure]. Il n’est pas possible de connecter vos plateformes publicitaires à votre compte [!DNL Marketo Measure] et d’activer le balisage automatique, car cela entraîne la concurrence entre le système de balisage [!DNL Marketo Measure] et le système de balisage de Kenshoo/Marin. Cela entraîne la modification et l’ajout incorrect de nos paramètres. Pour contourner ce problème, les modèles de suivi avec des paramètres [!DNL Marketo Measure] doivent être configurés dans Kenshoo et Marin.

## Pour les comptes [!DNL Adwords] {#for-adwords-accounts}

Configurez un modèle de suivi comme suit :

* Cliquez sur l’onglet **[!UICONTROL Campagnes]** .
* Cliquez sur le lien **[!UICONTROL Bibliothèque partagée]** dans la barre de navigation latérale.
* Cliquez sur **Options d’URL**.
* En regard de &quot;Modèle de suivi&quot;, cliquez sur **Modifier**.
* Renseignez l’URL :

   * Si TOUTES vos URL de publicité comportent un &quot;?&quot; dans , utilisez cette URL :
      * `{lpurl}&_bk={keyword}&_bt={creative}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`
   * Si AUCUNE de vos URL de publicité n’a de &quot;?&quot; dans , utilisez cette URL :
      * `{lpurl}?_bk={keyword}&_bt={creative}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`


## Pour les comptes [!DNL Bing Ads] {#for-bing-ads-accounts}

Configurez un modèle de suivi comme suit :

* Cliquez sur l’onglet **[!UICONTROL Campagnes]** .
* Cliquez sur le lien **[!UICONTROL Bibliothèque partagée]** dans la barre de navigation latérale.
* Cliquez sur **Options d’URL**.
* En regard de &quot;Modèle de suivi&quot;, cliquez sur **Modifier**.
* Renseignez l’URL :

   * Si TOUTES vos URL de publicité comportent un &quot;?&quot; dans , utilisez cette URL :
      * `{lpurl}&_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`
   * Si AUCUNE de vos URL de publicité n’a de &quot;?&quot; dans , utilisez cette URL :
      * `{lpurl}?_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`
