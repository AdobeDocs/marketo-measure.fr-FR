---
unique-page-id: 18874759
description: Ajout [!DNL Marketo Measure] à [!DNL Hubspot] - [!DNL Marketo Measure]
title: Ajout  [!DNL Marketo Measure]  à  [!DNL Hubspot]
exl-id: 633e7ef7-7959-461e-881f-dcc543595b66
feature: Tracking
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 1%

---

# Ajout de [!DNL Marketo Measure] aux [!DNL Hubspot] {#adding-marketo-measure-to-hubspot}

Découvrez comment ajouter le [!DNL Marketo Measure] JavaScript pour effectuer le suivi de vos pages de destination [!DNL Hubspot] et des envois de formulaires.

Hubspot est un peu différent des autres systèmes d&#39;automatisation marketing dans la mesure où il peut héberger vos landing pages / formulaires ET votre site web. Il est important de noter que les instructions ci-dessous permettent d’effectuer le suivi [!DNL Marketo Measure] de l’activité sur les pages hébergées par [!DNL Hubspot]. Si vous alimentez votre site web avec un CMS autre que [!DNL Hubspot] (par exemple, Wordpress), vous devez également ajouter le JavaScript [!DNL Marketo Measure] à ce CMS.

>[!NOTE]
>
>Si vous déployez JavaScript par l’intermédiaire d’un fournisseur de gestion des balises tel que [!DNL Google Tag Manager], il n’est pas nécessaire de coder manuellement le JavaScript [!DNL Marketo Measure] en dur sur votre site web.

## Prise en main {#getting-started}

Une fois la connexion à votre compte [!DNL Hubspot] effectuée, procédez comme suit.

1. Accédez à Contenu .

1. Cliquez sur **[!UICONTROL Paramètres du contenu]**.

1. Dans [!UICONTROL Paramètres de contenu], cliquez sur l’HTML En-tête du site (voir l’image ci-dessous).

1. Ajoutez le script suivant dans votre `<header>` :

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

   Il doit ressembler à ceci :

```text
<!-- Marketo Measure Javascript -->
<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="">
```

>[!TIP]
>
>Il se peut qu’il existe déjà d’autres fragments de code de suivi dans cette zone, tels qu’un code Google Analytics. Veillez à les séparer par un point-virgule `;` un seul espace, comme suit :
>
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="someothercode" src="someotherfile.js" ></script>`
