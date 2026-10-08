---
description: Bonnes pratiques relatives aux conseils de segmentation pour les utilisateurs de Marketo Measure
title: Bonnes pratiques relatives à la segmentation
exl-id: 68281210-383b-4688-86e9-27fbdc1fabbb
feature: Segmentation
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: d3432b7d-03be-560e-8abb-8681f1afaeb4
    internal-label: Segmentation
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 98%
---
# Bonnes pratiques relatives à la segmentation {#best-practices-for-segmentation}

## Vue d’ensemble {#overview}

La segmentation [!DNL Marketo Measure] vous permet de définir des règles, qui agissent en tant que filtres, en fonction de vos champs CRM. Vous pouvez ainsi les regrouper dans des segments individuels. Ces segments sont ensuite disponibles dans vos tableaux de bord Discover et vos rapports [!DNL Salesforce].

La segmentation fait partie intégrante de votre compte [!DNL Marketo Measure], notamment au sein des tableaux de bord Discover. Comme les tableaux de bord Discover de [!DNL Marketo Measure] affichent un jeu prédéterminé de filtres, la segmentation vous permet de disséquer vos données dans Discover comme vous le feriez dans les rapports [!DNL Salesforce].

Lorsqu’elles sont transmises à [!DNL Salesforce], les valeurs de segment sont écrites dans le champ « Segment » et se trouvent dans n’importe quel type de rapport Buyer Touchpoint. Cela permet d’uniformiser les rapports sur les deux plateformes. Le segment se trouve également dans la section des détails de n’importe quel point de contact.

Lors d’une transmission à [!UICONTROL Discover], les segments apparaissent sous la forme d’un filtre disponible dans le menu déroulant des filtres, situé sur tous les tableaux de bord.

## Bonne pratique {#best-practice}

Gardez à l’esprit les bonnes pratiques suivantes, que vous définissiez la segmentation pour la première fois ou que vous examiniez simplement la segmentation qui a été précédemment définie.

* Ne vous compliquez pas la tâche !
* Alignez le nom du segment sur la nomenclature de votre organisation, c’est-à-dire la catégorie = nom du filtre, le segment = valeur du filtre.
* N’utilisez pas de champs de formule dans vos règles
* Dans la mesure du possible, créez la segmentation à la fois sur les leads/contacts et les opportunités afin de pouvoir l’utiliser dans l’ensemble du funnel.
  * Si vous êtes client ou cliente Marketo Measure Ultimate et que vous avez défini votre objet de tableau de bord par défaut sur Contact, n’utilisez pas les deux champs ci-dessous, spécifiques au prospect ([en savoir plus ici](/help/data-integrity-requirement.md){target="_blank"}).
    * b2b.personStatus
    * b2b.isConverted
  * Toutes les catégories de segments ne s’appliquent pas nécessairement à l’ensemble du funnel.
    * Par exemple, une catégorie de segment telle que « Type d’opportunité » ne s&#39;applique pas aux leads, tandis qu’un segment lié à « Zone géographique » peut généralement être défini dans tout le funnel.
* Pensez aux façons dont vous souhaitez actuellement répartir vos données, que ce soit dans le CRM ou dans un outil de BI. Envisagez de procéder en tant que segment dans [!DNL Marketo Measure] afin d’avoir les mêmes rapports dans Discover.

## Bonne pratique de maintenance {#best-practice-for-maintenance}

La vérification de votre segmentation au moins deux fois par an vous permettra de vous assurer qu’elle est à jour. En guise de bonne pratique, il est recommandé de consulter vos règles dans l’onglet [!UICONTROL Segments] de vos Paramètres du compte [!DNL Marketo Measure], ainsi que l’extraction de rapports dans [!DNL Salesforce] pour passer en revue vos segments en action. Ces étapes vous aideront, ainsi que votre équipe, à avoir davantage confiance dans votre segmentation et, par la suite, dans votre création de rapports [!DNL Marketo Measure].

Vous pourrez vouloir réviser votre segmentation pour les raisons suivantes :

* Changements au sein de votre équipe marketing
* Modifications apportées aux champs utilisés pour définir vos segments
* Ajouts ou modifications aux segments déjà créés

>[!MORELIKETHIS]
>
>[Comment configurer la segmentation personnalisée](/help/channel-tracking-and-setup/custom-segmentation.md)
