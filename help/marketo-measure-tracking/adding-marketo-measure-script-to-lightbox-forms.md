---
description: Ajout  [!DNL Marketo Measure]  script aux conseils Lightbox Forms pour les utilisateurs de Marketo Measure
title: Ajout d’un script  [!DNL Marketo Measure]  à des formulaires Lightbox
exl-id: fa9ce480-fc4f-4abd-8555-dbb74849747e
feature: Tracking
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 2%

---

# Ajout d’un script [!DNL Marketo Measure] à Lightbox Forms {#adding-marketo-measure-script-to-lightbox-forms}

Découvrez comment ajouter correctement le JavaScript [!DNL Marketo Measure] à un formulaire dans une Lightbox.

Un lightbox ouvre un formulaire devant votre contenu lorsque le visiteur effectue une action spécifique (c’est-à-dire cliquer sur une partie particulière de la page, passer un certain temps sur la page, etc.). En règle générale, nous demandons à ce que le [!DNL Marketo Measure] JavaScript soit placé en tête de la page de destination, mais pour les formulaires d’une lightbox, une étape supplémentaire est nécessaire.

Étant donné qu’un formulaire dans une Lightbox est essentiellement un formulaire dans un iFrame, le script est placé dans cet iFrame.

Tout d’abord, localisez l’iFrame dans lequel réside le formulaire [!UICONTROL lightbox].

![Tout d’abord, localisez l’iFrame dans lequel réside le formulaire Lightbox.](assets/adding-providers-8.png)

Placez ensuite le [!DNL Marketo Measure] JavaScript dans l’iFrame.

![Placez ensuite le JavaScript Marketo Measure dans l’iFrame.](assets/adding-providers-5.png)

Enfin, lorsque le JavaScript est ajouté, validez le suivi des envois de formulaires en suivant ces instructions :

1. Copiez l’URL de la page de destination contenant le formulaire [!UICONTROL lightbox].
1. Ouvrez un navigateur Incognito et collez l’URL.
1. Envoyez le formulaire à l’aide d’une adresse e-mail unique.
1. Vérifiez que le test a été suivi en vérifiant dans votre CRM l’adresse e-mail unique utilisée et assurez-vous que les données de point de contact sont renseignées.
