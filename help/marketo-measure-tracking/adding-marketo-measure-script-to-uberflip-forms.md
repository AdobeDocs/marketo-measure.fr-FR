---
description: Ajout  [!DNL Marketo Measure]  script à  [!DNL Uberflip] Forms - [!DNL Marketo Measure]
title: Ajout  [!DNL Marketo Measure]  script à  [!DNL Uberflip] Forms
exl-id: fb123e15-523d-4931-b4c1-705fe49be3d0
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---


# Ajout d’[!DNL Marketo Measure] script à [!DNL Uberflip] Forms {#adding-marketo-measure-script-to-uberflip-forms}

Si vous utilisez actuellement [!DNL Uberflip] pour gérer votre contenu, il est important de prendre les mesures nécessaires pour vous assurer que [!DNL Marketo Measure] effectue le suivi de ces envois de formulaire. Votre Responsable Succès chez [!DNL Uberflip] devrait également pouvoir vous aider à cet égard.

1. Ajoutez ce script à la section [!DNL Uberflip]Custom Code>HTML[!UICONTROL  de ].

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Assurez-vous que ce code de préambule [!DNL Marketo Measure] se déclenche au chargement de la page et au changement de page AJAX. Effectuez cette opération dans la section [!UICONTROL Code personnalisé>JS]

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   Ajoutez ce préambule aux hooks d’événement AJAX JavaScript [!DNL Hubs.onLoad] et [!DNL Hubs.onPageChange] ci-dessous. (Remarque : ces hooks d’événement peuvent également contenir d’autres codes. Veillez également à inclure le préambule.)

```javascript
   Hubs.onLoad = function () {
    window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };
   }
   Hubs.onPageChange = function () {
   window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };
   }
```

1. Créez et définissez une fonction qui envoie des données à Bizible lors d’un envoi de CTA de formulaire. Cela se trouve dans la section [!UICONTROL Code personnalisé>JavaScript]. (Remarque : cette fonction ne nécessite que le paramètre ctaData fourni par Uberflip, mais vous pouvez inclure les autres paramètres ctaId et ctaName au cas où l&#39;utilisateur souhaiterait personnaliser son code pour transmettre également ces données.)

```javascript
function bizibleFormCode(ctaId, ctaData, ctaName) {
   var email = ctaData["email"];
   if (email) {
      Bizible.Push('User', {
         eMail: email, // required
      });
   }
}
```

1. Lorsqu’un CTA de formulaire est envoyé, assurez-vous que votre fonction [!DNL Marketo Measure] est exécutée conformément aux instructions ci-dessous. Cette opération est effectuée dans la section [!UICONTROL Code personnalisé>JS]. (Remarque : si vous disposez d’un autre code dans le hook d’événement JavaScript Hubs.onCtaFormSubmitSuccess, veillez à inclure également cet appel de fonction).

   `Hubs.onCtaFormSubmitSuccess = function (ctaId, ctaData, ctaName) {`
   `bizibleFormCode(ctaId, ctaData, ctaName);`\
   `}`
