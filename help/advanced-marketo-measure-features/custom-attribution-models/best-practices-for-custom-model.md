---
description: Bonnes pratiques pour le modèle personnalisé - [!DNL Marketo Measure]
title: Bonnes pratiques relatives aux modèles personnalisés
exl-id: 7c19bb6a-30fc-4cbd-a58e-f20751102afe
feature: Custom Models
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 2%

---

# Bonnes pratiques relatives aux modèles personnalisés {#best-practices-for-custom-model}

## Vue d’ensemble {#overview}

Outre les [!DNL Marketo Measure] modèles d’attribution prêts à l’emploi, les clients de niveau 2 et plus ont accès à un modèle d’attribution personnalisé.

Le modèle d’attribution personnalisée [!DNL Marketo Measure] permet aux utilisateurs de choisir les positions de points de contact de jalon et/ou les étapes personnalisées à inclure dans le modèle. En outre, les utilisateurs peuvent contrôler le pourcentage du crédit attribué à chaque étape dans le modèle (les utilisateurs peuvent définir jusqu’à 6 étapes personnalisées supplémentaires) ou utiliser les valeurs de pourcentage d’attribution suggérées par le modèle d’apprentissage automatique [!DNL Marketo Measure].

Il existe deux aspects clés de votre modèle d’attribution personnalisée :

**Les étapes personnalisées** permettent aux utilisateurs de définir leur entonnoir en ce qui concerne leurs activités et processus. Les étapes personnalisées doivent représenter des &quot;jalons&quot; tout au long du parcours de l’acheteur, tout comme les jalons [!DNL Marketo Measure] (Première touche, touche de création de piste, touche de création d’opportunité et touche gagnant fermé) qui s’inscrivent dans les modèles d’attribution des stocks. Il est essentiel que vos étapes personnalisées soient correctement définies et mappées dans votre compte pour s’assurer que [!DNL Marketo Measure] effectue correctement le suivi des transitions d’étape. Cela permet d’identifier les points de contact à associer à chaque étape et d’attribuer le crédit de manière appropriée. Le mappage d’étape personnalisé est essentiellement une extension du &quot;mappage d’étape&quot; standard et doit suivre les mêmes pratiques.

>[!NOTE]
>
>Pour plus d’informations, consultez la ressource Meilleures pratiques de mappage des environnements intermédiaires .

**La modélisation d’attribution personnalisée** est définie une fois que vous avez sélectionné l’entonnoir Étapes personnalisées. Les utilisateurs peuvent ensuite contrôler la quantité de crédit d’attribution à attribuer à chaque étape personnalisée, ainsi qu’aux étapes de jalon [!DNL Marketo Measure]. Les utilisateurs peuvent attribuer du crédit à chaque étape selon leur bon vouloir ou faire référence au modèle d’apprentissage automatique [!DNL Marketo Measure] qui agit comme un &quot;modèle suggestif&quot; basé sur des données historiques.

Il est essentiel que ces deux aspects de votre modèle personnalisé soient définis correctement et précisément pour garantir que [!DNL Marketo Measure] produise un modèle d’attribution personnalisée précis.

## Bonne pratique {#best-practice}

Que vous configuriez votre modèle personnalisé pour la première fois ou que vous examiniez ce qui a été précédemment établi, il est important de garder à l’esprit les bonnes pratiques suivantes.

* Commencer simple
   * Identifiez les étapes clés que vous souhaitez ajouter à votre modèle personnalisé, qui sont essentielles pour la création de rapports [!DNL Marketo Measure]. En règle générale, il s’agit d’étapes sur lesquelles vous êtes généralement mesuré ou dont vous souhaitez obtenir des informations.
   * Vous pouvez toujours ajouter à votre modèle personnalisé au fil du temps.
* Utilisation du modèle d’apprentissage automatique [!DNL Marketo Measure]
   * Si vous avez du mal à décider de la ventilation d’attribution en pourcentage, le modèle d’apprentissage automatique [!DNL Marketo Measure] peut vous aider à prendre des décisions éclairées lors de la définition de votre modèle d’attribution personnalisé.
   * Lors de l’affichage du modèle d’apprentissage automatique, les pourcentages d’attribution de chaque étape reflètent l’impact potentiel de vos efforts marketing.
      * Un pourcentage plus élevé signifie que le marketing peut influencer directement le mouvement de l’entonnoir à ce stade.
      * Un pourcentage d’attribution plus faible signifie que les étapes sont moins importantes pour votre équipe de surveillance.
* Vous devez définir les principales étapes de l’entonnoir en fonction des phases de piste ou de contact, et non sur les deux.
   * Cela signifie que vous devez vous assurer que toutes les personnes passent par cette étape sur l’objet relatif.
      * Par exemple : si vous définissez l’étape MQL à partir de l’objet Lead, toutes les personnes doivent accéder à votre système en tant que piste et être marquées comme MQL dans leur enregistrement Lead afin que [!DNL Marketo Measure] reflète précisément la touche liée à la transition du prospect vers MQL. Si ce n’est pas le cas, et que certaines personnes passent à Contact avant de devenir MQL en tant que prospect, [!DNL Marketo Measure] ne pourra pas tenir compte de cela avec précision dans vos données de point de contact et nous devrons supposer que cette personne a déjà MQL. [!DNL Marketo Measure] ne peut pas prendre en compte le saut d’étape. De ce fait, nous allons déduire que les étapes ont été franchies même si elles ne l’ont pas fait.
* Assurez-vous que le suivi de l’historique des champs est activé pour tous les champs utilisés pour définir les étapes personnalisées que vous incorporez.
* N’utilisez pas de champs de formule pour définir une étape personnalisée
   * Un champ booléen est une recommandation recommandée.
* N’incorporez pas d’étapes personnalisées dans votre modèle personnalisé qui correspond à une position de point de contact [!DNL Marketo Measure] Milestone (FT, LC, OC, Won/Lost)
   * Si vous le faites, ces positions se produisent toujours simultanément et peuvent entraîner un crédit d’attribution exagéré pour certaines parties de votre entonnoir.
* Travail avec votre équipe d’Opt-marketing
   * L’intégration de l’équipe qui travaille le plus avec les étapes et leur signification garantit que vous utilisez les étapes correctes et qu’elles sont correctement définies.

## Bonne pratique de maintenance {#best-practice-for-maintenance}

La révision de votre modèle personnalisé au moins deux fois par an vous permettra de vous assurer que vos rapports d’attribution personnalisés sont précis et fiables.

Si votre modèle personnalisé utilise le modèle d’apprentissage automatique, vous devez revoir son application dans le modèle personnalisé trimestriel afin de vous assurer que votre modèle personnalisé est le plus à jour possible.

D’autres raisons peuvent déclencher une révision de votre modèle personnalisé, telles que...

* Changements au sein de votre équipe marketing
* Toute modification apportée à vos étapes CRM
* Mises à jour de l’entonnoir de votre entreprise
* Affichage de données de recettes inexactes dans votre rapport [!DNL Marketo Measure] lors de l’application du modèle personnalisé
* Affichage des positions de point de contact renseignées qui ne sont plus pertinentes pour l’entonnoir de votre entreprise

>[!MORELIKETHIS]
>
>* [Modèle d’attribution personnalisée et configuration](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md)
>* [Activer Le Suivi De L’Historique Des Champs Pour Le Modèle Personnalisé](/help/advanced-marketo-measure-features/custom-attribution-models/custom-model-setup-enable-field-history-tracking.md)
>* [Modèle d’apprentissage automatique](/help/advanced-marketo-measure-features/custom-attribution-models/machine-learning-model-faq.md)
