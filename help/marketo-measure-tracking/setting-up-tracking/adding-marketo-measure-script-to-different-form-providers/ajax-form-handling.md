---
unique-page-id: 18874745
description: Gestion AJAX formulaire - [!DNL Marketo Measure] - Documentation du produit
title: Gestion AJAX formulaire
exl-id: 042e42ff-d8d9-4380-b878-aba4934bc4a0
source-git-commit: ae5b77744d523606ce6cfcf48d7e8d5049d5ccb7
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Gestion AJAX formulaire {#ajax-form-handling}

Pour signaler manuellement les conversions des clients à [!DNL Marketo Measure], nous avons fourni une API très simple que vous pouvez utiliser. Ces deux API JavaScript sont automatiquement disponibles sur votre site, si vous y avez votre code de suivi. Pas besoin de faire quoi que ce soit de spécial pour y accéder.

## Scénario 1 : HTML de formulaire avec envoi AJAX {#scenario-html-form-with-an-ajax-submit}

Lorsque vous utilisez des formulaires contenant des AJAX (ou un autre mécanisme) pour envoyer des dates de conversion du client vers nos serveurs, [!DNL Marketo Measure] peut ne pas connaître la conversion des clients via les chemins standard que nous surveillons. Dans ce scénario, nous pouvons utiliser une API simple (fournie ci-dessous).

Si vous gérez vos propres envois de formulaire, vous pouvez appeler explicitement [!DNL Marketo Measure] de JavaScript. [!DNL Marketo Measure] collectera toutes les informations pertinentes du formulaire et les publiera de manière asynchrone sur nos serveurs.

**Vous trouverez ci-dessous un exemple de code utilisant JQuery (en supposant que l’ID sur le formulaire est &quot;formId&quot;) :**

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// Give Marketo Measure the JQuery Selector for the form and we'll collect the data automatically.  
Bizible.Push('Form',$('#*formId*'));
```

**Vous trouverez ci-dessous un exemple de code n’utilisant pas JQuery (en supposant que l’ID sur le formulaire est &quot;formId&quot;) :**

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// Give Marketo Measure the Form ID and we'll collect the data automatically.
Bizible.Push('Form','MyFormID');
```

## Scénario 2 - Informations de piste collectées dans un formulaire autre qu’un HTML {#scenario-lead-information-collected-in-a-non-html-form}

Si les informations d’une piste convertie sont collectées à l’aide de champs JavaScript ou de champs de texte simples sans formulaire HTML, cette solution fonctionnera pour vous. L’API à utiliser dans ce scénario est partagée ci-dessous :

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// If your site is using Ajax, or you are running a secure site, it is best to send us the data directly.  
Bizible.Push('User', {
eMail: 'user@gmail.com' // required  
});  
```

Dans ce code, la variable [!UICONTROL email] est obligatoire. [!DNL Marketo Measure] publiera ces données de manière asynchrone sur nos serveurs.

## Scénario 3 - Signaler les informations utilisateur à partir de la page de remerciement {#scenario-report-user-information-from-the-thank-you-page}

Dans certains cas, il est plus pratique de signaler les informations de piste à [!DNL Marketo Measure] à partir de la page de remerciement, une fois le formulaire envoyé. La méthode la plus simple pour générer des rapports sur ces informations consiste à ajouter à la page un élément masqué qui contient les informations de l’envoi du formulaire, et [!DNL Bizible.js] lira ces informations lorsque la page de remerciement sera chargée.

**Par exemple:**

```html
<div id="bizible.reportUser" style="display:none"  
data-email="user@gmail.com">  
```

Peu importe que l’élément masqué soit un div, un script ou tout autre type de balise. [!DNL Marketo Measure] recherche l’id=&quot;bizible.reportUser&quot; pour lire les informations.
