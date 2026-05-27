---
unique-page-id: 18874753
description: Ajout  [!DNL Marketo Measure]  Forms d'action - [!DNL Marketo Measure]
title: Ajout de  [!DNL Marketo Measure]  à des formulaires Act-On
exl-id: 3d246e6a-ad3b-4683-b2b7-ab3f0f4c5ab2
feature: Tracking
TQID: https://experienceleague.adobe.com/BUdHiCxfaG7a8Tays-Oqg9ZJQjSZJMM4-ChPHuF0RCg
product_v2: id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
source-git-commit: 9ceb54139bfa9b6ce7c2c5fbb4e25e649f5708a3
workflow-type: tm+mt
source-wordcount: 77
ht-degree: 6%

---

# Ajout de [!DNL Marketo Measure] à Act-On Forms {#adding-marketo-measure-to-act-on-forms}

## Itinéraire {#directions}

1. Dans le formulaire que vous modifiez, sélectionnez l’option **[!UICONTROL Paramètres]** dans le coin droit.
1. Recherchez une zone intitulée [!UICONTROL  « Web Analytics externe »] C’est à cet endroit que vous allez déposer le fragment de code de suivi [!DNL Marketo Measure].

## Code JavaScript [!DNL Marketo Measure] {#marketo-measure-javascript}

`script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

>[!NOTE]
>
>Il se peut qu’il y ait déjà d’autres fragments de code de suivi dans cette zone, comme un code [!DNL Google Analytics]. Veillez à les séparer à l’aide d’un point-virgule `;` d’un seul espace, comme suit :
>
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>**; **<script async="true" type="someothercode" src="someotherfile.js" ></script>`
