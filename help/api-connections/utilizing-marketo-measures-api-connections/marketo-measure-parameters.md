---
unique-page-id: 18874608
description: "[!DNL Marketo Measure] Paramètres - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Paramètres"
exl-id: d66b9864-0d7e-455a-ae20-cca555f4d8c8
feature: APIs, Integration, UTM Parameters
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# Paramètres [!DNL Marketo Measure] {#marketo-measure-parameters}

## [!DNL Marketo Measure] Paramètres expliqués {#marketo-measure-parameters-explained}

Pour obtenir des informations supplémentaires sur l’utilisation des UTM, [!DNL Marketo Measure] ajoute des paramètres personnalisés à vos publicités dans [!DNL Google] AdWords, Bing Ads et [!DNL Facebook] Publicités. [!DNL Marketo Measure] s’intègre à ces plateformes afin d’automatiser la plupart du processus de configuration. Si vous choisissez d’utiliser le balisage automatique, [!DNL Marketo Measure] ajoute automatiquement ses paramètres aux URL de vos publicités. [!DNL Marketo Measure] téléchargera également automatiquement vos coûts marketing à partir des plateformes et les chargera dans la variable [!DNL Marketo Measure] application.

Exemple d&#39;URL sans paramètres :

`http://adobe.com/landing-page?myParam=foo`

Exemple d’URL avec [!DNL Marketo Measure] parameters:

`http://adobe.com/landing-page?myParam=foo&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Paramètres AdWords {#adwords-parameters}

* `_bk={keyword}`
   * Représente le mot-clé utilisé dans le moteur de recherche.
   * Elle est similaire au paramètre de terme de la gestion dynamique des balises.

* `_bt={creative}`
   * Représente l’ID ou le nom de création.
   * Elle est similaire au paramètre de contenu UTM.

* `_bm={matchtype}`
   * Représente le degré de correspondance du mot-clé.
   * Les types de correspondance de mots-clés permettent de contrôler quelles recherches déclenchent votre publicité. Par exemple, vous pouvez utiliser une correspondance large pour afficher votre publicité auprès d’un large public ou une correspondance exacte pour éclairer des groupes de clients spécifiques.
   * Les trois types de correspondance sont : large, flou et exact.

>[!TIP]
>
>Pour plus d’informations sur les types de correspondance, [voici un article pertinent sur AdWords](https://support.google.com/adwords/answer/2497836?hl=en){target="_blank"}.

* `_bn={network}`
   * Représente le type de réseau publicitaire - [affichage ou recherche](https://support.google.com/adwords/answer/1752334?hl=en){target="_blank"}.
   * Ceci est similaire au paramètre source UTM.

* `_bg={adgroupID}`
   * Représente l’identifiant du groupe publicitaire auquel la publicité appartient.

>[!NOTE]
>
>Nous ne prenons pas en charge les paramètres d’URL de redirection.

## Paramètres Bing Ads {#bing-ads-parameters}

* `_bt={adid}`
* `utm_medium=cpc`
* `utm_source=bing`
* `utm_term={keyword}`

## Paramètres facebook {#facebook-parameters}

* `_bf ={creative}`
   * Il représente l’ID ou le nom de l’élément créatif.
