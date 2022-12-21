---
unique-page-id: 18874519
description: Ajouter [!DNL Marketo Measure] Script pour Lightbox Forms - [!DNL Marketo Measure] - Documentation du produit
title: Ajouter [!DNL Marketo Measure] Script pour Lightbox Forms
exl-id: fa9ce480-fc4f-4abd-8555-dbb74849747e
source-git-commit: ae5b77744d523606ce6cfcf48d7e8d5049d5ccb7
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Ajouter [!DNL Marketo Measure] Script pour Lightbox Forms {#adding-marketo-measure-script-to-lightbox-forms}

Découvrez comment ajouter correctement le [!DNL Marketo Measure] JavaScript vers un formulaire dans une Lightbox.

Un cadre lumineux ouvre un formulaire devant votre contenu lorsque le visiteur effectue une action spécifique (c’est-à-dire lorsqu’il clique sur une partie spécifique de la page, passe un certain temps sur la page, etc.). En règle générale, nous demandons simplement que le [!DNL Marketo Measure] JavaScript placé dans l’en-tête de la page d’entrée, mais pour les formulaires dans un cadre lumineux, une étape supplémentaire est nécessaire.

Un formulaire dans un cadre lumineux étant essentiellement un formulaire dans un iFrame, notre script doit être placé dans ce cadre.

Tout d’abord, recherchez l’iFrame . [!UICONTROL Lightbox] form y vit.

![](assets/1.png)

Ensuite, placez le [!DNL Marketo Measure] JavaScript dans l’iFrame.

![](assets/2.png)

Enfin, lorsque le code JavaScript est ajouté, nous vous encourageons à valider le suivi des envois de formulaire en suivant les instructions suivantes :

1. Copiez l&#39;URL de la landing page contenant le [!UICONTROL Lightbox] formulaire.
1. Ouvrez un navigateur Incognito et collez l’URL.
1. Envoyez le formulaire à l’aide d’une adresse électronique unique.
1. Vérifiez que le test a été suivi en vérifiant dans votre CRM l’adresse email unique utilisée. Vérifiez que les données de point de contact sont renseignées.
