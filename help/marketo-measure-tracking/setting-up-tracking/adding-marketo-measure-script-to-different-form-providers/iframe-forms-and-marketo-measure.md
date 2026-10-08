---
unique-page-id: 18874741
description: IFrame Forms et [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: Formulaires IFrame et [!DNL Marketo Measure]
exl-id: fe8d7403-27be-4702-a1b6-d574e1243c0a
feature: Tracking
TQID: 'https://experienceleague.adobe.com/qR5a7F-h839nvcMRlQ6x6qjkQK3plhZO30aEzqxD00s'
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: dcbeff6e-0253-5a4b-9ac2-1b67cc4a6286
    internal-label: Tracking
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 85%
---
# Formulaires IFrame et [!DNL Marketo Measure] {#iframe-forms-and-marketo-measure}

Avec [!DNL Marketo Measure], l’une des principales fonctionnalités est le suivi de vos efforts de marketing numérique par le biais de sessions sur votre site et d’envois de formulaire. En règle générale, lorsque le code JavaScript est placé sur le site, nous le joignons automatiquement à tous les formulaires du site. Toutefois, cette fonctionnalité est limitée si le formulaire est contenu dans un IFrame.

Considérez un IFrame comme une page intégrée dans une page. De la même manière que nous demandons l’ajout du script à toutes les pages de votre site, nous avons besoin que le script soit placé dans l’IFrame afin de garantir le suivi.

Dans de nombreux cas, l’IFrame est géré via un fournisseur d’automatisation du marketing. Vous devrez donc le configurer dans cette plateforme ou via votre fournisseur de formulaires.

Il est recommandé de placer le code JavaScript dans l’élément « head » de l’IFrame. À partir de là, nous nous connecterons automatiquement aux formulaires présents dans ce cadre.

![](assets/1-1.png)

Si vous avez des questions sur l’ajout de notre JavaScript aux formulaires IFrame, contactez l’équipe du compte Adobe (votre gestionnaire de compte) ou l’assistance de [Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
