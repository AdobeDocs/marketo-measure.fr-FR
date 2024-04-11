---
unique-page-id: 18874608
description: « Paramètres [!DNL Marketo Measure] -  [!DNL Marketo Measure] »
title: « Paramètres [!DNL Marketo Measure] »
exl-id: d66b9864-0d7e-455a-ae20-cca555f4d8c8
feature: APIs, Integration, UTM Parameters
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: ht
source-wordcount: '230'
ht-degree: 100%

---

# Paramètres [!DNL Marketo Measure] {#marketo-measure-parameters}

## Paramètres [!DNL Marketo Measure] expliqués {#marketo-measure-parameters-explained}

Pour obtenir des informations supplémentaires sur l’utilisation des UTM, [!DNL Marketo Measure] ajoute des paramètres personnalisés à vos publicités dans [!DNL Google] AdWords, Bing Ads et [!DNL Facebook] Ads. [!DNL Marketo Measure] s’intègre à ces plateformes afin d’automatiser la plupart des processus de configuration. Si vous choisissez d’utiliser le balisage automatique, [!DNL Marketo Measure] ajoute automatiquement ses paramètres aux URL de vos publicités. [!DNL Marketo Measure] téléchargera également automatiquement vos coûts marketing à partir des plateformes et les chargera dans l’application [!DNL Marketo Measure].

Exemple d’URL sans paramètres :

`http://adobe.com/landing-page?myParam=foo`

Exemple d’URL avec des paramètres [!DNL Marketo Measure] :

`http://adobe.com/landing-page?myParam=foo&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Paramètres AdWords {#adwords-parameters}

* `_bk={keyword}`
   * Représente le mot-clé utilisé dans le moteur de recherche.
   * Cette valeur est similaire au paramètre de terme UTM.

* `_bt={creative}`
   * Représente l’identifiant ou le nom de création.
   * Ce paramètre est similaire au paramètre de contenu UTM.

* `_bm={matchtype}`
   * Représente le degré de correspondance du mot-clé.
   * Les types de correspondance de mots-clés vous permettent de contrôler quelles recherches déclenchent votre publicité. Par exemple, vous pouvez utiliser une correspondance large pour afficher votre publicité auprès d’une large audience ou une correspondance exacte pour cibler des groupes de clientes et clients spécifiques.
   * Les trois types de correspondance son : large, approximatif et exact.

>[!TIP]
>
>Pour plus d’informations sur les types de correspondance, [voici un article pertinent sur AdWords](https://support.google.com/adwords/answer/2497836?hl=fr){target="_blank"}.

* `_bn={network}`
   * Représente le type de réseau publicitaire – [affichage ou recherche](https://support.google.com/adwords/answer/1752334?hl=fr){target="_blank"}.
   * Ce paramètre est similaire au paramètre de source UTM.

* `_bg={adgroupID}`
   * Représente l’identifiant du groupe publicitaire auquel la publicité appartient.

>[!NOTE]
>
>Nous ne prenons pas en charge les paramètres de redirection d’URL.

## Paramètres des publicités Bing {#bing-ads-parameters}

* `_bt={adid}`
* `utm_medium=cpc`
* `utm_source=bing`
* `utm_term={keyword}`

## Paramètres de Facebook {#facebook-parameters}

* `_bf ={creative}`
   * Ce paramètre représente l’identifiant ou le nom de création.
