---
description: FAQ sur le modèle de machine learning - [!DNL Marketo Measure]
title: Questions fréquentes sur le modèle de machine learning
exl-id: 2fc142b2-8ac4-4c48-a8f1-398e29ccfe97
feature: Custom Models
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 1%

---


# Questions fréquentes sur le modèle de machine learning {#machine-learning-model-faq}

Le modèle de machine learning [!DNL Marketo Measure] utilise les données de vos points de contact pour calculer la pondération d’attribution qui doit être attribuée à chaque étape. Cela est déterminé par l’importance de chaque étape dans la conclusion des transactions.

Quels sont les pourcentages d’attribution du modèle de machine learning qui m’indiquent pour chaque étape ?

Les pourcentages d’attribution de chaque étape reflètent l’impact potentiel de vos efforts marketing. Un pourcentage plus élevé signifie que le marketing peut directement influencer le mouvement du funnel à ce stade. Un pourcentage d’attribution inférieur signifie que les étapes sont moins importantes à surveiller par votre équipe.

Comment le modèle de machine learning est-il calculé ?

[!DNL Marketo Measure] calcule l’importance de chaque étape personnalisée en utilisant les données de point de contact de votre compte. Les critères utilisés pour déterminer l&#39;importance de chaque étape sont les suivants :

* Exactitude du modèle : si nous créons un modèle prédictif avec les données de point de contact pour prédire si nous finirons par remporter un accord, quelle sera l’exactitude du modèle ? Une plus grande précision prédictive signifie que les détails de cette étape sont davantage corrélés avec la conclusion d&#39;une transaction
* Taux de conversion : si les leads ou les opportunités à ce stade sont convertis à l’étape suivante à un taux élevé, cela suggère que les activités marketing qui se sont produites à ce stade n’ont pas eu beaucoup d’importance. Inversement, si une certaine étape se convertit à l’étape suivante à un faible taux, cela peut suggérer que les activités marketing qui se sont produites à cette étape ont eu une influence sur la conversion.
* Poids d’unicité du point de contact : si une étape se produit en tant que transition autonome, ce qui signifie qu’il n’y a pas eu d’autres transitions d’étape qui se sont produites au même moment, cette étape peut recevoir un poids d’attribution plus élevé. Inversement, si un point de contact d’une étape est partagé avec d’autres étapes (par exemple, le point de contact partage les étapes Première touche, Conversion de lead et Conversion d’opportunité), cette étape pourrait recevoir une pondération d’attribution plus faible.

Le poids final d’une étape personnalisée est calculé comme suit :

**_Pourcentage du modèle = Précision du modèle x Taux de conversion x Poids d’unicité du point de contact_**

À la fin, tous les poids d’étape personnalisés sont normalisés et convertis en % comme illustré ci-dessous.

Pourquoi est-ce que je ne vois aucun nombre dans la colonne Machine Learning ?

Lorsque le modèle d’attribution personnalisé est activé pour votre compte, il faut généralement entre 3 et 7 jours pour que notre modèle s’exécute et génère ces nombres, en fonction de vos données historiques.

À quelle fréquence le modèle de machine learning est-il mis à jour ?

Nous réexécutons le modèle tous les 7 jours.

Pourquoi le modèle définit-il toujours les contours intermédiaires sur 10 % ?

L’attribution d’un crédit d’attribution de 10 % aux contacts intermédiaires est un paramètre standard dans tous nos modèles d’attribution.

Quand dois-je modifier ma distribution d’attribution ?

Contactez votre gestionnaire de compte pour discuter des implications de la modification de vos pourcentages d’attribution et des étapes à inclure dans votre modèle personnalisé. Chaque [!DNL Salesforce] et processus de vente est unique et nous voulons nous assurer que votre modèle personnalisé est modélisé avec précision.

Cela dit, nous avons identifié certaines tendances générales parmi nos clients :

Une tendance que nous avons constatée est qu&#39;il n&#39;est pas toujours avantageux d&#39;inclure plus d&#39;étapes dans votre modèle. Par exemple, lorsque les clients et clientes ont ajouté plusieurs étapes Opportunité en bas du funnel, ces étapes ont tendance à recevoir des valeurs de pourcentage d’attribution très faibles. Des valeurs de pourcentage faibles indiquent un taux de conversion élevé, ce qui signifie généralement que ces étapes n’ont pas autant d’impact sur la conclusion des affaires. Certains clients décident finalement de ne pas inclure ces étapes dans le funnel. Si vous décidez de supprimer une étape de votre modèle d’attribution, le modèle de machine recalcule et redistribue les pourcentages.

Nous avons également remarqué un taux de conversion élevé entre les étapes de création de leads et de qualification marketing. Par conséquent, l’étape de qualification marketing pourrait recevoir une pondération d’attribution en pourcentage plus faible. Selon votre cycle commercial et commercial, il peut être bénéfique de supprimer cette étape du modèle personnalisé.

Gardez à l’esprit que si vous souhaitez effectuer le suivi des activités marketing tout au long d’une transition d’étape spécifique, mais que vous ne souhaitez pas que cette étape reçoive un crédit d’attribution, vous pouvez inclure cette étape dans votre modèle et attribuer un crédit d’attribution de 0 % à cette étape.
