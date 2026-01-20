---
description: Bonnes pratiques relatives au modèle personnalisé  [!DNL Marketo Measure]
title: Bonnes pratiques relatives aux modèles personnalisés
exl-id: 7c19bb6a-30fc-4cbd-a58e-f20751102afe
feature: Custom Models
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 2%

---

# Bonnes pratiques relatives aux modèles personnalisés {#best-practices-for-custom-model}

## Vue d’ensemble {#overview}

Outre les modèles d’attribution prêts à l’emploi [!DNL Marketo Measure], les clients de niveau 2 et supérieurs ont accès à un modèle d’attribution personnalisé.

Le modèle d’attribution personnalisé [!DNL Marketo Measure] permet aux utilisateurs et utilisatrices de choisir les positions de point de contact jalonné et/ou les étapes personnalisées à inclure dans le modèle. En outre, les utilisateurs et utilisatrices peuvent contrôler le pourcentage de crédit attribué à chaque étape du modèle (les utilisateurs et utilisatrices peuvent définir jusqu’à 6 étapes personnalisées supplémentaires) ou utiliser les valeurs de pourcentage d’attribution suggérées par le modèle de machine learning [!DNL Marketo Measure].

Votre modèle d’attribution personnalisé comporte deux aspects clés :

Les **étapes personnalisées** permettent aux utilisateurs de définir leur funnel en fonction de leurs activités et processus. Les étapes personnalisées doivent représenter des « jalons » dans l’ensemble du parcours de l’acheteur, de la même manière que les jalons [!DNL Marketo Measure] (Première touche, Étape de création de lead, Étape de création d’opportunité et Étape close et confirmée) dans les modèles d’attribution de stock. Il est essentiel que vos étapes personnalisées soient correctement définies et mappées dans votre compte pour vous assurer que [!DNL Marketo Measure] effectue correctement le suivi des transitions d’étape. Cela permet d’identifier les points de contact à associer à chaque étape et d’attribuer le crédit de manière appropriée. Le mappage d’étape personnalisé est essentiellement une extension du « mappage d’étape » standard et doit suivre les mêmes pratiques.

>[!NOTE]
>
>Référencez la ressource des bonnes pratiques de mappage d’étape pour plus d’informations

La **modélisation d’attribution personnalisée** est définie une fois que vous avez sélectionné votre funnel d’étapes personnalisées. Les utilisateurs et utilisatrices peuvent ensuite contrôler le montant du crédit d’attribution à affecter à chaque étape personnalisée ainsi qu’aux étapes jalons [!DNL Marketo Measure]. Les utilisateurs peuvent attribuer des crédits à chaque étape comme bon leur semble, ou référencer le modèle de machine learning [!DNL Marketo Measure] qui agit comme un « modèle suggestif » basé sur des données historiques.

Il est essentiel que ces deux aspects de votre modèle personnalisé soient définis correctement et précisément pour garantir que [!DNL Marketo Measure] produit un modèle d’attribution personnalisé précis.

## Bonne pratique {#best-practice}

Que vous configuriez votre modèle personnalisé pour la première fois, ou que vous examiniez ce qui a été précédemment établi, il est important de garder à l’esprit les bonnes pratiques suivantes.

* Démarrer simple
   * Identifiez les étapes clés que vous souhaitez ajouter à votre modèle personnalisé et qui sont essentielles pour vos rapports [!DNL Marketo Measure]. En règle générale, il s’agit d’étapes par rapport auxquelles vous êtes généralement mesuré ou sur lesquelles vous souhaitez apprendre à utiliser insight
   * Vous pouvez toujours ajouter à votre modèle personnalisé au fil du temps
* Utilisation du modèle de machine learning [!DNL Marketo Measure]
   * Si vous avez du mal à décider de la répartition de l’attribution en pourcentage, le modèle de machine learning [!DNL Marketo Measure] peut vous aider à prendre des décisions éclairées lors de la définition de votre modèle d’attribution personnalisé.
   * Lors de l’affichage du modèle de machine learning, les pourcentages d’attribution de chaque étape reflètent l’impact potentiel de vos efforts marketing
      * Un pourcentage plus élevé signifie que le marketing peut directement influencer le mouvement du funnel à ce stade
      * Un pourcentage d’attribution inférieur signifie que les étapes sont moins importantes à surveiller par votre équipe
* Vous devez définir les principales étapes de funnel en fonction des étapes de lead ou de contact, et non des deux
   * Cela signifie que vous devez vous assurer que toutes les personnes passeront par cette étape sur l’objet correspondant
      * Par exemple : si vous définissez l’étape MQL à partir de l’objet Lead , toutes les personnes doivent accéder à votre système en tant que Lead et être marquées comme MQL dans leur enregistrement Lead afin que [!DNL Marketo Measure] reflète exactement quel contact a été associé à la transition du Lead vers MQL. Si ce n’est pas le cas, et que certaines personnes passent au contact avant de devenir MQL en tant que lead, [!DNL Marketo Measure] ne pourrez pas en tenir compte avec précision dans vos données de point de contact et nous devrons supposer que cette personne a déjà un compte MQL. [!DNL Marketo Measure] ne peut pas tenir compte du saut d’étape, nous déduirons donc que les étapes ont été passées même si elles ne l’ont pas été.
* Assurez-vous que le suivi de l’historique des champs est activé pour tous les champs utilisés pour définir les étapes personnalisées que vous incorporez
* N’utilisez pas de champs de formule pour définir une étape personnalisée
   * Un champ booléen est une recommandation de bonne pratique
* N’incorporez pas dans votre modèle personnalisé d’étapes qui coïncident avec une position de point de contact jalonné [!DNL Marketo Measure] (FT, LC, OC, close et confirmée/perdue)
   * Si vous le faites, ces positions se produisent toujours simultanément et peuvent entraîner un crédit d’attribution exagéré à certaines parties de votre funnel.
* Travailler avec votre équipe d’opportunités commerciales
   * Faire intervenir l’équipe qui travaille le plus proche des étapes et de leur signification permet de s’assurer que vous utilisez les étapes correctes et qu’elles sont correctement définies

## Bonne pratique de maintenance {#best-practice-for-maintenance}

En examinant votre modèle personnalisé au moins deux fois par an, vous vous assurerez que vos rapports d’attribution personnalisés sont précis et fiables.

Si votre modèle personnalisé utilise le modèle de machine learning, vous devez vérifier son application dans le modèle personnalisé tous les trimestres pour vous assurer que votre modèle personnalisé est aussi à jour que possible.

D’autres raisons qui peuvent déclencher une révision de votre modèle personnalisé incluent :

* Changements au sein de votre équipe marketing
* Toutes les modifications apportées à vos étapes CRM
* Mises à jour de funnel de vos organisations
* Affichage de données de chiffre d’affaires inexactes dans vos rapports [!DNL Marketo Measure] lors de l’application du modèle personnalisé
* Affichage des positions de point de contact renseignées qui ne sont plus pertinentes pour votre organisation funnel

>[!MORELIKETHIS]
>
>* [ Modèle et configuration d’attribution personnalisés ](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md)
>* [Activer Le Suivi De L’Historique Des Champs Pour Le Modèle Personnalisé](/help/advanced-marketo-measure-features/custom-attribution-models/custom-model-setup-enable-field-history-tracking.md)
>* [ Modèle de machine learning ](/help/advanced-marketo-measure-features/custom-attribution-models/machine-learning-model-faq.md)
