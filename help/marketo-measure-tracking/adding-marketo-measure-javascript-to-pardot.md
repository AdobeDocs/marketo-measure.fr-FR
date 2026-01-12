---
description: Ajout de [!DNL Marketo Measure] JavaScript à [!DNL Pardot] - [!DNL Marketo Measure]
title: Ajout de  [!DNL Marketo Measure] JavaScript à  [!DNL Pardot]
exl-id: e49190ad-aa86-4f8f-a9ed-48de9e937a7e
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---


# Ajout de [!DNL Marketo Measure] JavaScript à [!DNL Pardot] {#adding-marketo-measure-javascript-to-pardot}

Les formulaires [!DNL Pardot] nécessitent une manipulation supplémentaire dans le modèle de formulaire, au-delà de la mise en place d’un script sur le site pour que les [!DNL Marketo Measure] puissent reconnaître les envois de formulaire. Le processus est simple : il suffit de placer le script de suivi [!DNL Marketo Measure] dans le modèle de formulaire [!DNL Pardot].

## Instructions détaillées {#step-by-step-instructions}

Une fois la connexion à votre compte [!DNL Pardot] effectuée, procédez comme suit.

1. Accédez à **[!UICONTROL Marketing]**.

1. Cliquez sur **[!UICONTROL Pages de destination]**.

1. Sélectionnez **[!UICONTROL Modèle de mise en page]**.

   ![&#x200B; 3](assets/1-3.png)

1. Déterminez le modèle de mise en page approprié et cliquez sur **[!UICONTROL Modifier]** à droite.

   ![&#x200B; 1](assets/2-1.png)

1. Copiez et collez le code JavaScript [!DNL Marketo Measure] juste avant la balise d’en-tête close sur votre page HTML.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Suivez ces étapes pour tous les modèles de mise en page de page de destination applicables.

1. Assurez-vous que le [!DNL Marketo Measure] JavaScript figure également sur la page générale du site.

   Dans le modèle de mise en page [!DNL Pardot], le code se présente comme suit :

```text
<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>
   </head>
   <body>
```

## Remarques supplémentaires {#additional-notes}

Si l’IFrame [!DNL Pardot] comporte la balise HTML suivante :

`<base href="http://go.pardot.com">`

_Et_ l’IFrame lui-même est en fait une page sécurisée (HTTPS) plutôt qu’une page non sécurisée (HTTP). Lors du chargement du script dans l’IFrame [!DNL Pardot], le navigateur tente de charger une version HTTP du script sur une page HTTPS, ce qui échoue et interrompt le suivi. La solution consiste à mettre à jour le script sur l’IFrame [!DNL Pardot] pour charger la version sécurisée du script :

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Il se peut qu’il y ait déjà d’autres fragments de code de suivi dans cette zone, comme un code [!DNL Google Analytics]. Veillez à les séparer par un point-virgule `;` un seul espace, comme illustré dans cet exemple :

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="othercode_example" src="otherfile_example.js" ></script>`
