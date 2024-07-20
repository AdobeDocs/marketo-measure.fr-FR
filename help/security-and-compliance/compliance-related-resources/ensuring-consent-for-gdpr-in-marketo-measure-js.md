---
unique-page-id: 35586069
description: Garantir le consentement au RGPD dans Marketo Measure Js - Marketo Measure - Documentation du produit
title: Garantir le consentement au RGPD dans Marketo Measure Js
exl-id: 9afc5e4d-cf97-4c49-b9ee-ee1cc99c1f90
feature: Tracking
source-git-commit: 4787f765348da71bc149c997470ce678ba498772
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 100%

---

# Garantir le consentement au RGPD dans Marketo Measure Js {#ensuring-consent-for-gdpr-in-marketo-measure-js}

Le Règlement général sur la protection des données (RGPD) est une loi de l’Union européenne entrée en vigueur le 25 mai 2018.

## Vue d’ensemble {#overview}

Le RGPD a pour but de renforcer les droits des personnes concernées au sein de l’Union européenne (UE) et de l’Espace économique européen (EEE) concernant l’utilisation et la protection de leurs données personnelles. Le terme « Données personnelles » désigne toute information relative à une personne physique, identifiée ou identifiable. Le RGPD s’applique à toute organisation à l’intérieur ou à l’extérieur de l’UE qui commercialise des biens ou des services et/ou qui suit les comportements des personnes concernées au sein de l’UE et de l’EEE. Si vous faites affaire avec des personnes concernées en Europe, et que cela implique de traiter leurs données personnelles, cette législation s’applique à vous. Les sanctions en cas de non-conformité sont importantes, avec de lourdes amendes pour les personnes qui enfreignent le règlement. L’amende maximale pour une violation unique est de 20 millions d’euros ou 4 % du chiffre d’affaires annuel mondial, le montant le plus élevé s’appliquant.

Par défaut, [!DNL bizible.js] collecte les données d’analyse des utilisateurs et utilisatrices, sauf si la configuration spécifie qu’il convient d’attendre le consentement. Lorsque [!DNL bizible.js] est configuré pour attendre le consentement de l’utilisateur ou l’utilisatrice, il ne crée aucun cookie et n’envoie aucune donnée d’analyse tant que le consentement n’est pas confirmé.

## Comment attendre le consentement {#how-to-wait-for-consent}

Il existe deux façons de définir [!DNL bizible.js] afin d’attendre le consentement.

Option 1 - Remplacer la balise par défaut du script [!DNL bizible.js] par :

`<script id="bizible-settings" type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" data-consent-button-id="ConsentButtonId"></script>`

**Si vous utilisez [!DNL Google Tag Manager] pour installer le script**, gardez à l’esprit que GTM supprime les attributs data-. Utilisez donc le script suivant à la place :

`<span id="bizible-settings" data-consent-button-id="ConsentButtonId"></span>`
`<script type="text/javascript" src=https://cdn.bizible.com/scripts/bizible.js async=""></script>`

>[!NOTE]
>
>Dans ce cas, [!DNL bizible.js] associe un événement on-click à l’élément HTML avec l’identifiant « ConsentButtonId ».

Lorsque vous cliquez sur cet élément HTML, [!DNL bizible.js] crée un cookie pour vous rappeler que le consentement de l’utilisateur ou l’utilisatrice a été reçu et de commencer à collecter les données d’analyse comme vous le faites habituellement.

**-ou-**

Option 2 - Remplacer la balise de script par défaut [!DNL bizible.js] par :

`<script id="bizible-settings" type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" data-requires-user-consent="true"></script>`

Ceci indique à [!DNL bizible.js] de ne pas effectuer de suivi tant que le consentement n’a pas été confirmé, ce qui peut être effectué avec l’API JS suivante :

*window[&#39;Bizible&#39;] = window[&#39;Bizible&#39;] || { _queue: [], Push: function (o, p) { this._queue.push({ type: o, data: p }); } };*

*Bizible. Push(&#39;Consent&#39;, true);*

**Si vous utilisez [!DNL Google Tag Manager] pour installer le script**, gardez à l’esprit que GTM supprime les attributs data-. Utilisez donc le script suivant à la place :

`<span id="bizible-settings" data-requires-user-consent="true"></span>`
`<script type="text/javascript" src=https://cdn.bizible.com/scripts/bizible.js async=""></script>`

>[!NOTE]
>
>bizible.js crée un cookie afin de vous rappeler que le consentement de l’utilisateur ou l’utilisatrice a été reçu et de commencer à collecter les données d’analyse comme vous le faites habituellement, uniquement après l’appel de l’API JS.

En revanche, les clientes et clients peuvent également utiliser cette API pour retirer le consentement de l’utilisateur ou l’utilisatrice :

`window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) { this._queue.push({ type: o, data: p }); } };`

`Bizible.Push('Consent', false);`

Lorsque ce code s’exécute, il supprime tous les cookies que [!DNL bizible.js] a créés précédemment et ne reprend la collecte des données d’analyse que si l’utilisateur ou l’utilisatrice y consent à nouveau.
