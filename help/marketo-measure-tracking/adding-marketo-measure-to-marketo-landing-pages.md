---
description: Ajout de [!DNL Marketo Measure] aux conseils sur les pages de destination de Marketo pour les utilisateurs de Marketo Measure
title: Ajout de [!DNL Marketo Measure] aux pages de destination de Marketo
exl-id: 3771d4d2-8723-452a-b23d-cea3b11ab9ee
feature: Tracking
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: dcbeff6e-0253-5a4b-9ac2-1b67cc4a6286
    internal-label: Tracking
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 2%
---
# Ajout de [!DNL Marketo Measure] aux pages de destination de Marketo {#adding-marketo-measure-to-marketo-landing-pages}

Découvrez comment ajouter le suivi aux pages de destination [!DNL Marketo Engage], car elles nécessitent une manipulation supplémentaire. [!DNL Marketo Measure] JavaScript doit être en place sur la page de destination et sur le formulaire [!DNL Marketo Engage] lui-même. Pour ce faire, vous devez charger le [!DNL Marketo Measure] JavaScript dans [!DNL Marketo Engage], comme expliqué dans les instructions suivantes.

>[!NOTE]
>
>Si vous déployez JavaScript par l’intermédiaire d’un fournisseur de gestion des balises tel que [!DNL Google Tag Manager], vous n’avez pas besoin d’ajouter manuellement [!DNL Marketo Measure] JS à [!DNL Marketo Engage].

## Comment ajouter [!DNL Marketo Measure] script aux pages de destination [!DNL Marketo Engage] {#how-to-add-marketo-measure-script-to-marketo-engage-landing-pages}

1. Connectez-vous à votre compte [!DNL Marketo Engage].
1. Sélectionnez votre page de destination et cliquez sur **[!UICONTROL Modifier le brouillon]**.
1. Faites glisser l’élément HTML.
1. Saisissez le [!DNL Marketo Measure] JavaScript dans la section [!UICONTROL head] :

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Exemple dans la capture d’écran ci-dessous

1. Cliquez sur **[!UICONTROL Enregistrer]**

   ![1. Cliquez sur Enregistrer.](assets/adding-pages-1.png)

## Remarques supplémentaires {#additional-notes}

* Vous avez peut-être déjà mis en place d’autres fragments de code de suivi, tels qu’un code [!DNL Google Analytics]. Cela ne pose aucun problème. Veillez à les séparer par un point-virgule `;` d’un seul espace. Voici un exemple de ce à quoi cela pourrait ressembler :

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="someothercode" src="someotherfile.js" ></script>`

* Il est probable que vous ayez plusieurs modèles de page de destination en cours d’utilisation. Veillez à ajouter le code à tous les modèles comportant des formulaires.

* Parfois, lorsque vous modifiez le modèle pour les pages de destination, vous devez réapprouver les pages par lesquelles la page de destination est utilisée. Cet article explique [comment approuver en masse](https://experienceleague.adobe.com/docs/marketo/using/product-docs/demand-generation/landing-pages/landing-page-actions/approve-multiple-landing-pages-at-once.html){target="_blank"}.
