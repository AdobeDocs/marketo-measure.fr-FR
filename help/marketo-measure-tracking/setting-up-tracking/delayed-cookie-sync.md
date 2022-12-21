---
unique-page-id: 30082018
description: Synchronisation des cookies retardée - [!DNL Marketo Measure] - Documentation du produit
title: Synchronisation différée des cookies
exl-id: 394053ed-5642-48e4-b83c-c483a58ebbd7
source-git-commit: ae5b77744d523606ce6cfcf48d7e8d5049d5ccb7
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# Synchronisation différée des cookies {#delayed-cookie-sync}

Cette modification de la valeur par défaut [!DNL Marketo Measure] JavaScript fournit les [!DNL bizible.js] Prise en charge des API, de sorte que vous puissiez configurer le JS pour stocker temporairement les activités des utilisateurs des visiteurs, mais pas pour envoyer les informations au [!DNL Marketo Measure] jusqu’à ce que l’utilisateur donne son consentement.

## Procédures {#how-to}

Remplacer la valeur par défaut [!DNL bizible.js] balise de script avec les éléments suivants :

`<script id="bizible-settings" type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" data-consent-button-id="ConsentButtonId"></script>`

L’attribut data-consent-button-id=&quot;ConsentButtonId&quot; indique [!DNL bizible.js] pour ne pas envoyer de données d’analyse tant qu’un élément de HTML avec cet identifiant n’a pas été cliqué.

Les clients peuvent également définir la variable [!UICONTROL data-consent-button-id] pour être inexistant (par exemple, &quot;foobar&quot;) et utiliser l’API suivante pour indiquer [!DNL bizible.js] que l’utilisateur a consenti :

`window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`
`Bizible.Push("Consent", true });`

>[!NOTE]
>
>Le consentement de l’utilisateur est enregistré dans le cookie, ce qui signifie qu’une fois que l’utilisateur a consenti, il n’est plus nécessaire d’effectuer cet appel sur les pages suivantes.

## Limitation {#limitation}

Parce que [!DNL bizible.js] enregistre temporairement les activités web non envoyées dans les cookies propriétaires des clients et la taille des cookies propriétaires est limitée. seules trois demandes non envoyées peuvent être enregistrées à un moment donné.

S’il existe déjà trois requêtes en attente, toutes les activités suivantes seront ignorées ; cela permet de conserver la première page vue, qui contient des informations précieuses sur le référent.
