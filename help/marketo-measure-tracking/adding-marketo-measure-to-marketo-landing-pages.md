---
description: Ajout [!DNL Marketo Measure] aux [!DNL Marketo] pages de destination - [!DNL Marketo Measure]
title: Ajout de  [!DNL Marketo Measure]  à des pages de destination Marketo
exl-id: 3771d4d2-8723-452a-b23d-cea3b11ab9ee
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 3%

---


# Ajout de [!DNL Marketo Measure] aux pages de destination de Marketo {#adding-marketo-measure-to-marketo-landing-pages}

Découvrez comment ajouter le suivi aux pages de destination [!DNL Marketo Engage], car elles nécessitent une manipulation supplémentaire. [!DNL Marketo Measure] JavaScript doit être en place sur la page de destination et sur le formulaire [!DNL Marketo Engage] lui-même. Pour ce faire, vous devez charger le [!DNL Marketo Measure] JavaScript dans [!DNL Marketo Engage], comme expliqué dans les instructions suivantes.

>[!NOTE]
>Si vous déployez JavaScript par l’intermédiaire d’un fournisseur de gestion des balises tel que [!DNL Google Tag Manager], vous n’avez pas besoin d’ajouter manuellement [!DNL Marketo Measure] JS à [!DNL Marketo Engage].

## Comment ajouter [!DNL Marketo Measure] script aux pages de destination [!DNL Marketo Engage] {#how-to-add-marketo-measure-script-to-marketo-engage-landing-pages}

1. Connectez-vous à votre compte [!DNL Marketo Engage].
1. Sélectionnez votre page de destination et cliquez sur **[!UICONTROL Modifier le brouillon]**.
1. Faites glisser l’élément HTML.
1. Saisissez le [!DNL Marketo Measure] JavaScript dans la section [!UICONTROL head] :

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Exemple dans la capture d’écran ci-dessous

1. Cliquez sur **[!UICONTROL Enregistrer]**

   ![Éditeur de page de destination Marketo avec script Bizible ajouté à l’en-tête](assets/adding-bizible-to-marketo-landing-pages-1.png)

## Remarques supplémentaires {#additional-notes}

* Vous avez peut-être déjà mis en place d’autres fragments de code de suivi, tels qu’un code [!DNL Google Analytics]. Cela ne pose aucun problème. Veillez à les séparer par un point-virgule `;` d’un seul espace. Voici un exemple de ce à quoi cela pourrait ressembler :

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="someothercode" src="someotherfile.js" ></script>`

* Il est probable que vous ayez plusieurs modèles de page de destination en cours d’utilisation. Veillez à ajouter le code à tous les modèles comportant des formulaires.

* Parfois, lorsque vous modifiez le modèle pour les pages de destination, vous devez réapprouver les pages par lesquelles la page de destination est utilisée. Cet article explique [comment approuver en masse](https://experienceleague.adobe.com/docs/marketo/using/product-docs/demand-generation/landing-pages/landing-page-actions/approve-multiple-landing-pages-at-once.html?lang=fr){target="_blank"}.
