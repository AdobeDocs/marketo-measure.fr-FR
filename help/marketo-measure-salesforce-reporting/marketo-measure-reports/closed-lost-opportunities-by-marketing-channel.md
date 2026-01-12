---
description: Opportunités closes et perdues par canal marketing - [!DNL Marketo Measure]
title: Opportunités concrétisées ou perdues par canal marketing
exl-id: 010169fc-f7e7-4ab2-92fe-87e4250dd536
feature: Channels, Reporting
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 3%

---


# Opportunités concrétisées ou perdues par canal marketing {#closed-lost-opportunities-by-marketing-channel}

Bien que ce rapport puisse dépendre de vos étapes d’opportunité, il dévoilera quels canaux marketing ont contribué à des opportunités qui ne sont pas fermées et confirmées.

1. Cliquez sur l’onglet **[!UICONTROL Rapports]** dans Salesforce et sélectionnez **[!UICONTROL Nouveau rapport]**.

   ![Onglet Rapports Salesforce avec le bouton Nouveau rapport en surbrillance](assets/1-3.jpg)

1. Dans le type de recherche rapide dans « Attribution Bizible » et sélectionnez le type de rapport **[!UICONTROL Point de contact d’attribution Bizible avec opportunité]**, puis sélectionnez **[!UICONTROL Créer]**.

   ![Sélection du type de rapport présentant l’option Point de contact d’attribution Bizible avec opportunité](assets/2-3.jpg)

1. En commençant par la partie supérieure du rapport, affichez « [!UICONTROL Tous les points de contact d’attribution Bizible] » et ajustez le champ de date en fonction de la période sur laquelle vous souhaitez créer votre rapport. Dans notre exemple, nous prenons All Time. De plus, remplacez le format de rapport Tabulaire par Résumé.

   ![Filtre de rapport affichant tous les points de contact d’attribution Bizible avec sélecteur de période](assets/3-3.jpg)

   ![Options de format de rapport avec le format Résumé sélectionné](assets/4-2.jpg)

1. À présent, nous allons ajouter des champs au rapport. Dans la recherche rapide sur la gauche, saisissez « Canal marketing » et ajoutez-le au regroupement Résumé dans le rapport.

   ![Report Builder affichant le champ Canal marketing ajouté au regroupement récapitulatif](assets/5.jpg)

1. Ensuite, nous allons ajouter un filtre pour ne regarder que les opportunités perdues closes. Dans la recherche rapide sur la gauche, recherchez le champ « Phase » et faites-le glisser dans la zone de filtrage.

   ![Zone de filtre du rapport avec champ Étape glissée dans la section de filtre](assets/6.jpg)

1. De là, vous sélectionnerez la loupe pour choisir la ou les étapes que vous utilisez pour les opportunités « Fermées et perdues ». Dans notre cas, nous utiliserons le nom standard « Fermé et perdu ».

   ![Sélecteur de filtre d’étape affichant l’option de sélection d’étape Fermée et perdue &#x200B;](assets/7.jpg)

1. Maintenant, allez-y et exécutez le rapport !

   Il s’agit d’un rapport d’opportunités résumé par la mesure Canal marketing des opportunités closes et perdues sur vos canaux. Ce rapport vous permet de comprendre les canaux qui peuvent être peu performants. N’hésitez pas à ajouter des filtres ou des champs sur lesquels vous souhaitez créer des rapports.

>[!MORELIKETHIS]
>[[!DNL Marketo Measure] Tutoriels : rapports SFDC supplémentaires](https://experienceleague.adobe.com/fr/docs/marketo-measure-learn/tutorials/onboarding/marketo-measure-102/addtional-salesforce-reports)
