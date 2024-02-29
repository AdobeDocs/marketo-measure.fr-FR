---
unique-page-id: 18874757
description: Ajouter [!DNL Marketo Measure] JavaScript vers [!DNL Pardot] - [!DNL Marketo Measure]
title: Ajouter [!DNL Marketo Measure] JavaScript vers [!DNL Pardot]
exl-id: e49190ad-aa86-4f8f-a9ed-48de9e937a7e
feature: Tracking
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Ajouter [!DNL Marketo Measure] JavaScript vers [!DNL Pardot] {#adding-marketo-measure-javascript-to-pardot}

[!DNL Pardot] Les formulaires nécessitent une gestion supplémentaire dans le modèle de formulaire, au-delà de l’insertion de scripts sur le site pour que [!DNL Marketo Measure] pour reconnaître les envois de formulaire. Le processus est simple ; il ne nécessite que de placer la variable [!DNL Marketo Measure] script de suivi dans la variable [!DNL Pardot] modèle de formulaire.

## Instructions étape par étape {#step-by-step-instructions}

Une fois que vous êtes connecté à votre [!DNL Pardot] , suivez les étapes ci-dessous.

1. Accédez à **[!UICONTROL Marketing]**.

1. Cliquez sur **[!UICONTROL Pages d’entrée]**.

1. Sélectionner **[!UICONTROL Modèle de mise en page]**.

   ![](assets/1-3.png)

1. Déterminez le modèle de disposition approprié, puis cliquez sur **[!UICONTROL Modifier]** à droite.

   ![](assets/2-1.png)

1. Copiez et collez le [!DNL Marketo Measure] Code JavaScript situé juste avant la balise d’en-tête de fermeture de la page de HTML.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Suivez ces étapes pour tous les modèles de mise en page de page d’entrée applicables.

1. Assurez-vous que la variable [!DNL Marketo Measure] JavaScript se trouve également sur la page générale du site.

   Dans le [!DNL Pardot] Modèle de mise en page, le code ressemblera à ceci :

```text
<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>
   </head>
   <body>
```

## Remarques supplémentaires {#additional-notes}

Si la variable [!DNL Pardot] IFrame comporte la balise de HTML suivante :

`<base href="http://go.pardot.com">`

_Et_ l’IFrame lui-même se trouve en fait sur une page sécurisée (HTTPS) au lieu d’une page non sécurisée (HTTP), lorsque nous tentons de charger notre script sur la variable [!DNL Pardot] Sirame, le navigateur tentera de charger une version HTTP de notre script sur une page HTTPS qui échouera et nous empêchera d’effectuer le suivi. La solution consiste à mettre à jour le script sur la variable [!DNL Pardot] IFrame pour charger la version sécurisée de notre script :

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Il peut également y avoir d’autres fragments de code de suivi dans cette zone, tels qu’une [!DNL Google Analytics] code. Veillez à les séparer par un point-virgule. `;` et un seul espace, comme illustré dans cet exemple :

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="othercode_example" src="otherfile_example.js" ></script>`
