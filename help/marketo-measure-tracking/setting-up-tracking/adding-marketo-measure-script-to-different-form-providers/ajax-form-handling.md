---
unique-page-id: 18874745
description: Gestion AJAX formulaire - [!DNL Marketo Measure]
title: Gestion des formulaires AJAX
exl-id: 042e42ff-d8d9-4380-b878-aba4934bc4a0
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 1%

---

# Gestion des formulaires AJAX {#ajax-form-handling}

Pour signaler manuellement les conversions des clients vers [!DNL Marketo Measure], vous pouvez utiliser une API simple. Ces deux API JavaScript sont automatiquement disponibles sur votre site, si vous y avez du code de suivi. Il n&#39;est pas nécessaire de faire quoi que ce soit de spécial pour y accéder.

## Scénario 1 : HTML d’un formulaire avec envoi AJAX {#scenario-html-form-with-an-ajax-submit}

Lorsque vous utilisez des formulaires contenant des AJAX (ou un autre mécanisme) pour envoyer des dates de conversion du client vers nos serveurs, [!DNL Marketo Measure] peut ne pas connaître la conversion du client via l’un des chemins standard que nous surveillons. Dans ce scénario, nous pouvons utiliser une API simple (fournie ci-dessous).

Si vous gérez vos propres envois de formulaire, vous pouvez appeler explicitement [!DNL Marketo Measure] à partir de JavaScript. [!DNL Marketo Measure] collecte toutes les informations pertinentes du formulaire et les publie de manière asynchrone sur nos serveurs.

**Voici un exemple de code utilisant JQuery (en supposant que l&#39;ID sur le formulaire est &quot;formId&quot;) :**

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// Give Marketo Measure the JQuery Selector for the form and we'll collect the data automatically.  
Bizible.Push('Form',$('#*formId*'));
```

**Voici un exemple de code n’utilisant pas JQuery (en supposant que l’ID sur le formulaire est &quot;formId&quot;) :**

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// Give Marketo Measure the Form ID and we'll collect the data automatically.
Bizible.Push('Form','MyFormID');
```

## Scénario 2 - Informations de piste collectées dans un formulaire non HTML {#scenario-lead-information-collected-in-a-non-html-form}

Si les informations d’une piste convertie sont collectées à l’aide de JavaScript ou de champs de texte simple sans formulaire HTML, cette solution fonctionne pour vous. L’API à utiliser dans ce scénario est partagée ci-dessous :

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// If your site is using Ajax, or you are running a secure site, it is best to send us the data directly.  
Bizible.Push('User', {
eMail: 'user@gmail.com' // required  
});  
```

Dans ce code, le champ [!UICONTROL email] est requis. [!DNL Marketo Measure] publie ces données de manière asynchrone sur nos serveurs.

## Scénario 3 - Signaler les informations utilisateur à partir de la page de remerciement {#scenario-report-user-information-from-the-thank-you-page}

Parfois, il est plus pratique de signaler les informations de piste à [!DNL Marketo Measure] à partir de la page de remerciement, une fois le formulaire envoyé. La méthode la plus simple pour signaler ces informations consiste à ajouter à la page un élément masqué qui contient les informations de l’envoi du formulaire, et [!DNL Bizible.js] lira ces informations lorsque la page de remerciement aura été chargée.

**Par exemple :**

```html
<div id="bizible.reportUser" style="display:none"  
data-email="user@gmail.com">  
```

Peu importe que l’élément masqué soit un div, un script ou tout autre type de balise. [!DNL Marketo Measure] recherche l’id=&quot;bizible.reportUser&quot; pour lire les informations.
