---
unique-page-id: 18874753
description: Ajouter [!DNL Marketo Measure] à la Forms d’activation - [!DNL Marketo Measure]
title: Ajout de  [!DNL Marketo Measure]  à des formulaires Act-On
exl-id: 3d246e6a-ad3b-4683-b2b7-ab3f0f4c5ab2
feature: Tracking
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 6%

---

# Ajouter [!DNL Marketo Measure] à la Forms d’activation {#adding-marketo-measure-to-act-on-forms}

## Instructions {#directions}

1. Dans le formulaire en cours de modification, sélectionnez le **[!UICONTROL Paramètres]** dans le coin droit.
1. Recherchez une zone nommée [!UICONTROL &quot;Analyse Web externe&quot;.] C’est là que vous déposez le [!DNL Marketo Measure] fragment de code de suivi.

## Code JavaScript [!DNL Marketo Measure] {#marketo-measure-javascript}

`script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

>[!NOTE]
>
>Il peut déjà y avoir d’autres fragments de code de suivi dans cette zone, tels qu’une [!DNL Google Analytics] code. Veillez à les séparer à l’aide d’un point-virgule. `;` et un seul espace, comme ceci :
>
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>**; **<script async="true" type="someothercode" src="someotherfile.js" ></script>`
