---
unique-page-id: 18874759
description: Ajout de [!DNL Marketo Measure] à [!DNL Hubspot] - [!DNL Marketo Measure]
title: Ajout de [!DNL Marketo Measure] à [!DNL Hubspot]
exl-id: 633e7ef7-7959-461e-881f-dcc543595b66
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 1%

---

# Ajout de [!DNL Marketo Measure] à [!DNL Hubspot] {#adding-marketo-measure-to-hubspot}

Découvrez comment ajouter le JavaScript [!DNL Marketo Measure] pour effectuer le suivi de vos [!DNL Hubspot] landing pages et envois de formulaire.

La zone réactive est un peu différente des autres systèmes d’automatisation marketing, dans la mesure où elle peut héberger vos landing pages/formulaires ET votre site web. Il est important de noter que les instructions ci-dessous concernent l’activité de suivi [!DNL Marketo Measure] sur des pages hébergées par [!DNL Hubspot]. Si vous mettez votre site web sous tension avec un CMS autre que [!DNL Hubspot] (par exemple, Wordpress), vous devez également ajouter le JavaScript [!DNL Marketo Measure] à ce CMS.

>[!NOTE]
>
>Si vous déployez JavaScript par l’intermédiaire d’un fournisseur de gestion des balises tel que [!DNL Google Tag Manager], il n’est pas nécessaire de coder manuellement en dur le JavaScript [!DNL Marketo Measure] sur votre site web.

## Prise en main {#getting-started}

Une fois que vous êtes connecté à votre compte [!DNL Hubspot], procédez comme suit.

1. Accédez à Contenu.

1. Cliquez sur **[!UICONTROL Paramètres de contenu]**.

1. Dans [!UICONTROL Paramètres Contenu], cliquez sur l’HTML En-tête du site (voir l’image ci-dessous).

1. Ajoutez le script suivant dans votre `<header>` :

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

   Il doit ressembler à ceci :

```text
<!-- Marketo Measure Javascript -->
<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="">
```

>[!TIP]
>
>Il peut déjà y avoir d’autres fragments de code de suivi dans cette zone, tels qu’un code Google Analytics. Veillez à les séparer par un point-virgule `;` et un espace unique, comme suit :
>
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="someothercode" src="someotherfile.js" ></script>`
