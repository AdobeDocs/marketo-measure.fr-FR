---
unique-page-id: 35586069
description: Garantir le consentement pour le RGPD dans Marketo Measure Js - Marketo Measure - Documentation du produit
title: Garantir le consentement pour le RGPD dans Marketo Measure JSON
exl-id: 9afc5e4d-cf97-4c49-b9ee-ee1cc99c1f90
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# Garantir le consentement pour le RGPD dans Marketo Measure JSON {#ensuring-consent-for-gdpr-in-marketo-measure-js}

Le Règlement général sur la protection des données (RGPD) est une loi de l’Union européenne qui est entrée en vigueur le 25 mai 2018.

## Vue d’ensemble {#overview}

Le RGPD a pour but de renforcer les droits des personnes concernées au sein de l’Union européenne (UE) et de l’Espace économique européen (EEE) en ce qui concerne l’utilisation et la protection de leurs données personnelles. &quot;Données personnelles&quot; désigne toute information relative à une personne physique identifiée ou identifiable. Le RGPD s’applique à toute organisation à l’intérieur ou à l’extérieur de l’UE qui commercialise des biens ou des services et/ou qui suit les comportements des sujets des données au sein de l’UE et de l’EEE. Si vous faites affaire avec des sujets des données en Europe qui impliquent le traitement de leurs données personnelles, cette législation s’applique à vous. Les sanctions en cas de non-conformité sont importantes, avec de lourdes amendes pour ceux qui enfreignent le règlement ; l&#39;amende maximale pour une violation unique est de 20 millions d&#39;euros ou 4% du chiffre d&#39;affaires annuel mondial, selon la plus élevée des deux.

Par défaut, [!DNL bizible.js] collecte les données d’analyse des utilisateurs, sauf si elles sont configurées spécifiquement pour attendre le consentement. When [!DNL bizible.js] est configuré pour attendre le consentement de l’utilisateur, il ne crée aucun cookie ni n’envoie aucune donnée d’analyse tant que le consentement n’est pas atteint.

## Comment attendre le consentement {#how-to-wait-for-consent}

Il existe deux façons de définir [!DNL bizible.js] pour attendre le consentement.

Option 1 - Remplacer la valeur par défaut [!DNL bizible.js] balise de script avec :

`<script id="bizible-settings" type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" data-consent-button-id="ConsentButtonId"></script>`

**Si vous utilisez [!DNL Google Tag Manager] pour installer le script**, gardez à l’esprit que GTM supprime les attributs data- . Utilisez donc le script suivant à la place :

`<span id="bizible-settings" data-consent-button-id="ConsentButtonId"></span>`
`<script type="text/javascript" src=https://cdn.bizible.com/scripts/bizible.js async=""></script>`

>[!NOTE]
>
>Dans ce cas, [!DNL bizible.js] associe un événement &quot;onclick&quot; à l’élément de HTML avec l’identifiant &quot;ConsentButtonId&quot;.

Lorsque vous cliquez sur cet élément de HTML, [!DNL bizible.js] crée un cookie pour vous rappeler que le consentement de l’utilisateur a été reçu et commencer à collecter les données d’analyse comme vous le faites habituellement.

**-ou-**

Option 2 - Remplacer la valeur par défaut [!DNL bizible.js] balise de script avec :

`<script id="bizible-settings" type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" data-requires-user-consent="true"></script>`

Ceci indique : [!DNL bizible.js] pour ne pas effectuer de suivi tant que le consentement n’a pas été atteint, ce qui peut être effectué avec l’API JS suivante :

*window[&#39;Bizible&#39;] = fenêtre[&#39;Bizible&#39;] || { _queue : [], Push : function (o, p) { this._queue.push({ type : o, data: p }); } };*

*Bizible.Push(&#39;Consent&#39;, true);*

**Si vous utilisez [!DNL Google Tag Manager] pour installer le script**, gardez à l’esprit que GTM supprime les attributs data- . Utilisez donc le script suivant à la place :

`<span id="bizible-settings" data-requires-user-consent="true"></span>`
`<script type="text/javascript" src=https://cdn.bizible.com/scripts/bizible.js async=""></script>`

>[!NOTE]
>
>bizible.js crée un cookie afin de vous rappeler que le consentement de l’utilisateur a été reçu et de commencer à collecter les données d’analyse comme d’habitude uniquement après l’appel de l’API JS.

En revanche, les clients peuvent également utiliser cette API pour retirer le consentement de l’utilisateur :

`window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) { this._queue.push({ type: o, data: p }); } };`

`Bizible.Push('Consent', false);`

Lorsque ce code s’exécute, il supprime tous les cookies qui [!DNL bizible.js] créé précédemment et ne procédera à la reprise de la collecte des données d’analyse que si l’utilisateur y consent à nouveau.
