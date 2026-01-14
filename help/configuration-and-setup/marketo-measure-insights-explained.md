---
description: Explication de [!DNL Marketo Measure] Insights - [!DNL Marketo Measure]
title: Explication des analyses [!DNL Marketo Measure]
exl-id: d479a15f-4c92-4302-8ce8-6487645012e1
feature: Reporting
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# Explication des analyses [!DNL Marketo Measure] {#marketo-measure-insights-explained}

Découvrez la vue [!DNL Marketo Measure] Insights dans [!DNL Salesforce], notamment ce que représentent les différentes icônes et comment utiliser la fonctionnalité. Cette fonctionnalité est particulièrement utile pour afficher les 20 premières sessions d’un prospect, d’un contact ou d’un compte.

Une fois qu’une personne est suivie par [!DNL Marketo Measure] JavaScript et qu’elle remplit un formulaire sur votre site web, elle devient un prospect de votre système et ses données de marketing numérique sont envoyées à votre organisation Salesforce (SFDC). Dans ce cas, les données de point de contact sont renseignées dans la section [!DNL Marketo Measure] les informations sur le lead (une application de zone de travail) dans les objets de lead/contact/opportunité/compte.

Tout d’abord, vous voyez au milieu de vos informations, le nombre de sessions que la personne a eues sur votre site web. Vous pouvez faire défiler ces sessions et naviguer à volonté.

![Tout d’abord, vous voyez au milieu de vos informations, le nombre](assets/marketo-app-1.png)

Vous pouvez consulter le cumul de toutes vos sessions si vous cliquez sur « Toutes » dans la partie supérieure centrale de vos informations. Vous pouvez y comprendre les dates des sessions individuelles, le canal ou la source qui les a animées, ainsi qu’un ensemble d’icônes spécifiant plus d’informations.

La première chose que vous voyez est les icônes FT ou LC. Ils représentent la position du point de contact des sessions répertoriées. Plus précisément, FT représente First Touch et LC représente Lead Creation. Vous pouvez avoir plusieurs sessions, mais un seul point de contact peut être FT ou LC. Vous ne trouverez jamais plusieurs FT ou LC associés à une seule personne.

Les icônes qui ressemblent à du papier indiquent qu’une page vue s’est produite au cours de la session. Il est probable que cette icône soit présente dans chaque session.

![Les icônes qui ressemblent à du papier indiquent qu’une page vue a été effectuée](assets/marketo-app-2.png)

L’icône qui ressemble à un bécher indique qu’une expérience de test A/B s’est produite. Nous intégrons à ce stade Optimizely et VWO. Avec cette intégration, nous sommes en mesure de pousser l’expérience et la variation que l’utilisateur a vues sur sa session spécifique.

![L’icône qui ressemble à un bécher signale qu’un test A/B ](assets/marketo-app-3.png)

Si vous cliquez sur une session spécifique (vous pouvez le faire en cliquant sur la date réelle de la session ou dans la partie centrale supérieure des sessions groupées), vous pourrez voir les détails de la session. Au cours de chaque session, vous pouvez voir toutes les pages spécifiques que l’utilisateur a vues, classées par date et heure.

![Si vous cliquez sur une session spécifique (vous pouvez le faire en cliquant sur](assets/marketo-app-4.png)

Sur le côté droit de chaque session, vous pouvez voir davantage de données marketing granulaires qui poussent les champs [!DNL Marketo Measure] dans votre SFDC. Dans cet exemple, vous pouvez voir Groupe publicitaire, Contenu publicitaire, Campagne, Mot-clé, Medium. Vous pouvez également faire défiler la page vers le bas pour afficher davantage de données [!DNL Marketo Measure] que nous fournissons.

Enfin, une fois qu’une personne possède une myriade de sessions, vous pouvez utiliser certains filtres dans [!UICONTROL Insights] pour rechercher des parties spécifiques de son engagement sur votre site. Vous pouvez par exemple filtrer par [!UICONTROL position du point de contact].

Vous pouvez également effectuer une recherche par Pages vues, Tests AB ou Forms.
