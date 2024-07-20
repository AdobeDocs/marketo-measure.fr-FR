---
unique-page-id: 18874753
description: Ajout de [!DNL Marketo Measure] à la Forms d’activation - [!DNL Marketo Measure]
title: Ajout de  [!DNL Marketo Measure]  à des formulaires Act-On
exl-id: 3d246e6a-ad3b-4683-b2b7-ab3f0f4c5ab2
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '76'
ht-degree: 6%

---

# Ajout de [!DNL Marketo Measure] à la Forms d’activation {#adding-marketo-measure-to-act-on-forms}

## Instructions {#directions}

1. Dans le formulaire que vous modifiez, sélectionnez l’option **[!UICONTROL Paramètres]** dans le coin droit.
1. Recherchez une zone intitulée [!UICONTROL &quot;Analyses Web externes&quot;.] C’est là que vous déposez le fragment de code de suivi [!DNL Marketo Measure].

## Code JavaScript [!DNL Marketo Measure] {#marketo-measure-javascript}

`script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

>[!NOTE]
>
>Il peut déjà y avoir d’autres fragments de code de suivi dans cette zone, tels qu’un code [!DNL Google Analytics]. Veillez à les séparer à l’aide d’un point-virgule `;` et d’un espace unique, comme suit :
>
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>**; **<script async="true" type="someothercode" src="someotherfile.js" ></script>`
