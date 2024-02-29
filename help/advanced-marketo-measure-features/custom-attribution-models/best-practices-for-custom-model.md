---
description: Bonnes pratiques relatives au modèle personnalisé - [!DNL Marketo Measure]
title: Bonnes pratiques relatives aux modèles personnalisés
exl-id: 7c19bb6a-30fc-4cbd-a58e-f20751102afe
feature: Custom Models
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 2%

---

# Bonnes pratiques relatives aux modèles personnalisés {#best-practices-for-custom-model}

## Vue d’ensemble {#overview}

En plus de la variable [!DNL Marketo Measure] Les clients de niveau 2 et plus, prêts à l’emploi, ont accès à un modèle d’attribution personnalisé.

La variable [!DNL Marketo Measure] Le modèle d’attribution personnalisée permet aux utilisateurs de choisir les positions de point de contact de jalon et/ou les étapes personnalisées à inclure dans le modèle. En outre, les utilisateurs peuvent contrôler le pourcentage du crédit attribué à chaque étape dans le modèle (les utilisateurs peuvent définir jusqu’à 6 étapes personnalisées supplémentaires) ou utiliser les valeurs de pourcentage d’attribution suggérées par la variable [!DNL Marketo Measure] Modèle d’apprentissage automatique.

Il existe deux aspects clés de votre modèle d’attribution personnalisée :

**Étapes personnalisées** permettent aux utilisateurs de définir leur entonnoir en fonction de leurs activités et processus. Les étapes personnalisées doivent représenter des &quot;jalons&quot; tout au long du parcours de l’acheteur, tout comme le [!DNL Marketo Measure] les jalons (Première touche, Contact de création de piste, Touche de création d’opportunités et Touche de sortie) s’inscrivent dans les modèles d’attribution de stock. Il est essentiel que vos étapes personnalisées soient correctement définies et mappées dans votre compte pour vous assurer que [!DNL Marketo Measure] effectue correctement le suivi des transitions d’étape. Cela permet d’identifier les points de contact à associer à chaque étape et d’attribuer le crédit de manière appropriée. Le mappage d’étape personnalisé est essentiellement une extension du &quot;mappage d’étape&quot; standard et doit suivre les mêmes pratiques.

>[!NOTE]
>
>Pour plus d’informations, consultez la ressource Meilleures pratiques de mappage des environnements intermédiaires .

**Modélisation d’attribution personnalisée** est défini une fois que vous avez sélectionné l’entonnoir Étapes personnalisées . Les utilisateurs peuvent ensuite contrôler le volume de crédit d’attribution à attribuer à chaque étape personnalisée, ainsi que la variable [!DNL Marketo Measure] étapes de jalon. Les utilisateurs peuvent attribuer du crédit à chaque étape selon leur bon vouloir ou référencer la variable [!DNL Marketo Measure] Modèle d’apprentissage automatique qui agit comme un &quot;modèle suggestif&quot; basé sur des données historiques.

Il est essentiel que ces deux aspects de votre modèle personnalisé soient définis correctement et précisément pour s’assurer que [!DNL Marketo Measure] génère un modèle d’attribution personnalisé précis.

## Bonne pratique {#best-practice}

Que vous configuriez votre modèle personnalisé pour la première fois ou que vous examiniez ce qui a été précédemment établi, il est important de garder à l’esprit les bonnes pratiques suivantes.

* Commencer simple
   * Identifiez les étapes clés que vous souhaitez ajouter à votre modèle personnalisé qui sont essentielles à votre [!DNL Marketo Measure] création de rapports. En règle générale, il s’agit d’étapes sur lesquelles vous êtes généralement mesuré ou dont vous souhaitez obtenir des informations.
   * Vous pouvez toujours ajouter à votre modèle personnalisé au fil du temps.
* Utilisez la variable [!DNL Marketo Measure] Modèle d’apprentissage automatique
   * Si vous avez du mal à décider de la ventilation d’attribution en pourcentage, la variable [!DNL Marketo Measure] Le modèle d’apprentissage automatique peut vous aider à prendre des décisions éclairées lors de la définition de votre modèle d’attribution personnalisé.
   * Lors de l’affichage du modèle d’apprentissage automatique, les pourcentages d’attribution de chaque étape reflètent l’impact potentiel de vos efforts marketing.
      * Un pourcentage plus élevé signifie que le marketing peut influencer directement le mouvement de l’entonnoir à ce stade.
      * Un pourcentage d’attribution plus faible signifie que les étapes sont moins importantes pour votre équipe de surveillance.
* Vous devez définir les principales étapes de l’entonnoir en fonction des phases de piste ou de contact, et non sur les deux.
   * Cela signifie que vous devez vous assurer que toutes les personnes passent par cette étape sur l’objet relatif.
      * Par exemple : si vous définissez l’étape MQL à partir de l’objet Lead, toutes les personnes doivent accéder à votre système en tant que piste et être marquées comme MQL dans leur enregistrement Lead pour [!DNL Marketo Measure] pour indiquer précisément quel contact était lié à la transition du prospect vers MQL. Si ce n&#39;est pas le cas, et que certaines personnes passent à contacter avant de devenir MQL en tant que prospect, [!DNL Marketo Measure] ne sera pas en mesure d’en tenir compte avec précision dans vos données de point de contact et nous devrons supposer que cette personne a déjà MQL. [!DNL Marketo Measure] ne peut pas tenir compte de l’sauts d’étape, nous allons donc déduire que les étapes ont été franchies même si elles ne l’ont pas été.
* Assurez-vous que le suivi de l’historique des champs est activé pour tous les champs utilisés pour définir les étapes personnalisées que vous incorporez.
* N’utilisez pas de champs de formule pour définir une étape personnalisée
   * Un champ booléen est une recommandation recommandée.
* N’incorporez pas d’étapes personnalisées dans votre modèle personnalisé qui correspond à une [!DNL Marketo Measure] Position du point de contact Milestone (FT, LC, OC, perte/perte/perte/perte/perte/perte/perte/perte/perte/perte de propriété)
   * Si vous le faites, ces positions se produiront toujours simultanément et peuvent entraîner un crédit d’attribution exagéré pour certaines parties de votre entonnoir.
* Travail avec votre équipe d’Opt-marketing
   * Si vous intégrez l’équipe qui travaille le plus étroitement avec les scènes et leur signification, vous aurez la garantie d’utiliser les scènes correctes et de les définir correctement.

## Bonne pratique de maintenance {#best-practice-for-maintenance}

La révision de votre modèle personnalisé au moins deux fois par an vous permettra de vous assurer que vos rapports d’attribution personnalisés sont précis et fiables.

Si votre modèle personnalisé utilise le modèle d’apprentissage automatique, vous devez revoir son application dans le modèle personnalisé trimestriel afin de vous assurer que votre modèle personnalisé est le plus à jour possible.

D’autres raisons peuvent déclencher une révision de votre modèle personnalisé, telles que...

* Changements au sein de votre équipe marketing
* Toute modification apportée à vos étapes CRM
* Mises à jour de l’entonnoir de votre entreprise
* Affichage de données de recettes inexactes dans votre [!DNL Marketo Measure] création de rapports lors de l’application du modèle personnalisé
* Affichage des positions de point de contact renseignées qui ne sont plus pertinentes pour l’entonnoir de votre entreprise

>[!MORELIKETHIS]
>
>* [Modèle et configuration d’attribution personnalisée](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md)
>* [Activation Du Suivi De L’Historique Des Champs Pour Un Modèle Personnalisé](/help/advanced-marketo-measure-features/custom-attribution-models/custom-model-setup-enable-field-history-tracking.md)
>* [Modèle d’apprentissage automatique](/help/advanced-marketo-measure-features/custom-attribution-models/machine-learning-model-faq.md)
