---
unique-page-id: 18874755
description: Ajout de [!DNL Marketo Measure] à [!DNL Marketo] Pages d’entrée - [!DNL Marketo Measure]
title: Ajout de  [!DNL Marketo Measure]  à des pages de destination Marketo
exl-id: 3771d4d2-8723-452a-b23d-cea3b11ab9ee
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 3%

---

# Ajout de [!DNL Marketo Measure] aux pages d’entrée Marketo {#adding-marketo-measure-to-marketo-landing-pages}

Découvrez comment ajouter le suivi aux landing pages [!DNL Marketo Engage], car elles nécessitent une gestion supplémentaire. [!DNL Marketo Measure] JavaScript doit être en place sur la page d’entrée et le formulaire [!DNL Marketo Engage] lui-même. Pour ce faire, vous devez charger le [!DNL Marketo Measure] JavaScript dans [!DNL Marketo Engage] comme expliqué dans les instructions suivantes.

>[!NOTE]
>
>Si vous déployez JavaScript par l’intermédiaire d’un fournisseur de gestion des balises tel que [!DNL Google Tag Manager], vous n’avez pas besoin d’ajouter manuellement [!DNL Marketo Measure] JS à [!DNL Marketo Engage].

## Comment ajouter [!DNL Marketo Measure] Script aux [!DNL Marketo Engage] landing pages {#how-to-add-marketo-measure-script-to-marketo-engage-landing-pages}

1. Connectez-vous à votre compte [!DNL Marketo Engage].
1. Sélectionnez votre landing page et cliquez sur **[!UICONTROL Modifier le brouillon]**.
1. Faites glisser l’élément HTML .
1. Saisissez le JavaScript [!DNL Marketo Measure] dans la section [!UICONTROL head] :

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Exemple dans la capture d’écran ci-dessous

1. Cliquez sur **[!UICONTROL Enregistrer]**.

   ![](assets/adding-bizible-to-marketo-landing-pages-1.png)

## Remarques supplémentaires {#additional-notes}

* Il se peut que d’autres fragments de code de suivi soient déjà en place, tels qu’un code [!DNL Google Analytics]. Il n’y a aucun problème avec cela. Veillez à les séparer par un point-virgule `;` et un seul espace. Voici un exemple :

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="someothercode" src="someotherfile.js" ></script>`

* Il est probable que plusieurs modèles de page d’entrée soient utilisés. Veillez à ajouter le code à tous les modèles qui contiennent des formulaires.

* Parfois, lorsque vous éditez le modèle des landing pages, vous devez réapprouver les pages utilisées par la landing page. Cet article explique [comment approuver en masse](https://experienceleague.adobe.com/docs/marketo/using/product-docs/demand-generation/landing-pages/landing-page-actions/approve-multiple-landing-pages-at-once.html?lang=fr){target="_blank"}.
