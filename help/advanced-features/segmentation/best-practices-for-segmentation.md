---
description: Bonnes pratiques relatives à la segmentation -  [!DNL Marketo Measure]
title: Bonnes pratiques relatives à la segmentation
exl-id: 68281210-383b-4688-86e9-27fbdc1fabbb
feature: Segmentation
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 100%

---


# Bonnes pratiques relatives à la segmentation {#best-practices-for-segmentation}

## Vue d’ensemble {#overview}

La segmentation [!DNL Marketo Measure] vous permet de définir des règles, qui agissent en tant que filtres, en fonction de vos champs CRM. Vous pouvez ainsi les regrouper dans des segments individuels. Ces segments sont ensuite disponibles dans vos tableaux de bord Discover et vos rapports [!DNL Salesforce].

La segmentation fait partie intégrante de votre compte [!DNL Marketo Measure], notamment au sein des tableaux de bord Discover. Comme les tableaux de bord Discover de [!DNL Marketo Measure] affichent un jeu prédéterminé de filtres, la segmentation vous permet de disséquer vos données dans Discover comme vous le feriez dans les rapports [!DNL Salesforce].

Lorsqu’elles sont transmises à [!DNL Salesforce], les valeurs de segment sont écrites dans le champ « Segment » et se trouvent dans n’importe quel type de rapport Buyer Touchpoint. Cela permet d’uniformiser les rapports sur les deux plateformes. Le segment se trouve également dans le détail du point de contact de n’importe quel point de contact.

Lors d’une transmission à [!UICONTROL Discover], les segments apparaissent sous la forme d’un filtre disponible dans le menu déroulant des filtres, situé sur tous les tableaux de bord.

## Bonne pratique {#best-practice}

Gardez à l’esprit les bonnes pratiques suivantes, que vous définissiez la segmentation pour la première fois ou que vous examiniez simplement la segmentation qui a été précédemment définie.

* Ne vous compliquez pas la tâche !
* Alignez le nom du segment sur la nomenclature de votre organisation, c’est-à-dire la catégorie = nom du filtre, le segment = valeur du filtre.
* N’utilisez pas de champs de formule dans vos règles
* Dans la mesure du possible, créez la segmentation à la fois sur les leads/contacts et opportunités afin de pouvoir l’utiliser dans l’entonnoir entier
   * Si vous êtes client ou cliente Marketo Measure Ultimate et que vous avez défini votre objet de tableau de bord par défaut sur Contact, n’utilisez pas les deux champs ci-dessous, spécifiques au prospect ([en savoir plus ici](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}).
      * b2b.personStatus
      * b2b.isConverted
   * Toutes les catégories de segments ne s’aligneront pas sur l’ensemble de l’entonnoir
      * Par exemple, une catégorie de segment « Type d’opportunité » ne sera pas liée aux leads, mais un segment lié à « Région » est probablement une catégorie qui peut être définie dans tout l’entonnoir
* Pensez aux façons dont vous souhaitez actuellement répartir vos données, que ce soit dans le CRM ou dans un outil de BI. Envisagez de procéder en tant que segment dans [!DNL Marketo Measure] afin d’avoir les mêmes rapports dans Discover.

## Bonne pratique de maintenance {#best-practice-for-maintenance}

La vérification de votre segmentation au moins deux fois par an vous permettra de vous assurer qu’elle est à jour. En guise de bonne pratique, il est recommandé de consulter vos règles dans l’onglet [!UICONTROL Segments] de vos Paramètres du compte [!DNL Marketo Measure], ainsi que l’extraction de rapports dans [!DNL Salesforce] pour passer en revue vos segments en action. Ces étapes vous aideront, ainsi que votre équipe, à avoir davantage confiance dans votre segmentation et, par la suite, dans votre création de rapports [!DNL Marketo Measure].

Vous pourrez vouloir réviser votre segmentation pour les raisons suivantes :

* Changements au sein de votre équipe marketing
* Modifications apportées aux champs utilisés pour définir vos segments
* Ajouts ou modifications aux segments déjà créés

>[!MORELIKETHIS]
>[Comment configurer la segmentation personnalisée](/help/advanced-features/segmentation/custom-segmentation.md)
