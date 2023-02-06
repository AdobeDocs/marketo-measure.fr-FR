---
unique-page-id: 18874755
description: Ajouter [!DNL Marketo Measure] to [!DNL Marketo] Pages d’entrée - [!DNL Marketo Measure] - Documentation du produit
title: Ajouter [!DNL Marketo Measure] aux pages d’entrée Marketo
exl-id: 3771d4d2-8723-452a-b23d-cea3b11ab9ee
source-git-commit: 82cc8269bfdb26b6acf039d0ce0e06564f5e2612
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Ajouter [!DNL Marketo Measure] aux pages d’entrée Marketo {#adding-marketo-measure-to-marketo-landing-pages}

Découvrez comment ajouter le suivi à [!DNL Marketo Engage] Pages d’entrée, car elles nécessitent une gestion supplémentaire. [!DNL Marketo Measure] JavaScript doit être en place à la fois sur la page d’entrée et sur la page [!DNL Marketo Engage] formulaire lui-même. Pour ce faire, vous devez charger la variable [!DNL Marketo Measure] JavaScript dans [!DNL Marketo Engage] comme expliqué dans les directions suivantes.

>[!NOTE]
>
>Si vous déployez le code JavaScript par le biais d’un fournisseur de gestion des balises tel que [!DNL Google Tag Manager], vous n’avez pas besoin d’ajouter manuellement [!DNL Marketo Measure] JS vers [!DNL Marketo Engage].

## Comment ajouter [!DNL Marketo Measure] Script vers [!DNL Marketo Engage] Pages d’entrée {#how-to-add-marketo-measure-script-to-marketo-engage-landing-pages}

1. Connectez-vous à [!DNL Marketo Engage] compte .
1. Sélectionnez votre landing page et cliquez sur **[!UICONTROL Modifier le brouillon]**.
1. Faites glisser l’élément HTML .
1. Saisissez le [!DNL Marketo Measure] JavaScript dans la variable [!UICONTROL head] section :

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Exemple dans la capture d’écran ci-dessous

1. Cliquez sur **[!UICONTROL Enregistrer]**.

   ![](assets/adding-bizible-to-marketo-landing-pages-1.png)

## Remarques supplémentaires {#additional-notes}

* D’autres fragments de code de suivi sont peut-être déjà en place, tels qu’un [!DNL Google Analytics] code. Il n’y a pas de problème avec cela. Veillez simplement à les séparer par un point-virgule. `;` et un seul espace. Voici un exemple :

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="someothercode" src="someotherfile.js" ></script>`

* Il est probable que plusieurs modèles de page d’entrée soient utilisés. Veillez à ajouter le code à tous les modèles qui contiennent des formulaires.

* Parfois, lorsque vous modifiez le modèle des landing pages, vous devez réapprouver les pages utilisées par la landing page. Cet article explique : [Approbation en masse](https://experienceleague.adobe.com/docs/marketo/using/product-docs/demand-generation/landing-pages/landing-page-actions/approve-multiple-landing-pages-at-once.html){target="_blank"}.
