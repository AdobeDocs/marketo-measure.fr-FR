---
unique-page-id: 18874759
description: Ajouter [!DNL Marketo Measure] to [!DNL Hubspot] - [!DNL Marketo Measure]
title: Ajouter [!DNL Marketo Measure] to [!DNL Hubspot]
exl-id: 633e7ef7-7959-461e-881f-dcc543595b66
feature: Tracking
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 1%

---

# Ajouter [!DNL Marketo Measure] to [!DNL Hubspot] {#adding-marketo-measure-to-hubspot}

Découvrez comment ajouter le [!DNL Marketo Measure] JavaScript pour effectuer le suivi de votre [!DNL Hubspot] landing pages et envois de formulaire.

La zone réactive est un peu différente des autres systèmes d’automatisation marketing, dans la mesure où elle peut héberger vos landing pages/formulaires ET votre site web. Il est important de noter que les instructions ci-dessous servent à [!DNL Marketo Measure] suivi de l’activité [!DNL Hubspot]- pages hébergées. Si vous mettez votre site web sous tension avec un CMS autre que [!DNL Hubspot] (Par exemple, Wordpress), vous devrez ajouter la variable [!DNL Marketo Measure] JavaScript vers ce CMS également.

>[!NOTE]
>
>Si vous déployez le code JavaScript par le biais d’un fournisseur de gestion des balises tel que [!DNL Google Tag Manager], vous n’avez pas besoin de coder manuellement en dur la variable [!DNL Marketo Measure] JavaScript dans votre site web.

## Prise en main {#getting-started}

Une fois que vous êtes connecté à votre [!DNL Hubspot] , procédez comme suit.

1. Accédez à Contenu.

1. Cliquez sur **[!UICONTROL Paramètres de contenu]**.

1. Within [!UICONTROL Paramètres de contenu], cliquez sur le HTML En-tête du site (voir l’image ci-dessous).

1. Ajoutez le script suivant dans votre `<header>`:

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

   Il doit ressembler à ceci :

```text
<!-- Marketo Measure Javascript -->
<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="">
```

>[!TIP]
>
>Il peut déjà y avoir d’autres fragments de code de suivi dans cette zone, tels qu’un code Google Analytics. Veillez à les séparer par un point-virgule. `;` et un seul espace, comme ceci :
>
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="someothercode" src="someotherfile.js" ></script>`
