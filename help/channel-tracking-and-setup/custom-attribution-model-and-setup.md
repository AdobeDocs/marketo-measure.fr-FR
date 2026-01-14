---
description: Modèle d’attribution personnalisé et conseils de configuration pour les utilisateurs de Marketo Measure
title: Configuration et modèle et d’attribution personnalisés
exl-id: 7b156db2-9ac6-4d32-ac67-06c0aa15d651
feature: Attribution, Custom Models
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 1%

---

# Configuration et modèle et d’attribution personnalisés {#custom-attribution-model-and-setup}

Consultez ci-dessous un aperçu du modèle d’attribution personnalisé [!DNL Marketo Measure] et de sa configuration.

## Modèle d’attribution personnalisé {#custom-attribution-model}

Le modèle d’attribution personnalisé [!DNL Marketo Measure] permet aux utilisateurs et utilisatrices de choisir les points de contact ou les étapes personnalisées à inclure dans le modèle. Les utilisateurs peuvent contrôler le pourcentage de crédit de chiffre d’affaires attribué à ces étapes et points de contact ou peuvent utiliser les valeurs de pourcentage d’attribution suggérées par le modèle de machine learning [!DNL Marketo Measure].

## Comment configurer votre modèle d’attribution personnalisé {#how-to-set-up-your-custom-attribution-model}

1. Déterminez les étapes à inclure dans votre modèle personnalisé.

   Pour commencer à créer votre modèle d’attribution personnalisé, vous devez sélectionner les étapes importantes pour votre équipe marketing. Outre les étapes jalonnées [!DNL Marketo Measure] (FT, LC, OC, Fermée), vous pouvez ajouter jusqu’à six statuts lead/contact ou étapes d’opportunité supplémentaires dans votre modèle personnalisé. Par exemple, il est courant que l’étape MQL soit incluse dans le modèle personnalisé. Les équipes marketing veulent souvent savoir quels efforts ou canaux génèrent des transitions vers l’étape MQL.

   Se connecter à [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}. Accédez à [!UICONTROL Mon compte] > [!UICONTROL Paramètres] et sous la section CRM, sélectionnez **[!UICONTROL Mappage d’étape]**.

   Sélectionnez ensuite les leads/contacts et les étapes d’opportunité à inclure en cochant la case **[!UICONTROL Inclure dans le modèle]**.

   >[!NOTE]
   >
   >Vous êtes autorisé à effectuer jusqu’à six étapes personnalisées (sans inclure les valeurs par défaut : FT, LC, OC, Fermé).

   ![Vous êtes autorisé à effectuer jusqu’à six étapes personnalisées (sans inclure les valeurs par défaut :](assets/custom-models-1.png)

   >[!NOTE]
   >
   >_Tous_ les leads/contacts et les étapes d’opportunité apparaîtront ici, même si l’étape est inactive ou plus utilisée dans [!DNL Salesforce]. Si vous souhaitez supprimer ces étapes, vous devez les supprimer définitivement dans [!DNL Salesforce].

   Lorsque vous avez sélectionné vos étapes, veillez à cliquer sur le bouton **[!UICONTROL Enregistrer et traiter]** au bas de la page. Les étapes apparaissent désormais dans l’onglet **[!UICONTROL Paramètres d’attribution]** et vous pouvez attribuer des pourcentages d’attribution à chaque étape. Les étapes personnalisées sont également affichées dans la suite de performances marketing en tant qu’étape de prospect ou d’opportunité dans la cascade de demandes.

   Si vous souhaitez inclure d’autres étapes dans le modèle, mais qu’elles ne figurent pas dans la liste [!UICONTROL Statut du lead/contact] ou [!UICONTROL Étape de l’opportunité], vous pouvez définir votre propre étape personnalisée en vous basant sur les champs de votre CRM.

   Dans l’exemple ci-dessous, une étape « MQL » personnalisée est définie à l’aide d’un champ de date. La règle indique simplement que si le champ Date MQL n’est pas vide, il doit être considéré comme un MQL et doit être inclus dans le modèle personnalisé. Il est également important de trier les étapes personnalisées une fois qu’elles ont été créées afin qu’elles suivent la progression de votre cycle de vente.

   ![Dans l’exemple ci-dessous, une étape « MQL » personnalisée est définie à l’aide d’un &#x200B;](assets/custom-models-10.png)

   >[!CAUTION]
   >
   >N’oubliez pas d’activer le suivi de l’historique pour les champs personnalisés.

Si un champ personnalisé est utilisé dans votre modèle personnalisé, le suivi de l’historique des champs DOIT être activé dans le CRM. Pour obtenir des instructions sur l’activation du suivi de l’historique des champs, voir [Configuration du modèle personnalisé : activer le suivi de l’historique des champs](/help/channel-tracking-and-setup/custom-model-setup-enable-field-history-tracking.md).

1. Déterminez les pourcentages d’attribution pour le modèle personnalisé.

   Accédez à la **[!UICONTROL Paramètres d’attribution]** dans les applications [!DNL Marketo Measure] ; les étapes personnalisées s’affichent ici dans le tableau d’attribution. Le tableau d’attribution affiche tous les modèles d’attribution [!DNL Marketo Measure] et la pondération d’attribution de chaque modèle. Les pourcentages d’attribution des cinq premiers modèles sont fixes et ne peuvent pas être modifiés.

   Dans la colonne tout à droite intitulée « **[!UICONTROL Personnalisé]** », vous pouvez définir la pondération en pourcentage pour chaque étape de votre modèle d’attribution personnalisé. Saisissez les valeurs de chaque étape dans la colonne Personnalisé et cliquez ensuite sur **[!UICONTROL Enregistrer et retraiter]**.

   À gauche de la colonne _Personnalisé_ se trouve le modèle de machine learning **[!DNL Marketo Measure]**. Le modèle de machine learning calcule la pondération d’attribution en fonction de l’importance relative pour remporter une offre en fonction de ce qui s’est passé à chaque étape personnalisée. Pour plus d’informations sur le modèle de machine learning, consultez la section [FAQ sur le modèle de machine learning](/help/channel-tracking-and-setup/machine-learning-model-faq.md).

   ![Le Marketo Measure se trouve à gauche de la colonne Personnalisé](assets/custom-models-2.png)

## Positions du point de contact {#touchpoint-positions}

Une fois les pourcentages d’attribution enregistrés et traités, les points de contact sont mis à jour et reçoivent leurs nouvelles étapes et positions. Le point de contact qui s’est produit le plus récemment, avant une transition d’étape, sera crédité pour cette étape (comme illustré ci-dessous). La pondération et le chiffre d’affaires personnalisés sont également redistribués.

![Une fois les pourcentages d’attribution enregistrés et traités, les points de contact sont &#x200B;](assets/custom-models-3.png)

## La différence entre les étapes Funnel et les étapes de modèle personnalisé {#the-difference-between-funnel-stages-and-custom-model-stages}

Vous pouvez désormais afficher les étapes personnalisées dans votre Funnel marketing, même si le modèle personnalisé n’est pas activé. Cela s’effectuerait par l’intermédiaire de notre fonctionnalité Phase de Funnel. Les étapes funnel vous permettent désormais d’ajouter des étapes à funnel, mais sans afficher l’attribution.

Les étapes funnel seront toujours suivies en tant que points de contact et apparaîtront toujours en tant que positions de point de contact dans votre CRM. Sans modèle personnalisé, ces points de contact peuvent toujours bénéficier de l’attribution Deuxième touche en cas de remplissage de formulaire (10 % pour les points de contact intermédiaires), mais d’un crédit d’attribution nul s’il s’agit uniquement d’une visite web.

Comme vous pouvez le voir ci-dessous, nous avons inclus l’étape Diligence dans nos étapes Funnel. Cela signifie que nous aurons des points de contact où la position contient Diligence, mais ces points de contact ne recevront du crédit d’attribution Middle Touch que si le modèle personnalisé n’est pas activé (au plus 10 %).

![Comme vous pouvez le voir ci-dessous, nous avons inclus l’étape Diligence comme élément distinct](assets/custom-models-7.png)

>[!NOTE]
>
>Le comportement des modèles personnalisés BAT consiste à diviser le pourcentage de touche intermédiaire du modèle personnalisé uniformément sur les autres étapes, à condition qu’il n’y ait pas de touche intermédiaire.
