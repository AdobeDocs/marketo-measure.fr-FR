---
unique-page-id: 18874745
description: Gestion des formulaires AJAX - [!DNL Marketo Measure]
title: Gestion des formulaires AJAX
exl-id: 042e42ff-d8d9-4380-b878-aba4934bc4a0
feature: Tracking
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 1%

---

# Gestion des formulaires AJAX {#ajax-form-handling}

Pour signaler manuellement des conversions de clients à [!DNL Marketo Measure], vous pouvez utiliser une API simple. Ces deux API JavaScript sont automatiquement disponibles sur votre site, si vous y avez ajouté du code de suivi. Pas besoin de faire quoi que ce soit de spécial pour y accéder.

## Scénario 1 : formulaire HTML avec envoi AJAX {#scenario-html-form-with-an-ajax-submit}

Lors de l’utilisation de formulaires contenant AJAX (ou un autre mécanisme) pour envoyer des dates de conversion du client à nos serveurs, [!DNL Marketo Measure] ne sommes peut-être pas au courant de la conversion du client par l’intermédiaire de l’un des chemins d’accès standard que nous surveillons. Dans ce scénario, nous pouvons utiliser une API simple (fournie ci-dessous).

Si vous gérez vos propres envois de formulaire, vous pouvez appeler explicitement [!DNL Marketo Measure] depuis le JavaScript. [!DNL Marketo Measure] collecte toutes les informations pertinentes du formulaire et les publie de manière asynchrone sur nos serveurs.

**Vous trouverez ci-dessous un exemple de code utilisant JQuery (en supposant que l’ID du formulaire soit « formId ») :**

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// Give Marketo Measure the JQuery Selector for the form and we'll collect the data automatically.  
Bizible.Push('Form',$('#*formId*'));
```

**Vous trouverez ci-dessous un exemple de code n’utilisant pas JQuery (en supposant que l’identifiant sur le formulaire soit « formId ») :**

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// Give Marketo Measure the Form ID and we'll collect the data automatically.
Bizible.Push('Form','MyFormID');
```

## Scénario 2 - Informations de lead collectées dans un formulaire non HTML {#scenario-lead-information-collected-in-a-non-html-form}

Si les informations d’un prospect converti sont collectées à l’aide de JavaScript ou de champs de texte simples sans formulaire HTML, cette solution fonctionne pour vous. Partagé ci-dessous est l’API à utiliser dans ce scénario :

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// If your site is using Ajax, or you are running a secure site, it is best to send us the data directly.  
Bizible.Push('User', {
eMail: 'user@gmail.com' // required  
});  
```

Dans ce code, le champ [!UICONTROL e-mail] est obligatoire. [!DNL Marketo Measure] publie ces données de manière asynchrone sur nos serveurs.

## Scénario 3 - Signaler les informations sur l’utilisateur à partir de la page de remerciement {#scenario-report-user-information-from-the-thank-you-page}

Parfois, il est plus pratique de signaler les informations de prospect à [!DNL Marketo Measure] à partir de la page de remerciement, une fois le formulaire envoyé. La méthode la plus simple pour signaler ces informations consiste à ajouter un élément masqué à la page qui contient les informations issues de l’envoi du formulaire. [!DNL Bizible.js] lirez ces informations lorsque la page « Merci » sera chargée.

**Par exemple :**

```html
<div id="bizible.reportUser" style="display:none"  
data-email="user@gmail.com">  
```

Peu importe que l’élément masqué soit un div, un script ou tout autre type de balise. [!DNL Marketo Measure] recherche l’id=« bizible.reportUser » pour lire les informations.
