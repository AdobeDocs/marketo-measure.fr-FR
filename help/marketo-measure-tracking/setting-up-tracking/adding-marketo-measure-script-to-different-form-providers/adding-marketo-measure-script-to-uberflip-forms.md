---
unique-page-id: 18874749
description: Ajouter [!DNL Marketo Measure] Script vers [!DNL Uberflip] FORMS - [!DNL Marketo Measure]
title: Ajouter [!DNL Marketo Measure] Script vers [!DNL Uberflip] Forms
exl-id: fb123e15-523d-4931-b4c1-705fe49be3d0
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# Ajouter [!DNL Marketo Measure] Script vers [!DNL Uberflip] Forms {#adding-marketo-measure-script-to-uberflip-forms}

Si vous utilisez actuellement [!DNL Uberflip] pour gérer votre contenu, il est important de prendre les mesures suivantes pour vous assurer que [!DNL Marketo Measure] effectue le suivi de ces envois de formulaire. Votre gestionnaire de succès à [!DNL Uberflip] devrait également être en mesure de vous aider à cela.

1. Ajoutez ce script à [!DNL Uberflip]&#39;s [!UICONTROL Code personnalisé > HTML] .

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Assurez-vous que [!DNL Marketo Measure] Le code du préambule se déclenche au chargement de la page et lors de la modification AJAX page. Procédez comme suit dans la section [!UICONTROL Code personnalisé > JS] section

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   Ajoutez ce préambule aux deux [!DNL Hubs.onLoad] et la variable [!DNL Hubs.onPageChange] AJAX des hooks d’événement JavaScript, comme ci-dessous. (Remarque : il se peut que vous disposiez également d’un autre code dans ces hooks d’événement. Veillez également à inclure le préambule.)

   `Hubs.onLoad = function () {`

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   `}`

   `Hubs.onPageChange = function () {`

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   `}`

1. Créez et définissez une fonction qui envoie des données à Bizible lors d’un envoi CTA de formulaire. Cela permet d’accéder au [!UICONTROL Code personnalisé > JavaScript] . (Remarque : cette fonction nécessite uniquement le paramètre ctaData Uberflip fourni, mais vous pouvez inclure d’autres paramètres ctaId et ctaName si l’utilisateur souhaite personnaliser son code pour transmettre ces données également).

   `function bizibleFormCode(ctaId, ctaData, ctaName) {`
   `var email = ctaData["email"];`
   `if(email){`
   `Bizible.Push('User', {`
   `eMail: email, // required`
   `}); }`

   `}`

1. Lorsqu’un formulaire CTA est envoyé, assurez-vous que la variable [!DNL Marketo Measure] est exécutée comme ci-dessous. Cela se fait dans la variable [!UICONTROL Code personnalisé > JS] . (Remarque : il se peut que vous disposiez d’un autre code dans le crochet d’événement JavaScript Hubs.onCtaFormSubmitSuccess, veillez également à inclure cet appel de fonction).

   `Hubs.onCtaFormSubmitSuccess = function (ctaId, ctaData, ctaName) {`
   `bizibleFormCode(ctaId, ctaData, ctaName);`\
   `}`
