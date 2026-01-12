---
description: Bonnes pratiques relatives à la fusion de prospects - [!DNL Marketo Measure]
title: Bonnes pratiques de fusion des prospects
exl-id: d9293ed7-a794-4e52-a269-20a7fb36ce50
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 5%

---


# Bonnes pratiques de fusion des prospects {#best-practices-for-merging-leads}

Lors de la fusion de prospects dans [!DNL Salesforce], il est toujours préférable de veiller à ne pas perdre de données.

À titre de référence, voici la répartition des [comment fusionner des prospects](https://help.salesforce.com/s/articleView?id=leads_merge.htm&language=en_US&type=5) du support [!DNL Salesforce].

L’[!DNL Marketo Measure] intervient lorsqu’il est temps de sélectionner les champs qui se renseignent sur l’enregistrement fusionné. Lors de la sélection de l’enregistrement de Principal, vérifiez que les champs [!DNL Marketo Measure] sont sélectionnés pour être transférés vers le nouvel enregistrement.

S’il existe plusieurs enregistrements avec des données [!DNL Marketo Measure], assurez-vous que l’enregistrement de Principal comporte les champs sélectionnés pour le prospect qui a été créé en premier. Des données d’[!DNL Marketo Measure] supplémentaires seront présentes dans la section Insights. Assurez-vous également que l’adresse e-mail du prospect suivi correspond à l’adresse e-mail conservée, car elle nous permet de continuer à mettre à jour ce prospect avec toute nouvelle donnée d’attribution.

À partir de là, vous devriez être libre de fusionner les leads et [!DNL Marketo Measure] données seront transférées vers le nouvel enregistrement.

Pour toute question, n’hésitez pas à contacter l’équipe du compte Adobe (votre gestionnaire de compte) ou l’assistance de [Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

La boîte de dialogue Fusionner les leads de Salesforce ![avec les champs Marketo Measure conservés](assets/1.jpg)
