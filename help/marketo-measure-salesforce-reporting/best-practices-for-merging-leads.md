---
description: Conseils sur les bonnes pratiques de fusion des prospects pour les utilisateurs de Marketo Measure
title: Bonnes pratiques relatives à la fusion de leads
exl-id: d9293ed7-a794-4e52-a269-20a7fb36ce50
feature: Tracking
product_v2:
  - id: e6fc4016-a972-4f36-8c30-a6a5f82ad0c8
    internal-label: Marketo Measure
feature_v2:
  - id: dcbeff6e-0253-5a4b-9ac2-1b67cc4a6286
    internal-label: Tracking
source-git-commit: 940fee4abd0e09b6bf513b5e7526d3c242bd31c7
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 7%
---
# Bonnes pratiques relatives à la fusion de leads {#best-practices-for-merging-leads}

Lors de la fusion de prospects dans [!DNL Salesforce], il est toujours préférable de veiller à ne pas perdre de données.

À titre de référence, voici la répartition des [comment fusionner des prospects](https://help.salesforce.com/s/articleView?id=leads_merge.htm&language=en_US&type=5) du support [!DNL Salesforce].

L’[!DNL Marketo Measure] intervient lorsqu’il est temps de sélectionner les champs qui se renseignent sur l’enregistrement fusionné. Lors de la sélection de l’enregistrement de Principal, vérifiez que les champs [!DNL Marketo Measure] sont sélectionnés pour être transférés vers le nouvel enregistrement.

S’il existe plusieurs enregistrements avec des données [!DNL Marketo Measure], assurez-vous que l’enregistrement de Principal comporte les champs sélectionnés pour le prospect qui a été créé en premier. Des données d’[!DNL Marketo Measure] supplémentaires seront présentes dans la section Insights. Assurez-vous également que l’adresse e-mail du prospect suivi correspond à l’adresse e-mail conservée, car elle nous permet de continuer à mettre à jour ce prospect avec toute nouvelle donnée d’attribution.

À partir de là, vous devriez être libre de fusionner les leads et [!DNL Marketo Measure] données seront transférées vers le nouvel enregistrement.

Pour toute question, n’hésitez pas à contacter l’équipe du compte Adobe (votre gestionnaire de compte) ou l’assistance de [Marketo](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

![Si vous avez des questions, n&#39;hésitez pas à contacter le ](assets/additional-functionality-8.jpg)
