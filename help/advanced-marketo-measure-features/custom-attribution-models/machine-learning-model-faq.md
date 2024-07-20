---
unique-page-id: 18874775
description: FAQ sur le modèle d’apprentissage automatique - [!DNL Marketo Measure]
title: Questions fréquentes sur le modèle de machine learning
exl-id: 2fc142b2-8ac4-4c48-a8f1-398e29ccfe97
feature: Custom Models
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 1%

---

# Questions fréquentes sur le modèle de machine learning {#machine-learning-model-faq}

Le modèle d’apprentissage automatique [!DNL Marketo Measure] utilise vos données de point de contact pour calculer la quantité de pondération d’attribution à attribuer à chaque étape. Ceci est déterminé par l&#39;importance de chaque étape dans la conclusion des accords.

Que me disent les pourcentages d’attribution du modèle d’apprentissage automatique pour chaque étape ?

Les pourcentages d’attribution de chaque étape reflètent l’impact potentiel de vos efforts marketing. Un pourcentage plus élevé signifie que le marketing peut directement influencer le mouvement de l’entonnoir à ce stade. Un pourcentage d’attribution plus faible signifie que les scènes sont moins importantes à surveiller pour votre équipe.

Comment le modèle d’apprentissage automatique est-il calculé ?

[!DNL Marketo Measure] calcule l’importance de chaque étape personnalisée à l’aide des données de point de contact de votre compte. Les critères utilisés pour déterminer l’importance de chaque étape sont les suivants :

* Précision du modèle : si nous créons un modèle prédictif avec les données du point de contact pour prédire si nous finirons par gagner un accord, quel degré de précision le modèle sera-t-il ? Une plus grande précision prédictive signifie que les détails de cette étape sont plus liés à la conclusion ou non d’un accord.
* Taux de conversion : si les prospects ou les opportunités à ce stade sont convertis à l’étape suivante à un taux élevé, cela suggère que les activités marketing qui se sont produites à ce stade n’ont pas eu beaucoup d’importance. Inversement, si une certaine étape se convertit à une étape suivante à un taux faible, cela peut suggérer que les activités marketing qui se sont produites à cette étape ont eu une influence sur la conversion.
* Poids d’unicité des points de contact : si une étape se produit en tant que transition autonome, ce qui signifie qu’il n’y a pas eu d’autres transitions d’étape qui se sont produites en même temps, cette étape pourrait recevoir un poids d’attribution plus élevé. Inversement, si un point de contact pour une étape est partagé avec d’autres étapes (par exemple, le point de contact partage les étapes Première touche, Conversion de piste et Conversion d’opportunités), cette étape peut recevoir une pondération d’attribution plus faible.

Le poids final d’une étape personnalisée est calculé comme suit :

**_Pourcentage du modèle = précision du modèle x taux de conversion x poids de l’unicité du point de contact_**

À la fin, tous les poids d’étape personnalisés sont normalisés et convertis en % comme illustré ci-dessous.

Pourquoi ne vois-je aucun chiffre dans la colonne Apprentissage automatique ?

Lorsque le modèle d’attribution personnalisé est activé pour votre compte, il prend généralement entre 3 et 7 jours pour que notre modèle s’exécute et crée ces nombres, en fonction de vos données historiques.

À quelle fréquence le modèle d’apprentissage automatique est-il mis à jour ?

Nous réexécutons le modèle tous les 7 jours.

Pourquoi le modèle définit-il toujours les touches du milieu sur 10 % ?

L’attribution d’un crédit d’attribution de 10 % aux écrans tactiles moyens est un paramètre standard pour tous nos modèles d’attribution.

Quand dois-je modifier ma distribution d’attribution ?

Contactez votre gestionnaire de compte pour discuter des implications de la modification des pourcentages d’attribution et des étapes à inclure dans votre modèle personnalisé. Chaque [!DNL Salesforce] et processus de vente est unique et nous voulons nous assurer que votre modèle personnalisé est correctement modélisé.

Cela dit, nous avons identifié certaines tendances générales chez nos clients :

Une tendance que nous avons remarqué est qu’il n’est pas toujours bénéfique d’inclure plus d’étapes dans votre modèle. Par exemple, lorsque les clients ont ajouté plusieurs phases d’opportunité vers le bas de l’entonnoir, elles ont tendance à recevoir des valeurs de pourcentage d’attribution très faibles. Les valeurs en pourcentage faible indiquent un taux de conversion élevé, ce qui signifie généralement que ces étapes n’ont pas autant d’impact sur la conclusion des offres. Certains clients décident finalement de ne pas inclure ces étapes dans l’entonnoir. Si vous décidez de supprimer une étape de votre modèle d’attribution, le modèle automatique recalcule et redistribue les pourcentages.

Nous avons également remarqué qu’il existe un taux de conversion élevé entre la création de piste et les étapes qualifiées en marketing. Par conséquent, l’étape Qualifiée en marketing pourrait recevoir une pondération d’attribution en pourcentage plus faible. En fonction de votre cycle de vente et de votre entreprise, il peut être bénéfique de supprimer cette étape du modèle personnalisé.

Gardez à l’esprit que si vous souhaitez effectuer le suivi des activités marketing par le biais d’une transition à une étape spécifique, mais que vous ne souhaitez pas que cette étape reçoive un crédit d’attribution, vous pouvez l’inclure dans votre modèle et lui attribuer un crédit d’attribution de 0 %.
