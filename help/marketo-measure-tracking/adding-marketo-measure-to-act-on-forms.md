---
description: Ajout  [!DNL Marketo Measure]  conseils sur les Forms d’action pour les utilisateurs de Marketo Measure
title: Ajout de  [!DNL Marketo Measure]  à des formulaires Act-On
exl-id: 3d246e6a-ad3b-4683-b2b7-ab3f0f4c5ab2
feature: Tracking
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 6%

---

# Ajout de [!DNL Marketo Measure] à Act-On Forms {#adding-marketo-measure-to-act-on-forms}

## Itinéraire {#directions}

1. Dans le formulaire que vous modifiez, sélectionnez l’option **[!UICONTROL Paramètres]** dans le coin droit.
1. Recherchez une zone intitulée [!UICONTROL &#x200B; « Web Analytics externe ».] C’est à cet endroit que vous allez déposer le fragment de code de suivi [!DNL Marketo Measure].

## Code JavaScript [!DNL Marketo Measure] {#marketo-measure-javascript}

`script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

>[!NOTE]
>
>Il se peut qu’il y ait déjà d’autres fragments de code de suivi dans cette zone, comme un code [!DNL Google Analytics]. Veillez à les séparer à l’aide d’un point-virgule `;` d’un seul espace, comme suit :
>
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>**; **<script async="true" type="someothercode" src="someotherfile.js" ></script>`
