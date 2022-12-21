---
description: Bonnes pratiques relatives à la segmentation - [!DNL Marketo Measure] - Documentation du produit
title: Bonnes pratiques relatives à la segmentation
exl-id: 68281210-383b-4688-86e9-27fbdc1fabbb
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# Bonnes pratiques relatives à la segmentation {#best-practices-for-segmentation}

## APERÇU {#overview}

[!DNL Marketo Measure] La segmentation vous permet de définir des règles, qui sont essentiellement des filtres, en fonction de vos champs CRM afin de les regrouper dans des segments individuels. Ces segments seront ensuite disponibles dans vos tableaux de bord Discover , ainsi que dans vos [!DNL Salesforce] création de rapports.

La segmentation est essentielle à l’utilisation de [!DNL Marketo Measure] , notamment au sein des panoramas Discover. Parce que la variable [!DNL Marketo Measure] Les panoramas Discover se limitent à un ensemble prédéterminé de filtres ; la segmentation vous permet de disséquer vos données dans Discover comme vous le feriez dans votre [!DNL Salesforce] création de rapports.

Lorsque la variable est envoyée à [!DNL Salesforce], les valeurs de segment sont écrites dans le champ &quot;Segment&quot; et se trouvent dans n’importe quel type de rapport de point de contact Acheteur. Cela permet d’uniformiser les rapports sur les deux plateformes. Le segment se trouve également sur le &quot;détail du point de contact&quot; de n’importe quel point de contact.

Lorsque vous accédez à Discover, les segments apparaissent sous la forme d’un filtre disponible dans le menu déroulant de filtre situé sur tous les panoramas.

## Bonne pratique {#best-practice}

Gardez à l’esprit les bonnes pratiques suivantes, que vous définissiez la segmentation pour la première fois ou que vous examiniez simplement la segmentation qui a été précédemment définie.

* Restez simple !
* Alignez le nom du segment sur la nomenclature de votre organisation, c’est-à-dire la catégorie = nom du filtre, le segment = valeur du filtre.
* Ne pas utiliser de champs de formule dans vos règles
* Dans la mesure du possible, créez la segmentation à la fois sur les pistes/contacts et opportunités afin de pouvoir l’utiliser dans l’entonnoir entier.
   * Toutes les catégories de segments ne s’aligneront pas sur l’ensemble de l’entonnoir.
      * Par exemple, une catégorie de segment &quot;Type d’opportunité&quot; ne sera pas liée aux pistes, mais un segment lié à &quot;région&quot; est probablement une catégorie qui peut être définie dans tout l’entonnoir.
* Pensez aux façons dont vous souhaitez actuellement répartir vos données, que ce soit dans le CRM ou dans un outil de BI, envisagez de créer ceci en tant que segment dans [!DNL Marketo Measure] afin que vous puissiez avoir le même rapport dans Discover.

## Bonne pratique pour la maintenance {#best-practice-for-maintenance}

La vérification de votre segmentation au moins deux fois par an vous permettra de vous assurer que votre segmentation est à jour. Il est recommandé de consulter vos règles dans le[!UICONTROL Segments]Onglet &#39; de votre [!DNL Marketo Measure] Paramètres du compte, ainsi que l’extraction de rapports dans [!DNL Salesforce] pour passer en revue vos segments en action. Ces étapes vous aideront, ainsi que votre équipe, à vous sentir confiant dans votre segmentation et, par la suite, dans votre [!DNL Marketo Measure] création de rapports.

D’autres raisons peuvent déclencher une révision de votre segmentation, telles que...

* Chiffre d’affaires de votre équipe marketing
* Modifications apportées aux champs utilisés pour définir vos segments
* Ajouts ou modifications aux segments déjà créés

>[!MORELIKETHIS]
>
>[Configuration de la segmentation personnalisée](/help/advanced-marketo-measure-features/segmentation/custom-segmentation.md)
